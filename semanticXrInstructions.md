# Semantic-XR Instructions
This section includes explanations for the fields of the Semantic-XR format. Examples for values for some of the fields can be found in the examples described in the [Semantic-XR examples document](/Examples/semanticXrExamples.md). The `schemaVersion` field value is used to determine which fields are mandatory and which are optional. Note that some of the definitions are a bit loose - this is both part of the early stage phase of this format and both for enabling creative uses for its users.

## Semantic XR fields' explanations

* `semanticXr`: a description of an XR experience as meaningful and well-defined data in order to make it more accessible. The root element of the file.

* `schemaVersion` : a specific version of the semantic format template JSON that the document follows: what fields are included and which are mandatory and which are optional. schemaVersion is not strictly a semantic versioning string but it could be a string that can describe combinations of mandatory\ optional sets of fields (for example: BasicWithoutImages_0.0.1 or GlobalPositionsOnly_0.1.0 etc.). It could also be used in the future for short codes to represent agreed upon conformance levels (in a similar manner to W3C WCAG’s A, AA and AAA conformance levels for web content - a W3C XCAG standard for XR might be defined as part of [future standardization work](/Documents/semanticXrStandardization.md) :smiley: ). schemaVersion would probably include a namespace component to avoid naming collisions - this might be based on using a domain-like string structure. A Semantic-XR generator can publish its supported schemaVersions to align expectations with its clients.

* `id` : a section that identifies the point in time in a specific reality that this Semantic-XR data represents. Note that realityInstanceId and realityInstanceTimestamp are optional which opens up a lot of opportunities to represent composite realities.
  * `realityId` : a type of reality, like a name of a video game or a name of a movie.
  * `realityInstanceId` : id for a specific instance of the reality mentioned above. For example a specific game played at a specific time and place or a specific screening of a movie.
  * `realityInstanceTimestamp` : a timestamp within the specific reality instance mentioned above. If the game or movie is paused for example, then this timestamp is paused as well.
  
* `units` : the units used in the document (note that field values should be decimal and not float in order to represent exact values and enable many orders of magnitude of difference between values in the same document while keeping accuracy).
  * `time` : which units of time are used in the document, for example for realityInstanceTimestamp.
  * `space` : which units of distance are used in the document, for example for pointsOfCollisionPrediction.collisionsPredictions.distance.
  * `language` : which natural language is being used in the document, for example for descriptions and instructions.

* `descriptions` : short descriptions of different aspects of the reality's 3D scene
  * `reality` : description of the reality (game, movie etc.)
  * `scene` : description of the current 3D scene in general at id.realityInstanceTimestamp point in time.
  * `frame` : description of the very specific main frame that is shown in id.realityInstanceId at id.realityInstanceTimestamp point in time. The frame description could be created algorithmically using rules to generate the frame description based on other Semantic-XR fields (like forming a sentence based on horizontal positions and\ or distances of the different visible entities). Alternatively the frame description could also be created using AI based on the image and other fields like semanticLevelOfDetail.
  
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
    * `cognitive`: for example how to access the instructions and descriptions for specific entities.

