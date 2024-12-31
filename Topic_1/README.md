[Back To Main](/README.md)

# 1.1 Linux Evolution and Popular Operating Systems

Linus Torvalds began developing Linux in 1991, drawing inspiration from the Unix operating system and another system developed by AT&T Laboratories in the 1970s. At that time, affordable Unix systems for office computers running on the x86 platform were unavailable. Linux was created to fill this gap in the market.

## Distributions

**Distribution:** a bundle that consists of a Linux *kernel* and a selection of applications that are maintained by a company or user community.
  * A distribution's goal is to optimize the kernel and the applications that run on the operating system for a certain use case or user group.
  * Distributions include specific tools for software installation and system administration. This is why some distributions are made for desktops and some are used for servers.

**Package:** a bundle of software and a corresponding configuration and documentation that makes it easier for the user to install, update and use the software.

### Debian distribution family

**Package Manager:** `dpkg`

**Maintainers use the `deb` package format to specify how the software is installed on the operating system and how it is configured by default.*

*Debian* GNU/Linux distribution is the biggest distribution of the Debian distribution family. It was created by Ian Murdock in 1993 and it aims to provide a very reliable operating system. Its also promotes Richard Stallman's vision of an operating system that respects the freedoms of the user to run, study, distribute and improve the software. 

*Ubuntu* is another well-known Debian-based distribution, created by Mark Shuttleworth and his team in 2004. It aims to provide an easy-to-use Linux desktop environment and make free software accessible to everyone worldwide, while also reducing the cost of professional services. The distribution follows a scheduled release cycle, with new versions every six months and long-term support releases every two years.

### Red Hat

**Package Format:** `rpm`

1994 - Red Hat Linux distribution was started.\
2003 - Re-branded to *Red Hat Enterprise Linux* (RHEL).\
2019 - Acquired by IBM.

*Red Hat* provides companies with a reliable enterprise solution and commercial support designed to ease the use of Linux in professional server environments. In other words, Red Hat is tailored for enterprise servers. Some of its software and services require a paid subscription
  * CentOS is a free version of RHEL, it uses its source code but lacks the commercial support.

Red Hat also created Fedora in 2003, it is a progressive distribution aimed at desktops, often testing new technologies for RHEL.

### SUSE

1992 - Founded in Germany as a Unix service provider.\
1994 - First version of SUSE *Linux* was releases.\
2004 - SUSE released the *openSUSE* project.

SUSE linux became mostly known for its YaST configuration tool. It allows administrators to install and configure software and hardware, set up servers and networks. SUSE also released SUSE Linux Enterprise Server which is similar to RHEL. It is distributed as a server as well as a desktop environment. 

Later on openSUSE was released to allow developers and users to test and further develop the system. openSUSE is freely available to download for anyone.

## Embedded Systems

**Embedded Systems:** a combination of computer hardware and software designed to have a specific function within a larger system.
  * They usually are part of another device and help to control these devices.

### Android

2003 - Android Inc. was Founded\
2005 - Google bought Android Inc.

Android was initially created as an operating system meant to run on digital cameras. Once Google acquired it, they made it into one of the most popular mobile operating systems.

Android on embedded devices has many advantages. The operating system is intuitive and easy to use with a graphical user interface, it has a very wide developer community, therefore it is easy to find help for development. It is also supported by the majority of the hardware vendors with an Android driver, therefore it is easy and cost effective to prototype an entire system.

### Raspbian and the Raspberry Pi

The Raspberry Pi is a low-cost, credit-card-sized computer developed by the Raspberry Pi Foundation, a UK-based educational charity. Its primary goal is to teach young people programming and computer functionality. While designed for educational purposes, it is also used in DIY projects and industrial prototyping. The Raspberry Pi features General Purpose Input-Output (GPIO) pins for connecting electronic devices and extension boards, making it ideal for hardware development. It uses ARM processors and operates on SD memory cards, running various operating systems, with Raspbian (a Debian-based distribution) being the most popular. Other Linux distributions, such as Kodi for media centers, are also available.

## Linux and the Cloud

Cloud computing refers to the use of computing resources provided by public or private cloud providers. As of 2017, Linux powers 90% of public cloud workloads, with providers like Amazon Web Services (AWS), Google Cloud Platform (GCP), and Microsoft Azure offering Linux-based services. Linux is typically offered as part of Infrastructure as a Service (IaaS), where users quickly provision virtual machines. Cloud providers offer various pre-configured Linux images for users to choose from, often with tools to customize the installation, such as adjusting file systems to fit the cloud instance's storage.

