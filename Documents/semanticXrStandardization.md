# Semantic-XR Standardization

This page describes how the Semantic-XR format could be used in the future as part of potential standardization of XR Accessibility ("XR" in the broad sense of **any** 3D or 4D media). A few areas are discussed:
* The semantic data model itself
* Integration points with different 3D content types
* Conformance levels
* Scope


**_Note: The suggestions below, this page and this repository are not in any way formal standards and are simply proposals for further community discussion._**

## Semantic Data Model
Standardization of the Semantic Data Model itself (what does it contain or does not contain, how it is versioned etc.) would enable things like its validation, its more efficient usage and aligning expectations with its clients. The following document provides [a long list of specific examples how a Semantic Data Model (and specifically, Semantic-XR) could enable a rich ecosystem of accessibility solutions for people with disabilities](/Documents/semanticXrForExistingAccessibilitySolutionsAndRequirements.md).

## Integration Points with Different 3D Content Types
In addition to having a standardized Semantic Data Model, having also standard ways in which it is integrated into different 3D content types (such as videos, images and XR) could be highly useful to enable its efficient use by assistive technology.

Below are a few initial thoughts about possible design approaches for such integration points.
### Video
A video with 3D content could be made more accessible by having a Timed Text Track which would include the current Semantic Data Model contents at a specific timestamp in the video. In the web platform context, in addition to the existing track's "kind" optional values (such as "captions", "subtitles" and "metadata") there could also be a "semantic" "kind" value that would specify that the track contents are according to the standard semantic data model specifications.
### 3D Content and XR
In the web platform context, a canvas element could be allowed to have Timed Text Tracks associated with it. Either as children or in other ways. This would allow for semantic content (in addition to subtitles, captions etc.) to be added to any dynamic 3D content. Text Track's "addCue()" method calls could then be used to dynamically add the relevant Semantic Data Model contents at specific points in time. This could be a powerful way to leverage existing standards in order to provide 3D content accessibility for people with disabilites.

## XR Accessibility Conformance Levels
Standardized versioning of the Semantic Data Model as described above could be leveraged in order to define Accessibility Conformance Levels. In the context of this repository, `schemaVersion` is an important field of the Semantic-XR format. Below is an explanation of this field as well as a description of how it could be used to enable the definition of XR Accessibility Conformance Levels.

A specific Semantic-XR document’s schemaVersion field value describes which Semantic-XR fields are mandatory and must be included in this specific Semantic-XR document and which fields are optional. schemaVersion field’s value is not strictly a semantic versioning string but it could be a string that can describe combinations of mandatory and optional sets of fields (for example: GlobalPositionsOnly_0.1.0 or BasicWithoutImages_0.0.1 etc.). schemaVersion values would probably include a namespace component to avoid naming collisions - this might be based on using a domain-like string structure. A Semantic-XR generator (like one in a video game or a movie player) can publish its supported schemaVersions to align expectations with its clients.

schemaVersion could also be used in the future for short codes to represent agreed upon conformance levels. In a similar manner to W3C WCAG’s A, AA and AAA conformance levels for web content - a W3C XCAG (XR Content Accessibility Guidelines) standard could be defined. The new standard could include WCAG-like conformance levels based on the Semantic-XR’s schemaVersion values. For example A, AA or AAA schemaVersion field values would specify different lists of mandatory fields that should appear in the Semantic-XR metadata that would in turn enable different types and levels of Accessibility Solutions supporting multiple disabilities.

## Scope
Supporting semantic 3D content accessibility on the web platform would be a very major milestone. After that, there are also other platforms such as XR headsets\ glasses, gaming consoles and operating systems for mobile, desktop\ laptop, TV, watch etc. which could benefit from the Semantic Data Model standardization in 2 ways:
1. As part of their integration with web content they would gain the semantic 3D content accessibility in integrated web pages.
2. Natively supporting the Semantic Data Model in those platforms could also be implemented in order to provide native semantic 3D content accessibility.