# Moving from OneNote to Github

## A word about the Microsoft OneDrive

The most honest way to start this paper is giving my 2 cents about Microsoft OneNote: 
I Love it! Really. I think it is a great product and I have been using it for a couple of years. 
OneNote was the preferred note-taking app against tools like Google Keep, notepad(sic), Evernote and others. 

## Reasons to get out of Onedrive

Although, I'm writing some code here and there during the last years and today, I have lot of code notes. 

Most of the time, I have used a code Editor like Vim or Vscode.

I do some task in vscode like: 
- navigating through directories;
- writing code in Go, powershell, C#, javastript and shell bash, Json, Toml. 
- writing music tabs. 
- reading markdown notes. 
- taking notes in markdown style.
- Running commands and code in terminal. 

So, why not move my notes to the same vscode and use it as only one tool? 

I'm a techie by nature. For me, There are another three strong reasons to get out of OneNote. 
Let's see: 

- Reason number one: There's no markdown notation in OneNote.
  
I don't have time to complicated text formatting. Markdown gives me superpowers to format as I'm writing the text. I need to write well-structured text, but I don't have time to spent using OneNote rich-formatting resources. It's about agility. It's about time. Markdown also has another advantage: I don't need to take a look at document preview. I can do it, but most of the time, I don't need it. 

Markdown notation also offers support to writing code notes as default. I can mix pure text with code snippets in the same document. 

- Reason number 2: there isn't a OneNote Linux App. 

Yes, we can use the OneOne thought the browser, but it's slow, even on the fast connections. It's painful! I can't understand WHY Microsoft didn't create the electron App version! 

Now, let's look at my solution. 

## Syncing notes

One of the most notable capability of OneNote is syncing. I often use Git and Github to sync my project across different enviroments and it has been proved a good solution. 

So, I did a private Github repo named `myNotes`. This repo is synced to my local environment using Git. 

Inside of `myNotes` folder I created several folders, corresponding to OneNotes sections. Inside each section folder I have markdown files (.md) corresponding to OneNote pages. 

There's no auto syncing and it's a downside of my solution. Instead, I do  `git add` and `git commit` commands as I do in my normal dayly workflow. 

To take notes I use the Visual Studio Code (vscode) as my primary tool. I can do a `control+B` to open vscode explorer to create or open folders and .md files. 

Some vscode extensions are mandatory: 

- **Markdown All in one**. It's a swarm knife. It can be used to format text and code following the Mardown notation, leaving me about boring tasks like create lists, tables and TOCs (Table of Contents).
- **Markdown Lint**. This extension helps me to check the markdown sintax of my documents. 
- **Mardown Preview**. This is a good extension to get affordable document previews. It's possibile to create standalone and synced document previews.
- **Song txt**. It's used to create guitar tablatures.    

When I'm only with the cellphone, I still using OneNote. It's especially useful taking notes on the road or while I'm talking to someone. Later the notes are converted to markdown files if necessary. 

I can clone myNotes repo on windows or linux without necessary stay connected all time. 
When I have doubts about certain contents it's possible to use git branches. 
I also can reuse pieces of my contents to create new documents like blog entries or a post in a social media, without leave the vscode (getting more information value). 
At last, using the github app, I can access all my notes from my cell or any other device. 


















