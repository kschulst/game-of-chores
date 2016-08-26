# Game of Chores
Cynical use of gamification to magically transform your lazy kids into home makers

## Models

#### Game
A game represents the "chore universe". All game universes are separate.

```JSON
{
    "id": "G123",
    "name": "Linerleveien 18"
}
```

#### GameMaster
Game masters are the ones administering the game and defining the rules such as rewards, etc. Game masters can create chores, achievements, rewards, etc. In a typical family game of chores, the game master(s) will be the parents (and the children will be the players).

_Abilities:_
* Administer players
* Administer chores
* Administer achievements
* Administer rewards
* Approve chores

```JSON
{
    "id": "GM123",
    "name": "Pappa",
    "game": "G123"
}
```

#### Player
A player can perform chores and earn rewards and achievements. In a family setting, this will typically be the kids.

_Abilities:_
* See upcoming (e.g. today's chores)
* Mark chore as done. This can be as easy as ticking off the chore. Version 2: Option to attach image evidence that the chore is done. This could be sent as push message to the game master(s) along with a request for approval.
* Be notified of missed chores - and its consequences ;-)
* Administer chore notifications
* "Cash in" on rewards 

```JSON
{
    "id": "P123",
    "game": "G123",
    "name": "Jonathan"
    "score": {
        "R1": 1000,
        "R123": 123
    },
    "chores": [
        {
            "id": "C123",
            "doneTimestamp": "2015-07-14T10:08:15Z",
        }
    ],
    "achievements": ["", "", ""]
}
```

#### Chore
A "doable", something that can trigger a reward if done.

```JSON
{
    "id": "C123",
    "name": "Re opp sengen din",
    "description": "",
    "image": "...base64encoded...",
    "requireApprovalByGM": "true",
    "rewards": [
        {
            "reward": "R123",
            "quantity": "10"
        }
    ]
}
```

#### Reward
An "earnable", this can be whatever, but all games should have at least one kind of currency.
As the players earns rewards they will level up and receive Achievements. Advanced feature to be discussed: 
They will gradually become more proficient in the chores types they do the most. This could result in a number
of events:

* Fame beyond the chore universe (World Champion Bed Maker)
* Development of primary skills (such as discipline, promptness, strive)

```JSON
{
    "id": "R1",
    "name": "XP",
    "description": "Experience points",
    "image": "...base64encoded...",
},
{
    "id": "R123",
    "name": "Skylanderpoeng",
    "description": "1 SP == 10 NOK",
    "image": "...base64encoded...",
}
```

#### Achievement
To further add on to the gamification frenzy, achievements can be triggered by completing some kind of criteria, such as completing a specific chores n times for consective days (Re opp senga 10 dager på rad).
An achievement can be either public or secret. Players will be able to browse (and strive/plan for) their publicly available achivements. The secret achievements will come more as surprises. The idea here is that this will add a kind of mystery element to the game.

```JSON
{
    "id": "A123",
    "name": "Re opp sengen 10 dager i strekk",
    "description": "Du har redd opp sengen din 10 ganger på rad!",
    "image": "...base64encoded...",
    "criteria": "choreX x 10",
    "rewards": [
        {
            "rewardType": "PO123",
            "quantity": "10"
        }
    ]
}
```

