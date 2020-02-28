# sticky-kubectl

sticky-kubectl is a Bash wrapper around kubectl providing a unique kubeconfig per terminal tab or window. What you do to your kubeconfig in one terminal session does not affect other sessions.

## Benefits

* Last prompt decoration in a tab (e.g. `PS1` for Bash) that shows current context and namespace is always accurate, even if you've switched contexts in another tab.
* Saves passing the context each time as an kubectl argument.
* No pollution of environment variables--they are only set in the current shell (i.e. the wrapper).
* Warns when canonical kubeconfig (i.e. `~/.kube/config`) no longer matches current tab's copy.

## How It Works

1. Copies canonical kubeconfig (i.e. `~/.kube/config`) to a temporary direction expressly created for this terminal tab.
2. Sets kubeconfig to this new file before calling the real kubectl.

## Installing

1. Put this script in a directory in your `PATH` that precedes the location of the real kubectl.
2. Make it executable.
3. Customize the script to suit your needs.

## Requirements

* Your terminal emulator must set environment variable `TERM_SESSION_ID`.

## Testing

Tested on macOS and iTerm2.
