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

### Flaws / Opportunities for Improvement:

#### Toggle for Adding Items

**Level:** Conceptual  
**Severity:** Moderate  
**Flaw/Opportunity:** Puloma and Sydney both found it inconvenient to add multiple types of clothing items in succession, as there is no quick way to toggle between categories such as tops, bottoms, shoes, and accessories. This disruption makes the process inefficient for users adding diverse items at once.  
**Why It’s Occurring:** The current design assumes users will add items of a single type repeatedly, without accounting for scenarios where users need to switch categories frequently. This lack of a persistent toggle or shortcut adds unnecessary friction to the flow.  
**Proposed Solution:** Introduce a category toggle or dropdown menu that allows users to switch item types without leaving the current screen. Alternatively, implement a bulk-add feature where users can input multiple items across different categories within a single form, streamlining the process.

#### Improved OOTD Modal

**Level:** Physical  
**Severity:** Major  
**Flaw/Opportunity:** The modal used for selecting clothing articles in an OOTD post is difficult to navigate when in the "all" section, as it lacks a scrolling feature. This limitation prevents users from viewing all items in their closet and can obstruct the post button, interrupting the posting flow.  
**Why It’s Occurring:** The modal is not responsive and goes off the screen when there are many items, which does not accommodate larger inventories or ensure all interface elements remain accessible on-screen.
**Proposed Solution:** Enable vertical scrolling within the modal to allow users to view all items and interact with buttons without obstruction.

#### Donation Messaging Prompts

**Level:** Linguistic  
**Severity:** Moderate  
**Flaw/Opportunity:** When requesting a donation item, users were unsure what information to include, such as pickup location, time, or item details. This lack of guidance resulted in incomplete messages and the need for additional back-and-forth communication.  
**Why It’s Occurring:** The messaging interface does not provide prompts or suggestions, leaving users to guess what information is necessary for successful communication.  
**Proposed Solution:** Add placeholder text or a list of suggested prompts within the messaging box (e.g., "Include your preferred pickup time and location" or "Specify the item you're inquiring about"). A short checklist or tooltip near the form could further guide users and standardize interactions.

#### Enhanced Filtering for Donation Items

**Level:** Conceptual  
**Severity:** Moderate  
**Flaw/Opportunity:** Users browsing donation items found the experience inefficient due to the inability to filter by attributes such as size, condition, or type of clothing. This limitation made finding suitable items more time-consuming and frustrating.  
**Why It’s Occurring:** Filtering options are currently limited to broad categories, with no functionality for detailed attributes. This creates unnecessary friction when users have specific criteria in mind.  
**Proposed Solution:** Expand filtering functionality to include attributes such as size, condition, color, and brand. Implement a multi-filter interface where users can combine criteria (e.g., "size M + good condition") to streamline the browsing experience and reduce time spent searching.

### Confirmation Modal for Post Deletion

**Level:** Physical  
**Severity:** Minor  
**Flaw/Opportunity:** Deleting an OOTD post is currently a single-click action, increasing the likelihood of accidental deletions. Although users can recreate deleted posts, this adds unnecessary frustration and time.  
**Why It’s Occurring:** The system lacks a confirmation step for deletions, which can lead to errors if users click the delete button unintentionally.  
**Proposed Solution:** Add a confirmation modal that asks, "Are you sure you want to delete this post?" before completing the action. Optionally, include an “Undo” option immediately after deletion to further reduce the impact of accidental actions.