* `semanticSpatialEntities` : the main list of semantic spatial entities with their properties.
  * `semanticSpatialEntityId` : an id that uniquely identifies this entity in this reality instance.
  * `name` : natural language name of this entity.
  * `description` : short natural language description of this entity.
  * `instructions` : instructions for this entity (for example, for operating it or interacting with it).
  * `physical` : physical properties of this entity.
    * `location` : location of the entity. All entities' locations should be in the same coordinate system.
      * `x`, `y`, `z` : location of the entity across the different axis. <TBD>
    * `rotation` : rotation of the entity.
      * `pitch`, `yaw`, `roll` : rotation parameters of the entity.
  * `colors` : one or more colors ordered by dominance in the entity.
  * `materials` : natural language names of the materials the entity is made of, one or more materials ordered by dominance in the entity.
  * `volume` : exact or approximate (for example, bounding box) volume.
  * `form` : exact or approximate (for example, bounding box) form.
  * `actions` : natural language descriptions of the actions of the entity (like: running or talking), one or more in order of importance.
  * `semanticLevelOfDetail` : This very powerful field would enable the creator to define a default semantic level of detail hierarchy for a scan of the entities and define levels of details for zooming in and out semantically on the scene and going over the entities from a specific level of detail in a specific semantic order. It could greatly help in making scenes with a very large number of entities accessible. This field value on the entity, when applied to multiple entities, would enable the creation of the relations.semanticLevelOfDetail field’s graph (that appears down below under relations field). relations.semanticLevelOfDetail field's graph could provide for the user a powerful capability of an accessibility experience similar to a screen reader: like moving forward and backwards in HTML headings of a the same level and also moving up and down in levels of a specific entity. In addition to scanning 3D scenes horizontally or vertically or from closest to most distant element etc. from certain viewpoints, this opens up a way to scan the scene semantically in the way the creator or annotator of the scene defined. It could be implemented for example by values (tags) in a dot notation format of Level1Keyword_Order.Level2Keyword_Order.Level3Keyword_Order. The dots separate between levels of details and the order part recommends an inner order for a specific level of detail. As an example, a list of tags in a specific scene could be: house_1, house_1.door_1, house_1.window_2, house_1.window_3, house_1.kitchen_4, house_1.kitchen_4.oven_1, house_1.kitchen_4.refrigerator_2, house_1.window_5. In case of no immediate parent an empty string could also be added, for example: house_1, .car_1, .car_2, ..rocks_1. Virtual entities could be created as well, for example : pileOfRocks_1, groupOfPeople_1 etc.
  * `categoriesAndAttributes` : array of categories and their attributes which describe the entity.
    * `category`: non comprehensive list of examples for categories of entities: star, planet, landscape, landscapeArchitecture, architecture, internalDesign, object, location, livingEntity, player, light, camera, controller, pointOfView, hitPoint, effect, music, text, table, chair, shadow, semanticXr etc. Note that the option to have semanticXr as a nested semanticSpatialEntity is extremely powerful (for usage examples see the [Semantic-XR examples document's composite Semantic-XR section](/Examples/semanticXrExamples.md#composite-semantic-xr)). It would be useful to define standard categories as part of a standard while still enabling custom ones.
    * `attributes`: attributes and their values within the specific category. For example: for category 'text' the attributes could include the actual text in different languages. The value of the attributes field could include nested fields\ arrays itself.

* `pointsOfView` : points in space from which view-based data is generated.
  * `semanticSpatialEntityId` : the pointOfView itself is a semanticSpatialEntity with location, rotation etc.
  * `source` : semanticSpatialEntityId of the entity which is the source of this pointOfView (for example the player, a camera, a controller, a portal, an eye etc.).
  * `visibleSemanticSpatialEntities` : array of all semantic spatial entities that are visible from this point of view.
    * `semanticSpatialEntityId`
	* `projectedSemanticSpatialEntityCenter` : properties of the center point of the semantic spatial entity.
	  * `location` : the coordinates of the projection of the semantic spatial entity on this point of view.
        * `horizontalFraction` : fraction of width (0=left, 0.5=middle, 1=right).
        * `verticalFraction` : fraction of height (0=top, 0.5=middle height, 1=bottom).
      * `distance` : distance from this point of view in space units.
  * `visualHitPoint` : semanticSpatialEntityId of the extrapolated hit point of this pointOfView with the 3D space in front of it. For example, a controller-based point of view's hit point id would enable using it as a laser pointer and have it read aloud text, name of pointed entity, distance to an entity etc.
  * `images` : optional images generated from this point of view. As this is a JSON file there is a need to do BASE64 encoding of the data and **verify** the data source for security reasons. Data URLs might be useful here with their pros and cons for the image's `value` field. Note that images can be for example 360 degrees images or be in other kinds of shapes, types of data and formats. Example types of images:
    * value of type "image": regular RGB image of the frame.
    * value of type "depthMap" : depth map.
    * value of type "instanceSegmentation" : instance segmentation - each instance is identified by its semanticSpatialEntityId.
    * value of type "semanticSegmentation" : semantic segmentation - ordered categories are taken from the category properties of the instance (see "instanceSegmentation").
    * value of type "preProcessedImage" : RGB image before applying any effects like blur etc. which could be problematic from an accessibility perspective.
    * value of type "realityTypeImage" : marking each area of the frame with the type of reality it represenets - real world, VR, AR content, passthrough etc.
    * value of type "semanticLevelOfDetail" : different semanticLevelOfDetail values. This could be used for example to enable highlighting and\ or masking important parts of the image using flexible importance thresholds.
    * value of type "edges" : identifying the edges of the entities.
    * value of type "normals" : identifying the "normal" values for the frame.
  
    image's `legend` maps color values to an array of values that are relevant for the specific image type (`"legend":{color:[], color:[], color:[], …}`). For example it could map an image color to to semanticSpatialEntityId in case of instanceSegmentation or to ordered category values in case of semanticSegmentation or to depth value in case of depthMap.

    image’s `lens` describes characteristics of the generator of the image content (for example camera settings used for an image). It would be useful in the future to define a common terminology of lens' fields that would be part of the Semantic-XR format.

    The images' color depth should be chosen to be sufficient to represent the expected number of colors needed (for example the number of semanticSpatialEntityIds in case of instanceSegmentation).

    Note: in case of two eyes' inputs for example in VR or glasses-based AR that would require pairs of images - one for each eye - this could be achieved using the existing support for multiple points of view (they would just be associated with the same player - left eye and right eye).

    In the future new types of images could be added.
* `pointsOfCollisionPrediction` : points in space from which collision prediction data is generated.
  * `semanticSpatialEntityId` : the pointOfCollisionPrediction itself is a semanticSpatialEntity with location, rotation etc.
  * `source` : semanticSpatialEntityId of the entity which is the source of this pointOfCollisionPrediction (for example the player, a hand, a finger, a controller etc.).
  * `collisionsPredictions` : what the semanticSpatialEntityId would collide with if it would have moved in a specific direction, for example what the player would collide with if they would have moved in a specific direction or if their hand would move in a specific direction. Could enable for example to assist players with low vision with indication of what's in front of them or with footsteps sounds that fit the type of surface that the player walks on.
    * `directionName` : one of predefined direction names ('forward', 'backward', 'left', 'right', 'up' and 'down').
    * `semanticSpatialEntityId` : the id of the entity that the player\ hand\ finger\ controller etc. would collide with. For example, a finger-based point of collision prediction would enable identifying what the finger points at and if it's a text then read it. As another example, a hand-based point of collision prediction would enable identifying what the hand waves at and read aloud the name or instructions of the pointed entity etc.
    * `name` : the name of the entity that the player\ hand\ finger\ controller etc. would collide with.
    * `distance` : the distance until collision.
    * `collisionPredictionMethod` : the method by which collision prediction is computed (for example, a line trace, a box trace, a sphere trace, tracing using the shape of the `source` entity etc.)
    * `collisionPredictionHitPoint` : semanticSpatialEntityId of the extrapolated hit point of this pointOfCollisionPrediction with the 3D space in the specific direction.
    * `directionRotation` : an alternative to directionName to provide parameters of an arbitrary direction.
      * `pitch`, `yaw`, `roll` : rotation parameters.

* `audio` : audio related semantic entities which could enable customized closed captions for example (3rd party developer can enable different fonts, background and foreground colors, names of speakers, speech direction indication etc.). Note that some of the fields in the audio section below are still experimental\ optional.
  * `voices`
    * `semanticSpatialEntityId` : id of the voice (enabling knowing its location, direction and other attributes).
	* `source` : the source of the voice, for example, human1's semanticSpatialEntityId.
	* `target` : the target of the voice, for example, human2's semanticSpatialEntityId (it could also be the semanticSpatialEntityId of a "virtual" entity like a crowd or a group of people).
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
  * `music` : music which can be heard in the entire or in part of the 3D world.
	* `semanticSpatialEntityId` : id from which location and form can be found for example.
	* `source` : id of the source of the music.
    * `timeRange` : time range for this music playing.
        * `startTime` : timestamp when the music started.
        * `estimatedEndTime` : an estimate for when this music would end playing.
	* `audio` : the audio of the music.
	* `musicalNotation`
	* `lyrics`
	* `description`
* `relations` : relations between entities, realities etc.
  * `semanticLevelOfDetail` : semantic hierarchy of entities - from high level to low level. For detailed instructions and what this field enables see semanticSpatialEntities.semanticLevelOfDetail field instructions above.
	  * `semanticSpatialEntityId` : highest level entity (for example, earth)
	  * `children` : lower level entities (for example, continents)
        * Here goes even lower level entities...
  * `crossSemanticXrEquality`
    * For details see: [Examples of crossSemanticXrEquality](Examples/semanticXrExamples.md#crosssemanticxrequality-examples). If a field is missing in an entry it means it equals all possible values for this field - all realityIds or all realityInstanceIds or all realityInstanceTimestamps or all semanticSpatialEntityIds (or their combination in case more than one field is missing).
      * `[` : beginning of an array of equal entities
        * `[`
          * `{`
	      * `realityId`
		  * `realityInstanceId`
	      * `realityInstanceTimestamp` (here could also be a range or a collection of ranges like: '0-60,90-120')
		  * `semanticSpatialEntityId`
		  * `}`, 
          * `{`
	      * `realityId`
		  * `realityInstanceId`
	      * `realityInstanceTimestamp` (here could also be a range or a collection of ranges like: '0-60,90-120')
		  * `semanticSpatialEntityId`
		  * `}...`
		* `]...`
      * `]` : end of an array of equal entities