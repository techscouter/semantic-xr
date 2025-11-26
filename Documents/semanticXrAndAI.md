# Semantic-XR and AI
Semantic-XR and AI can be combined in several different ways and provide multiple advantages:

## Use Cases of Semantic-XR and AI

### Semantic-XR for the Real World and for Generative AI
In addition to [the way a 3D game engine or graphics software can easily generate Semantic-XR for its created media using tags](/Implementation/semanticXrTagsBasedApproach.md) there is a big motivation to enable creation of Semantic-XR for the Real World and for Generative AI based media which are major parts of one’s daily experience and would become even more so in the future.

The steps to accomplish Semantic-XR for Real World and Generative AI based media are similar:
* Create a very large amount of synthetic data for training purposes. Synthetic data of images and videos together with their accompanying Semantic-XR metadata would be created using a game engine or graphics software that supports Semantic-XR generation. Game engines today can create many different kinds of styled content including almost-photorealistic videos which would support the real world media use case.
* AI Training phase of a multi-modal AI model using the synthetic data and its accompanying Semantic-XR metadata.
* AI Inference phase of real world media’s Semantic-XR enabling its usage by a variety of Accessibility Solutions.
* Generation of Semantic-XR as accompanying metadata of Generative AI based media. So generated media (photos, videos, animation films etc.) could be annotated with Semantic-XR metadata right from the start by the generative model that was trained using the synthetic data from the first step above. As generated media becomes more ubiquitous this solution could contribute to the accessibility of such AI-based generated media.

#### Notes on the above AI training phase
* Building a very large tagged synthetic dataset as described above would also enable not using AI that was trained on copyrighted materials but having AI that was trained on content created specifically for this purpose.
* This dataset would also enable training the AI on the content creators' tags and not on generic content found online with its many types of biases (this is assuming the dataset content creators are not biased of course...).
* One could also add (with permission) to this AI training dataset also images and their descriptions from other training datasets that were specifically collected from people who are blind or have low vision in order to enrich the training data.


### Semantic-XR as Input to Generative AI
Creation in the reverse order - instead of inference from 3D or 4D content (3D images or videos) then moving from the Semantic-XR into 3D or 4D content using AI. 3D or 4D content generation especially by people with disabilities can be done using writing a Semantic-XR document and providing it as input to an AI-based generation tool which would enable immediate accessibility of this content by its accompanying Semantic-XR and further editing and generation cycles. So a closed feedback loop would look like:
* First generate Semantic-XR manually (like the old days of manual HTML editing) or via a dedicated editor or a script and then an AI based solution would use this Semantic-XR as an aid and guideline (using things like ControlNet etc.) and turn it into 3D or 4D content.
* This content would become accessible as it has an accompanying Semantic-XR metadata and would allow its repeated and iterative editing either via the underlying Semantic-XR or directly, all while having immediate accessibility feedback.

## Added Value of Semantic-XR
Here are several advantages of using Semantic-XR for Accessibility Solutions over plain AI-based scene descriptions and Q&A with AI:
* Additional knowledge - the creator of the content has a lot of knowledge about their content which AI may be missing just from a black-box analysis. Creator-known information like names of people or names of objects or actions etc. could be added and made accessible via Accessibility Solutions for the benefit of users.
* Scope - curation of what information should be available at a certain point in the experience (for example, specifying what are the highest semantic level of detail entities when the creator wants to focus on that in a scene or highlighting the existence and location of a visual menu in a video game). This could be achieved using the Semantic-XR metadata. As an example, a photo of a group of people dining in a restaurant could be a capture of a memorable family dinner or it could be an advertisement for the restaurant or it could be the background for an event hardly noticed at the far side of the photo. All of these are interpretations of the scene which are difficult to understand just by “looking” at the image using AI. Semantic-XR’s  `relations.semanticLevelOfDetail` field’s value for example could communicate what are the most important parts of the scene.
* Creator based descriptions (of entities or scenes for example) instead of external AI based ones.
* Non visual metadata, like instructions for example.
* Non visible content (via hidden semanticSpatialEntities or multiple pointsOfView for example).
* Accurate semantic metadata, like very accurate locations (for example: of people, objects, rooms, buildings etc.).
* Enabling Accessibility Solutions that are ready to be reused and operated (like a specific keyboard shortcut for a spatial audio based scene scan) instead of a long dialogue with an AI Large Language Model (LLM) so that it understands what it is asked for.
* Hybrid approach - still use an AI to describe the scene and ask questions about it but the AI would have in addition to the image or video also the Semantic-XR metadata to work with.
* Enables solutions with immediate real time feedback, for example in voice-based AI interactions with the content, without requiring "thinking" and analysis delays.
