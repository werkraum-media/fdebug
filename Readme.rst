TYPO3 f:debug alternative
=========================

TYPO3 offers an ``f:debug`` ViewHelper to introspect variables.
That ViewHelper is a small wrapper around ``DebuggerUtility`` of EXT:extbase.

The result of ``DebuggerUtility`` is always developer focused.
``f:debug`` on the other hand is used within Fluid and should be integrator focused.

This extension provides an alternative to existing ``f:debug`` which focuses on
integrators.

Installation
------------

Run ``composer req --dev werkraummedia/fdebug:^1.0``.

Usage
-----

1:1 the original ``f:debug``, no need to change anything.
The original ViewHelper is overloaded and not usable anymore.

The goal
--------

Improve usage for integrators. E.g. show data they have access to within Fluid.
Don't focus on properties, but actual available info.
Inspect methods and public properties. Respect method names.

This should become part of TYPO3 core (by providing a patch) once it is stable
enough.
Right now it might lack features or break under some circumstances.

Please give it a try and open issues or provide pull requests.

Why an extension?
-----------------

That allows for usage of ``ext_localconf.php`` to overload Fluid namespace ``f``.
Also it allows to easily share and update the current state and prevent inclusion
into production systems.

Current features
----------------

Do not render protected or private properties. These are not available within Fluid.

Render methods which are public and start with ``get``, ``has`` or ``is`` and don't
need any arguments.
