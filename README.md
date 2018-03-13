Emacs Lisp name-generator
=========================

Docker-like names generator written in Emacs Lisp (elisp).

### Usage

## Installation

Place `name-generator.el` inside the directory of your choice (e.g. `~/.emacs.d/lisp/`)
and add the following to your Emacs `init.el`, `~/.emacs/`, ...:

```el
(add-to-list 'load-path "~/.emacs.d/lisp/")
(load "name-generator")
```

## Usage

Basic usage:

`M-:` or `eval-expression`: `(generate-random-name)`

Personally, I use it to create temp scratch buffers with creative and,
more importantly, human-friendly names like so:

```el
(defun open-new-random-named-scratch ()
  "Opens a new scratch buffer with a friendly name."
  (interactive)
  (switch-to-buffer (cl-loop for name = (generate-random-name)
                          while (get-buffer name)
                          finally (cl-return name))))
(global-set-key (kbd "C-c n") 'open-new-random-named-scratch)
```


### Other implementations

* [Go][1] (original)
* [Node.js][2]
* [Python, JavaScript and TypeScript][3]
* Not exactly the same, but also fun: [Fantasy Name Generator][4]

[1]: https://github.com/docker/docker/blob/master/pkg/namesgenerator/names-generator.go
[2]: https://github.com/atomiqio/docker-namesgenerator
[3]: https://github.com/shamrin/namesgenerator
[4]: https://github.com/skeeto/fantasyname
