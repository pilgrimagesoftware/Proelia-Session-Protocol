Sample "Conversation"
===================

This document demonstrates the "conversation" between multiple Proelia apps over an ADN message channel in setting up and running a game session.

The participants in this conversation are as follows:

* *Game Master*: User 1199
* *Player 1*: User 1234
* *Player 2*: User 2345
* *Player 3*: User 3456
* *Observer*: User 7848

Some notes regarding the progress of this conversation:

* *Player 1* and *Player 2* are part of the game session when it is created.
* *Player 3* joins the session in-progress by submitting a request to the *Game Master*.
* *Observer* joins the session in-progress by submitting a request to the *Game Master*, at which point the channel's `readers` ACL is modified and a broadcast is sent notifying the players that an observer has joined.

**Game Master**

* *Create channel for game session*: When the channel is created, the `readers` and `writers` ACLs are set to be mutable, so that the game master may update who may participate in or observe the game session.

	{
		"annotations": [
			{
				"type": "com.pilgrimagesoftware.proelia.session",
				"value": {
					"name": "Sample session",
					"started": "2012-12-31T23:59:59Z",
					"system": "dndnext",
					"session_id": "1234567"
				}
			},
			...
		],
		"readers": {
			"any_user": true,
			"immutable": false,
		},
		"type": "com.pilgrimagesoftware.proelia.session",
		"writers": {
			"immutable": false,
			"user_ids": [
				"1199",
				"1234",
				"2345"
			],
		},		
	}

* *Send broadcast message about game session*

	{
		"session_id": "<uuid>",
		"type": "start_session"
	}

**Player 1**

**Player 2**

**Player 3**

**Observer**

