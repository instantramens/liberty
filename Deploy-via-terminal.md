Deploying Ultraviolet through a terminal is made easy.

## Prerequisites

- NodeJS > LTS ([linux](https://github.com/nodesource/distributions)) ([windows](https://nodejs.org/))

We don't support versions of NodeJS that are older than LTS. Running newer non-LTS versions may lead to weird behavior, however it should still work.

> NodeJS LTS is currently 18.x. NodeJS 16 is unsupported and should not be used.

> The version of NodeJS that your package manager provides may be [severely outdated and vulnerable](https://gist.github.com/e9x/b549f46081ce794914461f2fbb9566bd). Use [NodeSource](https://github.com/nodesource/distributions) instead.

## If you opened this repository in Replit:

- skip the [clone](#clone) step, start at [install](#install)
- use the Replit terminal instead of the console by selecting "Shell" under tools or selecting the "Shell" tab in the Replit terminal

## Steps

1. Clone

   ```sh
   git clone https://github.com/titaniumnetwork-dev/Ultraviolet-App.git
   cd Ultraviolet-App
   ```

2. Install

   ```sh
   npm install
   ```

   > If this takes long, you may attempt to omit dev dependencies:

   ```sh
   npm install --omit=dev
   ```

3. Start

   Once dependencies are installed, select the "Run" button on Replit or run:

   ```sh
   npm start
   ```

   Alternatively, run on a port:

   ```sh
   PORT=8080 npm start
   ```

   You can stop it at any time by pressing <kbd>CTRL</kbd> + <kbd>C</kbt>

## What's next?

If you aren't using Replit, you may want to explore:

- [[Running in the background]]
- Fixing SSL errors for Ultraviolet: [[Configure SSL]]