# 1.2 Major Open Source Applications

## Software Packages
 
Most Linux distributions come with a set of default applications pre-installed, and they also provide access to vast repositories of additional software through their package managers. Different distributions use different package management systems. For example, Debian, Ubuntu, and Linux Mint use tools like `dpkg`, `apt-get`, and `apt` for managing `DEB` packages, while Red Hat, Fedora, and CentOS use `rpm`, `yum`, and `dnf` for `RPM` packages. It's important to install packages from the correct repository for each distribution. The package manager automatically handles dependencies, which are additional packages needed by programs. Commands like `dpkg` and `rpm` manage individual package files, but most package management tasks are performed using `apt-get` or `apt` for DEB-based systems and `yum` or `dnf` for RPM-based systems, which also handle downloading, updating, and dependency management.

## Package Installation

### DEB Packages

If a package is not installed on your system, you can search for it in your distribution's repositories using the `apt-cache search package_name` or `apt search package_name` commands. The `apt-cache` command helps search for packages and provides information about available packages.


Installing or removing packages requires administrative permissions, typically granted to the root user. On desktop systems, regular users can use `sudo` to gain the necessary permissions, and will be prompted to enter their password. For DEB packages, installation is done with the command `apt-get install package_name` or `apt install package_name`. After inputting the command with the chosen *package_name*, the package will be downloaded and installed ont he system. Any dependencies that the package eventually needs will also be downloaded and installed. Once everything is downloaded, all the files are copied to the proper locations and any additional configuration weill be performed and the command will become available.

### RPM Packages

In RPM-based distributions, you can search for packages using the commands `yum search package_name` or `dnf search package_name`. If you're unsure about the package needed for a specific task, such as displaying text with a cartoonish cow, you can use descriptive terms in the search commands, similar to how it's done with DEB packages:

```bash
$ yum search speaking cow
```

After finding a suitable package at the repository, it can be installed with `yum install package_name` or `dnf install package_name`

```bash
$ yum install cowsay
```

## Package Removal

The same commands used to install packages are also used to remove them. To uninstall a package, you can use `apt-get remove package_name` or `apt remove package_name` for DEB packages, and `yum remove package_name` or `dnf remove package_name` for RPM packages. The `sudo` command is required for removal, just like for installation.

## Office Applications

Office applications are used for editing documents like texts, presentations, and spreadsheets, and are typically organized into office suites. For a long time, OpenOffice.org was the most popular office suite on Linux, which was later renamed Apache OpenOffice after being transferred to the Apache Foundation. Meanwhile, the Document Foundation created LibreOffice, a fork of OpenOffice.org with the same features and compatibility with Microsoft Office formats. Both suites prefer the Open Document Format (ODF), an open and ISO-standardized file format. Key applications in both suites include Writer (text editor), Calc (spreadsheets), Impress (presentations), Draw (vector drawing), Math (formulas), and Base (database). LibreOffice, licensed under LGPLv3, is more widely adopted due to its active development community and ability to integrate improvements from Apache OpenOffice, which is licensed under Apache License 2.0.

## Web Browsers

For most users, the primary purpose of a computer is to access the Internet, and web browsers are the most important application for this. Web pages now function as full-featured apps, accessible from anywhere without the need for extra software. The main web browsers on Linux are Google Chrome and Mozilla Firefox. Chrome is based on the open-source Chromium browser, while Firefox, developed by Mozilla, has roots in the Netscape browser and is closely involved with open web standards. Mozilla also develops Thunderbird, an email client that offers additional features compared to webmail. For learning about web development, the MDN Web Docs by Mozilla is a valuable resource.

## Multimedia

Desktop applications are still the best choice for creating multimedia content, as tasks like video rendering require significant system resources that are better handled by local applications. Popular multimedia applications for Linux include:

* **Blender:** A 3D renderer for animations and 3D printing.
* **GIMP:** A full-featured image editor similar to Adobe Photoshop, for creating and editing bitmap images.
* **Inkscape:** A vector graphics editor, similar to Corel Draw or Adobe Illustrator, using the open SVG format.
* **Audacity:** An audio editor for filtering, applying effects, and converting audio formats.
* **ImageMagick:** A command-line tool for converting and editing images, as well as creating PDFs from images.

For multimedia playback, VLC is the most popular video player, with alternatives like smplayer. For local music playback, options include Audacious, Banshee, and Amarok, which also manage music collections.

