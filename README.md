## Trello API Testing

API tests for the Trello REST API, written in Postman.

### What is tested

The collection runs as one end-to-end scenario. Every action is followed by a GET request that checks whether the change was really saved:

1. Create a board, a list on it and a card in the list
2. Update the board, the list and the card
3. Delete the card and check that it returns 404
4. Archive the list and check that it is closed (Trello doesn't allow deleting lists, only archiving them)
5. Delete the board and check that it returns 404
6. Request a board with an invalid token and check that it returns 401

The order and dependencies between requests are described in [execution-schedule.md](trello/execution-schedule.md).

### How the tests work

The ids of created resources are saved to environment variables and used in the next requests, so the whole flow runs on its own data.

Names are generated randomly in pre-request scripts, so the collection can be run many times without conflicts.

Besides the status code, the tests check the response body: that ids have the correct format, that a list belongs to the right board and a card to the right list, and that GET requests return the same data that was created or updated.

Status code and response time are checked once at the collection level. Requests that are expected to return 404 or 401 are excluded from the status check.

The board is deleted at the end, which also removes everything on it, so the run doesn't leave test data behind.

### How to run

1. Import the collection and the environment from the `trello` folder into Postman.
2. Add your own Trello API key and token to the environment.
3. Run the collection with the Collection Runner.

API key and token are not included in the repository.

### Tools

Postman, JavaScript (Postman test scripts)
