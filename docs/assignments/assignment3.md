---
title: "Assignment 3: Convergent Design"
layout: doc
---

# Assignment 3: Convergent Design

Collaborator: ChatGPT for help with ideation, summarization, feedback on design tradeoffs

## Pitch

> ### Introducing ReWear – Where Style Meets Sustainability.

Imagine a world where your your closet isn't just a place for forgotten, unworn clothes -- it's a platform for creativity, connection, and conscious fashion choices. That's what ReWear is all about. Designed for fashion-forward people who not only want to look good, but want to do good, ReWear makes it easy to build a sustainable wardrobe without sacrificing your personal style.

**Here’s how it works:**

Start by **cataloging your wardrobe**: upload your clothes, piece by piece, into your virtual closet.

Ready to declutter? **List your clothes for donation** in just a few taps. Local users can browse, message you, and **set up a pickup or swap** -- no waste, no hassle, just sustainable exchanges.

Want to share your style? Snap a photo, tag your items, and post your **Outfit of the Day (OOTD)** for the world to see. And if you’re looking for inspiration, you can **browse other users' outfits**, get styling tips, and see how they’re remixing their own wardrobe.

And it’s all backed by an active community. **Drop a comment, favorite a post, save looks for later** -- ReWear is your one-stop shop where eco-friendly fashion meets social connection.

It’s time to give your wardrobe a second life. Let’s reimagine, reuse, and ReWear -- because when you do good, you look good.

## Functional Design: Concepts

### 1. `Authenticating`

#### Purpose:

authenticate users so that app users correspond to people and only valid users can access the app and perform actions

#### Operational Principle:

after a user registers with a username and password pair, they can authenticate themselves as that user by providing that username and password pair.

#### State:

registered: **set** User
username, password: registered -> **one** String

#### Actions:

```
register(username, password)
    registered += (username, password)

unregister(username):
    registered -= username

authenticate(username, password):
    return (username, password) in registered
```

### 2. `Sessioning`

#### Purpose:

enable authenticated actions for a period of time

#### Operational Principle:

after a session starts and before it ends, the getUser action returns the user identified at the start

<!-- If a user logs in, a session is created. As long as the session is valid (within the set period), the user can perform actions without needing to log in again. -->

#### State:

active: **set** Session
user: active -> one User

#### Actions:

```
start (user: User, __out__ sess: Session):
    active += user

getUser (sess: Session, __out__ user: User):
    user in active if Session.user == user

end (sess: Session):
    active -= sess

```

### 3. `Cataloging`

#### Purpose:

to allow users to upload, modify, and manage collections of items

#### Operational Principle:

if a user uploads an item, the item is stored in their catalog and can be accessed and modified at a later time

<!--
If a user uploads a clothing item, the item is stored in their virtual closet and can be accessed later for viewing, tagging, or donating. -->

#### State:

catalog: **one** User -> **set** Item

#### Actions:

```
addToCatalog(u: User, item: Item):
    catalog[u] += item

removeFromCatalog(u: User, item: Item)
    catalog[u] -= item

getCatalog(u: User)
    return catalog[u]
```

### 4. `Posting`

#### Purpose:

to allow users to share content

#### Operational Principle:

if a user creates a post, the post becomes visible to other users in the relevant feed

<!--
If a user creates a post, the post becomes visible to other users in the relevant feed (OOTD feed for outfits or donation feed for items).
Users can tag clothing items in OOTD posts or mark items for donation. -->

#### State:

posts: **one** User -> **set** Post

#### Actions:

```
createPost(u: User, p: Post):
    posts[u] += p

editPost(u: User, oldPost: Post, newPost: Post)
    posts[u] -= oldPost
    posts[u] += newPost

deletePost(u: User, p: Post):
    posts[u] -= p

getPosts(u: User):
    return posts[u]
```

### 5. `Commenting`

#### Purpose:

users can comment in reply to other item

#### Operational Principle:

after making a comment on an item, when a user brings up that item, the comment is also included with the item

#### State:

comments: **one** Item -> **set** Comment

#### Actions:

```
addComment(item: Item, c: Comment)
    comments[item] += c

deleteComment(item: Item, c: Comment)
    comments[item] -= c

getComments(item: Item):
    return comments[item]
```

### 6. `Favoriting`

#### Purpose:

users can keep track of items to return to later

#### Operational Principle:

after a user marks an item as favorited, they can quickly find it again in a list of favorited items

<!-- If a user saves an OOTD or donation post, it is stored in their list of saved posts for later viewing. -->

#### State:

favoritedItems: **one** User -> **set** Item

#### Actions:

```
favoriteItem(u: User, i: Item):
    favoriteItems[u] += i

unfavoriteItem(u: User, i: Item):
    favoriteItems[u] -= i

getFavoritedItems(u: User):
    return favoritedItems[u]
```

### 7. `Messaging`

#### Purpose:

users can send individual, private information to other users

#### Operational Principle:

after a user sends a message to another user with some content, the receiving user can view the content of the message

<!-- If a user sends a message to another user, the recipient receives the message and can reply to coordinate further. -->

#### State:

messages: (User, User) -> **set** Message

#### Actions:

```
sendMessage(sender: User, recipient: User, message: Message):
    messages[sender, recipient] += message

getMessages(u: User):
    return message for message in messages if message[0] == u or message[1] == u
```

