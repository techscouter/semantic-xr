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
* For example a computer screen or a cinema screen inside VR or photographs or TV shows in passthrough mode which are Semantic-XR entities by themselves (advanced usage of this could be used for reflections and/or views behind transparent surfaces).

## crossSemanticXrEquality examples
This single field opens up a lot of opportunities, such as conveying equality of entities in space and time. For example:

### Live Broadcast
In this case, there is the event and the live TV broadcast shown on two specific TV sets that are all synced in time. Note the absence of realityInstanceTimestamp (time is the same in all 3 realities) and the absence of semanticSpatialEntityId (entities are the same in all realities).

        "crossSemanticXrEquality":
        [
            [
                {
                    "realityType" : "Opening Ceremony",
                    "realityInstanceId : "2045",
                },
                {
                    "realityType": "TV Broadcast",
                    "realityInstanceId": "Opening Ceremony @ 2045 | TV Set 1"
                },
                {
                    "realityType": "TV Broadcast",
                    "realityInstanceId": "Opening Ceremony @ 2045 | TV Set 2"
                }
            ]
        ]

### Slow Motion Video
In this case, we have a game that is played, a movie of the game at regular speed and a slow motion version at half the speed playing somewhere else. Note the different values for realityInstanceTimestamp for the slow motion movie clip and the absence of semanticSpatialEntityId in all elements (as they are equal for all)

        "crossSemanticXrEquality":
        [
            [
                {
                    "realityType": "DemoGameCubes",
                    "realityInstanceId": "WorldChampionshipApril2022",
                    "realityInstanceTimestamp": 0
                },
                {
                    "realityType": "MovieClip",
                    "realityInstanceId": "DemoGameCubes|WorldChampionshipApril2022|9kuh76ygtfr543ed",
                    "realityInstanceTimestamp": 0
                },
                {
                    "realityType": "MovieClip",
                    "realityInstanceId": "DemoGameCubes|WorldChampionshipApril2022|SlowMotion|0poli6tgfredvb5t",
                    "realityInstanceTimestamp": 0
                }
            ],
            [
                {
                    "realityType": "DemoGameCubes",
                    "realityInstanceId": "WorldChampionshipApril2022",
                    "realityInstanceTimestamp": 1
                },
                {
                    "realityType": "MovieClip",
                    "realityInstanceId": "DemoGameCubes|WorldChampionshipApril2022|9kuh76ygtfr543ed",
                    "realityInstanceTimestamp": 1
                },
                {
                    "realityType": "MovieClip",
                    "realityInstanceId": "DemoGameCubes|WorldChampionshipApril2022|SlowMotion|0poli6tgfredvb5t",
                    "realityInstanceTimestamp": 2
                }
            ],
            [
                {
                    "realityType": "DemoGameCubes",
                    "realityInstanceId": "WorldChampionshipApril2022",
                    "realityInstanceTimestamp": 2
                },
                {
                    "realityType": "MovieClip",
                    "realityInstanceId": "DemoGameCubes|WorldChampionshipApril2022|9kuh76ygtfr543ed",
                    "realityInstanceTimestamp": 2
                },
                {
                    "realityType": "MovieClip",
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
                "realityType": "DemoGameCubesMultiplayer",
                "realityInstanceId": "DemoGameCubesMultiplayer|6hdkil9uejdoek3o|Server"
            },
            {
                "realityType": "DemoGameCubesMultiplayer",
                "realityInstanceId": "DemoGameCubesMultiplayer|6hdkil9uejdoek3o|Player1"
            },
            {
                "realityType": "DemoGameCubesMultiplayer",
                "realityInstanceId": "DemoGameCubesMultiplayer|6hdkil9uejdoek3o|Player2"
            },
        ]

### Game streaming on a slow internet connection
Note the 2 seconds delay between the server and the game played by player 3.

        "crossSemanticXrEquality":
        [
            {
                "realityType": "DemoGameCubesMultiplayer",
                "realityInstanceId": "DemoGameCubesMultiplayer|6hdkil9uejdoek3o|Server",
                "realityInstanceTimestamp": 20

            },
            {
                "realityType": "DemoGameCubesMultiplayer",
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
                    "realityType": "Movie",
                    "realityInstanceId": "TimeTravelMovie1"
                    "realityInstanceTimestamp" : 1988-12-18
                    "semanticSpatialEntityId" : "Human1"
                },
                {
                    "realityType" : "RealityUnderlyingMovie",
                    "realityInstanceId" : "TimeTravelMovie1"
                    "realityInstanceTimestamp" : 1995-12-20
                    "semanticSpatialEntityId" : "Human1"
                }
            ],
            [
                {
                    "realityType": "Movie",
                    "realityInstanceId": "TimeTravelMovie1"
                    "realityInstanceTimestamp" : 1988-12-19
                    "semanticSpatialEntityId" : "Human1"
                },
                {
                    "realityType" : "RealityUnderlyingMovie",
                    "realityInstanceId" : "TimeTravelMovie1"
                    "realityInstanceTimestamp" : 1975-12-20
                    "semanticSpatialEntityId" : "Human1"
                }
            ]
        ]
        
### Non-Fungible Tokens (NFTs)
Same portrait NFT image that serves as an avatar in a certain virtual world while serving as a background image in a different virtual world.

        "crossSemanticXrEquality":
        [
            {
                "realityType": "Virtual World",
                "realityInstanceId": "Application1|9lkjurfbhgft56y7"
                "semanticSpatialEntityId" : "Avatar|XYZ"
            },
            {
                "realityType" : "Virtual World",
                "realityInstanceId" : "Application2|9kjh64gtrfdesxcs"
                "semanticSpatialEntityId" : "BackgroundImage|ABC"
            },
            {
                "realityType" : "NFT inventory",
                "realityInstanceId" : "Company1",
                "semanticSpatialEntityId" : "NFT|123456"
            }
        ]

### Exercise for the reader (1)
Representing different physics and philosophical theories of the world using Semantic-XR.

### Exercise for the reader (2)
See message of commit `cd4e2e34f2a061f0436678211cb4375ca4276d96` in this repository for more examples.