# Tags-based Approach for Implementing a Semantic-XR Generator
The tags below describe a tags-based approach for implementing a Semantic-XR generator. Once this input is provided, a game engine library could potentially generate Semantic-XR instances using these tags in real time.
  
## Functions for SemanticXr class object
    getSemanticXr(schemaVersion: String) -> JSON
    
## Tags for SemanticXr class instance object
    sxr.schemaVersion=
    sxr.reality.id=
    sxr.reality.instanceId=
    sxr.reality.description=
    sxr.reality.instructions=
    sxr.units.time=
    sxr.units.space=
    sxr.units.language=
    sxr.accessibility.instructions.general=
    sxr.accessibility.instructions.vision=
    sxr.accessibility.instructions.hearing=
    sxr.accessibility.instructions.motor=
    sxr.accessibility.instructions.speech=
    sxr.accessibility.instructions.cognitive=
    sxr.relations.crossSemanticXrEquality=[[{"realityId":,"realityInstanceId":,"realityInstanceTimestamp":,"semanticSpatialEntityId":},...]...]
    
## Tags for Semantic Spatial Entities
    sxr
    sxr.name=
    sxr.description=
    sxr.instructions=
    sxr.semanticLevelOfDetail=
    sxr.categoriesAndAttributes=[{"category":,"attributes":{}},...]
    sxr.actions=[{"animationState":,"actionName":},...]
    sxr.materials=
    sxr.pointOfView=[{"lens":{}},...]
    sxr.pointOfCollisionPrediction=[{"directionName":, "directionRotation":, "collisionPredictionMethod":},...]

## Tags for Scenes' Bounding Boxes (innermost volume overrides the outer ones)
    sxr.scene
    sxr.scene.name=
    sxr.scene.description=
    sxr.scene.instructions=
    sxr.accessibility.instructions.general=
    sxr.accessibility.instructions.vision=
    sxr.accessibility.instructions.hearing=
    sxr.accessibility.instructions.motor=
    sxr.accessibility.instructions.speech=
    sxr.accessibility.instructions.cognitive=