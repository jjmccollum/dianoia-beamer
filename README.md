# dianoia-beamer
LaTeX template for Australian Catholic University's Dianoia Institute of Philosophy Beamer presentations

## About This Project
I personally prefer using LaTeX to Microsoft Office for my work, and since Australian Catholic University (ACU) did not have LaTeX beamer templates for slide presentations, I decided to put some together based on ACU's existing PowerPoint templates. This Beamer template corresponds to ACU's PowerPoint template for the Dianoia Institute of Philosophy. That said, it is worth clarifying that these are not official ACU resources and that they will not necessarily replicate the exact layout of the PowerPoint template down to the pixel. I have done the best I could comparing both templates by eye, and I hope that these templates will be sufficient for students and faculty who also prefer to use LaTeX.

This template will attempt to use Georgia for the serif font, Arial for the sans-serif font, and Arial Bold for the titling font (per ACU guidelines). If you are using a Windows computer, this should be fine, as these are either system fonts, but if the fonts cannot be found on your system, then the usual LaTeX fonts will be used. Latin Modern Math (the standard LaTeX math font) is used for math. The specification of custom fonts is done using the `fontspec` package, so to use this feature, you must typset in Xe(La)TeX. If you want to typeset in plain LaTeX, simply comment out the following lines in `beamerthemedianoia.sty` and add `\def\titlingfont{\sffamily}` before them:

```tex
% Theme fonts (comment this section out and replace it with \def\titlingfont{\sffamily} if you want to use plain LaTeX)
\RequirePackage{fontspec}
\defaultfontfeatures{Scale=MatchLowercase}
% Serif font
% Use Georgia if present on the system
\IfFontExistsTF{Georgia}{
	\setmainfont[Ligatures=Common]{Georgia}%
} {
	% Otherwise, just use the default LaTeX serif face
}
% Sans-serif font
% Use Arial if present on the system
\IfFontExistsTF{Arial}{
	\setsansfont[Ligatures=Common]{Arial}%
} {
	% Otherwise, just use the default LaTeX sans serif face
}
% Titling font
% Use Arial Bold if present on the system
\IfFontExistsTF{Arial Bold}{
	\newfontfamily\titlingfont[Ligatures=Common]{Arial Bold}
} {
	% Otherwise, just use the default LaTeX sans serif face as the titling face
	\def\titlingfont{\sffamily}
}
% Math font
\RequirePackage[mathup=sym]{unicode-math}
\setmathfont{Latin Modern Math} % use the default LaTeX math font
```

The body text of slides can be set in serif or in sans-serif. The default setting in Beamer is sans-serif. If you wish to use serif, then add `\usefonttheme{serif}` after you specify `\usetheme{dianoia}` in your document.

This template should work with different aspect ratios. I have only tested it for 4:3 and 16:9, as these are the two most common.

The template also includes code to support section title slides in accordance with the PowerPoint template. These can be invoked with the `\sectionframe` command after a new section.

All of these features and others are demonstrated in the `template.tex` file, which you can find in the `tex` directory. For now, you must organize your project structure according to the project structure in this repo, with your main document parallel to the `.sty` files and the images. If you notice any incorrect behavior, feel free to note it in an issue.