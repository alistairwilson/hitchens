---
layout: post
title: How to Generate Numbered Headings and/or Lists in Ulysses
author: Alistair Wilson
category: Mac Apps
---
## What's Missing in Ulysses?
If you write long form pieces or complex manuscripts and you're on Mac, it's likely that Ulysses features heavily in your setup. Whilst it *is* powerful and has many nice features, it does lack two key features that tools like *MS Word* do have:
- Outline Numbered Lists
- Outline Numbered Headings

These two formatting features really do make complex or structured documents, especially technical or academic papers, a lot clearer and easily navigable.
![]()[image-1]()
  
Ulysses haven't been forthcoming on updates to the app to improve complex numbering to achieve this:
> 1
> 1.1
> 1.1.1
Thus, my workflow before doing this mod, was to export my document to `.docx` and then complete my final *list* and *headline* formatting touches in *MS Word*, whose gravitational pull I have been fighting against for a number of years… Just like you I bet!
Then recently I dug into the problem some more to see if I can come up with a fix until the feature exists natively in the editor. And a fix I did come up with.
## What to expect from this modification
If you follow this process, you will be able to output beautiful HTML documents which include outline numbered headings and outline numbered lists, without changing a thing in the editing experience.
This is a limited fix, as it works **ONLY for the HTML output option**, and not for Ulysses other output options like `.pdf` or `.docx`
**But…** When you open your rendered HTML document, you can paste formatted content into *MS Word* neatly to get your `.docx`, publish the HTML source to the web, or print the document from the browser (using print to PDF) to get a neatly formatted PDF document. So there are just one or two final manual steps to get your document with outline numbered goodies.
[**Here's an example**]()[1]() for this very post, written in Ulysses, exported to HTML and printed to PDF.
### Here's a theme I made earlier
I watched Blue Peter as youngster, so I'm just going to give you a copy of the exact theme I have created if you're not fussed about the learning piece. Note that it features both outline numbered headings and outline numbered lists.
[CLICK TO DOWNLOAD MY MODIFIED THEME]()[2]()
## Materials
For this modification project, you're going to need:
- Ulysses
- A `.ulstyle` theme you want to modify to include either outline numbered headings or lists. I based mine on the excellent `Medium Style` theme by *Leonardo*. But you can use ANY non-native HTML theme. See all HTML Ulysses themes [**here**]()[3]() or go directly to the `Medium Style` theme **[here ]()[4]()**. This is that theme renders:
![]()[image-2]()
- A good plain text editor (I use and love *[**BBEdit** ]()[5]()*or ***[Brackets ]()[6]()***). You need the text editor to make changes to the theme's CSS file within the `.ulstyle` file.
- The CSS code snippets below:
### Outline Numbered Lists CSS Code
> This code means that you can indent a numbered list to produce beautifully nested and lists with incremental decimal point sub lists (**1** becomes **1.1** becomes **1.1.1** *etc* as you tab -\> a list item)
ol { counter-reset: item }ol li{ display: block }ol li:before { content: counters(item, ".") " "; counter-increment: item }
### Outline Numbered Headings CSS Code
> This code will number headings from H2 - H6, it does not number H1 headings (which would more correctly be used as major titles in your documents rather than numbered sections).
 body {
counter-reset: h2
}

h2 {
counter-reset: h3
}

h3 {
counter-reset: h4
}

h4 {
counter-reset: h5
}

h5 {
counter-reset: h6
}

h2:before {
counter-increment: h2;
content: counter(h2) ". "
}

h3:before {
counter-increment: h3;
content: counter(h2) "."counter(h3) ". "
}

h4:before {
counter-increment: h4;
content: counter(h2) "."counter(h3) "."counter(h4) ". "
}

h5:before {
counter-increment: h5;
content: counter(h2) "."counter(h3) "."counter(h4) "."counter(h5) ". "
}

h6:before {
counter-increment: h6;
content: counter(h2) "."counter(h3) "."counter(h4) "."counter(h5) "."counter(h6) ". "
}

h2.nocount:before,
h3.nocount:before,
h4.nocount:before,
h5.nocount:before,
h6.nocount:before {
content: "";
counter-increment: none
}
## Step by step guide
1. **Create a test document**: Grab the sample copy below if you need:
	# Test Doc
	## Test doc Heading 2
	## Test doc another Heading 2
	 Test list
	 1. With
	 2. Parent
	 3. Items, and
	 4. Some (indent this)
	 5. Child items (indent this)
	 6. And another parent
	### And a subheading
	 Or come to think of it,
	### Two subheadings
2. **Open style preference pane**: Double click the `.ulstyle` file that you intend to modify. This will open the `Ulysses > Preferences > Styles` pane where you will see all of the themes you've added to Ulysses:
![]()[image-3]()
This is where you see all themes available in Ulysses
3. **Open style file**: Locate the style file you just downloaded. `ctrl+Click` it and click `Edit in…` and choose your Plain Text Editor:
![]()[image-4]()
I edit `.ulstyle` files in BBEdit, but you can use whatever text editor you like
4. **Outline Numbered List**: We could just dump the code snippets above anyway in the CSS file, but I like to insert the code snippets roughly near the CSS code for the elements they concern. So, navigate to `Line 102`. Copy and paste the first code snippet from above into that line:
![]()[image-5]()
![]()[image-6]()
Paste the CSS snippet for outline numbered lists (or *nested lists*)
**✅** - Outline numbered lists *COMPLETE*
5. **Outline Numbered Headings**: Navigate back up the code to `Line 72`, this is just under all the heading styling and above `blockquote {`. Paste the second code snippet from above right there.
**✅** - Outline numbered headings *COMPLETE*
6. **Save the file**: Then exit your text browser.
7. a. **Check it worked**: Preview your file hit **⌘** + **⇧** + **P**.
![Preview: Note that nothing changes in the \*editing\* experience.]()[image-7]()
![Preview: Note that nothing changes in the \*editing\* experience.]()[image-8]()
![Preview: Note that nothing changes in the \*editing\* experience.]()[image-9]()
7. b. **Flick between themes for fun**: You should be able to flick between your styles in and see the effect of the numbering easily in the preview.
![Preview: Flick between the unmodified and modified theme]()[image-10]()
![Preview: Flick between the unmodified and modified theme]()[image-11]()
## Edit: Cascading font-sizes for headings
Please note that the styling above adds numbering but no additional styling to headers. The code snippet below alters sizing incrementally as heading number increases:
h1 {font-size:2.5em;}
h2 {font-size:1.8em;}
h3 {font-size:1.6em;}
h4 {font-size:1.4em;}
h5 {font-size:1.2em;}
h6 {font-size:1.0em;}
Ideally you should find the current font sizes in each `h` class and delete them... but if you're in a rush you can just paste this at the bottom of your CSS file... the last declared rule wins, so don't paste it at the top! Then you'll get something like this:
![]()[image-12]()
---- 
I hope you found that little upgrade useful and that you enjoy your newly numbered Ulysses documents!
[1]():	https://www.dropbox.com/s/dc5rlfg7eikgny4/How%20to%20Generate%20Numbered%20Headings%20and_or%20Lists%20in%20Ulysses.pdf?dl=0
[2]():	https://drive.google.com/open?id=1HFeFVq4deH4se7LNvdbpZoGF3bLjDBzV
[3]():	https://styles.ulyssesapp.com/tagged/html?page=1&sort=popular
[4]():	https://styles.ulyssesapp.com/bundle/Medium+Style/5541f24f6fbeb3fd238c123e
[5]():	https://www.barebones.com/products/bbedit/
[6]():	http://brackets.io/
[image-1]():	https://everdigital.ghost.io/content/images/2019/02/Outline-Numbering-Not-Available-on-Ulysses.png
[image-2]():	https://everdigital.ghost.io/content/images/2019/02/image.png
[image-3]():	https://everdigital.ghost.io/content/images/2019/02/locate-downloaded-ulstyle-theme.png
[image-4]():	https://everdigital.ghost.io/content/images/2019/02/Edit-Ulysses-style-file-in-text-editor.png
[image-5]():	https://everdigital.ghost.io/content/images/2019/02/Add-css-to-Ukysses-style-theme-1.png width=796 height=258
[image-6]():	https://everdigital.ghost.io/content/images/2019/02/Code-snippet-for-outline-numbered-lists.png width=1190 height=258
[image-7]():	https://everdigital.ghost.io/content/images/2019/02/Editor-after-modification---outline-numbering-not-shown---Ulysses.png width=950 height=755
[image-8]():	https://everdigital.ghost.io/content/images/2019/02/Preview-before-modification---no-outline-numbering---Ulysses.png width=1054 height=838
[image-9]():	https://everdigital.ghost.io/content/images/2019/02/Preview-after-modification---with-outline-numbering---Ulysses.png width=1095 height=806
[image-10]():	https://everdigital.ghost.io/content/images/2019/02/Change-Ulysses-Theme-in-preview.png width=465 height=214
[image-11]():	https://everdigital.ghost.io/content/images/2019/02/Select-Modified-Ulysses-Theme-in-preview.png width=354 height=193
[image-12]():	https://everdigital.ghost.io/content/images/2019/02/locate-downloaded-ulstyle-theme.png

