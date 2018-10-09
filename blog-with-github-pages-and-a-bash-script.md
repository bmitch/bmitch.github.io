Blog with GitHub pages and a bash script

Since I've recently started this blog I thought a good first post would be about how I set it up.

I've been searching for a way to create and host a blog with minimal setup and something that would involve minimal maintenance.

I wanted to avoid having to setup and maintain a server. It's something I can do and currently do but free time is at a minimum lately so if I could avoid that entirely, that would be great.

Also wanted to be able to edit my blog content using Markdown. 

Finally, I'd like the blog to have a very basic and simplistic design. 

I had seen some tutorials online that showed how you can use GitHub pages to host static content. Some people had been using static content generates like [Hugo](https://gohugo.io/) or [Jekyll](https://jekyllrb.com/) and then uploading the content to their GitHub pages account. 

Tried these options out and they did work but still involved installing the libraries on my local machine which wasn't a huge deal but I felt there could be something easier. I also had a bit of trouble trying to apply different styles to the content and also finding a style that looked good.

Then I stumbled across a blog that looked very minimalistic (wish I could remember what blog it was now) and noticed in the footer it mentioned it was made with [https://github.com/cfenollosa/bashblog](https://github.com/cfenollosa/bashblog).

bashblog is a bash script that generates a static blog site. It fulfilled a few of the things I was looking for:

* Minimal setup - bashblog has no dependencies, it's just a bash script
* Simplistic design
* Supports markdown 

So it was time to put the two together. Here's the steps I took:

## 01 - Setup GitHub pages
Best guide for this is located at https://pages.github.com/. Once you are done you can go to https://<yourgithubprofile>.github.io and see a "Hello World" you created by following the guide.

But for a quick version:

* Create a GitHub repo named `username.github.io`, where `username` is your GitHub username.
* Clone the repo to your local machine: `git clone https://github.com/username/username.github.io`
* Enter the folder: `cd username.github.io`
* Create an index.html page: `echo "Hello World" > index.html`
* Commit and push your changes:
```
git add --all
git commit -m "Initial commit"
git push -u origin master
```
At this point you should see your "Hello World" at `https://<yourgithubprofile>.github.io`. (If you don't see it right away you may need to refresh a few times.)

## 02 - Download bashblog
Go to the [bashblog repo](https://github.com/cfenollosa/bashblog/) and download the `bb.sh` script to your local machine into the same folder where your index.html is. You could also create a `.gitignore` file and add `bb.sh` to it if you don't want to have the script committed with your blog content.

From there you will probably have to make it executable with `cmhod +x bb.sh`

## 03 - Configure bashblog
Type `touch .config` to create a config file that will hold your settings. First thing I did was setup my default editor by adding:
```
editor=vim
```

## 04 - Create your first post
To create a new post run `./bb.sh post`. This will open up the editor you defined in your config with the template content of a new blog post.

Replace the `Title on this line` with your desired blog post title.

Below that you can replace the segment that starts with `The rest of the text` with the body of your blog post.

At the bottom is a section for tags which you can add as well.

Once finished it will prompt you to post the new content. If you decide to post it you will see that the bashblog script rebuilds the index page, tags and RSS feed. 

## 05 - Push to GitHub
From here you can commit and push your new entry to the GitHub repo.

After a minute or so your new content will be live on your GitHub pages URL.

# Conclusion
Overall I found this a very minimalist way to create and maintain a blog. Some other things I plan to do eventually is add Google Analytics support and obtain a custom domain that points to my GitHub pages account. 

Tags: bashblog, bash, github,  



