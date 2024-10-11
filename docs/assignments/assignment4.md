---
title: "Assignment 4: Backend Design & Implementation"
layout: doc
---

# Assignment 4: Backend Design & Implementation

## Concepts + Abstract Data Models

### 1. `Authenticating`

#### State:

-   `registered: __set__ User`
-   `username, password: registered -> __one__ String`

#### Actions:

```
register(username, password)
    registered += (username, password)

unregister(username):
    registered -= username

authenticate(username, password):
    return (username, password) in registered
```

### 2. `Sessioning[User]`

#### State:

-   `active: __set__ Session`
-   `user: active -> __one__ User`

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

#### State:

-   `catalog: __one__ User -> __set__ Item`

#### Actions:

```
addToCatalog(u: User, item: Item):
    catalog[u] += item

removeFromCatalog(u: User, item: Item)
    catalog[u] -= item

getCatalog(u: User)
    return catalog[u]
```

### 4. `Posting[User, Item]`

#### State:

-   `posts: __one__ User -> __set__ Post`
-   `time: Post -> __one__ Date`
-   `author: Post -> __one__ User`
-   `content: Post -> __some__ Item`
-   `title: Post -> __one__ String`
-   `caption: Post -> __one__ String`

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

### 5. `Labeling` [NEW; replacing commenting]

#### Purpose:

users can tag items with a descriptive label to track information about an item

#### Operational Principle:

after a user adds a label to an item, the label becomes associated with the item and can be used for categorization/filtering

#### State:

-   `labels: Item -> __set__ Label`
-   `name: Label -> String`

#### Actions:

```
addItemLabel(item: Item, label: Label):
    labels[item] += label

removeItemLabel(item: Item, label: Label):
    labels[item] -= label

getItemLabels(item: Item):
    return labels[item]

editItemLabels(item: Item, oldLabel: Label, newLabel: Label):
    labels[item] -= oldLabel
    labels[item] += newLabel

```

<!--
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
``` -->

### 6. `Favoriting`

#### State:

-   `favoritedItems: __one__ User -> __set__ Item`

#### Actions:

```
favoriteItem(u: User, i: Item):
    favoriteItems[u] += i

unfavoriteItem(u: User, i: Item):
    favoriteItems[u] -= i

getFavoritedItems(u: User):
    return favoritedItems[u]
```

### 7. `Messaging[User]`

#### State:

-   `messages: (User, User) -> __set__ Message`
-   `to: Message -> one User`
-   `from: Message -> one User`
-   `time: Message -> one Date`
-   `content: Message -> one String`

#### Actions:

```
sendMessage(sender: User, recipient: User, message: Message):
    messages[sender, recipient] += message

getMessages(u: User):
    return message for message in messages if message[0] == u or message[1] == u
```

### 8. `Donating[User, Item]`

Purpose:
The Donating concept allows users to manage the donation process for items they no longer need. Users can mark items from their catalog as available for donation, unlist them if they change their mind, and mark them as donated once another user has claimed the item.

Operational Principle:
After a user lists an item for donation, it becomes visible as available to other users for claiming. Once the item is claimed, the user can mark it as donated. This process helps streamline giving away items and ensures the item’s donation status is clear at all times.

#### State:

-   donations: **one** User -> **set** Item
-   status: Item -> **one** DonationStatus (where DonationStatus is one of NotListed, ListedForDonation, or Donated)

#### Actions:

```
listForDonation(u: User, item: Item):
    donations[u] += item
    status[item] = DonationStatus.ListedForDonation

unlistForDonation(u: User, item: Item):
    status[item] = DonationStatus.NotListed

markAsDonated(u: User, item: Item):
    status[item] = DonationStatus.Donated

getListedItems(u: User):
    return items in donations[u] where status == DonationStatus.ListedForDonation

getDonatedItems(u: User):
    return items in donations[u] where status == DonationStatus.Donated

getDonationStatus(u: User, item: Item):
    return status[item]
```

## App Definition

    concept ReWear
        include Authenticating
        include Sessioning [Authenticating.User]
        include Cataloging [Sessioning.User]
        include Donating
        include Posting [Sessioning.User, Cataloging.Item]
        include Labeling [Cataloging.Item]
        include Message [Sessioning.User]
        include Favoriting [Sessioning.User, Posting.Post]

## Data Model

![data_model](/../assets/images/data-model.jpeg)

## Deployed Website

https://rewear.vercel.app/

https://github.com/emilymchen/rewear

## Routes outline

https://github.com/emilymchen/rewear/blob/main/server/routes.ts

## Design Reflection

During the implementation of the backend service, I realized I never set up a way for users to mark items for donation, so I introduced a new **Donating** concept that allows users to manage the donation state of their item (unlisted, listed for donation, and donated, where listed means it's available for other users to claim, and donated means another user has picked up the item).

I also realized I left categories and labeling ambiguous. I want users to be able to mark their clothing items as being tops, bottoms, shoes, etc., and also to be able to label things like their brand, size, and color. Initially, I thought these could both be handled in the same new concept of Labeling, but I realized that the categories themselves would be better handled as part of the Cataloging concept, since those are not determined by the user, so I added in a new Labeling concept to replace Commenting, since that didn't seem as critical to the function of my program.

I also found an ambiguity where I didn't specify the different types of posts, OOTD or donation item.

sorry this assignment is kinda bad i am having a rough week :,)
