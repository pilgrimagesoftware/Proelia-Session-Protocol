Messages
========

Message content is provided via annotations. A minimum of two annotations are enclosed in each message. One annotation (of type "`com.pilgrimagesoftware.proelia.session`" contains the `session ID` and an optional `request ID`. The `session ID` is assigned by the game master client when the channel is created. The `request ID` is the ID of a request from a player or observer client for which the message is a response.

Following is a sample message that would be sent.

	{
		"id": "<msg-id>",
		"channel_id": "<channel-id>",
		"created_at": "<date>",
		"machine_only": true,
		"source": { ... },
		"thread_id": "<thread-id>",
		"user": { ... },
		"annotations": [
			{
				"type": "com.pilgrimagesoftware.proelia.session",
				"value": {
					"session_id": "<session-id>",		
					"request_id": "<request-id>",
					"sequence_number": <sequence-number>
				}
			},
			{
				"type": "com.pilgrimagesoftware.proelia.<type>",
				"value": { <see below> }
			}
		]
	}

Start Session
---

	"type": "com.pilgrimagesoftware.proelia.start_session",
	"value": {
		"assignments": [
			{
				"participant_id": "<participant-id>",
				"user_id": "<user-id>"
			},
			...
		]
	}

Session State
---

	"type": "com.pilgrimagesoftware.proelia.session_state",
	"value": {
		"assignments": [
			{
				"participant_id": "<participant-id>",
				"user_id": "<user-id>"
			},
			...
		]
		"started": "<date>",
		"turn": "<participant-id>"
	}

Add Participant
---

	"type": "com.pilgrimagesoftware.proelia.add_participant",
	"value": {
		"participant_id": "<participant-id>",
		"user_id": "<user-id>",		
		"attributes": {
			"<attribute-name>": "<attribute-value>",
			...
		},
	}

Remove Participant
---

	"type": "com.pilgrimagesoftware.proelia.remove_participant",
	"value": {
		"participant_id": "<participant-id>",
	}

Assign Participant
---

	"type": "com.pilgrimagesoftware.proelia.assign_participant",
	"value": {
		"participant_id": "<participant-id>",
		"user_id": "<user-id>"
	}

Update Map
---

	"type": "com.pilgrimagesoftware.proelia.update_map",
	"value": {
		"action": "<action>",
		"token": {
			"participant_id": "<participant-id>",
			"location": {
				"x": 0.0,
				"y": 0.0,
				"z": 0.0
			}
		},
		"region": {
			"region_id": "<region-id>",
			"location": {
				"x": 0.0,
				"y": 0.0,
				"z": 0.0
			},
			"size": {
				"width": 0.0,
				"height": 0.0,
				"depth": 0.0
			},
			"color": "<rrggbbaa>"
		},
		"tile": {
			"image": "<url>",
			"location": {
				"x": 0.0,
				"y": 0.0
			},
			"scale": 1.0
		}
	}
	
Actions:

* "add_token"
* "move_token"
* "remove_token"
* "add_region"
* "move_region"
* "set_background"
* "add_tile"
* "place_tile"
* "remove_tile"

Participant State
---

	"type": "com.pilgrimagesoftware.proelia.participant_state",
	"value": {
		"participant_id": "<participant-id>",
		"attributes": {
			"<attribute-name>": "<attribute-value>",
			...
		},
		"token_image": "<url>",
		"encounter_state": "<encounter-state>"
	}

Update Participant
---

	"type": "com.pilgrimagesoftware.proelia.update_participant",
	"value": {
		"participant_id": "<participant-id>",
		"attributes": {
			"<attribute-name>": "<attribute-value>",
			...
		},
		"token_image": "<url>",
		"encounter_state": "<encounter-state>"
	}
	
Encounter states:

* "active"
* "removed"

Update Region
---

	"type": "com.pilgrimagesoftware.proelia.update_region",
	"value": {
		"region_id": "<region-id>",
		"location": {
			"x": 0.0,
			"y": 0.0,
			"z": 0.0
		},
		"size": {
			"width": 0.0,
			"height": 0.0,
			"depth": 0.0
		}
		"anchor": {
			"x": 0.0,
			"y": 0.0,
			"z": 0.0
		},
		"color": "<rrggbbaa>"
	}

End Session
---

	"type": "com.pilgrimagesoftware.proelia.end_session",
	"value": {
		"session_id": "<session-id>"
	}

Update Turn
---

	"type": "com.pilgrimagesoftware.proelia.update_turn",
	"value": {
		"participant": "<participant-id>"
	}

Start Encounter
---

	"type": "com.pilgrimagesoftware.proelia.start_encounter",
	"value": {
		
	}

End Encounter
---

	"type": "com.pilgrimagesoftware.proelia.end_encounter",
	"value": {
		
	}

Map State
---

	"type": "com.pilgrimagesoftware.proelia.map_state",
	"value": {
		"segment": {
			"current": 1,
			"total": 1
		}
		"background": {
			"image": "<url>",
			"scale": 1.0
		},
		"flags": {
			"show_grid": true,
			"show_background": true,
			"show_removed": false,
			"show_conditions": true,
			"show_borders": true
		},
		"grid": {
			"width": 20,
			"height": 20,
			"line_style": "<style>",
			"line_color": "<rrggbbaa>",
			"line_thickness": 1.0,
			"line_x_offset": 0.0,
			"line_y_offset": 0.0,
			"side_length": 10
		},
		"participants": [
			{
				"participant_id": "<participant-id>",
				"location": {
					"x": 0.0,
					"y": 0.0,
					"z": 0.0
				}
				"color": "<rrggbbaa>",
				"marker": "<marker>",
				"type": "<type>",
				"tag": "<tag>",
				"size": 1,
				"name": "<name>",
				"image": "<url>"
			},
			...
		],
		"regions": [
			{
				"region_id": "<region-id>",
				"name": "<name>",
				"color": "<rrggbbaa>",
				"location": {
					"x": 0.0,
					"y": 0.0,
					"z": 0.0
				},
				"size": {
					"width": 0.0,
					"height": 0.0,
					"depth": 0.0
				}
			},
			...
		],
		"tiles": [
			{
				"image": "<url>",
				"location": {
					"x": 0.0,
					"y": 0.0
				},
				"scale": 1.0
			},
			...
		]
	}

*Segment*: If the map state data is too large to fit into the annotations dictionary in an ADN message (8K is the maximum size as of this writing), then the data will be divided into segments and sent over multiple state messages. The `segment` object will indicate which segment this message contains, and how many total segments should be expected.

*Line styles*: The following line style values are defined: `solid`, `dashed`, `dotted`