## Server Programs

When a web browser loads a page, it connects to a remote computer (server) to request specific information. The server, which manages and provides this data, runs an HTTP server program such as Apache, Nginx, or lighttpd. Web pages may involve static or dynamic content, with the server sending data and the browser rendering it using HTML and supporting files. Server-side scripting often uses PHP, while client-side scripting uses JavaScript. Servers can also interact with database servers, such as MariaDB (a fork of MySQL) or PostgreSQL, to retrieve or store data. Databases, especially relational ones, organize and manage large amounts of data efficiently, both for web and local applications.

## Data Sharing

In local networks, such as those in offices or homes, it's important for computers to communicate with each other. For Linux machines, the Network File System (NFS) is commonly used to share files between computers. NFS allows one computer to share directories with others on the network, enabling them to read and write files. Samba, on the other hand, is used for file and printer sharing between Linux and other operating systems, including Windows.

In some networks, a domain controller manages login authorization and access to resources. Linux workstations can connect to a domain controller using Samba or SSSD. Samba 4 can even act as a domain controller in mixed networks.

For cloud computing and web-based data sharing, two popular open-source solutions are ownCloud and Nextcloud. Both offer file sharing, synchronization, collaborative workspaces, and integration with calendars, contacts, and email. Nextcloud includes private audio/video conferencing, while ownCloud focuses more on file sharing and third-party integrations. Both provide free self-hosted versions, and paid versions offer additional features and support. When hosting either on a private server, it is crucial to enable HTTPS for secure connections.

## Network Administration

Communication between computers relies on proper network configuration, typically managed by a router using two key services: DHCP (Dynamic Host Configuration Protocol) and DNS (Domain Name System).

DHCP assigns IP addresses to devices when they connect to a network, either through a wired connection or wirelessly. It automates IP address distribution in local networks, avoiding the need for manual configuration, which is impractical for large networks. Most routers come with DHCP pre-configured.

DNS translates human-readable domain names (e.g., www.lpi.org) into IP addresses (e.g., 203.0.113.165) to enable communication. The DNS server's IP address is provided by the ISP's DHCP server and is used by all connected devices.

Both DHCP and DNS settings can be modified through the router's web interface, allowing restrictions on IP assignments or using third-party DNS servers like Google or OpenDNS for potentially faster responses and added features.

## Programming Languages

All computer programs are written using programming languages, and Linux systems provide a variety of these languages for different purposes. Programs typically begin as source code, written in a human-readable language, and are either compiled or interpreted for execution by the computer.

Compiled languages, like C and Java, require a compiler to convert the source code into a binary or bytecode, specific to a processor or platform. Interpreted languages, like JavaScript, Perl, Shell scripts, Python, and PHP, do not require prior compilation and are executed by an interpreter, making development faster but often less efficient.

Some popular programming languages include:

* **JavaScript:** Primarily used for web development, now also for servers and mobile apps.
* **C:** Known for its speed and flexibility, used in operating systems and applications across platforms.
* **Java:** A portable language that can run across different operating systems.
* **Perl:** Specializes in text processing, particularly with regular expressions.
* **Shell (Bash):** Used for scripting and automating tasks in the command line.
* **Python:** Popular for beginners and professionals, known for its simplicity.
* **PHP:** Primarily used for server-side web development and generating dynamic web content.

While compiled languages are converted into machine code or bytecode, interpreted languages are executed directly by an interpreter. The combination of Linux, Apache, MySQL/MariaDB, and PHP (LAMP) is a common solution for web servers.

# 1.3 Open Source Software and Licensing

## Definition of Free and Open Source Software

### Criteria of Free Software

> To understand the concept, you should think of "free" as in "free speech," not as in "free beer".\
> -Richard Stallman, What is free software?

Free software, as defined by Richard Stallman, is based on four essential freedoms:

1. Freedom 0: The freedom to run the program for any purpose, without restrictions on where, how, or for what purpose the software is used.
2. Freedom 1: The freedom to study the program’s source code and modify it to suit your needs. Access to the source code is required.
3. Freedom 2: The freedom to redistribute copies of the software to others, promoting widespread use and community development.
4. Freedom 3: The freedom to distribute modified versions of the software, allowing others to benefit from changes, while maintaining the original freedoms.

These freedoms stand in contrast to proprietary software, which restricts the access, use, and modification of the program, treating it as private property. Free software encourages collaboration, sharing, and improvement by a community of users and developers.

