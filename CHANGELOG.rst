0.3.1 (2019-03-02)
==================

Features
--------

- Added a custom cursor hiding implementation to avoid depending on the cursor library, which was re-released under the GPL.  `#57 <https://github.com/sarugaku/vistir/issues/57>`_


0.3.0 (2019-01-01)
==================

Features
--------

- Added a new ``vistir.misc.StreamWrapper`` class with ``vistir.misc.get_wrapped_stream()`` to wrap existing streams
  and ``vistir.contextmanagers.replaced_stream()`` to temporarily replace a stream.  `#48 <https://github.com/sarugaku/vistir/issues/48>`_

- Added new entries in ``vistir.compat`` to support movements to ``collections.abc``: ``Mapping``, ``Sequence``, ``Set``, ``ItemsView``.  `#51 <https://github.com/sarugaku/vistir/issues/51>`_

- Improved ``decode_for_output`` to handle decoding failures gracefully by moving to an ``replace`` strategy.
  Now also allows a translation map to be provided to translate specific non-ascii characters when writing to outputs.  `#52 <https://github.com/sarugaku/vistir/issues/52>`_

- Added support for properly encoding and decoding filesystem paths at the boundaries across python versions and platforms.  `#53 <https://github.com/sarugaku/vistir/issues/53>`_


Bug Fixes
---------

- Fix bug where FileNotFoundError is not imported from compat for rmtree  `#46 <https://github.com/sarugaku/vistir/issues/46>`_

- Fixed a bug with exception handling during ``_create_process`` calls.  `#49 <https://github.com/sarugaku/vistir/issues/49>`_

- Environment variables will now be properly passed through to ``run``.  `#55 <https://github.com/sarugaku/vistir/issues/55>`_


0.2.5 (2018-11-21)
==================

Features
--------

- Added the ability to always write spinner output to stderr using ``write_to_stdout=False``.  `#40 <https://github.com/sarugaku/vistir/issues/40>`_

- Added extra path normalization and comparison utilities.  `#42 <https://github.com/sarugaku/vistir/issues/42>`_


0.2.4 (2018-11-12)
==================

Features
--------

- Remove additional text for ok and fail state  `#35 <https://github.com/sarugaku/vistir/issues/35>`_

- Backported compatibility shims from ``CPython`` for improved cleanup of readonly temporary directories on cleanup.  `#38 <https://github.com/sarugaku/vistir/issues/38>`_


0.2.3 (2018-10-29)
==================

Bug Fixes
---------

- Improved handling of readonly path write-bit-setting.  `#32 <https://github.com/sarugaku/vistir/issues/32>`_

- Fixed a bug with encoding of output streams for dummy spinner and formatting exceptions.  `#33 <https://github.com/sarugaku/vistir/issues/33>`_


0.2.2 (2018-10-26)
==================

Bug Fixes
---------

- Fixed a bug in the spinner implementation resulting in a failure to initialize colorama which could print control characters to the terminal on windows.  `#30 <https://github.com/sarugaku/vistir/issues/30>`_


0.2.1 (2018-10-26)
==================

Features
--------

- Implemented ``vistir.misc.create_tracked_tempdir``, which allows for automatically cleaning up resources using weakreferences at interpreter exit.  `#26 <https://github.com/sarugaku/vistir/issues/26>`_


Bug Fixes
---------

- Fixed a bug with string encodings for terminal colors when using spinners.  `#27 <https://github.com/sarugaku/vistir/issues/27>`_

- Modified spinners to prefer to write to ``sys.stderr`` by default and to avoid writing ``None``, fixed an issue with signal registration on Windows.  `#28 <https://github.com/sarugaku/vistir/issues/28>`_


0.2.0 (2018-10-24)
==================

Features
--------

- Add windows compatible term colors and cursor toggles via custom spinner wrapper.  `#19 <https://github.com/sarugaku/vistir/issues/19>`_

- Added new and improved functionality with fully integrated support for windows async non-unicode spinner.  `#20 <https://github.com/sarugaku/vistir/issues/20>`_

