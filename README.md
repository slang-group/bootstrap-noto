# Bootstrap-Noto

Simple customization using the Google Noto family of fonts in Bootstrap framework.

Google Noto supports dozens of alphabets supporting hundreds of languages, and this helps you
add them to your webpages.

Chinese, Japanese, and Korean characters (CJK) are supported by the Google Noto font, but currently not supported
by this repo.

## Demo

<a href="http://mapmeld.github.io/bootstrap-noto/">Homepage</a> implementing dist/main.css and a rare language font.

## Install

```
npm install node-sass clean-css -g
bower install
```

## Builds

It's not performant to include all of the world's languages' fonts on your page. Here's how to include
just the languages that you want, by default.

In main.scss, you will see custom build information:

```
$useGoogleFonts: true;
$fontURL: 'fonts/';
$activeLanguages: ('Noto Sans', 'Noto Serif', 'Noto Sans Thaana');
$includeBold: true;
```

The first line imports Noto Sans and Noto Serif from Google Fonts CDN, instead
of a relative path.

The second line is the relative URL to any of the Noto font files. Update this if you cannot access a font
at fonts/NotoSans-Regular.ttf

activeLanguages is a list of full names of fonts which you want to include.

includeBold will include a bold font if one exists. For example 'Noto Sans Ethiopic' would load
both Noto Sans Ethiopic Regular and Noto Sans Ethiopic Bold fonts. You can include
the bold font using either the "noto-sans-ethiopic-bold" class, or using font-family: 'Noto Sans Ethiopic Bold';

Run this after updating the source code, to change the files under dist/

```
npm run dist
```

## Console scraping from Google Noto

```
languages = document.getElementsByTagName("h4");
language = []
for (var i = 0; i < languages.length; i++) { language[i] = languages[i].textContent.trim(); }
for (var i = 0; i < language.length; i++) { console.log("@if index($activeLanguages, '" + language[i] + "') {\n  @font-face {\n    font-family: '" + language[i] + "';\n  src: url(\"#{$fontURL}.ttf\");\n  }\n}" ) }
```

## License

MIT License (same as Bootstrap)
