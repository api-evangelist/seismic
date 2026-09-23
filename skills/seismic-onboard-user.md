---
name: seismic-onboard-user
description: Create a Seismic user, assign role and team, and place them into the right groups — with the duplicate-write hazards called out.
api: Seismic Users API
base_url: https://api.seismic.com/integration/v2
operations:
  - listRoles
  - listTeams
  - listUsers
  - createUser
  - getUser
  - updateUser
  - listGroups
  - setUserGroups
  - getUserGroups
  - addGroupMember
  - listGroupMembers
scopes:
  - seismic.user.view
  - seismic.user.manage
  - seismic.configuration.view
---

# Onboard a Seismic user

## Before you start

- This flow performs **irreversible writes with no idempotency key**. `createUser` returns `409` if
  the user already exists — that `409` is your only replay protection, so always search first.
- Seismic also exposes a SCIM 2.0 surface at `https://api.seismic.com/scim/v2`. If the tenant
  provisions from an IdP, create the user there instead; creating the same person through both
  paths produces a conflict the integration API will not resolve for you.

## Steps

1. **Check for an existing user.** `listUsers` (`GET /users`) filtered to the target email. If a
   match exists, switch to `updateUser` and skip step 3.
2. **Resolve role and team ids.** `listRoles` (`GET /roles`) and `listTeams` (`GET /teams`). `User`
   carries `roleId` and `teamId` as opaque strings — there is no name-based assignment.
3. **Create.** `createUser` (`POST /users`) with `email`, `firstName`, `lastName`, `roleId`,
   `teamId`. Expect `201`. A `409` means the account already exists: fall back to step 1.
4. **Assign groups.** Either `setUserGroups` (`PUT /users/{userId}/groups`) to set the whole
   membership set at once, or `addGroupMember` (`POST /groups/{groupId}/members`) per group.
   Prefer `setUserGroups` — `PUT` is naturally idempotent here, while repeated `addGroupMember`
   calls return `409`.
5. **Verify.** `getUser` (`GET /users/{userId}`) and `getUserGroups`
   (`GET /users/{userId}/groups`). Do not trust the write response alone as proof of final state.

## Reversal

`deleteUser` (`DELETE /users/{userId}`) returns `204`. **Seismic documents no undelete and no
retention window** for users or groups. `updateUser` to a disabled `status` is the reversible
alternative; prefer it whenever the intent is "deactivate" rather than "erase".

## Events

`UserCreatedV1`, `UserUpdatedV1`, `UserDeletedV1` and `UserGroupMemberChangeV1` are published as
webhooks — subscribe rather than polling. See `asyncapi/seismic-webhooks.yml`.

## Rate limits

Tier 3 (600 calls per minute per tenant). A bulk onboarding loop will hit that ceiling at scale;
batch and pace accordingly.
