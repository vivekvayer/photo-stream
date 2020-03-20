![Photo Stream Social Preview](https://repository-images.githubusercontent.com/244708193/8710f480-6010-11ea-9fd6-41bdaea7ab02)

# Photo Stream -Your photos and data belong to you. Own it.

## WHAT is it?
- A home for your photos; browse some [examples](#examples)
- Open Source code developed by [@maxvoltar](https://twitter.com/maxvoltar) and [friends](#credits) who DO NOT monetize off Photo Stream.
- A gift of functioning code. Note this is not a tool with 3rd party support!

## WHY use it?
- Photo Stream is free.
- An alternative to WordPress.org.
- Its a new tool with a tight knit community; join to engage and contribute.
- Photo Stream sits on Github; a key toolkit in the world of development. Learn to use Github by using Photo Stream!

## HOW to install?
- [The easy way](#The-easy-way)
- [The techy way](#The-techy-way)

## HOW to use?
   - [Basic user instructions](#basic-user-instructions)
   - [Advanced user instructions](#advanced-user-instructions)

## Linking to external sites
   - [Basic links](#basic-links)
   - [Advanced links](#advanced-links)
   
## Micellaneous
- [Known issues](#known-issues)
- [Features](#features)


## How to Install?
### The easy way

1. Click on Fork (top right side) to automatically duplicate the code to your own Github.
2. Clear the `photos/original` directory (I deleted each photo, but feel free to do it faster in any way you know how).
3. Add your own photos ensuring that they are jpg files and NOT JPG files.
4. Deploy your forked code to [Netlify](https://netlify.com). Netlify is free by default. Upgrade if you want to your own domain and analytics)
5. NOTE this is a double check. In your build & deploy settings, set "Build command" to `jekyll build` and "Publish directory" to `_site/`.
6. Thats it. Share your link with friends!

### The techy way

Check to see if you have Ruby installed (`ruby -v`). If you don't, you can follow the installation instructions provided [here](https://www.ruby-lang.org/en/documentation/installation/).

Next you'll have to install [Jekyll](https://jekyllrb.com) (a simple `gem install bundler jekyll` should suffice).

```sh
bundle install
```

You'll also need some additional dependencies:

```sh
# Make sure xcode CLT is installed first:
xcode-select --install

# This takes a while. Plug your laptop in and go grab a coffee, a book, or just
# like, take a sec away from the computer and breathe for a bit.
brew install glib vips
```

## How to use

### Basic User Instructions
- Add a photo (not resized) in the `photos/originals` directory.
- Optionally you can name each photo, which will appear as the title of the photo page and in the RSS feed.
- Thats it! Your hosting service should periodically update based on the photos/original directory in your Github 

### Advanced User Instructions
This command will serve the static page on your local machine. http://localhost:4000
```sh
bundle exec jekyll serve
```

You can also statically build your site to be uploaded to a regular webhost. 
```sh
bundle exec jekyll build
```
Now upload the contents of the _site/ directory to your webserver.

#### Automating the build & upload with rsync
Copy the bash script 'build-n-rsync.sh' from the _script directory to the root of your photo-stream folder. 
Fill in the required credentials & run the script. It will build & upload your site. 

## Linking to external sites

### Basic links

Edit limited items in the file `/_config.yml`:

- `title`: The title of your photo stream
- `email`: Your email address (this line is optional, you can remove it)
- `author`
    - `name`: Your name
    - `email`: Your email address (optional)
    - `website`: Your website (could be the address of this photo stream)
- `description`: Description of your photo stream
- `baseurl`: Should be `""` **⚠️ Do not change unless you know what you're doing**
- `url`: Where will this photo stream live (example: `https://maxvoltar.photo`)
- `twitter_username`: Your Twitter username
- `github_username`: Your Github username
- `instagram_username`: Your Instagram username

Don't include the `@`-part of your social handles. By default links to your Github and Instagram profiles are hidden. You can uncomment these by going into `/index.html`. There, you can also add links to wherever you want. Just add more `<li>`'s with `class="link"` to the `<ul class="links">` list.

### Advanced links

Before publishing your website, Jekyll will resize your photos into 3 different buckets:

- `/photos/large`: These are only shown when a user navigates to a photo page. By default these are resized to a maximum of 2048 wide and 2048 tall. If you wish, you can change these by changing the values in `/_config.yml` (by default they look something like this: `resize_to_limit: [2048, 2048]`).
- `/photos/thumbnail`: These are used in the grid. Photo Stream will load all thumbnails above the fold, then more as you scroll down; all to save bandwidth. Standard size for these is 640 by 640 (max), but you can also change this if needed.
- `/photos/tint`: What you see while the page loads its first batch of thumbnails, also used as the background for photo pages. **⚠️ Do not make changes to the tint versions in your config file.**

## Features

- Lazy loading
- Only load larger resolutions when needed (to save on bandwidth)
- Photo tints
- Keyboard shortcuts
- Unique URL's for photos
- RSS feed (Which you can plug into [IFTTT](https://ifttt.com) and set up auto-posting to most social networks, like I've done [here](https://twitter.com/maxvoltar_photo). Make sure you select "Post a tweet with image" when setting it up to embed the photo.)
- Drag, drop, commit workflow ([learn more about how to add photos to your stream](https://github.com/maxvoltar/photo-stream#how-to-use))
- Optimized light and dark themes (auto-enabled depending on your OS preferences)
- Optional: Links to your social networks


## Examples

- [maxvoltar.photo](https://maxvoltar.photo)
- [joeyabanks.photo](https://joeyabanks.photo)
- [photos.alexbaldwin.com](https://photos.alexbaldwin.com)
- [scotts.camera](https://scotts.camera)
- [jad.photos](https://jad.photos)
- [photo.silvandaehn.com](https://photo.silvandaehn.com/)

## Credits

- [@maxvoltar](https://github.com/maxvoltar)
- [@benubois](https://github.com/benubois)
- [@mattsacks](https://github.com/mattsacks)
- [@pjaspers](https://github.com/pjaspers)
- [@cloudz](https://github.com/cloudz)

## Known issues

- You might see a `VIPS-WARNING` message while running `jekyll serve`. This is [a bug in libvips](https://github.com/libvips/libvips/issues/394#issuecomment-359780578) that's being tracked, but it's harmless.
