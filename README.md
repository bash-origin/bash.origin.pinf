bash.origin.pinf
================

A plugin for [Bash.Origin](https://github.com/bash-origin/bash.origin) to make [genesis.pinf.org](https://github.com/pinf/genesis.pinf.org) available for early preview.


Usage
-----

	#!/bin/bash
	# Source https://github.com/cadorn/bash.origin
	. "$HOME/.bash.origin"
	function init {
		eval BO_SELF_BASH_SOURCE="$BO_READ_SELF_BASH_SOURCE"
		BO_deriveSelfDir ___TMP___ "$BO_SELF_BASH_SOURCE"
		local __BO_DIR__="$___TMP___"


		pushd "$__BO_DIR__/demo-app"
			BO_callPlugin "bash.origin.pinf" pit
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

Calls [pit](https://github.com/pinf-it/pit-for-npm) passing along all arguments.


License
=======

Original Author: [Christoph Dorn](http://christophdorn.com)

[UNLICENSE](http://unlicense.org/)

