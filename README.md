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

* [AsyncAPI](https://www.asyncapi.com/) 

### Something not right?
Feel free to raise an Issue or submit a PR

<!-- GETTING STARTED -->
## Getting Started

These docs are dynamically generated from the asyncapi spec. To contribute to this documentation, simply update the [asyncapi document](asyncapi.yaml)

1. Install the [AsyncAPI Generator](https://github.com/asyncapi/generator) with `npm install -g @asyncapi/generator`
2. In the root directory generate new markdown from the AsyncAPI spec with ` ag asyncapi.yaml @asyncapi/html-template -o docs`
3. Navigate to index.html in your browser

*After making changes, you'll need to run step 3 again to regenerate the markdown*

## Contributing
All contributions welcome 
Please explain the reason for the change if not obvious.

1. Fork the repo
2. Clone the project to your local machine
3. Commit changes to your own branch
4. Push your work to your fork
5. Submit a Pull Request against `develop` and i'll review your changes

NOTE: Be sure to merge the latest from "upstream" before making a pull request!

