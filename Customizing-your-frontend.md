# Customizing your frontend

The static files (frontend) is generated in the [Ultraviolet-Static](https://github.com/titaniumnetwork-development/Ultraviolet-Static) repository. You can follow the instructions within the repository to modify the frontend here.

## Walkthrough

Follow the instructions for deployment found in other pages of the wiki. The following steps assume you are in a directory containing the content of Ultraviolet-Node.

1. Clone Ultraviolet-Static

```sh
$ git clone https://github.com/titaniumnetwork-development/Ultraviolet-Static.git
> Cloning into Ultraviolet-Static...
$ cd Ultraviolet-Static
```

2. Install dependencies

```sh
$ npm install
```

3. Make your changes

You may go back to this step anytime, however we recommend you make your changes before applying them.

The content inside `Ultraviolet-Static/public/` may be modified. This directory contains assets and HTML webpages.

4. Install the modified module

You should only have to do this once. Any future changes to `Ultraviolet-Static/public/` will immediately take effect.

Enter the Ultraviolet-Node directory:

```sh
$ cd ..
```

Install the new module:

```sh
$ npm install ./Ultraviolet-Static
```

5. Start

```sh
$ npm start
```
