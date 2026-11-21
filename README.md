# morta_mobprog
 
**Name:** Marvish Jerrime Morta
**Section:** INF246
 
## Lab Activity 1: discussion
 
### Integrating the image into newsfeed_card.dart
 
I added an optional `imageUrl` field to `NewsFeedCard` next to the existing `hasImage` flag. The post image is built with the `Image` widget (`Image.network`, or `Image.asset` for a local file) and placed between the post content and the like/comment row. The `Image` widget uses `fit: BoxFit.cover` and a width and height set with ScreenUtil, so the picture fills the card and stays responsive across screen sizes. An `errorBuilder` and a `loadingBuilder` show a `Placeholder`, so a broken link or a slow connection does not break the layout.
 
### Making it dynamic
 
Whether a post shows an image is decided by the `hasImage` boolean. In the build method, the card checks it with a conditional: if `hasImage` is true, it renders the image widget (`if (hasImage) _buildImage()`); otherwise nothing is rendered, so the post takes no space and a text-only post looks normal. Because `hasImage` defaults to `false`, existing posts such as "Kamusta" need no changes, while a post such as "Kicking off the holiday season with ICpEP-NCR!" sets `hasImage: true` in `newsfeed_screen.dart`. The same card widget is reused for every post, and each post decides what it shows through its constructor arguments.
 
### Other enhancements
 
- **Enhancement 1:** Image area uses the `Image` widget with a `Placeholder` fallback.
- **Enhancement 2:** The user profile icon is now a `CircleAvatar`.
- **Enhancement 3:** The like, comment and share buttons are widget-based (`InkWell` with an `Icon` and a `CustomText` label), and the like button shows only the number of likes.
