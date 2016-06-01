``gettext`` API
===============

Extract some docstring of :mod:`gettext` here (see the `full module description <https://docs.python.org/3.5/library/gettext.html#module-gettext>`_).

.. function:: bindtextdomain(domain, localedir=None)

   Bind the *domain* to the locale directory *localedir*.  More concretely,
   :mod:`gettext` will look for binary :file:`.mo` files for the given domain using
   the path (on Unix): :file:`localedir/language/LC_MESSAGES/domain.mo`, where
   *languages* is searched for in the environment variables :envvar:`LANGUAGE`,
   :envvar:`LC_ALL`, :envvar:`LC_MESSAGES`, and :envvar:`LANG` respectively.

   If *localedir* is omitted or ``None``, then the current binding for *domain* is
   returned. [#]_

.. function:: gettext(message)

   Return the localized translation of *message*, based on the current global
   domain, language, and locale directory.  This function is usually aliased as
   :func:`_` in the local namespace (see examples below).

Here's an example of typical usage for this API:

.. code-block:: python3

   import gettext
   gettext.bindtextdomain('myapplication', '/path/to/my/language/directory')
   gettext.textdomain('myapplication')
   _ = gettext.gettext
   # ...
   print(_('This is a translatable string.'))


Acknowledgements
----------------

The following people contributed code, feedback, design suggestions, previous
implementations, and valuable experience to the creation of this module:

* Peter Funk

* James Henstridge

* Juan David Ibáñez Palomar

* Marc-André Lemburg

* Martin von Löwis

* François Pinard

* Barry Warsaw

* Gustavo Niemeyer

.. rubric:: Footnotes


.. [#] The default locale directory is system dependent; for example, on RedHat Linux
   it is :file:`/usr/share/locale`, but on Solaris it is :file:`/usr/lib/locale`.
   The :mod:`gettext` module does not try to support these system dependent
   defaults; instead its default is :file:`sys.prefix/share/locale`. For this
   reason, it is always best to call :func:`bindtextdomain` with an explicit
   absolute path at the start of your application.
