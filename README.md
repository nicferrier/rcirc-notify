# rcirc-notify

## Introduction

rcirc-notify adds notification support to the Emacs IRC client rcirc.

## Installation

It's best to install rcirc-notify [via marmalade](http://marmalade-repo.org/packages/rcirc-notify).

Alternately you can copy the file to your load path and `(require 'rcirc-notify)`.

rcirc-notify supports the following notification utilities, ensure that one of them is installed:

 - [notify-send](http://manpages.ubuntu.com/manpages/gutsy/man1/notify-send.1.html) (Linux)
 - terminal-notify
 - [terminal-notifier](https://github.com/alloy/terminal-notifier) (Mac OS X >= 10.8)
 - [Growl](http://growl.info/) (Mac OS X)

## Usage

First of all test that you have a notification application set up properly:

      (rcirc-notify-page-me "Hello World")

If that displayed a notification you're ready to configure things. If not stop here and make sure you have one of the supported notification utilities installed!


The following customization variables are available:

| Name                           | Description                                                                              | Default                             |
| ------------------------------ | ---------------------------------------------------------------------------------------- | ----------------------------------- |
| `rcirc-notify-message`         | Format of the notification string to display when someone mentions your name / keywords. | "%s mentioned you: %s"              |
| `rcirc-notify-keywords`        | List of keywords that will trigger a notification in rcirc.                              | nil                                 |
| `rcirc-notify-keyword`         | Format of the notification string to display when someone mentions a keyword.            | "%s mentioned the keyword '%s': %s" |
| `rcirc-notify-message-private` | Format of the notification string to display when someone sends you a private message    | "%s sent a private message: %s"     |
| `rcirc-notify-popup-timeout`   | Number of seconds to display the notification popup for.                                 | 8640000                             |
| `rcirc-notify-timeout`         | Seconds between notifications from the same user, avoids being spammed by one person.    | 60                                  |


Additionally there is one hook `rcirc-notify-page-me-hooks` that can be used to perform something else on notification, for example playing a sound:

      ; Play a sound file on notification (using afplay, a program included with Mac OS)
      (add-hook 'rcirc-notify-page-me-hooks
         (lambda (msg)
           (start-process "beep-process" nil "afplay" "~/some-sound-file..m4a")))

## License

      ;; This program is free software; you can redistribute it and/or
      ;; modify it under the terms of the GNU General Public License as
      ;; published by the Free Software Foundation; either version 3 of
      ;; the License, or (at your option) any later version.
      ;;
      ;; This program is distributed in the hope that it will be
      ;; useful, but WITHOUT ANY WARRANTY; without even the implied
      ;; warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR
      ;; PURPOSE.  See the GNU General Public License for more details.
      ;;
      ;; You should have received a copy of the GNU General Public
      ;; License along with this program; if not, write to the Free
      ;; Software Foundation, Inc., 59 Temple Place, Suite 330, Boston,
      ;; MA 02111-1307 USA
