Este proyecto demuestra el flujo completo de un **pipeline ETL en Databricks** utilizando PySpark y SQL nativo.

- **Capa Bronze:** almacena los datos crudos del CSV original.
- **Capa Silver:** aplica limpieza, validación y estandarización.
- **Capa Gold:** genera indicadores analíticos listos para consumo (KPIs, BI).

La tabla final `pacientesgold` contiene los valores agregados por obra social:
edad promedio y cantidad total de pacientes.

Este proyecto implementa un flujo ETL (Extract, Transform, Load) en Databricks Community, simulando una arquitectura de datos basada en capas:

Bronze → datos crudos cargados desde un archivo CSV.

Silver → limpieza, validación y estandarización.

Gold → métricas agregadas y analíticas.

EL FLUJO DE TRABAJO QUE VAMOS A REALIZAR EN DATABRICKS


                     ┌─────────────────────────┐
                     │      FUENTE CRUDA       │
                     │   CSV / Excel / JSON    │
                     └───────────┬─────────────┘
                                 │ Ingesta
                                 ▼
                     ┌─────────────────────────┐
                     │        BRONZE           │
                     │  Tabla cruda en         │
                     │  workspace.default       │
                     │  pacientesbronce        │
                     └───────────┬─────────────┘
                                 │ Transformación
                    Limpieza     │ Validación
                                 ▼
                     ┌─────────────────────────┐
                     │         SILVER          │
                     │  Datos limpios y        │
                     │  estandarizados         │
                     │ pacientesSilver         │
                     └───────────┬─────────────┘
                                 │ Agregaciones
                                 ▼
                     ┌─────────────────────────┐
                     │          GOLD           │
                     │  Métricas, KPIs, BI     │
                     │ pacientesGold           │
                     └───────────┬─────────────┘
                                 │ Consulta SQL
                                 ▼
                     ┌─────────────────────────┐
                     │    Databricks SQL       │
                     │   Dashboards / BI       │
                     └─────────────────────────┘



Dentro de workspace creamos una nueva notebook donde vamos a ponerle el nombre ETL_3_Capas_Databricks.ipynb

luego vamos a cargar el csv en upload en add data donde le ponemos la ubicacion del archivo

esto carga los datos del csv y los pone en un tabla 

donde  nosotros tenemos que asignar los valores de 

catalog --> workspace

schema --> default

tabla name --> pacientesbronce

luego de creada la tabla

vamos a catalog 

defaulf --> tablas 

la tabla creada deberia estar ahy

esto seria la estrcutura de capas

Databricks Workspace
└── Catalog: workspace
    └── Schema: default
        ├── pacientesbronce   → Capa BRONZE (datos crudos)
        ├── pacientessilver   → Capa SILVER (datos limpios)
        └── pacientesgold     → Capa GOLD (métricas agregadas)

este proyecto esta finalizado con las tres capas

solo hacemos la consulta a la capa gold con los datos refinados
