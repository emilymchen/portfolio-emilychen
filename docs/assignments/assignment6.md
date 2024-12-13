---
title: "Assignment 6: User Testing & Analysis"
layout: doc
---

# Assignment 6: User Testing & Analysis

## Prepopulating Data

Link to website: https://rewear-frontend.vercel.app/

I populated my website with a couple of users and their respective outfit of the days (OOTDs) and donation items.

You can log into the sample account below:

```
username: emily
password: asdf
```

### OOTDs

![OOTDs](/../assets/images/ootds.png)

### Donation Items

![donations](/../assets/images/donations.png)

### Closet Items

![closet](/../assets/images/closet.png)

## User Instructions

| **Title**                                    | **User Instruction**                                                                                                                                                                                                                          | **Rationale**                                                                                                                                                                                                     |
| -------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Add articles of clothing to the closet**   | Register for an account, and add a top, a bottom, shoes, and an accessory to your closet.                                                                                                                                                     | Tests how intuitive the flow of adding items to the closet is, and whether users can correctly input and categorize a new item. Additionally, evaluates how convenient it is to add multiple items in succession. |
| **List an article of clothing for donation** | List one of the items in your closet for donation. Follow-up: Was the donation process intuitive and easy to find? What other additions could make the donation process more convenient for you?                                              | Tests how intuitive and straightforward it is to post an item for donation directly from the closet page.                                                                                                         |
| **Post an OOTD**                             | Post an outfit of the day (OOTD) using the items in your closet. Follow-up: How useful was the filtering by category feature? Was the process easy and intuitive? Did you feel there were enough options for expressing yourself in the post? | Ensures users can combine items from their closet into an OOTD post seamlessly and evaluates the ease of creating posts, including selecting items from a dynamic list.                                           |
| **Browse the OOTDs**                         | Browse the OOTDs posted by others, and filter by a specific user. Follow-up: How was the browsing experience? Are there other options for exploring that you would have liked?                                                                | Assesses the usability of the outfit explore page and the functionality of filtering and searching by user.                                                                                                       |
| **Request a donation item**                  | Browse the listed donation items, find one you like, and inquire about it. Follow-up: How was the experience of looking for a donation item? What additional information could have been helpful?                                             | Examines whether users can identify donation items and use the messaging system to initiate a request, focusing on the clarity of actions and feedback.                                                           |
| **Delete your OOTD post**                    | Delete the OOTD post you created earlier.                                                                                                                                                                                                     | Tests how straightforward it is to manage and delete previously created content, ensuring users feel confident performing this action.                                                                            |
| **Respond to a donation request**            | Respond to a message requesting your donation item by agreeing to donate it.                                                                                                                                                                  | Evaluates how users manage incoming communication and whether the system design supports easy, clear follow-up interactions for donation agreements.                                                              |
| **Mark an item as donated**                  | Mark the item as donated after responding to a request.                                                                                                                                                                                       | Ensures users understand how to finalize the donation process and navigate the completion of an item’s lifecycle states effectively in the app.                                                                   |
| **Favorite an OOTD**                         | Favorite and unfavorite an OOTD.                                                                                                                                                                                                              | Tests the intuitiveness and ease of using the favoriting feature, allowing users to save posts for style inspiration.                                                                                             |

## Interview Reports

### Report 1: Participant - Puloma

Puloma is a college student with an interest in sustainable fashion. She was enthusiastic about the app’s premise and shared her thoughts throughout the session. When Puloma began adding articles of clothing to her closet, she found the process straightforward, noting that the interface for inputting an item’s type and category was clear. However, she quickly pointed out that adding multiple types of items in a row felt cumbersome. “I wanted to switch from adding a top to shoes,” she remarked, “but there wasn’t a quick way to do that without going back and re-selecting the category.” She suggested that a toggle or a streamlined flow for switching item types would make the experience more fluid.

When listing an item for donation, Puloma initially clicked on the donation box instead of navigating directly to the item in her closet. She described this as “a small hiccup” but was able to figure it out on her own. She mentioned, “The donation process itself was really simple once I got there, but I wish it were easier to find from the start.” Puloma suggested that including a direct donation option or clearer pathways from the closet page/from the donation box might help streamline this step.

For posting an Outfit of the Day (OOTD), Puloma encountered some confusion with the caption box. She didn’t immediately realize its purpose, commenting, “I thought it was for tagging items at first, not for writing a caption.” Once this was clarified, she appreciated the functionality but noted that it would be nice to have options for backdating posts or adding entries for previous days. Puloma also struggled slightly with the modal for selecting clothing items, particularly when scrolling through the ‘all’ section. “I couldn’t see everything, so it felt a bit clunky,” she explained. "I also couldn't see the post button on my screen without zooming out or toggling to a different clothing category." She recommended adding a scrolling feature or better organization by category. Overall though, she had a generally positive experience with the app and provided very helpful feedback!

### Report 2: Participant - Sydney

Sydney, a college student trying to cut down on her wardrobe, shared her thoughts of the app throughout the interview. She quickly understood the process for adding clothing items to the closet, but like Puloma, found the flow to be a bit repetitive/not fluid when switching between categories. “I added a shirt and wanted to add pants right after, but it felt like starting over every time,” she said. She also mentioned that adding fields like brand, size, and condition could make the app more useful, saying, “I usually note the condition of items I plan to donate, so having that as an option would be great!”

When exploring the donation feature (both messaging an owner and messaging as a recipient), Sydney found the listing process simple but suggested adding prompts for inputting additional details like pickup locations or timing. “The donation messaging works, but I wasn’t sure what kind of information I was supposed to include,” she shared. She found searching for donation items straightforward but noted that filtering options -- such as by size or condition -- would make the experience more efficient. “I liked that I could browse all the items, but being able to narrow it down would save a lot of time,” she added.

Sydney had a positive experience with browsing OOTDs and appreciated the filtering by user feature. However, she felt that additional filters like style, weather, or tags would help users find specific fashion inspiration. “If I wanted to see outfits for a rainy day, I’d love a weather filter,” she suggested. Deleting an OOTD post was simple for her, though she thought a confirmation modal would provide reassurance in case of accidental clicks.

She also noted that she would like to see a designated place for a list of her favorited items, and that favoriting both donation listings in addition to OOTDs would be useful so she could mark items she was potentially interested in for later reference. Other than that, she found marking items for donation to be straightforward as well.

#### Observations for Improvement:

-   **Toggle for Adding Items (Conceptual, Moderate):** Switching between item types during the adding process was inconvenient, making it less efficient for users adding diverse items.
-   **Improved OOTD Modal (Physical, Major):** The lack of a scrolling feature in the ‘all’ section made item selection difficult since they cannot see all the items on their screen or the post button, disrupting the user’s flow.
-   **Donation Messaging Prompts (Linguistic, Moderate):** Providing guidance on what to include in messages (e.g., pickup details) could make the donation process smoother.
-   **Enhanced Filtering for Donation Items (Conceptual, Moderate):** Adding filters for size, condition, or type would streamline the browsing experience.
-   **Confirmation Modal for Post Deletion (Physical, Minor):** Adding a confirmation step would reduce the chance of accidental deletions.
