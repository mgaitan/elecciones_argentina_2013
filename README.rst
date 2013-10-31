Elecciones Argentina 2013
==========================

Dump de datos en formato CSV del programa http://www.resultados.gob.ar/inimesas.htm


Por qué?
---------

Es lamentable que el estado no publique los datos en un formato abierto. En cambio,
estos datos están empaquetados en una aplicación windows utilizando una base de datos
Microsoft Access (.mdb).

Liberando los datos
---------------------

Los csv se extrayeron a través del software libre `mdbtools <http://mdbtools.sourceforge.net>`_ ::


    $ sudo apt-get install mdbtools


Luego, usando IPython


.. code:: python

    In [1]: !!mdb-tables ARGENTINA2013.mdb
    Out[1]: ['CandidatosGobernador CandidatosPresidente ColoresElecciones ColoresForzados Concejales Departamento DNacionales DProvinciales Elecciones Gobernador IndEle MesasConcejales MesasDMunicipales MesasDNacionales MesasGobernador MesasPresidente MesasSNacionales MesasSProvinciales MesasTCuentas Municipios Partidos Poligonos Presidente Provincias Puntos SNacionales SProvinciales TCuentas Unidad VotosCandidaturaDMunicipales VotosCandidaturaDNacionales VotosCandidaturaDProvinciales VotosCandidaturaMesasConcejales VotosCandidaturaMesasDMunicipales VotosCandidaturaMesasDNacionales VotosCandidaturaMesasDProvinciales VotosCandidaturaMesasGobernador VotosCandidaturaMesasSNacionales VotosCandidaturaMesasSProvinciales VotosCandidaturaMesasTCuentas VotosCandidaturaSNacionales VotosCandidaturaSProvinciales VotosCandidaturaTCuentas VotosFormulaGobernador VotosFormulaPresidente VotosPartidosFormulaPresidente VotosSubLemaConcejales VotosSubLemaDMunicipales VotosSubLemaDNacionales VotosSubLemaDProvinciales VotosSublemaMesaConcejales VotosSublemaMesaDMunicipales VotosSublemaMesaDNacionales VotosSublemaMesaDProvinciales VotosSubLemaMesaGobernador VotosSubLemaMesaPresidente VotosSublemaMesaSNacionales VotosSublemaMesaSProvinciales VotosSublemaMesaTCuentas VotosSubLemaSNacionales VotosSubLemaSProvinciales VotosSubLemaTCuentas DMunicipales MesasDProvinciales VotosCandidaturaConcejales VotosCandidaturaMesasPresidente VotosPartidosFormulaGobernador ']

    In [2]: tables = _[0].split()

    In [3]: for table in tables:
       ...:     !mdb-export ARGENTINA2013.mdb {table} > {table}.csv
       ...:

