Requests
========

Requests are messages that are sent from a player or observer client that want to interact with the game session. Requests are simply that, requests for a change in the game session state. Any changes that a client submits via request cannot be assumed to have taken effect; the game master must publish changes via a session message. If one or more session messages are published as a result of a request, the originating request's `requestId` will be included in the message (for reference).

Join Game
---------

Submit Move
-----------

Update Character
----------------