- ``vistir.contextmanager.spinner`` and ``vistir.spin.VistirSpinner`` now provide ``write_err`` to write to standard error from the spinner.  `#22 <https://github.com/sarugaku/vistir/issues/22>`_

- Added ``vistir.path.create_tracked_tempfile`` to the API for weakref-tracked temporary files.  `#26 <https://github.com/sarugaku/vistir/issues/26>`_


Bug Fixes
---------

- Add compatibility shim for ``WindowsError`` issues.  `#18 <https://github.com/sarugaku/vistir/issues/18>`_

- ``vistir.contextmanager.spinner`` and ``vistir.spin.VistirSpinner`` now provide ``write_err`` to write to standard error from the spinner.  `#23 <https://github.com/sarugaku/vistir/issues/23>`_

- Suppress ``ResourceWarning`` at runtime if warnings are suppressed in general.  `#24 <https://github.com/sarugaku/vistir/issues/24>`_


0.1.7 (2018-10-11)
==================

Features
--------

- Updated ``misc.run`` to accept new arguments for ``spinner``, ``combine_stderr``, and ``display_limit``.  `#16 <https://github.com/sarugaku/vistir/issues/16>`_


0.1.6 (2018-09-13)
==================

Features
--------

- Made ``yaspin`` an optional dependency which can be added as an extra by using ``pip install vistir[spinner]`` and can be toggled with ``vistir.misc.run(...nospin=True)``.  `#12 <https://github.com/sarugaku/vistir/issues/12>`_

- Added ``verbose`` flag to ``vistir.misc.run()`` to provide a way to prevent printing all subprocess output.  `#13 <https://github.com/sarugaku/vistir/issues/13>`_


0.1.5 (2018-09-07)
==================

Features
--------

- Users may now pass ``block=False`` to create nonblocking subprocess calls to ``vistir.misc.run()``.
  ``vistir.misc.run()`` will now provide a spinner when passed ``spinner=True``.  `#11 <https://github.com/sarugaku/vistir/issues/11>`_


Bug Fixes
---------

- ``vistir.misc.run()`` now provides the full subprocess object without communicating with it when passed ``return_object=True``.  `#11 <https://github.com/sarugaku/vistir/issues/11>`_


0.1.4 (2018-08-18)
==================

Features
--------

- Implemented ``vistir.path.ensure_mkdir_p`` decorator for wrapping the output of a function call to ensure it is created as a directory.

  Added ``vistir.path.create_tracked_tmpdir`` functionality for creating a temporary directory which is tracked using an ``atexit`` handler rather than a context manager.  `#7 <https://github.com/sarugaku/vistir/issues/7>`_


Bug Fixes
---------

- Use native implementation of ``os.makedirs`` to fix still-broken ``mkdir_p`` but provide additional error-handling logic.  `#6 <https://github.com/sarugaku/vistir/issues/6>`_


0.1.3 (2018-08-18)
==================

Bug Fixes
---------

- Fixed an issue which caused ``mkdir_p`` to use incorrect permissions and throw errors when creating intermediary paths.  `#6 <https://github.com/sarugaku/vistir/issues/6>`_


0.1.2 (2018-08-18)
==================

Features
--------

- Added ``mode`` parameter to ``vistir.path.mkdir_p``.  `#5 <https://github.com/sarugaku/vistir/issues/5>`_


0.1.1 (2018-08-14)
==================

Features
--------

- Added suport for coverage and tox builds.  `#2 <https://github.com/sarugaku/vistir/issues/2>`_

- Enhanced subprocess runner to reproduce the behavior of pipenv's subprocess runner.  `#4 <https://github.com/sarugaku/vistir/issues/4>`_


Bug Fixes
---------

- Fixed an issue where ``vistir.misc.run`` would fail to encode environment variables to the proper filesystem encoding on windows.  `#1 <https://github.com/sarugaku/vistir/issues/1>`_

- Fixed encoding issues when passing commands and environments to ``vistir.misc.run()``.  `#3 <https://github.com/sarugaku/vistir/issues/3>`_


0.1.0 (2018-08-12)
=======================

Features
--------

- Initial commit and release  `#0 <https://github.com/sarugaku/vistir/issues/0>`_
