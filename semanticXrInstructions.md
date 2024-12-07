# Semantic-XR Instructions
This section includes explanations for the fields of the semantic format. Examples for values for some of the fields can be found in the documents in the Examples folder. The fields are mostly optional. Note that some of the definitions are a bit loose - this is both part of the early stage and research phase of this format and both for enabling creative uses for its users.

## Semantic XR fields' explanations

* `semanticXr`: a description of an XR experience as meaningful and well-defined data in order to make it more accessible. The root element of the file.

* `schemaVersion` : a specific version of the semantic format template JSON that the document follows. If you clone this repository and make changes, please add a prefix namespace unique to you to avoid version confusion.

* `id` : a section that identifies the point in time in a specific reality that this Semantic-XR data represents. Note that realityInstanceId and realityInstanceTimestamp are optional which opens up a lot of opportunities to represent composite realities.
  * `realityId` : a type of reality, like a name of a video game or a name of a movie.
  * `realityInstanceId` : id for a specific instance of the reality mentioned above. For example a specific game played at a specific time and place or a specific screening of a movie.
  * `realityInstanceTimestamp` : a timestamp within the specific reality instance mentioned above. If the game or movie is paused for example, then this timestamp is paused as well.
  
* `units` : the units used in the file (note that the values in this file should be decimal and not float in order to represent exact values and enable many orders of magnitude of difference between values in the file while keeping accuracy).
  * `time` : which units of time are used in the file, for example for realityInstanceTimestamp.
  * `space` : which units of distance are used in the file, for example for pointsOfCollisionPrediction.collisionsPrediction.distance.
  * `language` : which natural language is being used in the file, for example for descriptions and instructions.

* `descriptions` : short descriptions of different aspects of the reality's 3D scene
  * `reality` : description of the reality type (game, movie etc.)
  * `scene` : description of the scene in general at id.realityInstanceTimestamp point in time.
  * `frame` : description of the very specific frame that is shown at id.realityInstanceTimestamp point in time.
  
* `Instructions`
  * `reality` : for example, a summary of how to play the game.
  * `scene` : for example, what should be done in a specific game scene.
  * `frame` : instructions for a specific point in time within the reality.

  * `accessibility` : accessibility related information. The list below is partial and very generic and should serve as a starting point for a better list in the future.
    * `general` : general accessibility information. For example, pointer to an accessibility document for the game.
    * `vision` : accessibility information for people who are blind or have low vision. For example, how to enable internal text to speech engine.
    * `hearing` : accessibility information for people who are deaf or hard of hearing. For example, how to enable captions.
    * `motor` : for example information about options for remapping of controls.
    * `speech` : for example a list of input methods not requiring speech.
    * `cognitive`: for example how to access the instructions and descriptions.

* `semanticSpatialEntities` : the main list of semantic spatial entities with their properties.
  * `semanticSpatialEntityId` : an id that uniquely identifies this entity in this reality.
    * `name` : natural language name of this entity.
    * `description` : short natural language description of this entity.
    * `instructions` : instructions for this entity (for example, for operating it or interacting with it).
    * `physical` : physical properties of this entity.
      * `location` : location of the entity. All entities' locations should be in the same coordinate system.
        * `x`, `y`, `z` : location of the entity across the different axis. <TBD>
      * `rotation` : rotation of the entity.
        * `pitch`, `yaw`, `roll` : rotation parameters of the entity.
    * `colors` : one or more colors ordered by dominance in the entity.
    * `materials` : natural language descriptions of the materials the entity is made of, one or more materials ordered by dominance in the entity.
    * `volume` : exact or approximate (for example, bounding box) volume
    * `form` : exact or approximate (for example, bounding box) form
    * `actions` : natural language descriptions of the actions of the entity (like: running or talking), one or more in order of importance.
    * `categoriesAndAttributes` : array of categories and their attributes which describe the entity.
      * `category`: non comprehensive list of examples for categories of entities: landscape, landscapeArchitecture, architecture, internalDesign, prop, livingEntity, player, light, camera, controller, pointOfView, hitPoint, effect, music, text, table, chair, semanticXr etc. Note that the option to have semanticXr as a nested semanticSpatialEntity is extremely powerful (for usage examples see the Examples folder)
      * `attributes`: attributes and their values within the specific category. For example: for category 'text' the attributes could include the actual text in different languages. The value of the attributes field could include nested fields/arrays itself.

