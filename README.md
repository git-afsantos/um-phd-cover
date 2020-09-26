# UM PhD Thesis Covers

Are you a PhD student at the University of Minho, preparing your thesis for submission?
Are you writing your thesis with LaTeX?
Then, this repository is for you.

You might have noticed that there are quite a few formatting and style rules that your thesis must follow, especially regarding the **thesis cover**.
The University provides templates to create your thesis cover, but they are *Adobe Illustrator Artwork (AI)* files.

If you do not own Adobe Illustrator, you do not want to purchase it and/or you do not want to obtain an illegal copy of it, you do not have much of a choice but to roll your own attempt at creating the thesis cover from scratch.
At least, I did.
Now, this repository hosts the LaTeX files so that they may, hopefully, prevent you from wasting as much time as I did.

Simply compile the cover as its own PDF, and use `\includepdf` in your main thesis file.

## Instructions

The cover can be compiled with `pdftex`, `xetex` or `luatex`.

### Fonts

The University requires the use of the *NewsGotT* font, which is not available with `pdftex`, so I recommend `luatex` for the best results.

If you are compiling with `xetex` or `luatex`, first you need to download the required fonts: *NewsGotT Regular* and *NewsGotT Bold*.
Name the files `newsgott-regular.ttf` and `newsgott-bold.ttf`, respectively, and place them in the root of the repository (where `cover.tex` is).

If you can only compile with `pdftex`, for some reason, it uses a variant of the *Helvetica* font, which is **not** compliant with the University style, but is visually close enough.
This simply requires the installation of the `helvet` package.

Once the fonts are available, you should be able to compile the cover.

### Inserting Your Information

Editing the template to make your own cover is easy.
Open `cover.tex` and scroll down to a section that begins with the following marker.

```tex
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% Variables - EDIT THESE
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
```

There, you will find a series of `\gdef` variable declarations, whose values you can edit.
They should be straightforward to understand.
For instance, your full name can be inserted in the variable that reads:

```tex
\gdef\@author{Your Full Name Goes Here}
```

### Special Cases

#### MAP courses

This template covers the association programmes of Minho-Aveiro-Porto as well.
Simply change the line that reads `\gdef\mapi{0}` to `\gdef\mapi{1}`.
Your cover will now include all the requires University logos at the front.

#### Multiple Organic Units

The current version of the template does not support multiple Organic Units (e.g., a course that belongs both to the School of Engineering **and** the School of Sciences).
It does not include the necessary logos.
However, it should not be too hard to add, given the right tools.

#### Very Long Thesis Titles

If your thesis title is very long, it might not fit in the allocated space of the cover's spine.
Try it out. If it spans more than two lines, you need to adjust the spine code.

Look for a section that reads `% Cover Spine`.
Within it, look for the following bit of code.

```tex
    {\centering \fontsize{12}{14.4}\selectfont
        \rotatebox[origin=c]{90}{\parbox[c][13mm]{90mm}{\raggedright \textbf{\printtitle}}}\par}
```

You will want to increase those `90mm` up to, for instance, `120mm`.

## Copyright Notice

[André Santos](https://github.com/git-afsantos) is the author of the LaTeX code in this repository.
All the included University logos are copyright of the respective Universities, namely the University of Minho, University of Aveiro and the University of Porto.
These logos have been edited only to change the lettering colour, from their original colours to white, so that they comply with the PhD Thesis style rules set by the University of Minho.