## Functional Design: Synchronizations

### Subsets

\{Authenticating\}

\{Authenticating, Sessioning\}

\{Authenticating, Sessioning, Cataloging\}

\{Authenticating, Sessioning, Cataloging, Posting\}

\{Authenticating, Sessioning, Cataloging, Posting, Messaging\}

\{Authenticating, Sessioning, Cataloging, Posting, Favoriting\}

\{Authenticating, Sessioning, Cataloging, Posting, Commenting\}

### Synchronizations

    concept ReWear
        include Authenticating
        include Sessioning [Authenticating.User]
        include Cataloging [Sessioning.User]
        include Posting [Sessioning.User, Cataloging.Item]
        include Commenting [Posting.Post]
        include Message [Sessioning.User]
        include Favoriting [Sessioning.User, Posting.Post]

```
__sync__ register(username, password: String, __out__ user: User)
    Authenticating.register(username, password)
```

```
__sync__ login(username, password: String, __out__ user: User, __out__ session: Session)
    Authenticating.authenticate(username, password)
    Sessioning.start(user, session)
```

```
__sync__ logout(session: Session)
    Sessioning.end(session)
```

```
__sync__ addToCatalog(user: User, item: Item)
    Sessioning.getUser(session, user)
    Cataloging.addToCatalog(user, item)
```

```
__sync__ removeFromCatalog(user: User, item: Item)
    Sessioning.getUser(session, user)
    Cataloging.removeFromCatalog(user, item)
```

```
__sync__ createPost(user: User, p: Post)
    Sessioning.getUser(session, user)
    Posting.createPost(user, p)
```

```
__sync__ editPost(user: User, oldPost: Post, newPost: Post)
    Sessioning.getUser(session, user)
    Posting.editPost(user, oldPost, newPost)
```

```
__sync__ deletePost(user: User, p: Post)
    Sessioning.getUser(session, user)
    Posting.deletePost(user, p)
```

```
__sync__ favoriteItem(user: User, item: Item)
    Sessioning.getUser(session, user)
    Favoriting.favoriteItem(user, item)
```

```
__sync__ addComment(user: User, item: Item, comment: Comment)
    Sessioning.getUser(session, user)
    Commenting.addComment(item, comment)
```

```
__sync__ sendMessage(sender: User, recipient: User, message: Message)
    Sessioning.getUser(session, sender)
    Messaging.sendMessage(sender, recipient, message)
```

## Functional Design: Dependency Diagram

![dependency diagram](/../assets/images/dependency_diagram.jpg)

## Wireframes

![wireframes](/../assets/images/rewear_wireframes.png)

[Link to wireframes](https://www.figma.com/design/fbNzoYqpThmLuCrPiZCmdR/ReWear?node-id=0-1&t=UPBx4oyxHrrMfKPc-1)

The wireframes are pretty extensive and include some features that are beyond the scope of what I'd like to prioritize for the MVP. The rough order of priority for frames/workflows I am considering for the MVP are:

1. uploading clothes and managing those in the closet
2. posting clothes for donation
3. browsing clothes listed for donation and messaging the owner
   -- this is the point I am targeting for absolute MVP, ideally would get to #4 as well
4. posting OOTDs and browsing other users' OOTDs
5. favoriting OOTDs/items
6. commenting on OOTDs -- 2nd target
7. searching, sorting, filtering clothes listed for donation
8. location-based visibility of other users' donation boxes
9. viewing your past OOTDs

## Design Tradeoffs

#### 1. Location Privacy vs. Ease of Use

The more precise the location, the easier it is to coordinate donation pickups, but this compromises privacy.

Options:

-   Show exact user locations for easy meetups
-   Use approximate locations to protect privacy but reduce precision
-   Allow users to control location precision

**Rationale:**
I opted for approximate locations (e.g., a 5-10 mile radius ideally depending on location density) to balance privacy and ease of coordination. Exact locations pose safety risks, while too much abstraction hurts search accuracy. Users can control who sees their donation box (e.g., friends only or public), and a safety warning will encourage meeting in public places rather than residences.

#### 2. Simplified Posting vs. Detailed Cataloging

How much information should users provide when uploading items to their closet or donation list?

**Options:**

-   Quick and easy uploads with minimal details
-   Require detailed information (size, condition, brand, etc.)
-   Tiered system: quick uploads with optional details later

**Rationale:**

I chose a tiered approach to minimize friction. Quick uploads make the app accessible, while allowing users to add details later provides flexibility for organization or buyers looking for specifics. A popup will recommend adding details, but users can still list items quickly for convenience.

#### 3. Balancing the donator/receiver/explorer experience

ReWear serves clothing donators, receivers, and fashion explorers. How should their experiences be balanced?

**Options:**

-   Create separate sections and distinct user flows for each
-   Unified experience with integrated pages
-   Allow users to toggle their focus/switch between “Donator,” “Receiver,” and “Explorer” modes

**Rationale:**

I integrated experiences into the same core pages, since having to toggle between focuses or separate sections is disruptive. Explore has tabs for OOTDs and donation items, with donation boxes are accessible from OOTDs. The closet page houses both OOTD posting and item donations, keeping wardrobe management unified without disrupting user flows.
