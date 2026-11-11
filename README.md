# Carribu Developer Workbook

Onboarding, engineering practice and ownership-transfer documentation for Carribu's full-stack and native-mobile teams.

## Start here

Read [Carribu: Team Handover, Onboarding and Six-Month Development Plan](CARRIBU-HANDOVER-AND-ONBOARDING.md).

Use the [Developer Playbook](DEVELOPER-PLAYBOOK.md) for proposed daily contribution rules: branch and commit naming, PR reviews, squash merges, code conventions, testing, security, releases and incidents. Its Git workflow uses short-lived branches into `main`. Engineering-owner approval and repository configuration are still required; this document does not activate GitHub protections.

| Section | Contents |
|---|---|
| [Full-stack team plan](CARRIBU-HANDOVER-AND-ONBOARDING.md#part-a-full-stack-team-plan) | Backend, admin, super-admin, technical foundations, onboarding, tests and release readiness |
| [Native-mobile team plan](CARRIBU-HANDOVER-AND-ONBOARDING.md#part-b-native-mobile-team-plan) | Driver and parent Android apps, Kotlin/Compose foundations, device behavior, testing and signing |
| [Shared engineering standards](CARRIBU-HANDOVER-AND-ONBOARDING.md#part-c-shared-engineering-and-operational-standards) | TDD, Carribu domain rules, mentoring, API coordination, access and incident exercises |
| [Templates and acceptance](CARRIBU-HANDOVER-AND-ONBOARDING.md#part-d-reusable-templates-and-acceptance) | Work items, PRs, readiness scorecards, monthly reviews, releases and final handover |

The reference programme covers **November 2026-April 2027**. Adjust its dates and learning pace to the agreed team start date and demonstrated skills.

## Repository scope

This repository stores documentation, not application source code. Paths and commands in the guide refer to the separate Carribu application repositories in the developer workspace; they are not subdirectories of this workbook.

Repository-specific observations were recorded on November 1, 2026. Check each application's current README, manifests and build configuration before using its commands.

## Maintaining the workbook

Update the relevant plan when architecture, contracts, setup or release procedures change. Review the programme monthly during onboarding, and keep owners, prerequisites and acceptance evidence explicit.

The plans are proposed guidance, not confirmation that production access, CI, deployment controls or signing arrangements have been configured.

Never commit credentials, signing keys, service-account files, device tokens, or real student/guardian data to this repository.
