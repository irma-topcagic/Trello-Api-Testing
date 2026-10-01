## Trello API - Execution Schedule

This document defines the order in which API requests must be executed, based on their dependencies, along with the follow-up "Get" check performed after each action.

### Dependencies

| Request | Depends on |
|---|---|
| Create Board | – |
| Create List | Create Board |
| Create Card | Create List |
| Update Board, Delete Board | Create Board |
| Update List, Archive List | Create List |
| Update Card, Delete Card | Create Card |

### Execution order

| # | Request | Follow-up check | Expected result |
|---|---|---|---|
| 1 | Create Board | Get Created Board | Board exists with the generated name |
| 2 | Create List | Get Created List | List is on the created board |
| 3 | Create Card | Get Created Card | Card is in the created list |
| 4 | Update Board | Get Updated Board | Board has the new name |
| 5 | Update List | Get Updated List | List has the new name |
| 6 | Update Card | Get Updated Card | Card has the new name |
| 7 | Delete Card | Get Deleted Card | 404 Not Found |
| 8 | Archive List | Get Archived List | List is closed |
| 9 | Delete Board | Get Deleted Board | 404 Not Found |
| 10 | Get Board With Invalid Token | – | 401 Unauthorized |