### Open Source Software vs. Free Software

Free software and open source software are often used interchangeably (as FOSS or FLOSS), but they have distinct origins and ideologies. The term free software was coined by Richard Stallman in 1985 with the launch of the GNU project, emphasizing the four freedoms: the freedom to run, study, modify, and share software. For Stallman, free software is not just a technical concept but a social and political movement aimed at empowering users through freedom.

On the other hand, open source software emerged later with the rise of Linux and the internet. It focuses more on the pragmatic, technical benefits of open code, with less emphasis on the social aspects. The openness of source code became a defining feature, but the movement prioritized development efficiency over the original ideological goals of the free software movement.

While both movements work in the same ecosystem and aim to make software accessible, there are sometimes conflicts when software reveals its source code but doesn't adhere to the principles of free software, like restricting modifications or redistributions. These conflicts are often tied to software licenses, which govern the conditions of use, distribution, and modification. Free software movements may reject some open-source licenses if they don't meet the four freedoms, while the open-source community generally takes a more flexible, pragmatic approach to licensing.

## Licenses

Software, unlike physical products, is a digital product, and when sold, companies transfer the rights of use, not ownership. The details of these rights are outlined in the software license, making it a crucial document. While proprietary software vendors like Microsoft have custom licenses, advocates of free and open-source software (FOSS) aim for simpler, universally understandable licenses. However, challenges arise due to varying legal systems, such as differences between German and American copyright law. These legal discrepancies have led to diverse and sometimes conflicting FOSS licenses, and legal disputes can occur when different licenses or versions are mixed within a project. Both free software and open source movements have created organizations that manage and enforce their respective licenses.

### Copyleft

The Free Software Foundation (FSF) created the GNU General Public License (GPL), one of the most important licenses for free software, and offers several variations, such as the GNU Lesser General Public License (LGPL), GNU Affero General Public License (AGPL), and GNU Free Documentation License (FDL). These licenses ensure that free software and its modifications remain open and accessible. The FSF promotes "copyleft," a principle ensuring that software modifications remain free, in contrast to restrictive copyright. However, this can cause compatibility issues when combining software under different copyleft licenses. The LGPL, for example, allows for free software to be linked with non-free components, such as libraries. Dual licensing is another solution, offering software under both free and proprietary licenses. Developers must carefully choose licenses for their projects to ensure compatibility with other software and avoid future complications.

### Open Source Definition and Permissive Licenses

The Open Source Initiative (OSI), founded in 1998 by Eric S. Raymond and Bruce Perens, focuses on licensing issues and has developed a process for verifying compliance with its Open Source Definition. The OSI currently recognizes over 80 open-source licenses. Some of these, particularly the BSD licenses, contradict the copyleft principle. BSD licenses, originating from the Unix operating system, are permissive, meaning they allow software to be modified and redistributed with minimal restrictions. These licenses do not require modifications to be released as open source, offering maximum freedom for distribution and commercial use. The 2-Clause BSD License, for example, only requires retaining copyright notices and disclaimers in redistributed software.

### Creative Commons

The success of FLOSS (Free/Libre and Open Source Software) inspired efforts to apply the open-source principle to non-technical fields like knowledge sharing and creative collaboration. This led to the development of Creative Commons (CC), a nonprofit organization providing free legal tools for sharing and reusing creativity. Unlike traditional copyright, where authors transfer all rights to publishers, Creative Commons allows authors to retain rights and control how their work is used. Authors can select from various licenses with different levels of restriction, contributing to a collaborative exchange of work. CC’s “Choose a License” tool helps authors generate the appropriate license for their work.

For a better understanding, here is an overview of the six possible combinations and licenses
offered by CC:

* **CC BY (“Attribution”):** The free license that allows anyone to edit and distribute the work as long as they name the author.
* **CC BY-SA (“Attribution-ShareAlike”):** As CC BY, except that the modified work may only be distributed under the same license. The principle reminds of the copyleft, because the license is “inherited” here as well.
* **CC BY-ND (“Attribution-NoDerivatives”):** Like CC BY, except that the work may only be passed on unmodified.
* **CC BY-NC (“Attribution-NonCommercial”):** The work may be edited and distributed by naming the author, but only under non-commercial conditions.
* **CC BY-NC-SA (“Attribution-NonCommercial-ShareAlike”):** As BY-NC, except that the work may only be shared under the same conditions (i.e. a copyleftlike license).
* **CC BY-NC-ND (“Attribution-NonCommercial-NoDerivatives”):** The most restrictive license: the distribution is allowed with attribution of the author, but only unchanged and under non-commercial conditions.


