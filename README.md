<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<p align="center">

<img src="https://github.com/edingc/ansible-tpot-vultr/blob/main/images/screenshot.png?raw=true" alt="ansible-tpot-vultr Screen Shot" />

</p>

  <h3 align="center">ansible-tpot-vultr</h3>

  <p align="center">
    A set of Ansible plays to deploy/collect/destroy the T-Pot honeypot software on Vultr's cloud infrastructure.
    <br />
    <a href="https://github.com/edingc/ansible-tpot-vultr/issues">Report Bug</a>
    ·
    <a href="https://github.com/edingc/ansible-tpot-vultr/issues">Request Feature</a>
  </p>

<!-- TABLE OF CONTENTS -->
## Table of Contents

* [Built With](#built-with)
* [Getting Started](#getting-started)
  * [Prerequisites](#prerequisites)
  * [Installation](#installation)
* [Usage](#usage)
* [Contributing](#contributing)
* [License](#license)
* [Contact](#contact)
* [Acknowledgements](#acknowledgements)

### Built With/On

* [Ansible](https://github.com/ansible/ansible)
* [T-Pot](https://github.com/telekom-security/tpotce)
* [Vultr](https://www.vultr.com/)
* [Atom](https://github.com/atom/atom)


<!-- GETTING STARTED -->
## Getting Started

To get a local copy up and running follow these simple steps.

### Prerequisites

As this is an Ansible playbook, Ansible is required to be installed on a control
machine. [Ansible is available for almost every platform.](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

This playbook was developed using Ansible 2.11.5 on Mac OS X. It should run on any platform capable of supporting Ansible.

The following must be completed before running the playbook:

- Accounts must exist at [Vultr](https://www.vultr.com/register/) and [Cloudflare](https://dash.cloudflare.com/sign-up).
- Have a registered domain and [setup Cloudflare DNS](https://community.cloudflare.com/t/step-1-adding-your-domain-to-cloudflare/64309).
- Obtain API keys/token with proper privileges for [Vultr](https://my.vultr.com/settings/#settingsapi) and [Cloudflare](https://developers.cloudflare.com/api/tokens/create). The Cloudflare token should have privileges to update your registered DNS zone.
- [Setup public/private keys for Vultr instances](https://www.vultr.com/docs/deploy-a-new-server-with-an-ssh-key).


### Installation

1. Clone the ansible-tpot-vultr repository:
```sh
git clone https://github.com/edingc/ansible-tpot-vultr.git
```
2. Configure settings.yml with the necessary information.

3. Run the Ansible playbook:
```sh
ansible-playbook deploy.yml
```

<!-- USAGE EXAMPLES -->
## Usage

After the playbook has been run, T-Pot will have been deployed and started in the selected Vultr regions. It can be accessed through the methods [described in the T-Pot README](https://github.com/telekom-security/tpotce#ssh).

The playbook automatically creates an Ansible hosts file for later use:

```
[tpots]
newjersey.cloudappz.xyz:64295 name=newjersey
losangeles.cloudappz.xyz:64295 name=losangeles
```

To collect data from the honeypots, you can dump the Elasticsearch logs using the provided play:

```sh
ansible-playbook -i vultr_hosts dump_es.yml
```

The servers and DNS entries can be removed:

```sh
ansible-playbook destroy.yml
```

<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to be learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project.
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`).
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`).
4. Push to the Branch (`git push origin feature/AmazingFeature`).
5. Open a Pull Request.


<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE` for more information.

<!-- CONTACT -->
## Contact

Your Name - [@edingc](https://twitter.com/edingc) - cody@codyeding.com

Project Link: [https://github.com/edingc/ansible-tpot-vultr](https://github.com/edingc/ansible-tpot-vultr)

<!-- ACKNOWLEDGEMENTS -->
## Acknowledgements

* [Telekom Security](https://github.com/telekom-security/tpotce#ssh) for the T-Pot software.
* [Othneil Drew](https://github.com/othneildrew/Best-README-Template) for the great README.md template.
* Numerous other websites, Google searches and StackOverflow posts that yielded individual bits and bobs
necessary to get Ansible, Vultr, Cloudflare and T-Pot working together.


<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/edingc/ansible-tpot-vultr.svg?style=flat-square
[contributors-url]: https://github.com/edingc/ansible-tpot-vultr/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/edingc/ansible-tpot-vultr.svg?style=flat-square
[forks-url]: https://github.com/edingc/ansible-tpot-vultr/network/members
[stars-shield]: https://img.shields.io/github/stars/edingc/ansible-tpot-vultr.svg?style=flat-square
[stars-url]: https://github.com/edingc/ansible-tpot-vultr/stargazers
[issues-shield]: https://img.shields.io/github/issues/edingc/ansible-tpot-vultr.svg?style=flat-square
[issues-url]: https://github.com/edingc/ansible-tpot-vultr/issues
[license-shield]: https://img.shields.io/badge/License-MIT-yellow.svg
[license-url]: https://github.com/edingc/ansible-tpot-vultr/blob/master/LICENSE
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=flat-square&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/codyeding
