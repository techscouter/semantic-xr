# Introduction
This repository describes an accessibility-focused semantic 3D scene description format: a description of an XR experience as meaningful and well-defined data in order to make it more accessible.

# Background and Motivation
With the growing interest in XR experiences (also known as metaverse(s)) we should not leave anyone behind and enable any person who is interested in it to meaningfully participate in existing and future virtual worlds. The focus of the described format is to make XR experiences or metaverse(s) more accessible for people with disabilities. Please note that this is still an experimental technology in research phase and comes with its challenges (there is a dedicated Challenges section below).

# Format
The format itself is described in the file [semanticXr.json](semanticXr.json) which is a JSON file that serves as a template.

# Usage Examples
There are many usage examples provided. Like an example that [describes the semantic content of a scene from a demo 3D interactive environment](Examples/DemoGameCubes/DemoGameCubesREADME.md) (it is based on [my blog post about Making 3D Content More Accessible on the Web: "Semantic XR" Proof of Concept](http://accessiblerealities.com/blog/making-3d-content-more-accessible-on-the-web-semantic-xr-proof-of-concept/) ).  
There are also [other examples and links to related videos](Examples/semanticXrExamples.md).

# Format Instructions
Explanations for the format's fields can be found in [semanticXrInstructions.md](semanticXrInstructions.md).

# About
This repository is part of my social impact project (not a company) named [Accessible Realities](http://accessiblerealities.com/blog/about/) which aims to enable making video games and XR experiences more accessible for people with disabilities focused on people who are blind or have low vision.  
The roots of this work are in a blog post I wrote in 2010 about semantic representation and editing of media and its potential uses: [SEED: Semantic Editing, Encoding and Decoding](http://blog.techscouter.net/techscouter/seed-semantic-editing-encoding-and-decoding), a reference implementation of that idea and additional posts in that [blog](http://blog.techscouter.net/); in research as part of [my social impact project Accessible Realities](http://accessiblerealities.com/blog/about/) since 2017 and in a presentation I gave at the [W3C Workshop on Inclusive Design for Immersive Web standards](https://www.w3.org/2019/08/inclusive-xr-workshop/agenda.html) in 2019. A presentation titled: 'Enabling XR Accessibility with Semantic XR Data Model'.  
I Hope you find this format useful.  
Zohar Gan

# About this repository

## This repository is:
* Focused on **accessibility** purposes.
* Includes a **sementic** format which is a description of an XR experience as meaningful and well-defined data in order to make it more accessible. For example, it includes names and locations of objects.
* Could enable **personalization of accessibility support**. For example, enabling description of the 3D locations of the objects in multiple ways and enabling the user to choose their preferred method of making things accessible.
* **Designed for content creators** to expose the semantics of their media in order to make it accessible. Content creators like VR collaboration platforms' creators; AR/VR training and educational material producers; 3D game developers; video, animation and film studios (via game engine based virtual production) etc.
* Could **unify all types of 3D realities and content**: 3D games and virtual worlds, AR, MR, VR, the real world, videos, TV, films, pictures, animations, sketches (and who knows, maybe even imagination and dreams in the future...). For example, names and locations of objects are common to all these realities, in addition to many more optional reality characteristics specified in the format.
* Could provide **a way to interconnect between different realities** or different XR experiences or metaverses. Doing this in a human and machine readable way. See the format’s tag ***crossSemanticXrEquality*** for details on linking separate realities and their entities in terms of identity, space and time.
* Could enable **3rd party XR assistive technology creators** to provide support based on the agreed upon semantics of the XR experience if this is specified in such format without relying on the internals of the media. This would potentially, if implemented, allow augmenting the XR experience using screen readers (and their plugins), braille displays, browsers (and their extensions), dedicated software and even operating systems. This is of course dependent on these 3rd party creators' future adoption and support of such semantic format. One of the great challenges here would be how to verify the source of the semantic content.
* The semantic contents could be associated as **metadata** to 3D media including to 3D media streams.
* The format, specified as a **JSON template**, could be implemented in other ways as well like text-based YAML or in binary formats or to fit a game engine-supported/efficient/useful file formats like specific image formats or data structures other than JSON.

## This repository is not:
* The format is **not tied to a specific technology** but is intended to be generic.
* This repository’s **scope is not to maintain a standard**. It might be used as a starting point of a standard after additional research, testing and solving of potential challenges.
* The main focus is **on semantic representation, not on physical representation** like lights, objects' geometry and textures etc.
* The blueprint for how to build a generic generator for the semantic format is **based on game engines’ capabilities** and as-such on the XR experience creator control over what is being exposed to end users.
* The focus is on trying to accommodate accessibility requirements for people who are blind or have low vision and some support for people who are deaf or hard of hearing and some support for cognitive disabilities’ requirements (like on demand instructions and scene descriptions). **It could be extended to better support these disabilities if needed and to support other disabilities as well**.
* **Navigation** is not explicitly supported by this format but one could add navigation props using the existing mechanisms which will be exposed as semantic spatial entities (signs that describe the area around them, landmarks that can serve as beacons, road signs that point the way, scene descriptions etc.).
* This repository is **not accepting contributions at the moment**, it describes the semantic format as-is at this point in time.

# Challenges
This is still an **experimental technology in research phase** and comes with several challenges and as such also potential challenges that are yet to be identified. These challenges should be solved early on for this format to be a success. 
## Example challenges
* Impact on **performance** of generating the semantic data.
* Potential **privacy** issues, for example if players' details are provided as part of the semantic data without consent and/or in violation of privacy regulations.
* Potential **security** issues for consumers of semantic data from unverified sources.
* Potential **abuse in competitive games**.
* **Thorough testing** with people with disabilities and developers.
* There are **accessibility categories that would be difficult to support** by relying only on the semantic format. For example: content related (such as puzzle hints) and deep modifications (such as avoiding shaky camera movements).

# Tags-based approach for how to implement a semantic generator
Included is a [tags-based approach on how to implement a generator library for this format](Implementation/semanticXrTagsBasedApproach.md) that leverages game engine capabilities for its purpose. It includes a list of the tags that are needed to generate Semantic-XR based on game engine capabilities.