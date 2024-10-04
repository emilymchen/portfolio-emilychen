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

## App Definition

    concept ReWear
        include Authenticating
        include Sessioning [Authenticating.User]
        include Cataloging [Sessioning.User]
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
