===================
rc.tiles.collection
===================

A tile that shows collection results with customizable layouts
forked from collective/collective.tiles.collection

Features
--------

- Emulates the old portlet collection behaviors
- Mosaic-ready
- Additional css class field, to append a custom css class to the tile container
- Customizable layouts list



Installation
------------

Install rc.tiles.collection by adding it to your buildout::

    [buildout]

    ...

    eggs =
        rc.tiles.collection


and then running ``bin/buildout``


Usage
-----

You can't use this tile without a tile manager (or maybe, you can if you create
new tiles manually in some specific context) like `Mosaic <https://pypi.python.org/pypi/plone.app.mosaic>`_ or `redturtle.tiles.management <https://github.com/RedTurtle/redturtle.tiles.management>`_

When you try to create a new collection tile, you have a form like the portlet's one.

Customizable layouts
--------------------

When you create/edit a collection tile, there is a field that allows you to select the final layout from a list.
This list is generated with a specific set of view that satisfy following rules:

- The Class must implement **IRcTilesCollectionLayer** interface
- In the Class there should be an attribute **display_name** with a human-readable title
- The template need to define a macro called **collection-tile-macro**

This is an example:

`configure.zcml`::

    <browser:page
        name="additional_renderer"
        permission="zope2.View"
        for="*"
        class=".additional_render.View"
        layer=".interfaces.ISomeBrowserLayer"
        template="additional_render.pt"
    />


`additional_render.py`::

    from Products.Five.browser import BrowserView
    from rc.tiles.collection.interfaces import IRcTilesCollectionLayer
    from zope.interface import implements
    from rc.tiles.collection import _


    class AdditionalView(BrowserView):
        implements(ICollectionTileRenderer)

        display_name = _("Another tile layout")


`additional_render.pt`::

    <html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en"
          xmlns:tal="http://xml.zope.org/namespaces/tal"
          xmlns:metal="http://xml.zope.org/namespaces/metal"
          xmlns:i18n="http://xml.zope.org/namespaces/i18n"
          lang="en"
          metal:use-macro="here/main_template/macros/master"
          i18n:domain="rc.tiles.collection">
      <body>
        <metal:macro define-macro="collection-tile-macro">
          ...
        </metal:macro>
      </body>
    </html>


Translations
------------

This product has been translated into

- Italian


Contribute
----------

- Issue Tracker: https://github.com/collective/collective.tiles.collection/issues
- Source Code: https://github.com/collective/collective.tiles.collection

- Issue Tracker: https://github.com/rogeriocdluiz/rc.tiles.collection/issues
- Source Code: https://github.com/rogeriocdluiz/rc.tiles.collection


Credits
-------

Developed with the support of:

* `Regione Emilia-Romagna`__

Regione Emilia-Romagna supports the `PloneGov initiative`__.

__ http://www.regione.emilia-romagna.it/
__ http://www.plonegov.it/

Authors
-------

This product was developed by RedTurtle Technology team.

.. image:: http://www.redturtle.it/redturtle_banner.png
   :alt: RedTurtle Technology Site
   :target: http://www.redturtle.it/

forked from collective/collective.tiles.collection by:

* `Rogerio da Costa`__

__ http://www.rogeriodacosta.com.br



License
-------

The project is licensed under the GPLv2.























Contribute
----------



Support
-------

If you are having issues, please let us know.
We have a mailing list located at: project@example.com


License
-------

The project is licensed under the GPLv2.
