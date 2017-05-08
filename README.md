# Bad Usernames

A blacklist of usernames that should not be allowed in an application.

Main reasons is to avoid confusion and mistakes by other users if they interact with a user using a blacklisted username. This can be by accident, but also as more serious phishing attempts.

## Contents

Json files for each language. Defaults to plain English (en).

## Reasons

#### Url path

Many websites have user generated content under a sub folder by their username. Eg `john_smith`'s stuff can be under `http://www.example.com/john_smith/mymusic`. This seems harmless.

However if the username was `support` then `http://www.example.com/support/change_password.html` is not ok.

#### Subdomain

Other applications may use usernames as a subdomain. `john_smith.example.com` is fine. A username of `secure` could potentially expose `secure.example.com` which seems ripe for nefarious behaviour, not to mention `www` as username or subdomain of `mail.example.com`, etc.

#### Email aliases

Also if emails sent/received by the application perhaps uses the username as an smtp alias then `john_smith@example.com` is harmless. But someone at `root@example.com` could potently social engineer a SSL certificate change etc.

#### RFC 2142

https://www.ietf.org/rfc/rfc2142.txt provides a list of mandatory and common optional email aliases. It is a good idea to black list most of these as a username. https://webmasters.stackexchange.com/a/105020 is more elaborate.

## More rules

Suggested rules in addition to black list.

#### UTF 8

Allowing UTF-8 and similar character sets for usernames can be dangerous. It is user friendly to support UTF-8 especially with an international customer base. But it is a potential minefield with random characters that looks like ASCII a-z. In general ASCII only is recommended even if it restricts some `O'Reilly`, `Gøran`, etc. (See https://labs.spotify.com/2013/06/18/creative-usernames/)

#### I18n

In addition to UTF-8 character set be aware of confusion and phishing attempts with usernames that sound genuine in other languages. Even when language used for the application is english only. Hence the need for multiple language json files in this project.


#### Symbols

Also some usernames can be made to look genuine by inserting symbols e.g. underscores or dashes. One potential rule is to only allow a few special characters, perhaps only `_`. And then also only in the middle of the username and not at the beginning or end.

#### Prefix

Some usernames can be made to look genuine with clever prefixes. A more elaborate check could restrict if username is prefixed by a black listed username. So no `admin-web` would be allowed if `admin` was black listed.

#### Lowercase

Convert all usernames to lowercase. `Admin`, `admin` and `adMin` is the same username.

#### Length

Probably makes sense to have a minimum length username. 1, 2 or even 3 characters gets pretty vague. And perhaps a maximum length, though be generous, e.g. 128 characters.

#### Plurals

If not checking for prefixes, e.g. in English adding an `s` may make `admins` look genuine. 

## Non exhaustive

Phishers are devious and this black list is brittle and short. But it is a start.

## Contribute

Please send pull requests to https://github.com/flurdy/bad_usernames/pull. Especially for other languages.
