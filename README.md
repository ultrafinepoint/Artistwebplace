# artistwebplace

## Build Setup

```bash
# install dependencies
$ npm install

# start server with at localhost:3000
$ npm run dev
```
For detailed explanation on how things work, check out the [documentation](https://nuxtjs.org).

### Content
Metadata and a richtext field is what type of content this folder contains.
*This folder is not for images* --> See 'Assets' below.
Write your database of artwork here, 

#### How to write content
You can use markdown and specify a front-matter!
Refer to the example file as a template or look up these things on google.

#### File org.
In a folder convention as such:
*"/content/artwork/{ artwork.title }.md"*
- Remember this variable ( the one in brackets )
- you will need it for the assets folder

### Assets
Here you will store your media files.
These files paths are used when loading images on pages.
*It is important you follow the folder + naming convention.*
If an image is in the wrong place it will not load upon screen.

#### File org.
"/assets/" is the base folder.
Your artwork images are nested as such:
*"/assets/{ artwork.title }/original-1.jpg"*
please increment with total amount of images uploading per project

### Pages
Yup
