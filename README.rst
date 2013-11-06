Elecciones Argentina 2013
==========================

Dump de datos en formato CSV del programa http://www.resultados.gob.ar/inimesas.htm


¿Por qué?
---------

Estos datos están empaquetados en una aplicación windows utilizando una base de datos
Microsoft Access (.mdb). Son alternativos (digamos, más crudos) a los publicados en 
http://datospublicos.gob.ar/data/dataset/elecciones-2013



Liberando los datos
---------------------

Los csv se extrajeron a través del software libre `mdbtools <http://mdbtools.sourceforge.net>`_ ::


    $ sudo apt-get install mdbtools

Instalar el programa con Wine y luego, utilizando IPython


.. code:: python

    In [1]: cd ~/.wine/drive_c/ELECCIONES_NACIONALES_ARGENTINA_2013/DatosBD

    In [2]: !!mdb-tables ARGENTINA2013.mdb
    Out[2]: ['CandidatosGobernador CandidatosPresidente ColoresElecciones ColoresForzados Concejales Departamento DNacionales DProvinciales Elecciones Gobernador IndEle MesasConcejales MesasDMunicipales MesasDNacionales MesasGobernador MesasPresidente MesasSNacionales MesasSProvinciales MesasTCuentas Municipios Partidos Poligonos Presidente Provincias Puntos SNacionales SProvinciales TCuentas Unidad VotosCandidaturaDMunicipales VotosCandidaturaDNacionales VotosCandidaturaDProvinciales VotosCandidaturaMesasConcejales VotosCandidaturaMesasDMunicipales VotosCandidaturaMesasDNacionales VotosCandidaturaMesasDProvinciales VotosCandidaturaMesasGobernador VotosCandidaturaMesasSNacionales VotosCandidaturaMesasSProvinciales VotosCandidaturaMesasTCuentas VotosCandidaturaSNacionales VotosCandidaturaSProvinciales VotosCandidaturaTCuentas VotosFormulaGobernador VotosFormulaPresidente VotosPartidosFormulaPresidente VotosSubLemaConcejales VotosSubLemaDMunicipales VotosSubLemaDNacionales VotosSubLemaDProvinciales VotosSublemaMesaConcejales VotosSublemaMesaDMunicipales VotosSublemaMesaDNacionales VotosSublemaMesaDProvinciales VotosSubLemaMesaGobernador VotosSubLemaMesaPresidente VotosSublemaMesaSNacionales VotosSublemaMesaSProvinciales VotosSublemaMesaTCuentas VotosSubLemaSNacionales VotosSubLemaSProvinciales VotosSubLemaTCuentas DMunicipales MesasDProvinciales VotosCandidaturaConcejales VotosCandidaturaMesasPresidente VotosPartidosFormulaGobernador ']

    In [3]: tables = _[0].split()

    In [4]: for table in tables:
       ...:     !mdb-export ARGENTINA2013.mdb {table} > {table}.csv
       ...:

