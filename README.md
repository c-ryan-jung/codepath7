# Project 7 - WordPress Pentesting

Time spent: 4 hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. Authenticated Stored Cross-Site Scripting

- [ ] Summary: For this exploit, one can take advantage of the fact that there is a vulnerability where one can place an html link, but inside it hide a javascript alert command to run.
  - Vulnerability types: XSS
  - Tested in version: 4.2.2
  - Fixed in version: 4.2.3
- [ ] GIF Walkthrough:
- [ ] Steps to recreate: The code executes when the mouse is hovered over the link. In order to do this, an attack must have access to an account with posting privileges. The first step is to create a new post. Make sure that the body of the post is in text mode not visual mode. From here all one has to do is create an html code for a link, and inside that, have the javascript command of choice. For this example, I used <!--<a h r e f="[caption code=">]</a><a title=" onmouseover=alert('test')  ">link</a>\*/-->
      Afterwards, all one needs to do is create the post. When examining the post in question, for this example I chose a javascript line of code that executes an alert when a user hovers their mouse over the link.

- [ ] Affected source code:
  - [Link 1](https://core.trac.wordpress.org/changeset/33359)

2. Legacy Theme Preview Cross-Site Scripting

- [ ] Summary: For this exploit, when admin tries to preview a theme, the preview_theme_ob_filter_callback removes “onclick” handlers. This allows for one to use javascript in the the comments to cause an alert to pop up.
  - Vulnerability types: XSS
  - Tested in version: 4.2.3
  - Fixed in version: 4.2.4
- [ ] GIF Walkthrough:
- [ ] Steps to recreate:In order to do this, one must access the page as admin. Next post a comment containing a javascript command that executes when the mouse is hovered over a certain area, I used <!--<a href='/wp-admin/' title="" style="position:absolute;top:0;left:0;width:100%;height:100%;display:block;" onmouseover=alert(1)//' rel="nofollow">Test</a> Mouse over the area in question and the alert will pop up.-->
- [ ] Affected source code:
  - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)

3. Large file upload error XSS

- [ ] Summary:For this exploit, an admin tries to upload media that has been named with javascript and that is too big. An error will occur and the javascript will take advantage of that error and create an alert
  - Vulnerability types: XSS
  - Tested in version: 4.2
  - Fixed in version: 4.2.15
- [ ] GIF Walkthrough:
- [ ] Steps to recreate:
- [ ] Affected source code:
  - [Link 1](https://core.trac.wordpress.org/browser/tags/4.9/src/wp-includes/class-wp-xmlrpc-server.php#L5877)

## Assets

List any additional assets, such as scripts or files

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work

## License

    Copyright [2018] [Ryan Jung]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