## Business Models in Open Source

The rise of FLOSS (Free/Libre and Open Source Software) has created a unique blend of idealistic, non-commercial development alongside billion-dollar companies, such as Red Hat, which was acquired by IBM in 2018. Despite FLOSS being mostly free to use, its developers need to earn money, leading to the development of sustainable business models.

Common business models in FLOSS include:

1. **Crowdfunding:** Developers collect donations via platforms like Kickstarter, offering donors bonuses like exclusive access or features if goals are met.
2. **Dual Licensing:** Free software is offered alongside a more restrictive proprietary license, which includes additional services like faster support or platform-specific versions. For example, ownCloud offers a “Business Edition” with added services under a proprietary license.
3. **Professional Services:** Companies lacking in-house technical expertise purchase consulting, maintenance, or helpdesk services directly from software developers to ensure reliable and secure operation.
4. **Merchandising and Certification:** Successful software can be monetized through selling branded merchandise or offering certifications, like Moodle's trainer certification, which validates expertise in using the software.
5. **Software as a Service (SaaS):** Web-based software applications are hosted by a provider (e.g., CRM or CMS) who charges customers based on usage, relieving them from installation and maintenance duties. Security and availability are key factors in this model.
6. **Custom Extensions:** Smaller projects often develop software extensions tailored to specific customers, who may choose whether to share or keep these extensions private.

In summary, while FLOSS software is typically free, various creative business models ensure the financial sustainability of the movement, enabling developers and companies to continue contributing to and evolving the FLOSS ecosystem.

# 1.4 ICT Skills and Working in Linux

In the past, using Linux on the desktop was challenging due to the lack of polished applications and configuration tools. Initially, Linux was aimed at advanced users, so the focus was on developing essential command line tools, with more complex graphical tools coming later. However, Linux desktop environments have since matured, offering a full range of features and ease of use. Despite this, the command line remains a powerful tool for advanced users. This lesson will cover basic desktop skills to help users choose the right tools for different tasks, including accessing the command line.

## Linux User Interfaces

This lesson focuses on the two primary ways to interact with a Linux system: the command line and graphical user interfaces (GUIs). Both methods provide access to a wide range of applications for various tasks. The lesson will explore desktop environments, how to access the terminal, and tools used for presentations and project management.

### Desktop Environments

Linux uses a modular approach, allowing different parts of the system to be developed by various projects and developers. This results in multiple desktop environments to choose from, with Gnome and KDE being the two major ones. Gnome follows the "Keep It Simple, Stupid" (KISS) principle, offering streamlined applications, while KDE provides more customization options with a wider range of applications. Gnome uses the GTK toolkit (C language), and KDE uses the Qt library (C++). Using the same toolkit for related applications ensures a consistent look and feel, saves memory, and improves loading times.

### Getting to the Command Line

