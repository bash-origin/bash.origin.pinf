bash.origin.pinf
================

A plugin for [Bash.Origin](https://github.com/bash-origin/bash.origin) to make [genesis.pinf.org](https://github.com/pinf/genesis.pinf.org) tools available.


Usage
-----

	#!/bin/bash
	# Source https://github.com/cadorn/bash.origin
	. "$HOME/.bash.origin"
	function init {
		eval BO_SELF_BASH_SOURCE="$BO_READ_SELF_BASH_SOURCE"
		BO_deriveSelfDir ___TMP___ "$BO_SELF_BASH_SOURCE"
		local __BO_DIR__="$___TMP___"

		# Example: Provision PINF.Genesis for demo app
		pushd "$__BO_DIR__/demo-app" > /dev/null
			BO_callPlugin "bash.origin.pinf@0.1.0" ensure genesis $@
		popd > /dev/null

		# Example: Call PINF.IT for demo app
		pushd "$__BO_DIR__/demo-app"
			BO_callPlugin "bash.origin.pinf" pit
		popd

		# Example: Call PINF.TO for demo app
		pushd "$__BO_DIR__/demo-app"
			BO_callPlugin "bash.origin.pinf" pto
		popd
	}
	init


Test
----

	./test

After running the test you will find generated bundles at `./demo-app/bundles`.


API
---

### `pit ...`

Calls [pit](https://github.com/pinf-it/pit-for-npm) for current working directory passing along all arguments.


### `pto ...`

Calls [pto](https://github.com/pinf-to/pto-for-npm) for current working directory passing along all arguments.


### `ensure genesis ...`

Installs [genesis.pinf.org](https://github.com/pinf/genesis.pinf.org) for current working directory passing along all arguments.


License
=======

Original Author: [Christoph Dorn](http://christophdorn.com)

[UNLICENSE](http://unlicense.org/)