* `pointsOfView` : points in space from which view-based data is generated.
  * `semanticSpatialEntityId` : the pointOfView itself is a semanticSpatialEntity with location, rotation etc.
  * `source` : semanticSpatialEntityId of the entity which is the source of this pointOfView (for example the player, a camera, a controller, an eye etc.).
  * `visibleSemanticSpatialEntities` : array of all semantic spatial entities that are visible from this point of view.
    * `semanticSpatialEntityId`
	* `projectedSemanticSpatialEntityCenter` : properties of the center point of the semantic spatial entity.
	  * `location` : the coordinates of the projection of the semantic spatial entity on this point of view.
        * `horizontalFraction` : fraction of width (0=left, 0.5=middle, 1=right).
        * `verticalFraction` : fraction of height (0=top, 0.5=middle height, 1=bottom).
      * `distance` : distance from this point of view in space units.
  * `visualHitPoint` : semanticSpatialEntityId of the extrapolated hit point of this pointOfView with the 3D space in front of it. For example, a controller-based point of view's hit point id would enable using it as a laser pointer and have it read aloud text, name of pointed entity, distance to an entity etc.
  * `images` : optional images generated from this point of view. As this is a JSON file there is a need to do BASE64 encoding of the data and **verify** the data source for security reasons. Data URLs might be useful here with their pros and cons. Note that images can be for example 360 degrees images or be in other kinds of shapes, types of data and formats. Example types of images:
    * value of type "image": regular RGB image of the frame.
    * value of type "depthMap" : depth map.
    * value of type "instanceSegmentation" : instance segmentation - each instance is identified by its semanticSpatialEntityId.
    * value of type "semanticSegmentation" : semantic segmentation - ordered categories are taken from the category properties of the instance (see "instanceSegmentation").
    * value of type "preProcessedImage" : RGB image before applying any effects like blur etc. which could be problematic from an accessibility perspective.
    * value of type "realityTypeImage" : marking each area of the frame with the type of reality it represenets - real world, VR, passthrough etc.
    * value of type "edges" : identifying the edges of the entities.
    * value of type "normals" : identifying the "normal" values for the frame.
  
    image's `legend` maps color values to an array of values that are relevant for the specific image type (`"legend":{color:[], color:[], color:[], …}`). For example it could map an image color to to semanticSpatialEntityId in case of instanceSegmentation or to ordered category values in case of semanticSegmentation or to depth value in case of depthMap.

    image’s `lens` describes characteristics of the generator of the image content (for example camera settings used for an image). It would be useful in the future to define a common terminology of lens' fields that would be part of the Semantic-XR format.

    The images' color depth should be sufficient to represent the expected number of colors needed (for example the number of semanticSpatialEntityIds in case of instanceSegmentation).

    Note: in case of two eyes' inputs for example in VR or glasses-based AR that would require pairs of images - one for each eye - this could be achieved using the existing support for multiple points of view (they would just be associated with the same player - left eye and right eye).

    In the future new types of images can be added, for example: semanticLevelOfDetail etc.
