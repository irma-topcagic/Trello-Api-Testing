# Trello API - Execution Schedule

This document defines the order in which API requests must be executed, based on their dependencies, along with the follow-up "Get" check performed after each action.

## Requests, Dependencies and Order

| Requests | Dependency | Order |
|---|---|---|
| Create Board | None | Create Board |
| Update Board | Create Board | Create List |
| Get Board | Create Board | Create Card |
| Delete Board | Create Board | Update Board |
| Create List | Create Board | Get Board |
| Update List | Create List | Update List |
| Get List | Create List | Get List |
| Delete List | Create List | Update Card |
| Create Card | Create List | Get Card |
| Update Card | Create Card | Delete Card |
| Get Card | Create Card | Delete List |
| Delete Card | Create Card | Delete Board |

## Order After Checks

1. Create Board -> Get Board
2. Create List -> Get List
3. Create Card -> Get Card
4. Update Board -> Get Board
5. Update List -> Get List
6. Update Card -> Get Card
7. Delete Card -> Get Card
8. Delete List -> Get List
9. Delete Board -> Get Board
