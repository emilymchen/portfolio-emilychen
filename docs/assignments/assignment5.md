---
title: "Assignment 5: Frontend Design & Implementation"
layout: doc
---

# Assignment 4: Frontend Design & Implementation

## Heuristic Evaluation

https://www.figma.com/design/fbNzoYqpThmLuCrPiZCmdR/ReWear?node-id=0-1&node-type=canvas&t=9ZqHIwzIbiTJutxC-0

### Usability Criteria:

1. **Discoverability**:

-   The interface is relatively straightforward in terms of overall structure and labeling, with clear sections like "My Closet", "Explore", and "Inbox", with icons that help the user understand what each section represents.
-   Some parts of the interface, particularly in the closet, could benefit from more intuitive explanations or explanatory tooltips to help users quickly understand their functionality.
-   In particular, an explanation of what the donation box is, and what an OOTD is and how to post one, could be helpful for users that are new to the platform.
-   Adding more visual cues like icons or arrows could guide users toward important actions, like a plus button/icon near the "Post Your Outfit" button to indicate that that's where users can create a new outfit post.

2. **Safety**:

-   I actually missed a lot of risky actions that should still get included in my wireframes, like deleting items or posts, so these should definitely get added in the final design! Actions like those, along with actions like listing items for donation or posting an outfit of the day, could benefit from having safeguards such as confirmation dialogs.
-   Adding a confirmation prompt before completing these actions could prevent accidental actions, such as asking "Are you sure you want to donate this item?" before an item is donated.
-   This could also apply to any actions such as editing/updating a clothing article, or even when trying to navigate away from a clothing article that's been edited, by adding a popup that says something like "Are you sure you want to leave? Your unsaved changes will be lost".
-   I could also add form validation for certain parts of the app that expect the input to take on a certain form, like when setting donation locations, so that only valid and reasonable locations/addresses may be input.
-   Additionally, adding visual feedback for when actions are completed could be useful to users as well (e.g. "Your item has successfully been listed for donation").

### Physical Heuristics:

1. **Gestalt Principles**:

-   Pretty logical structure for layout, with grid format for items in the closet, and scrolling with multiple posts visible at once for browsing OOTDs or clothes listed for donation
-   Both formats are intuitive to their functionality in the application, but appear distinct from each other, which makes it easier for users to visually parse the information, while providing a distinction between the two modes of browsing
-   In the Closet section, the clothing categories are grouped together that indicates to users that they are a part of the closet as a whole but still accessible as individual sections
-   The settings could do a better job of categorizing the types of options/information so that users can know what they're modifying and how it relates to the use of the application more clearly
-   The spacing in the posts could be improved, since it's a bit cluttered and unclear what the different texts indicate and how their functionality works, so working with the whitespace and sizing could improve that
-   The modal windows in the closet (e.g. tops section) are consistent, which helps users understand that they're in a selection view and allows them to interact with different categories of items
-   The iconography isn't super consistent across the app

2. **Situational Context**:

-   The top navigation bar is persistent across all windows, which makes it easier for users to orient themselves and quickly return to main sections of the app, so they can jump between sections without confusion
-   However, I'm missing a way for users to tell what section they're currently in. Adding a highlight in the top navigation bar to what section the user is currently in would help them contextualize where in the application they are
-   The back arrow in several sections helps users understand how to navigate back to a previous step, which is helpful when viewing a single item from a list of posts or clothing articles
-   The consistent layout helps users understand their context based on the structure of the page
-   I could also add breadcrumbs for places where users are exploring multiple nested levels, like Explore > Donation Items > T-shirt so that users can understand their path clearly
-   The Donation Box groups relevant actions in one place, which helps the user understand that they're in a space that's dedicated to donation management
-   The OOTD posting feature is also a clean interface where they can enter specific details, which isolates the task of posting from the rest of the interface
-   Some more contextual suggestions could be provided based on a given task, such as suggesting related features in the OOTD posting section like viewing outfits similar to yours, or see how others styled a certain item
-   Icons and labels are used pretty effectively to communicate the current state as well
-   Confirmation of actions would be helpful so users know their action has been processed

### Linguistic Level:

1. **Speak a User’s Language**:

-   The labels are mostly understandable by the user yet brief (e.g Browse Donation Items), but the term OOTD is used without an explicit explanation anywhere, which could be confusing to newer users
-   The donation box concept is never really explained to users either, so a brief description of what the section is used for could be helpful as well
-   Common labels are used for common features, like 'Explore' and 'Inbox', and the settings being managed in the profile picture tab is also an intuitive/commonly used design language
-   Stronger action buttons are also colored differently (e.g. message a user vs donation closet when looking at a clothing article)

2. **Information Scent**:

-   section names offer strong information scent by making it easy for users to infer what kind of actions they'd be able to perform in each section
-   Labels on action buttons make it obvious what those buttons will do
-   Sections like the donation explore could offer more information scent through better filtering or sorting clues
-   Adding preview information in sections explaining what they are could also give users more context about what section they are interacting with
-   Progressive disclosure is pretty well applied, so only necessary information (e.g. image of a clothing article for donation) is shown at first, and more details are revealed as users interact with the system (click on a clothing article to see its brand, size, etc). This makes the interface less overwhelming and helps users focus on their current task.

## Implementation
