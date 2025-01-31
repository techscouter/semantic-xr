# Semantic-XR Examples
## 3D Game
* [Static Images from a game with matching Semantic-XR](DemoGameCubes/DemoGameCubesREADME.md)
* [Real Time 3D Game (video)](https://youtu.be/UIonbA-7YUM)
* [Video of a Real Time 3D game (video)](https://youtu.be/Q7JY3w7StHo)

## Movie
* [Movie](https://youtu.be/gh0vJOWk5EY) : depthMap image used for highlighting objects in a video and an image.
* Movie can be represented in Semantic-XR format by having no realityInstanceId and no realityInstanceTimestamp in the highest level semanticXr element. Child Semantic-XR entities do have timestamp and they represent frames in the movie. Virtual production methods using a game engine based Semantic-XR library could enable auto-generation of movie semantic descriptions. This could apply as well to animations. BTW, this opens up the possibility of "invisible movies" - movies that exist as text-only in a Semantic-XR format. Another possibility is annotating old movies with Semantic-XR metadata to make them more accessible.

## Real World
* [Audio-based AR (video).](https://youtu.be/Lsri6037iIE) This example uses AI (object recognition cloud service) in contrast to other examples which use a game engine library to generate the Semantic-XR content.

## Composite Semantic-XR
* For example a computer screen or a cinema screen inside a VR experience or photographs or TV shows in passthrough mode which are Semantic-XR entities by themselves (advanced usage of this could be used for reflections and\ or views behind transparent surfaces).

## crossSemanticXrEquality examples
This single field opens up a lot of opportunities, such as conveying equality of entities in space and time. For example:

### Live Broadcast
In this case, there is the event and the live TV broadcast shown on two specific TV sets that are all synced in time. Note the absence of realityInstanceTimestamp (time is the same in all 3 realities) and the absence of semanticSpatialEntityId (entities are the same in all realities).

        "crossSemanticXrEquality":
        [
            [
                {
                    "realityId" : "University XYZ Graduation Ceremony",
                    "realityInstanceId : "2045",
                },
                {
                    "realityId": "TV Broadcast",
                    "realityInstanceId": "University XYZ Graduation Ceremony @ 2045 | TV Set 1"
                },
                {
                    "realityId": "TV Broadcast",
                    "realityInstanceId": "University XYZ Graduation Ceremony @ 2045 | TV Set 2"
                }
            ]
        ]

### Slow Motion Video
In this case, we have a game that is played, a movie of the game at regular speed and a slow motion version at half the speed playing somewhere else. Note the different values for realityInstanceTimestamp for the slow motion movie clip and the absence of semanticSpatialEntityId in all elements (as they are equal for all).

        "crossSemanticXrEquality":
        [
            [
                {
                    "realityId": "DemoGameCubes",
                    "realityInstanceId": "WorldChampionshipApril2022",
                    "realityInstanceTimestamp": 0
                },
                {
                    "realityId": "MovieClip",
                    "realityInstanceId": "DemoGameCubes|WorldChampionshipApril2022|9kuh76ygtfr543ed",
                    "realityInstanceTimestamp": 0
                },
                {
                    "realityId": "MovieClip",
                    "realityInstanceId": "DemoGameCubes|WorldChampionshipApril2022|SlowMotion|0poli6tgfredvb5t",
                    "realityInstanceTimestamp": 0
                }
            ],
            [
                {
                    "realityId": "DemoGameCubes",
                    "realityInstanceId": "WorldChampionshipApril2022",
                    "realityInstanceTimestamp": 1
                },
                {
                    "realityId": "MovieClip",
                    "realityInstanceId": "DemoGameCubes|WorldChampionshipApril2022|9kuh76ygtfr543ed",
                    "realityInstanceTimestamp": 1
                },
                {
                    "realityId": "MovieClip",
                    "realityInstanceId": "DemoGameCubes|WorldChampionshipApril2022|SlowMotion|0poli6tgfredvb5t",
                    "realityInstanceTimestamp": 2
                }
            ],
            [
                {
                    "realityId": "DemoGameCubes",
                    "realityInstanceId": "WorldChampionshipApril2022",
                    "realityInstanceTimestamp": 2
                },
                {
                    "realityId": "MovieClip",
                    "realityInstanceId": "DemoGameCubes|WorldChampionshipApril2022|9kuh76ygtfr543ed",
                    "realityInstanceTimestamp": 2
                },
                {
                    "realityId": "MovieClip",
                    "realityInstanceId": "DemoGameCubes|WorldChampionshipApril2022|SlowMotion|0poli6tgfredvb5t",
                    "realityInstanceTimestamp": 4
                }
            ],
        ]

### Multi-player game
Different players share the same game entities at more or less the same time. Note the absence of realityInstanceTimestamp (as they are more or less equal for all) and the absence of semanticSpatialEntityId (as they are equal for all).
  
        "crossSemanticXrEquality":
        [
            {
                "realityId": "DemoGameCubesMultiplayer",
                "realityInstanceId": "DemoGameCubesMultiplayer|6hdkil9uejdoek3o|Server"
            },
            {
                "realityId": "DemoGameCubesMultiplayer",
                "realityInstanceId": "DemoGameCubesMultiplayer|6hdkil9uejdoek3o|Player1"
            },
            {
                "realityId": "DemoGameCubesMultiplayer",
                "realityInstanceId": "DemoGameCubesMultiplayer|6hdkil9uejdoek3o|Player2"
            },
        ]

### Game streaming on a slow internet connection
Note the 2 seconds delay between the server and the game played by player 3.

        "crossSemanticXrEquality":
        [
            {
                "realityId": "DemoGameCubesMultiplayer",
                "realityInstanceId": "DemoGameCubesMultiplayer|6hdkil9uejdoek3o|Server",
                "realityInstanceTimestamp": 20

            },
            {
                "realityId": "DemoGameCubesMultiplayer",
                "realityInstanceId": "DemoGameCubesMultiplayer|6hdkil9uejdoek3o|Player3",
                "realityInstanceTimestamp": 22
            }
        ]

### Time travel in a movie
A character (Human1) that appears throughout a movie (TimeTravelMovie1) and appears in the reality underlying that movie at two points in time, 20 years apart. Time units is days. The section below means that December 18 is being spent in 1995 and December 19 is being spent in 1975.

        "crossSemanticXrEquality":
        [
            [
                {
                    "realityId": "Movie",
                    "realityInstanceId": "TimeTravelMovie1",
                    "realityInstanceTimestamp" : "1988-12-18",
                    "semanticSpatialEntityId" : "Human1"
                },
                {
                    "realityId" : "RealityUnderlyingMovie",
                    "realityInstanceId" : "TimeTravelMovie1",
                    "realityInstanceTimestamp" : "1995-12-20",
                    "semanticSpatialEntityId" : "Human1"
                }
            ],
            [
                {
                    "realityId": "Movie",
                    "realityInstanceId": "TimeTravelMovie1"
                    "realityInstanceTimestamp" : "1988-12-19",
                    "semanticSpatialEntityId" : "Human1"
                },
                {
                    "realityId" : "RealityUnderlyingMovie",
                    "realityInstanceId" : "TimeTravelMovie1",
                    "realityInstanceTimestamp" : "1975-12-20",
                    "semanticSpatialEntityId" : "Human1"
                }
            ]
        ]
        
### Shared Entities and optional Non-Fungible Tokens (NFTs)
An example of a portrait image that serves as an avatar in a certain virtual world while serving as a background image in a different virtual world.

        "crossSemanticXrEquality":
        [
            {
                "realityId": "Virtual World 1",
                "realityInstanceId": "Application1|9lkjurfbhgft56y7",
                "semanticSpatialEntityId" : "Avatar|XYZ"
            },
            {
                "realityId" : "Virtual World 2",
                "realityInstanceId" : "Application2|7kjh64gtrfdesxcs",
                "semanticSpatialEntityId" : "BackgroundImage|ABC"
            },
            {
                "realityId" : "NFT inventory",
                "realityInstanceId" : "Company1",
                "semanticSpatialEntityId" : "NFT|123456"
            }
        ]

### Portals
Tracking a character that moved between two virtual worlds. In the example below "Character|12345" moved after one hour (3600 seconds) from one virtual world (one reality instance) to a second virtual world (second reality instance) where it got the id "Character|ABCDE". In the internal clock of the second reality instance the movement was 2 minutes (120) after its beginning. The moving character stayed in the second reality instance until it ended.

        "crossSemanticXrEquality":
        [
            {
                "realityId": "Virtual World 1",
                "realityInstanceId": "Application1|9lkjurfbhgft56y7",
                "realityInstanceTimestamp": "-3600",
                "semanticSpatialEntityId" : "Character|12345"
            },
            {
                "realityId" : "Virtual World 2",
                "realityInstanceId" : "Application2|7kjh64gtrfdesxcs",
                "realityInstanceTimestamp": "120-",
                "semanticSpatialEntityId" : "Character|ABCDE"
            }
        ]

`crossSemanticXrEquality` field can also be used to describe portals between multiple realities. For example the following field describes a portal that connect two reality instances:

        "crossSemanticXrEquality":
        [
            {
                "realityId": "Virtual World 1",
                "realityInstanceId": "Application1|9lkjurfbhgft56y7",
                "semanticSpatialEntityId" : "Portal|9876"
            },
            {
                "realityId" : "Virtual World 2",
                "realityInstanceId" : "Application2|7kjh64gtrfdesxcs",
                "semanticSpatialEntityId" : "Portal|KJIH"
            }
        ]



### Calibration
An example of that would be calibrating between the real world and an Augmented Reality Experience by describing the identity of marker entities using crossSemanticXrEquality.

### Exercise for the reader :smiley: (1)
Representing different physics and philosophical theories of the world using Semantic-XR.

### Exercise for the reader :smiley: (2)
See message of commit `cd4e2e34f2a061f0436678211cb4375ca4276d96` in this repository for more examples.