* `pointsOfCollisionPrediction` : points in space from which collision prediction data is generated.
  * `semanticSpatialEntityId` : the pointOfCollisionPrediction itself is a semanticSpatialEntity with location, rotation etc.
  * `source` : semanticSpatialEntityId of the entity which is the source of this pointOfCollisionPrediction (for example the player, a hand, a finger, a controller etc.).
  * `collisionPrediction` : what the semanticSpatialEntityId would collide with if it would have moved in a specific direction, for example what the player would collide with if they would have moved in a specific direction or if their hand would move in a specific direction. Could enable for example to assist players with low vision with indication of what's in front of them or with footsteps sounds that fit the type of surface that the player walks on.
    * `directionName` : one of predefined direction names ('forward', 'backward', 'left', 'right', 'up' and 'down').
    * `semanticSpatialEntityId` : the id of the entity that the player\ hand\ finger\ controller etc. would collide with. For example, a finger-based point of collision prediction would enable identifying what the finger points at and if it's a text then read it. As another example, a hand-based point of collision prediction would enable identifying what the hand waves at and read aloud the name or instructions of the pointed entity etc.
    * `name` : the name of the entity that the player\ hand\ finger\ controller etc. would collide with.
    * `distance` : the distance until collision.
    * `collisionPredictionMethod` : the method by which collision prediction is computed (for example, a line trace, a box trace, a sphere trace, tracing using the shape of the `source` entity etc.)
    * `collisionPredictionHitPoint` : semanticSpatialEntityId of the extrapolated hit point of this pointOfCollisionPrediction with the 3D space in the specific direction.
    * `directionRotation` : an alternative to directionName to provide parameters of an arbitrary direction.
      * `pitch`, `yaw`, `roll` : rotation parameters of the entity.

* `audio` : audio related semantic entities which could enable customized closed captions for example (3rd party developer can enable different fonts, background and foreground colors, names of speakers, speech direction indication etc.).
  * `voices`
    * `semanticSpatialEntityId` : id of the voice (enabling knowing its location, direction and other attributes).
	* `source` : the source of the voice, for example, human1.
	* `target` : the target of the voice, for example, human2.
    * `text` : container for the actual `text` and its `language` name.
      * `originalLanguage` : if there are text elements from multiple languages this specifies the original language of the voice.
    * `emotion` : the emotion of the speaker.
    * `sourceVoiceVolume` : the volume of the voice at the source point.
    * `timeRange` : time range for this voice speaking.
      * `startTime` : timestamp when the voice started.
      * `estimatedEndTime` : an estimate for when this voice would end speaking.
    * `audio`: the audio of the voice.
  * `effects` : sound effects.
	* `semanticSpatialEntityId` : id of the effect (enabling knowing its location and other attributes).
  * `music` : music which can be heard in part of the 3D world.
	* `semanticSpatialEntityId` : id from which location and form can be found for example
	* `source` : id of the source of the music.
    * `timeRange` : time range for this music playing.
        * `startTime` : timestamp when the music started.
        * `estimatedEndTime` : an estimate for when this music would end playing.
	* `audio` : the audio of the music.
	* `musicalNotation`
	* `lyrics`
	* `description`
* `relations` : relations between entities, realities etc.
  * `semanticLevelOfDetail` : semantic hierarchy of entities - from high level to low level.
	  * `semanticSpatialEntityId` : highest level entity (for example, earth)
	  * `children` : lower level entities (for example, continents)
        * Here goes even lower level entities...
  * `crossSemanticXrEquality`
    * For details see: [Examples of crossSemanticXrEquality](Examples/semanticXrExamples.md)
      * `[` : beginning of an array of equal entities
        * `[`
          * `{`
	      * `realityType`
		  * `realityInstanceId`
	      * `realityInstanceTimestamp` (here could also be a range or a collection of ranges like: '0-60,90-120')
		  * `semanticSpatialEntityId`
		  * `}`, 
          * `{`
	      * `realityType`
		  * `realityInstanceId`
	      * `realityInstanceTimestamp` (here could also be a range or a collection of ranges like: '0-60,90-120')
		  * `semanticSpatialEntityId`
		  * `}...`
		* `]...`
      * `]` : end of an array of equal entities