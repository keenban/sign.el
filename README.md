# Signel.el

**Signel** is a lightweight, asynchronous Signal client for Emacs. It communicates with a running `signal-cli` daemon via JSON-RPC to provide a seamless chat experience within your editor.

## Features

- **Strict Buffers:** Telega-style read-only history with a guarded input prompt.
- **Rich Media:** Inline rendering of images and buttons for file attachments.
- **Dashboard:** Auto-refreshing list of active conversations.
- **Notifications:** Integration with Emacs desktop notifications.
- **Async:** Non-blocking IO using Emacs process filters.

## Prerequisites

1.  **signal-cli:** You must have `signal-cli` installed and in your `$PATH`.
    * [Installation Instructions](https://github.com/AsamK/signal-cli)
2.  **Account Registered:** You must link or register your account via the command line *before* using Signel.
    ```bash
    # Example: Link a new device
    signal-cli link -n "emacs-client" | xargs -n 1 qrencode -t utf8
    ```

## Installation

### Manual
1.  Clone this repository:
    ```bash
    git clone [https://github.com/YOUR_USERNAME/signel.git](https://github.com/YOUR_USERNAME/signel.git) ~/.emacs.d/site-lisp/signel
    ```
2.  Add to your `init.el`:
    ```elisp
    (add-to-list 'load-path "~/.emacs.d/site-lisp/signel")
    (require 'signel)
    ```

### Use-Package
```elisp
(use-package signel
  :load-path "~/.emacs.d/site-lisp/signel"
  :config
  ;; REQUIRED: Your phone number (must match signal-cli)
  (setq signel-account "+15551234567")

  ;; OPTIONAL: Path to executable if not in $PATH
  ;; (setq signel-cli-program "/home/user/.local/bin/signal-cli")
)
