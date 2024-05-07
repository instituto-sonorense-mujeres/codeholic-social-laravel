sistemaisdb
```

mysql> show tables;
+-----------------------------+
| Tables_in_sistemaism        |
+-----------------------------+
| archivo                     |
| autorizacion                |
| bloqueo_sucursales          |
| cat_actividad               |
| cat_adiccion                |
| cat_agente_lesion           |
| cat_area_lesion             |
| cat_categoria               |
| cat_consecuencia_sexual     |
| cat_departamento            |
| cat_discapacidad            |
| cat_doc_anexo               |
| cat_efecto_economico        |
| cat_efecto_fisico           |
| cat_efecto_psicologico      |
| cat_escolaridad             |
| cat_estado                  |
| cat_estado_civil            |
| cat_factores_riesgo         |
| cat_fondo                   |
| cat_localidad               |
| cat_menu                    |
| cat_modalidad               |
| cat_municipio               |
| cat_ocupacion               |
| cat_plaza                   |
| cat_puesto                  |
| cat_salud_fisica            |
| cat_servicio_medico         |
| cat_tema                    |
| cat_tipo                    |
| cat_tipo_efecto             |
| cat_tipo_hecho              |
| cat_tipo_movimiento         |
| ci_sessions                 |
| cliente                     |
| cliente_archivo             |
| clientes_sucursales         |
| comisionista                |
| comisionista_archivo        |
| comisionista_autorizacion   |
| comisionista_modificacion   |
| conceptos                   |
| estudios                    |
| estudios_familiares         |
| groups                      |
| groups_puesto               |
| incidencias                 |
| meta                        |
| preferencias                |
| programas                   |
| programas_archivo           |
| programas_detalles          |
| tipo_archivo                |
| tipo_movimiento             |
| users                       |
| v_actividad                 |
| v_bitacora                  |
| v_categoria                 |
| v_com                       |
| v_comisionista              |
| v_comisionista_autorizacion |
| v_comisionista_extra        |
| v_listado_atenciones        |
| v_listado_estudios          |
| v_localidad                 |
| v_modificaciones            |
| v_municipio                 |
| v_plaza                     |
| v_relaciones                |
| v_relaciones_localidad      |
| v_resumen_inicial           |
| v_subactividad              |
| v_tema                      |
| v_usuarios                  |
+-----------------------------+


mysql> desc users;
+-------------------------+--------------------+------+-----+---------+----------------+
| Field                   | Type               | Null | Key | Default | Extra          |
+-------------------------+--------------------+------+-----+---------+----------------+
| id                      | int unsigned       | NO   | PRI | NULL    | auto_increment |
| group_id                | mediumint unsigned | NO   |     | NULL    |                |
| ip_address              | char(16)           | NO   |     | NULL    |                |
| username                | varchar(30)        | NO   | UNI | NULL    |                |
| password                | varchar(40)        | NO   |     | NULL    |                |
| salt                    | varchar(40)        | YES  |     | NULL    |                |
| email                   | varchar(100)       | NO   | UNI | NULL    |                |
| activation_code         | varchar(40)        | YES  |     | NULL    |                |
| forgotten_password_code | varchar(40)        | YES  |     | NULL    |                |
| remember_code           | varchar(40)        | YES  |     | NULL    |                |
| created_on              | int unsigned       | NO   |     | NULL    |                |
| last_login              | int unsigned       | YES  |     | NULL    |                |
| active                  | tinyint unsigned   | YES  |     | NULL    |                |
| sucursal                | int                | NO   |     | 0       |                |
+-------------------------+--------------------+------+-----+---------+----------------+

mysql -h localhost -u root -e "SELECT id, username, password, email FROM sistemaism.users" -B | sed 's/\t/,/g' > usuarios.csv

//// *** ////

DESC archivo;
+-----------------+--------------+------+-----+-------------------+-------------------+
| Field           | Type         | Null | Key | Default           | Extra             |
+-----------------+--------------+------+-----+-------------------+-------------------+
| id_archivo      | int          | NO   | PRI | NULL              | auto_increment    |
| nombre          | varchar(255) | NO   |     | NULL              |                   |
| ruta            | text         | NO   |     | NULL              |                   |
| id_tipo_archivo | int          | NO   | MUL | NULL              |                   |
| create          | timestamp    | YES  |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED |
| update          | timestamp    | YES  |     | NULL              |                   |
| id_usuario      | int unsigned | YES  | MUL | NULL              |                   |
+-----------------+--------------+------+-----+-------------------+-------------------+


mysql -h localhost -u root -e "SELECT id_archivo, nombre, ruta, id_tipo_archivo, id_usuario FROM sistemaism.archivo" -B | sed 's/\t/,/g' > archivo.csv

//// *** ////

desc autorizacion;
+--------------------+------------+------+-----+-------------------+-----------------------------------------------+
| Field              | Type       | Null | Key | Default           | Extra                                         |
+--------------------+------------+------+-----+-------------------+-----------------------------------------------+
| id_autorizacion    | int        | NO   | PRI | NULL              | auto_increment                                |
| id_tipo_movimiento | int        | NO   | MUL | NULL              |                                               |
| autorizado         | tinyint(1) | NO   |     | 0                 |                                               |
| observaciones      | text       | YES  |     | NULL              |                                               |
| create             | timestamp  | YES  |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED on update CURRENT_TIMESTAMP |
| id_usuario         | int        | NO   |     | NULL              |                                               |
+--------------------+------------+------+-----+-------------------+-----------------------------------------------+

mysql -h localhost -u root -e "SELECT id_autorizacion, id_tipo_movimiento, autorizado, observaciones, create, id_usuario FROM sistemaism.autorizacion" -B | sed 's/\t/,/g' > autorizacion.csv

//// *** ////

desc cat_actividad;
+------------------+--------------+------+-----+---------+----------------+
| Field            | Type         | Null | Key | Default | Extra          |
+------------------+--------------+------+-----+---------+----------------+
| id_actividad     | int          | NO   | PRI | NULL    | auto_increment |
| clave            | varchar(50)  | NO   |     | NULL    |                |
| actividad        | varchar(255) | NO   | MUL | NULL    |                |
| tipo             | varchar(50)  | NO   |     | NULL    |                |
| padre            | int          | YES  | MUL | NULL    |                |
| actividad_activo | tinyint      | NO   |     | 1       |                |
+------------------+--------------+------+-----+---------+----------------+

mysql -h localhost -u root -e "SELECT id_actividad, clave, actividad, tipo, padre, actividad_activo FROM sistemaism.cat_actividad" -B | sed 's/\t/,/g' > cat_actividad.csv

//// *** ////

 desc cat_adiccion;
+-----------------+--------------+------+-----+---------+----------------+
| Field           | Type         | Null | Key | Default | Extra          |
+-----------------+--------------+------+-----+---------+----------------+
| id_adiccion     | int          | NO   | PRI | NULL    | auto_increment |
| adiccion        | varchar(255) | NO   | UNI | NULL    |                |
| adiccion_activo | tinyint      | NO   |     | 1       |                |
+-----------------+--------------+------+-----+---------+----------------+

mysql -h localhost -u root -e "SELECT id_adiccion, adiccion, adiccion_activo FROM sistemaism.cat_adiccion" -B | sed 's/\t/,/g' > cat_adiccion.csv

//// *** ////

desc cat_agente_lesion;
+----------------------+--------------+------+-----+---------+----------------+
| Field                | Type         | Null | Key | Default | Extra          |
+----------------------+--------------+------+-----+---------+----------------+
| id_agente_lesion     | int          | NO   | PRI | NULL    | auto_increment |
| agente_lesion        | varchar(255) | NO   | UNI | NULL    |                |
| agente_lesion_activo | tinyint      | NO   |     | 1       |                |
+----------------------+--------------+------+-----+---------+----------------+

mysql -h localhost -u root -e "SELECT id_agente_lesion, agente_lesion, agente_lesion_activo FROM sistemaism.cat_agente_lesion" -B | sed 's/\t/,/g' > cat_agente_lesion.csv

//// *** ////

desc cat_area_lesion;
+--------------------+--------------+------+-----+---------+----------------+
| Field              | Type         | Null | Key | Default | Extra          |
+--------------------+--------------+------+-----+---------+----------------+
| id_area_lesion     | int          | NO   | PRI | NULL    | auto_increment |
| area_lesion        | varchar(255) | NO   | UNI | NULL    |                |
| area_lesion_activo | tinyint      | NO   |     | 1       |                |
+--------------------+--------------+------+-----+---------+----------------+

//// *** ////

desc cat_categoria;
+------------------+--------------+------+-----+---------+----------------+
| Field            | Type         | Null | Key | Default | Extra          |
+------------------+--------------+------+-----+---------+----------------+
| id_categoria     | int          | NO   | PRI | NULL    | auto_increment |
| clave            | varchar(50)  | NO   |     | NULL    |                |
| categoria        | varchar(150) | NO   |     | NULL    |                |
| categoria_activo | tinyint      | NO   |     | NULL    |                |
+------------------+--------------+------+-----+---------+----------------+

//// *** ////

desc cat_consecuencia_sexual;
+----------------------------+--------------+------+-----+---------+----------------+
| Field                      | Type         | Null | Key | Default | Extra          |
+----------------------------+--------------+------+-----+---------+----------------+
| id_consecuencia_sexual     | int          | NO   | PRI | NULL    | auto_increment |
| consecuencia_sexual        | varchar(255) | NO   | UNI | NULL    |                |
| consecuencia_sexual_activo | tinyint      | NO   |     | 1       |                |
+----------------------------+--------------+------+-----+---------+----------------+

//// *** ////

desc cat_departamento;
+---------------------+--------------+------+-----+---------+----------------+
| Field               | Type         | Null | Key | Default | Extra          |
+---------------------+--------------+------+-----+---------+----------------+
| id_departamento     | int          | NO   | PRI | NULL    | auto_increment |
| departamento        | varchar(255) | NO   | UNI | NULL    |                |
| departamento_activo | tinyint      | NO   |     | 1       |                |
+---------------------+--------------+------+-----+---------+----------------+

//// *** ////

desc cat_discapacidad;
+---------------------+--------------+------+-----+---------+----------------+
| Field               | Type         | Null | Key | Default | Extra          |
+---------------------+--------------+------+-----+---------+----------------+
| id_discapacidad     | int          | NO   | PRI | NULL    | auto_increment |
| discapacidad        | varchar(255) | NO   | UNI | NULL    |                |
| discapacidad_activo | tinyint      | NO   |     | 1       |                |
+---------------------+--------------+------+-----+---------+----------------+

```