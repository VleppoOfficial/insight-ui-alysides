# Vleppo Insight UI

This repository contains the source code for the Alysides blockchain explorer web application service for [Bitcore Node](https://github.com/VleppoOfficial/bitcore-node-alysides) using the [Insight API](https://github.com/VleppoOfficial/insight-api-alysides).

This is only the front-end component of the block explorer. If you're looking for the backend API service, take a look at https://github.com/VleppoOfficial/insight-api-alysides.

## Installation

This section provides full installation instructions of Insight UI and all its dependencies.

### Prerequisites

- [Bitcore Node](https://github.com/VleppoOfficial/bitcore-node-alysides)
- A node running [Vleppo Alysides](https://github.com/VleppoOfficial/alysides)
- GNU/Linux x86_32/x86_64, or OSX 64bit
- Node.js v4 (use [nvm](https://github.com/nvm-sh/nvm) to manage Node.js versions)
- ZeroMQ (libzmq3-dev for Ubuntu/Debian or zeromq on OSX)
- ~200GB of disk storage
- ~8GB of RAM

### Getting Started

1. Make sure you have the correct Node.js version installed: `nvm install v4`
    - **Note:** this command may not work immediately after installing nvm, you may need to reboot shell for changes to take effect.
2. Make sure you have ZeroMQ installed:
    - Linux: `sudo apt install libzmq3-dev`
    - OSX: `brew install zeromq`
3. Install bitcore-node-alysides:\
  `npm install -g https://github.com/VleppoOfficial/bitcore-node-alysides`\
  `bitcore-node create mynode`\
  `cd mynode`
4. Install Insight:\
  `bitcore-node install https://github.com/VleppoOfficial/insight-api-alysides`\
  `bitcore-node install https://github.com/VleppoOfficial/insight-ui-alysides#generic-ui`
5. Make sure to either setup an Alysides instance for your chain locally or have access to a running local or remote Alysides node.
6. In the machine where Alysides is running (can be the same as where bitcore-node is set up), create or edit the ".conf" file, located by default in ".komodo/your_chain_name/". Make sure the file includes the following lines:\
  `rpcuser=<your secure rpc user>`\
  `rpcpassword=<your secure rpc password>`\
  `rpcport=<your chain's rpc port>`\
  `server=1`\
  `txindex=1`\
  `addressindex=1`\
  `timestampindex=1`\
  `spentindex=1`\
  `zmqpubrawtx=tcp://127.0.0.1:28332`\
  `zmqpubhashblock=tcp://127.0.0.1:28332`
    - Make sure port 28332 is not blocked for both the bitcore-node and Alysides machines (including if both are being run on the same machine). The port number can be changed if necessary.
7. In the mynode folder, edit the bitcore-node.json file. Make sure to specify the Alysides node's IP address in rpchost (set to 127.0.0.1 if localhost), and the correct rpcuser, rpcpassword, rpcport and zmqpubrawtx according to the same values as in the node's .conf file.
8. Launch your Alysides node (if connected solely to a local node). 
9. Launch Insight: `bitcore-node start`
    - **Note:** After this, you may want to restart Alysides and use the `-reindex` launch parameter when starting Alysides again in order for Insight to successfully capture past transactions.

The server should now be running by default at `http://localhost:3001/insight/`. The API endpoints will be available by default at: `http://localhost:3001/insight-api-alysides/`.

## Development

To run Insight UI locally in development mode:

Install bower dependencies:

```
$ bower install
```

To compile and minify the web application's assets:

```
$ grunt compile
```

There is a convenient Gruntfile.js for automation during editing the code

```
$ grunt
```

## Multilanguage support

Insight UI uses [angular-gettext](http://angular-gettext.rocketeer.be) for multilanguage support.

To enable a text to be translated, add the ***translate*** directive to html tags. See more details [here](http://angular-gettext.rocketeer.be/dev-guide/annotate/). Then, run:

```
grunt compile
```

This action will create a template.pot file in ***po/*** folder. You can open it with some PO editor ([Poedit](http://poedit.net)). Read this [guide](http://angular-gettext.rocketeer.be/dev-guide/translate/) to learn how to edit/update/import PO files from a generated POT file. PO file will be generated inside po/ folder.

If you make new changes, simply run **grunt compile** again to generate a new .pot template and the angular javascript ***js/translations.js***. Then (if use Poedit), open .po file and choose ***update from POT File*** from **Catalog** menu.

Finally changes your default language from ***public/src/js/config***

```
gettextCatalog.currentLanguage = 'es';
```

This line will take a look at any *.po files inside ***po/*** folder, e.g.
**po/es.po**, **po/nl.po**. After any change do not forget to run ***grunt
compile***.


## Note

For more details about the [Insight API](https://github.com/VleppoOfficial/insight-api-alysides) configuration and end-points, go to [Insight API GitHub repository](https://github.com/VleppoOfficial/insight-api-alysides).

## Contribute

Contributions and suggestions are welcomed at the [Insight UI GitHub repository](https://github.com/VleppoOfficial/insight-ui-alysides).


## License
(The MIT License)

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
