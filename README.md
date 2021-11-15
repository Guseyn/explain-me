# Explain me
Document Driven Development Tool for creating documentation for each source file.

Inspired by [this awesome article](https://blog.izs.me/2017/06/documentation-driven-development/). But it works both ways, because most of the time we already have undocumented source code.

# How to install

//TODO...

# What it does

## Creates documentation for existing source code

**Explain me** creates corresponding directory to the one you want to create a documentation for. Each document in that directory has format `.md` and it contains all information about corresponding source file.

So, let's say we have directory with source code:

```bash
├── ProjectName
│   ├── a.js
│   ├── dir1
│   │   ├── b.js
│   ├── dir2
│   │   ├── c.js
```
When you type command:

```
explain init <source folder path> <docs folder name>
```
(by default `docs folder name` is `ProjectNameDocs` (name of your source folder + `Docs`))

you'll get following documentation folder in your source folder:

```bash
├── ProjectName
│   ├── ProjectNameDocs
│   │   ├── a.js.md
│   │   ├── dir1
│   │   │   ├── b.js.md
│   │   ├── dir2
│   │   │   ├── c.js.md
```

Now you can modify all your md files. You can set links to other files and dictionary of terms and ect.

## Creates dictionary

If you type command:

```
explain init dictionary <source folder path> <dictionary folder name>
```

(by default `dictionary folder name` is `ProjectNameDictionary` (name of your source folder + `Dictionary`))

you'll get dictionary folder:

```bash
├── ProjectName
│   ├── ProjectNameDictionary
```

So, in that folder you can create term files, each file for one specific term, where you can explain a certain variable or concept/pattern in the code.

## Creates doc for future source file/term.

By typing command

```
explain future <sourceFolderName/path/to/file.js>
```

you'll get created empty source file `sourceFolderName/path/to/file.js` and corresponding `sourceFolderName/docFolderName/path/to/file.md`. `docFolderName` is delcared in config file `.explain`:

```json
{
  "docFolderName": "docs",
  "dictionaryFolderName": "dictionary"
}
```

This file can be created manually and also when you [create documentation for existing source code](#creates-documentation-for-existing-source-code)

By typing command

```
explain future term <term name>
```

you'll get term file(with specified name) in configured `dictionaryFolderName`.

## Explains you term or source file

If you type command:

```
explain me [source file.js]
```

or

```
explain me term [term name]
```

you'll get opened browser with rendered markdown, where you can see documentation. Program also creates additional html files and you can configure their location as well in `.explain`:

```json
{
  "docFolderName": "docs",
  "dictionaryFolderName": "dictionary",
  "docHTMLFolderName": "html-docs"
}
```

The program will run server that serves static hmtl files. You can also specify port where all you docs can be opened in a browser:

```json
{
  "docFolderName": "docs",
  "dictionaryFolderName": "dictionary",
  "docHTMLFolderName": "html-docs",
  "port": 8080
}
```
As index page you will get folder tree. You can also add some general additional files with documentation there.

In order to just open index page, you can type command:

```
explain me all
```
