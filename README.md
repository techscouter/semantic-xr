**_Note: This repository has been archived with read-only mode in order for future work on it to happen at a standards organization. It is a proposal for further community discussion._**


# Introduction
This repository describes an accessibility-focused semantic 3D scene description format named Semantic-XR: a description of an XR experience as meaningful and well-defined data in order to make it more accessible.

## Usage Example
The format includes (among other fields) names and locations of objects in a 3D scene. If the names and locations metadata is externalized then Accessibility Solutions would be able to use them in different ways. One way could be providing spatial audio scans of the object names. Another way could be describing them in a natural language sentence available to screen readers. And yet another way could be making them accessible to a screen reader as lists so the user could navigate through these lists in the order of their distance from the user or from left to right for example. By having these options, users with disabilities could choose when and how they want to experience the 3D scene in a personalized way specific to their needs.
Objects' names and locations are common to all 3D scenes whether they are part of an XR Experience, a movie, a video game, an animation, a photo or video of the real world, an AI-generated image or video and more. Having a unified semantic 3D description format (which includes much more than names and locations) that can be made available as metadata to Accessibility Solutions can make all of these types of 3D scenes accessible in a decoupled way from the media type they originate from. This is just one aspect of Semantic-XR, for full details see below.


# Motivation
First, let's go over the "Why?": please find below a list of many communities that will benefit from Semantic-XR usage and its standardization and how they will benefit from it. Through that we can learn about the format's strengths, capabilities and opportunities to create a more accessible world including [advantages over plain AI-based scene descriptions](/Documents/semanticXrAndAI.md#added-value-of-semantic-xr).

## Communities that Could Benefit from Semantic-XR Usage and Standardization

* **For people with disabilities:** the potential of more than one billion people with disabilities to participate in XR Experiences via a large variety of new compatible Accessibility Solutions for many kinds of disabilities. Accessibility Solutions that would provide them the agency and options to choose where, when and how to explore the 3D environments in the XR Experiences.
* **For people with disabilities:** this solution is generic enough to support XR (VR, AR, MR) but also any 3D or 4D (3D plus time) content, not only what is usually categorized under 'XR'. For example: movies, animation films, video games, 3D models, CAD (Computer Aided-Design) content, images with 3D content, sketches with 3D content, real life photos and videos and live streams and generative AI content (via training and inference in real-time) and more...
* **For people with disabilities:** ability to create XR Experiences and XR Accessibility Solutions for themselves and for others (as it solves a major obstacle - accessible XR content is a big enabler for XR content authoring).
* **For people with disabilities:** ability to provide extensive support for a large variety of disabilities: vision, hearing, cognitive, motor.
* **For people with motor disabilities:** this XR Accessibility solution proposal includes an initial potential solution for a long standing challenge: Universal Controller Mapping. The Universal Controller Mapping infrastructure idea which is based on specific parts of the Semantic-XR format is discussed separately in a dedicated section in the High Impact Experimental Ideas page.
* **Accessibility Solutions Creators:** widespread support for their solution which would work with any XR Experience that supports the required schemaVersion(s). Ability to provide extensive support for a large variety of disabilities, Personalization, Ease of use, Flexibility, Extensibility (via Semantic-XR built-in format hooks and different schemaVersions) and more.
* **Traditional Accessibility Solutions providers:** ability to extend their tools to support XR and 3D and 4D content (for example screen readers that would be able to add scans of 3D scenes with spatial audio similar to traversing a list of headers on a web page or another example would be providing lists of different types of entities like people or locations).
* **New Accessibility Solutions providers:** ability to build solutions in a variety of ways: as game engines plugins, game engines built-in support, browsers plugins, browsers built-in support, Operating System level solutions (mobile\ desktop\ tablet\ laptop\ TV\ XR headsets etc.) or as part of the XR Experience itself using reusable or custom Accessibility Solutions.
* **XR Accessibility Solutions Researchers:** Semantic-XR enables easy prototyping without requiring access to the content via inaccessible and complex authoring software. This could be leveraged by accessibility researchers and consultants including people with disabilities that would prototype and build their own solutions that could then be made into reusable Accessibility Solutions. A researched, tested and verified easy-to-build browser extension can make its way to the browser, to a game engine plugin, into a video game and maybe even to the Operating System itself.
* **Creators of XR Experiences:** Semantic-XR is designed for content creators to expose the semantics of their media in order to make it accessible. For example, a streamlined way to support XR Accessibility would be using their authoring tool (by enabling a Semantic-XR plugin, choosing the supported schemaVersions and tagging their content according to the tagging instructions that are available in another section in this repository). This would enable them full creator control via the tags and supported schemaVersion over the contents of exported Semantic-XR. Once export is supported then both existing solutions can be reused and in addition customized accessibility solutions can be developed (for a specific experience or for their studio's reuse or for the entire community reuse via an open source solution). Content creators could include VR collaboration platforms' creators; AR/VR training and educational material producers; 3D game developers; video, animation and film studios (via game engine based virtual production or via AI based approach) etc.
* **Standards Organizations like the W3C:** we would have a uniform semantic metadata format for all 3D and 4D experiences (with a way to specify how these experiences relate to each other using the `crossSemanticXrEquality` field). Semantic-XR's `schemaVersion` field could be used like WCAG's levels of conformance - 3D and 4D content that would be Perceivable, Operable, Understandable and Robust. This could become: XCAG (“XR Content Accessibility Guidelines”). See more details in the section about Semantic-XR standardization.
* **Legal purposes:** if indeed a standard is defined then an XR Experience should support Semantic-XR's schemaVersion A or AA or AAA or other values for different levels of Accessibility Solutions support - simplified and familiar concept yet with extremely powerful descriptive power.
* **For developers of 3D and 4D tools:** once they implement a Semantic-XR Generator plugin the content created by the tool can be made accessible using reusable Accessibility Solutions. Also making their tool accessible for people with disabilities is easier - they need to support the tool interface while the XR content is already accessible. Examples for tools that would highly benefit from this solution: Unreal Engine, Unity, WebXR web frameworks, Blender, Unreal Engine for Fortnite, Godot, OpenUSD integration and others. A roadmap for a tool developer could be to support a basic Semantic-XR schemaVersion, then allowing community Accessibility Solution plugins integration, then support advanced schemaVersions, then develop tool UX accessibility support and finally developing Accessibility Solution plugins themselves.
* **For AI specialists:** for training and for inference of Semantic-XR for real life streams\ videos\ photos and for generative AI content which becomes more and more popular. For more details see the page [Semantic-XR and AI](/Documents/semanticXrAndAI.md).
* **For Metaverse creators and participants:** an example of "solve for one, extend to many" - solving the important spatial content interoperability challenge via the semantic interoperability high impact experimental idea (discussed separately in a dedicated section in the High Impact Experimental Ideas page).
* **For all:**  additional "solve for one, extend to many" opportunities. Just a few examples:
  * Search and query capabilities of 3D content and tracking of changes over time (that can be achieved by comparing subsequent Semantic-XR documents for differences like: "A new car appeared", "A person moved further away" etc.)
  * Analytics that leverages Semantic-XR data - for example for 3D games of sport like basketball or football etc. or VR based fitness experiences.
  * Creative web development that leverages the knowledge from the Semantic-XR format (for a concrete example [check out the following video for an example of adding interactivity and interaction between a web page’s graphical shape, video and image](https://www.youtube.com/watch?v=gh0vJOWk5EY)).
  * Compression - for example a Semantic-XR that includes a specific brand of a car seen in a certain location from a specific angle is a few bytes long but with proper rendering capabilities and prior knowledge of the car it can enable rendering a very high quality image of that car - enabling orders of magnitude levels of compression of media (idea discussed separately in the page about High Impact Experimental Ideas and mentioned in [my blog post from 2010 about Semantic Editing, Encoding and Decoding](https://blog.techscouter.net/techscouter/seed-semantic-editing-encoding-and-decoding)).
  
# The Format
The format itself is described in the file [semanticXr.json](/semanticXr.json) which is a JSON file that serves as a template for Semantic-XR content. Explanations for the format's fields can be found in the following [Semantic-XR Instructions document](/semanticXrInstructions.md).

# Examples
## Example Image with a Semantic-XR Representation
### Image

![A single large cube on the floor (a bit to the right) with surrounding wall and cloudy sky](Examples/DemoGameCubes/DemoGameCubes2.png)  

### Image's Semantic-XR

        {
            "semanticXr":{

                "instructions":{
                    "reality":"This is a 3D interactive story application. Use the keys W, A, S and D to move and Left and Right arrows to turn. Press Z to generate Semantic XR.",
                    "scene":"You should reach the destination block (visually indicated blue) while avoiding the other blocks (visually indicated grey).",
                    "frame":" block: right near"
                },
                
                "semanticSpatialEntities":[
                        {"semanticSpatialEntityId":"EditorCube8","name":"block","physical":{"location":{ "x":1073, "y":539, "z":113}}}],
                
                "pointsOfCollisionPrediction": [
			        {
                        "collisionsPredictions":[
                            {"directionName": "forward", "name":"obstacle", "distance":1701}
                        ]
                    }
                ],

                "id":{
                    "realityId":"SemanticXrAccessibilityProofOfConcept",
                    "realityInstanceId":"SemanticXrAccessibilityProofOfConcept2BB675B24CD2D1D3AEB1EDAF03CD68A0",
                    "realityInstanceTimestamp":21.121567
                }
            }
        }

## More Examples
There are many other usage examples provided. Like the following [document that describes the semantic contents of scenes from a demo 3D interactive environment](Examples/DemoGameCubes/DemoGameCubesREADME.md) (it is based on [my blog post about Making 3D Content More Accessible on the Web: "Semantic XR" Proof of Concept](http://accessiblerealities.com/blog/making-3d-content-more-accessible-on-the-web-semantic-xr-proof-of-concept/)).   

There are also [many other examples and links to related videos](Examples/semanticXrExamples.md).  

# Semantic-XR for Existing Accessibility Requirements and Solutions
The following [document about meeting existing requirements and about providing Accessibility Solutions](/Documents/semanticXrForExistingAccessibilitySolutionsAndRequirements.md) includes detailed descriptions how Semantic-XR could be used to provide solutions to a long list of XR accessibility User Requirements (by going over all the requirements in the W3C's XAUR document). In addition, it describes several existing commercial and open source Accessibility Solutions that could be mostly implemented by using Semantic-XR as their backend. It demonstrates the applicability of the format to real world requirements and its relevancy for real world solutions.

# Semantic-XR Standardization
For more information about potential future standardization check out [this document about Semantic-XR standardization potential](/Documents/semanticXrStandardization.md). This opens up an opportunity to standardization of XR Accessibility and of 3D scenes accessibility in general which are long standing challenges.

# How to Implement a Semantic Generator
There are multiple ways how to generate Semantic-XR for 3D content. One such method is for tools that are being used to create 3D content, like game engines. This method is described in the following [document about a tags-based approach on how to implement a generator library for this format](Implementation/semanticXrTagsBasedApproach.md). This approach leverages game engine capabilities for its purpose. It includes a list of the object tags that are needed in order to generate Semantic-XR based on game engine capabilities. This approach was developed and refined based on an experience of building an advanced prototype using an early version of the Semantic-XR format. Another way would be using AI to generate Semantic-XR for 3D media such as Real World videos and streams and for Generative AI based images and videos, it is described in [a dedicated section in the document about AI and Semantic-XR](/Documents/semanticXrAndAI.md#semantic-xr-for-the-real-world-and-for-generative-ai).

The techniques described above for generating Semantic-XR cover both 3D media that is generated through tools and 3D media that is recorded from the real world or generated via Generative AI. By using these techniques we can enable accessibility to a very wide range of 3D content. We can provide accessibility in a common way through Accessibility Solutions that work on top of the Semantic-XR format, no matter what its source media is.

# Semantic-XR High Impact Experimental Ideas
[The following document describes a list of high impact experimental ideas](/Documents/semanticXrHighImpactExperimentalIdeas.md) that could leverage Semantic-XR. These ideas were not fully tested and validated yet but if materialized, they could have a huge impact on XR Experiences and Accessibility Solutions. Among these ideas are: design of Metaverse Interoperability and Portals, Universal Controller Mapping and Orders of Magnitude Media Compression.

# Semantic-XR and AI
[This document describes the relation between Semantic-XR and AI and its impact](/Documents/semanticXrAndAI.md). Among the topics discussed are how Semantic-XR can be generated for Generative AI based media and for real world media. Another topic that is discussed is a list of advantages of using Semantic-XR for Accessibility Solutions over plain AI-based scene descriptions.

# Challenges
No technology comes without its challenges. [The following document describes a list of Semantic-XR related challenges with initial ideas on how to overcome these challenges](/Documents/semanticXrChallenges.md).

# About
This Semantic-XR repository is part of my social impact project (not a company) named [Accessible Realities](http://accessiblerealities.com/blog/about/). Accessible Realities social impact project aims to enable making video games, virtual worlds, XR experiences and 3D experiences in general more accessible for people with disabilities in general with a special focus on people who are blind or have low vision.  


The roots of this work are:
* A blog post I wrote in 2010 about semantic representation and editing of media and its potential uses: [SEED: Semantic Editing, Encoding and Decoding](http://blog.techscouter.net/techscouter/seed-semantic-editing-encoding-and-decoding) with a reference implementation of that idea and additional posts in that [blog](http://blog.techscouter.net/).
* My research as part of [my social impact project Accessible Realities](http://accessiblerealities.com/blog/) since 2017.
* A presentation I gave at the [W3C Workshop on Inclusive Design for Immersive Web standards](https://www.w3.org/2019/08/inclusive-xr-workshop/agenda.html) in 2019. A presentation titled: 'Enabling XR Accessibility with Semantic XR Data Model'.
  

I Hope you find this format useful.  
Zohar Gan