A graphical terminal emulator allows users to access a command line environment within a graphical interface. In Gnome, this is called Gnome Terminal, while in KDE it is Konsole, with other options like Xterm also available. These applications enable interaction with a shell for command-line operations. Another way to access the terminal is through virtual TTYs, accessed by pressing `Ctrl` + `Alt` + `F#` (where # is a function key between 1 and 7). After logging in, users will enter a terminal without a graphical interface, and will need to start an X or Wayland session to use graphical applications.

### Presentations and Projects

The key tool for presentations on Linux is LibreOffice Impress, part of the open-source LibreOffice suite, which serves as an alternative to Microsoft Office and can handle PowerPoint files (PPT, PPTX). However, it is recommended to use the native ODP format for better long-term accessibility and compatibility. For those who prefer code-based tools, Beamer (for LaTeX) is ideal for academic presentations involving complex math symbols, while Reveal.js allows the creation of interactive presentations using HTML, CSS, and JavaScript. Additionally, GanttProject and ProjectLibre are good alternatives to Microsoft Project, offering similar features and compatibility with Project files.

## Industry Uses of Linux

Linux is widely used in the software and internet industries, powering about 68% of website servers. Its popularity is attributed to its free nature, stability, flexibility, and performance, which make it cost-effective and scalable. Many Linux systems now operate in the cloud, using IaaS (Infrastructure as a Service), PaaS (Platform as a Service), or SaaS (Software as a Service) models.

IaaS involves sharing server resources through virtual machines managed by hypervisors like Xen, KVM, and VirtualBox. KVM is the most prominent Linux hypervisor, especially used in cloud services. PaaS allows users to deploy applications without managing underlying systems, with Heroku being a common example. SaaS provides software via subscription, with services like Dropbox and Salesforce.

OpenStack is an open-source project that provides a complete IaaS cloud environment on-premises, leveraging computing clusters. Setting up such an infrastructure can be complex.

## Privacy Issues whe using the Internet

The web browser is a crucial software for accessing online services, but many users lack knowledge on how to use it securely. Browsers track and analyze users' actions, making it important to secure internet access and prevent tracking for safe online use.

### Cookie Tracking

Cookies are small files stored by websites on your computer to save useful information, like shopping cart items. While they can improve user experience, they are also used by ad networks to track your browsing behavior across different sites. For example, if you visit an e-commerce site, cookies can enable ads for products you viewed to follow you around the web. These ads are targeted based on cookies stored by ad networks. To avoid this tracking, you can block third-party cookies or use a cookie manager to control which cookies are stored, although some site features may require them to function properly.

### Do Not Track (DNT)

The "Do Not Track" (DNT) feature in browsers allows users to signal their preference to avoid being tracked by websites. However, it doesn't guarantee privacy, as websites are not required to respect this request. When enabled, DNT sends a flag (DNT: 1) with the HTTP request, but it ultimately depends on the website whether they honor this choice.

### "Private" Windows

Private or incognito browsing modes in web browsers, like Firefox's "private mode" or Chrome's "incognito" mode, offer a level of privacy by creating a session that doesn't share data with your regular browser profile. When you close the private window, it deletes browsing data such as history, passwords, and cookies, which helps avoid tracking through cookies. However, it doesn't provide complete anonymity. Websites and other parties can still use other tracking methods, and browsing is only private on the specific computer being used. It's especially useful on public computers, but security risks like malware or keyloggers remain a concern.

### Choosing the Right Password

Choosing a secure password is crucial for protecting your online accounts. Commonly used passwords like "qwerty" or birthdates are easily guessable and should be avoided. A good strategy is to create a memorable sentence and use the first letter of each word to form a password. However, reusing passwords across different services is risky, as a breach in one service can compromise multiple accounts. A better solution is using a password manager, which securely stores your passwords in an encrypted format. KeePass and Bitwarden are popular open-source password managers. KeePass stores passwords locally, while Bitwarden uses the cloud for easy synchronization across devices. It's important to generate random passwords for each service to enhance security.

## Encryption

To protect data from unauthorized access, it should be encrypted before being transferred or stored. Data transmitted over the internet passes through multiple routers and networks where third parties could potentially intercept it. Similarly, data on physical media can be accessed by anyone who possesses it. Encrypting confidential information ensures that only authorized parties can access it.

### TLS

Transport Layer Security (TLS) is a protocol that ensures secure network connections using cryptography. It is the successor to the outdated Secure Sockets Layer (SSL) and is currently in version 1.3. TLS provides privacy and authenticity through symmetric and public-key cryptography, preventing eavesdropping and tampering during communication. To verify a website's trustworthiness, look for the "lock" symbol in the browser’s address bar, which indicates the use of HTTPS (HTTP over TLS) for secure data transmission.

### File and E-mail Encryption With GnuPG

GnuPG (GNU Privacy Guard) is an open-source tool for securing emails and other data through encryption and digital signatures. It implements the OpenPGP standard (RFC 4880) and uses public-key cryptography, where users have a pair of keys: a public key for encryption and a private key for decryption. GnuPG can be used to encrypt, sign, and verify emails, files, and directories, ensuring data integrity and authenticity. The private key is used for signing, and the corresponding public key is used for verification. While powerful, GnuPG can be complex, and more information is available on its website and various wikis.

### Disk Encryption

To secure your data, you can encrypt your entire disk or partition using open-source software, with two main encryption methods: stacked and block device encryption.

* **Stacked encryption** encrypts files before storing them on the filesystem and decrypts them when read, while maintaining normal file structure.
* **Block device encryption** encrypts all data, including metadata and directory structure, making the entire block appear as random data when offline.

For block encryption on Linux, dm-crypt with LUKS is the standard. For stacked encryption, EncFS is a simpler option that doesn't require root privileges. For cross-platform use, Veracrypt (the successor to Truecrypt) allows encrypted volumes to be accessed on Linux, macOS, and Windows.

[Back To Main](/README.md)