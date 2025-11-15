- updated to mongoose
- commented out the stuff in config/database.js

- changed all the ```.findOne``` statements from callback to ```.then``` statements
    - passport.js
    - auth.js
    - _posts.js might need to be updated later_

- changed all the ```.findById``` statements from callback to ```.then``` statements
    - passport.js

- __Delete: __In posts.js, replaced ```Post.remove()``` with ```Post.findOneAndDelete```. Changed options in cloudinary to { invalidate:true }.
    - Not sure if cloudinary fix works, it did remove the image by the morning.

- __Fixing the username/email: __ In posts.js ```.getProfile``` fixed the call for the user to deliver the entire document of the user.
```
const user = await User.findOne({ _id: req.user })
console.log(user)
const posts = await Post.find({ user: req.user.id });
res.render("profile.ejs", { posts: posts, user });
```

#### known errors
- duplicate sign ups crash the server