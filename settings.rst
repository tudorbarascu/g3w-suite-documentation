***************
Settings
***************

The following variables can be added to or edited in the project’s ``local_settings.py``:

Base settings
*************

``G3WADMIN_PROJECT_APPS``
^^^^^^^^^^^^^^^^^^^^^^^^^
Custom django map server module other than `qdjango` (QGIS-Server provider)

``G3WADMIN_LOCAL_MORE_APPS``
^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Custom django modules that is possible to add, i.e. ``g3w-admin-frontend`` (https://github.com/g3w-suite/g3w-admin-frontend) module and other third part django modules.
G3W-SUITE accessory modules:

    - ``g3w-admin-frontend`` (https://github.com/g3w-suite/g3w-admin-frontend)
    - ``caching``
    - ``filemanager``
    - ``editing``

``DATASOURCE_PATH``
^^^^^^^^^^^^^^^^^^^
Path to geo data directory (shp, Spatialite, raster, etc..).

``G3WFILE_FORM_UPLOAD_FORMATS``
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
List of formats file that `file form ajax uploader` can manage at global level.
Default is `['qgs', 'qgz', 'png', 'jpg', 'jpeg', 'pdf', 'doc', 'docx', 'xls', 'xlsx', 'ods']`

.. Important::
    Last part of path could be common with QGIS project datasource path. I.e.:

    *QGIS project*:
    <datasource>/<path>/<to>/**project_data**/<geodata>.shp</datasource>

    *local_settings.py*:
    DATASOURCE_PATH = /<local_server_<path>/<to>/**project_data**


Mandatory.

``G3WADMIN_VECTOR_LAYER_DOWNLOAD_FORMATS``
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Default is `['shp', 'xls']`, set download data format. Values possible:
  - *shp*: download into Esri Shape format.
  - *xls*: download into Excel format
  - *gpx*: download into GPS format (only for Point and Line layers)

``RESET_USER_PASSWORD``
^^^^^^^^^^^^^^^^^^^^^^^
Default is `False`, set tot `True` to activate reset user password by email workflow.
If set to True remember to set Django emailing settings (https://docs.djangoproject.com/en/2.2/topics/email/).

``CLIENT_OWS_METHOD``
^^^^^^^^^^^^^^^^^^^^^
Default is `'GET'`, set to `'POST'` to change default http call method.


Frontend portal setting
***********************

``FRONTEND``
^^^^^^^^^^^^
Default is ``False``, set to ``True`` for activate **G3W-SUITE** frontend portal like ``g3w-admin-frontend``.
If it's set to ``True`` base url path for G3W-SUITE admin section become `/admin/`.

``FRONTEND_APP``
^^^^^^^^^^^^^^^^
Module name added to ``G3WADMIN_LOCAL_MORE_APPS`` to use as `portal-frontend`. I.e.::

    G3WADMIN_LOCAL_MORE_APPS = [
        ...
        'frontend',
        ...
    ]

    FRONTEND = True
    FRONTEND_APP = 'frontend'


General layout settings
***********************

``G3WSUITE_POWERD_BY``
^^^^^^^^^^^^^^^^^^^^^^
Default is ``True``, set to ``False`` for don't show bottom `attribution` informations.

``G3WSUITE_CUSTOM_STATIC_URL``
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
A custom url from to load custom static files as images, css, etc..

``G3WSUITE_MAIN_LOGO``
^^^^^^^^^^^^^^^^^^^^^^
Main admin section logo image.
Mandatory is set ``G3WSUITE_CUSTOM_STATIC_URL``

``G3WSUITE_RID_LOGO``
^^^^^^^^^^^^^^^^^^^^^
Main admin section reduced logo image.
Mandatory is set ``G3WSUITE_CUSTOM_STATIC_URL``

``G3WSUITE_LOGIN_LOGO``
^^^^^^^^^^^^^^^^^^^^^^^
Login logo image.
Mandatory is set ``G3WSUITE_CUSTOM_STATIC_URL``

``G3WSUITE_CUSTOM_TITLE``
^^^^^^^^^^^^^^^^^^^^^^^^^
**G3W-SUITE** html page title.
If is not set, title is: `g3w-admin` for admin section and `g3w-client` for webgis client.

``G3WSUITE_FAVICON``
^^^^^^^^^^^^^^^^^^^^
Favorite icon image.
Mandatory is set ``G3WSUITE_CUSTOM_STATIC_URL``

``G3WSUITE_CUSTOM_CSS``
^^^^^^^^^^^^^^^^^^^^^^^
A list of custom css files added to `admin` pages and to the `client`.
Mandatory is set ``G3WSUITE_CUSTOM_STATIC_URL``.
I.e.::

    G3WSUITE_CUSTOM_CSS = [
        G3WSUITE_CUSTOM_STATIC_URL +'css/custom.css'
    ]

``G3WSUITE_CUSTOM_JS``
^^^^^^^^^^^^^^^^^^^^^^
A list of custom js files added to `admin` pages and to the `client`.
Mandatory is set ``G3WSUITE_CUSTOM_STATIC_URL``.
I.e.::

    G3WSUITE_CUSTOM_JS = [
        G3WSUITE_CUSTOM_STATIC_URL +'js/custom.js'
    ]


Client layout settings
**********************

``G3W_CLIENT_SEARCH_TITLE``
^^^^^^^^^^^^^^^^^^^^^^^^^^^
Custom webgis client `search` section title.

``G3W_CLIENT_SEARCH_ENDPOINT``
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Search url endpoint for 'searches calling', default `ows`.
 - `ows`: by wms search;
 - `api`: by g3w-suite layer vector API.

``G3W_CLIENT_HEADER_CUSTOM_LINKS``
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
A list of dict of custom links to add into main top bar of webgis client.
I.e.::

   G3W_CLIENT_HEADER_CUSTOM_LINKS = [
        {
            'url': 'https://gis3w.it',
            'title': 'Gis3W company',
            'i18n': True, #(False as default value)
            'target': '_blank'
            'img': 'https://gis3w.it/wp-content/uploads/2016/10/logo_qgis-1-100x100.png?x22227'
        },
        {
           'title': 'Modal 1',
           'content': '<p>Html example content to show in modal</p>',
           'type': 'modal',
           'position': 10
       },
   ]

`i18n` (optional) set True if you want lent client try to translate title.

``G3W_CLIENT_LEGEND``
^^^^^^^^^^^^^^^^^^^^^
A dict to customize **QGIS-server** legend image generate with WMS `GetLegendGraphics` request.
I.e.::

    G3W_CLIENT_LEGEND = {
       'color': 'red',
       'fontsize': 8,
       'transparent': True,
       'boxspace': 4,
       'layerspace': 4,
       'layertitle': True,
       'layertitlespace': 4,
       'symbolspace': None,
       'iconlabelspace': 2,
       'symbolwidth': 8,
       'symbolheight': 4
    }



``G3W_CLIENT_RIGHT_PANEL``
^^^^^^^^^^^^^^^^^^^^^^^^^^
Custom properties settings for webgis right panel section (default, width 33%).
A the moment only `width` is managed.
I.e.::

    G3W_CLIENT_RIGHT_PANEL = {
        'width': 33
    }


``G3W_CLIENT_NOT_SHOW_EMPTY_VECTORLAYER``
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Default is ``False``. Set to ``True`` for remove from webgis TOC vector layer empty, without data.

Editing settings
****************
Settings params for ``editing`` module.

``EDITING_SHOW_ACTIVE_BUTTON``
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Default is ``True``. Set to ``False`` for not show editing button activate/deactivate into layers project list.

``EDITING_ANONYMOUS``
^^^^^^^^^^^^^^^^^^^^^
Default is ``False``. Set to ``True`` to render possible give to `anonymous user` editing permissions.

``EDITING_LOGGING``
^^^^^^^^^^^^^^^^^^^
Default is ``False``. Set to ``True`` to log users editing action into database.


Caching settings
****************
Settings params for ``caching`` module

``TILESTACHE_CACHE_NAME``
^^^^^^^^^^^^^^^^^^^^^^^^^
A name to identify caching

``TILESTACHE_CACHE_TYPE``
^^^^^^^^^^^^^^^^^^^^^^^^^
Default is ``Disk`` to save tile on a disk. Set to ``Memcache`` for to use *Memcached* caching framework (https://www.memcached.org/)

``TILESTACHE_CACHE_DISK_PATH``
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Path to disk space where to save tile created by tilestache if ``TILESTAHCE_CACHE_TYEPE`` is se to ``Disk``.

``TILESTACHE_CACHE_TOKEN``
^^^^^^^^^^^^^^^^^^^^^^^^^^
Mandatory, strign to use as token for internal WMS call for caching module.

Filemanger settings
*******************
Settings params for ``filemanager`` module.

``FILEMANAGER_ROOT_PATH``
^^^^^^^^^^^^^^^^^^^^^^^^^
Mandatory, path to disk space where to CRUD geo data files i.e. Shp Raster, etc.

``FILEMANAGER_MAX_UPLOAD_N_FILES``
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Default is 5, max number files to upload simultaneously.

Qplotly settings
****************

``LOAD_QPLOTLY_FROM_PROJECT``
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Default is ``False``, set to ``True`` to import DataPlotly settings from QGIS project.

Openrouteservice settings
*************************

``ORS_API_ENDPOINT``
^^^^^^^^^^^^^^^^^^^^
Default is ``http://localhost:8080/ors/v2/``, this is the endpoint for Openrouteservice API.

``ORS_API_KEY``
^^^^^^^^^^^^^^^
Openrouteservice API key, optional, can be blank if the key is not required by the endpoint.

``ORS_PROFILES``
^^^^^^^^^^^^^^^^
List of available Openrouteservice profiles, default: ``("driving-car", "driving-hgv")``

Vendors settings
****************
Settings variables about third part services, i.e. Google API etc..

``VENDOR_KEYS``
^^^^^^^^^^^^^^^
A list with services API keys.
I.e.::

    VENDOR_KEYS = {
     'google': 'fhgnrjwipòflsjhjjdhjdhashhabs',
     'bing': 'agbsgtrkADgstejaaklkklkds8irncdfk'
    }

At the moment only `Google` and `Bing` services are supported, for background base map and for google geoconding
service plus of `Nominatim` default service.
