# lebenslauf

CV template for the ConTeXt document processing system. Manage multiple CV configurations (multiple languages, conditionally shown entries) with a single file and command line arguments.


## Usage

Basic document structure:

```tex
\input{lebenslauf} % path to template

% Personal details
\setupinformationtext[name={Max Mustermann}]
\setupinformationtext[en][birth={04/20/1985}]
\setupinformationtext[de][birth={20.04.1985}]

% Headings for entry categories in all languages
\setupcategorytext[en][experience=Experience,skills=Skills]
\setupcategorytext[de][experience=Erfahrung,skills=Kenntnisse]

\starttext

    \cv

    \startinformation
        \information[name]
        \information[birth]
    \stopinformation

    \startcategory[experience]
        \periodentry[en]{Aug 2017}{Mar 2018}{Internship at \TeX inc.}{Document processor}
        \periodentry[de]{08/2017}{03/2018}{Praktikum bei \TeX GmbH}{Dokumentenverarbeiter}
    \stopcategory

    \startcategory[skills]
        \entry[en]{Languages}{German, English}{}
        \entry[de]{Sprachen}{Deutsch, Englisch}{}
    \stopcategory

    \signatureanddate{signature.png} % leave argument empty if printed and pen-signed

\stoptext
```

Using the [modes](https://wiki.contextgarden.net/Modes) feature of ConTeXt with the `--mode=` command line argument, entries can be enabled and disabled on demand. Category headings are automatically hidden if all entries in the category are hidden. Predefined are information fields `name`, `address`, `phone`, `email`, `contract`, `birth` and `nationality` for languages English (`en`) and German (`de`). Other fields and languages can be added by setting the corresponding `multilangtext` key-value pairs (check out the template and its documentation).

Select the language of the output document with the `--lang=` command line argument, e.g.

```bash
context --lang=en example.tex
```

