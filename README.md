<div id="top"></div>
<!--
*** Thanks for checking out the Best-README-Template. If you have a suggestion
*** that would make this better, please fork the repo and create a pull request
*** or simply open an issue with the tag "enhancement".
*** Don't forget to give the project a star!
*** Thanks again! Now go create something AMAZING! :D
-->



<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->

<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/oliver-cool-beans/al-api-docs">
  </a>

<h3 align="center">Adventure Land Docs</h3>

  <p align="center">
    (Unofficial) documentation for Adventure Land - The CODE MMORPG from a concerned citizen 
    <br />
    <a href="https://oliver-cool-beans.github.io/al-api-docs/#/"><strong>Explore the docs »</strong></a>
    <br />
    <br />
  </p>
</div>

<h4 align="center" >Note: This project is a work in progress</h4>

### Built With

* [Docsify](https://docsify.js.org)
* [AsyncAPI](https://www.asyncapi.com/) 


<!-- GETTING STARTED -->
## Getting Started

These docs are dynamically generated from the asyncapi spec. To contribute to this documentation, simply update the [asyncapi document](asyncapi.yaml)

1. Install [Docsify](https://docsify.js.org/#/quickstart)
2. Install the [AsyncAPI Generator](https://github.com/asyncapi/generator) with `npm install -g @asyncapi/generator`
3. In the root directory generate new markdown from the AsyncAPI spec with `ag asyncapi.yaml @asyncapi/markdown-template -o docs`
4. run `docsify serve docs` to serve the docs, or manually serve the `index.html` your own way
5. Navigate to the documentation webpage in your browser `http://localhost:3000`

*After making changes, you'll need to run step 3 again to regenerate the markdown*
