Deploying Ultraviolet through a terminal is made easy.

> Don't copy the `$` in any of these commands when pasting in a terminal.

## If you opened this repository in Replit:

- skip the [clone](#clone) step, start at [install](#install)
- use the Replit terminal instead of the console by selecting "Shell" under tools or selecting the "Shell" tab in the Replit terminal

## Clone

```sh
$ git clone https://github.com/titaniumnetwork-development/Ultraviolet-Node.git
$ cd Ultraviolet-Node
```

## Install

```sh
$ npm install
```

> If this takes long, you may attempt to omit dev dependencies:

```sh
$ npm install --omit=dev
```

## Start

Once dependencies are installed, select the "Run" button on Replit or run:

```sh
$ npm start
```

Alternatively, run on a port:

```sh
$ PORT=8000 npm start
```
