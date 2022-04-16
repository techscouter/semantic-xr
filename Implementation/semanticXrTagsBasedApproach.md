# Tags-based Approach for Implementing a Semantic-XR Generator
The tags below describe a tags-based approach for implementing a Semantic-XR generator. Once this input is provided, a game-engine library could potentially generate Semantic-XR instances using these tags in real time.
  
## Functions for SemanticXr class object
    generateSemanticXr():JSON
    
## Tags for SemanticXr class object
    sxr.schemaVersion=
    sxr.reality.id=
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
    sxr.crossSemanticXrEquality=[[{"realityType":,"realityInstanceId":,"realityInstanceTimestamp":,"semanticSpatialEntityId":},...]...]
    sxr.relations=
    
## Tags for Semantic Entities
    sxr
    sxr.name=
    sxr.description=
    sxr.instructions=
    sxr.categoriesAndAttributes=[{"category":,"attributes":{}},...]
    sxr.actions=[{"animationState":,"actionName":},...]
    sxr.pointOfView=[{"lensParameters":{}},...]
    sxr.collisionDetection=[{"directionName":, "directionRotation":}]

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