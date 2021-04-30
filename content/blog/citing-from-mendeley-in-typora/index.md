---
title: Citing reference from Mendeley in Typora
date: "2021-04-30T15:00:32.169Z"
description: A short guide to write references for you who writes your academic paper in Markdown using Typora. The key to making this work is using Pandoc and a TeX library.
---



This is a short guide if you're writing your academic paper in Markdown using Typora. This can also be applied to other markdown editors by using frontmatter. The key to making this work is using pandoc and a TeX library (I'm using Windows and MiKTeX).

### Install Typora

There's a lot of reason why I prefer markdown over MS Word or LaTeX, but mainly because it's easier to write and read. It's just in the middle where Word is easy to use but have a rigid formatting for complex documents, while LaTeX has a steep learning curve but wide customizable formatting. I prefer Typora as my text editor for it's simple layout, making me focus on doing the actual job, which is writing rather than formatting.

### Install Pandoc and MiKTeX

If you're just taking notes and writing simple reports, Typora is all you need. But most people still prefer writing in MS Word, or even LaTeX, so it's hard for you to collaborate when you already fell in love with the simplicity of markdown. [Pandoc](https://pandoc.org/) is the swiss-army knife of document conversion. You'll can use it to convert your markdown files to a wide variety of formats and vice versa. To export PDFs with citations and other customize formatting, you'll need LaTeX library. [MiKTeX](https://miktex.org/) is often used for Windows, but it also supports Linux and macOS.

Installing both is very straight-forward. In Windows you go to each website, download installation file and follow along. For MiKTeX you also need to update after installation. Despite updating a bunch of files, in my case, some `.sty` files are still missing and were asked to be installed by Pandoc during my first PDF file conversion.

### Create a bibliographic file

For Mendeley users, in the desktop app, go to Tools->Options then BibTeX. Tick "Escape LaTeX special characters", "Enable BibTeX syncing" and "Create one BibTeX file for my whole library". Specify the path where you want to store your synced bibliographic file. Each time you add documents to your library, it will also update this `.bib` file. Take note of the path because you'll use it in Pandoc. In this example I put it in `D:\Documents\library.lib`

### Convert using Pandoc

To reference a paper from your Mendeley library, use it's Citation Key (found in details tab when clicking a document in Mendeley) and insert in your markdown like: `[@citation_key]`. After writing your report, in this example, I named it `report.md`, open a cmd line in the same folder, and type:

```
pandoc --citeproc "report.md" --bibliography D:\Documents\library.lib -o "report.pdf"
```

That's it, your report has correct citations and a reference section will be created automatically at the end of the page.

![markdown and the converted PDF side by side](./result.png "Markdown and the converted document in PDF")



You can also use the frontmatter to point your library. But to make this work, you need to have the document you want to convert to be in the same folder as `library.bib`. Then you can execute the pandoc command without `--bibliography D:\Documents\library.lib` part. To write a frontmatter, simply type `---` at the beginning of your document and fill with some metadata such as:

```
---
title: "Transfer Learning is a Gift"
date: \today
author: "Sandhi"
bibliography: "library.bib"
---
```

Not only reference, you can also format your documents to the required stylings specified by your journal. More on this on my next post!



















