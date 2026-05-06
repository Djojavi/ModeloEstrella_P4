# Practica 4
## Integrantes:
- Daniel Jaramillo
- Nayeli Leiva
- Bryan Maldonado
- Donoban Ramón
- Ricardo Villareal
## Ejercicio 21
## 1. Cargar el CSV como tabla

Se importó el archivo `products.csv` en Excel y se dejó como tabla con las columnas:

<img width="1285" height="718" alt="Screenshot 2026-05-05 190606" src="https://github.com/user-attachments/assets/41390275-ec01-4ae4-bce7-59433adb258d" />


## 2. Crear la dimensión `dim_category`

Se creó una nueva hoja llamada `dim_category`.

Se copió la columna `category` desde la tabla original.

Luego se aplicó:

**Quitar duplicados**

Después se agregó un identificador numérico:

<img width="571" height="460" alt="Screenshot 2026-05-05 190956" src="https://github.com/user-attachments/assets/62998de4-8c9d-45ec-9861-910e31bffec7" />


## 3. Crear la dimensión `dim_subcategory`

Se creó una nueva hoja llamada `dim_subcategory`.

Se copió la columna `sub_category` desde la tabla original.

Luego se aplicó:

**Quitar duplicados**

Después se agregó un identificador numérico:

<img width="514" height="684" alt="Screenshot 2026-05-05 191153" src="https://github.com/user-attachments/assets/01a3fbb7-e538-4416-927c-0a10a32a879d" />


## 4. Crear la tabla `fact_products`

Se creó una hoja llamada `fact_products`.

Inicialmente se copió la tabla original y luego se reemplazaron los textos de categoría y subcategoría por sus IDs.

La tabla final quedó así:

| product_id | product_name | category_id | subcategory_id |
|---|---|---|---|

Para traer el ID de categoría se usó:

```excel
=BUSCARX(C2;dim_category!$B:$B;dim_category!$A:$A)
```

Para traer el ID de subcategoría se usó:

```excel
=BUSCARX(D2;dim_subcategory!$B:$B;dim_subcategory!$A:$A)
```

Luego se eliminaron las columnas de texto:

<img width="1127" height="669" alt="Screenshot 2026-05-05 194025" src="https://github.com/user-attachments/assets/3a27bbe2-0adf-4d19-976b-3248cb72bbad" />


## 5. Agregar las tablas al modelo de datos

Se agregaron al modelo de datos las siguientes tablas:

| Tabla |
|---|
| fact_products |
| dim_category |
| dim_subcategory |

Ruta usada:

**Power Pivot → Agregar al modelo de datos**


## 5. Crear relaciones

Se crearon las siguientes relaciones:

| Tabla dimensión | Campo | Tabla de hechos | Campo |
|---|---|---|---|
| dim_category | category_id | fact_products | category_id |
| dim_subcategory | subcategory_id | fact_products | subcategory_id |

El modelo estrella declara que fact_products es la tabla central y se relaciona con dos dimensiones: dim_category y dim_subcategory.

La relación indica que una categoría puede tener muchos productos y una subcategoría también puede tener muchos productos

<img width="1159" height="632" alt="Screenshot 2026-05-05 194825" src="https://github.com/user-attachments/assets/6bbc0468-02a4-469f-86a5-fac098679323" />




## Ejercicio 22
Aqui explicar los scripts que usamos para sacar las tablas de dimensiones, hechos y como las poblamos
### 22.a
### 22.b Contestar las siguientes preguntas en SQL.
**1. ¿Cuántas ventas se realizaron por categoría de producto y mes?**
<img width="921" height="588" alt="image" src="https://github.com/user-attachments/assets/75323d99-c35f-47d3-8ac9-af3ec306310f" />
**2. ¿Cuál es el ingreso total (ventas) por cliente y género?**
<img width="921" height="584" alt="image" src="https://github.com/user-attachments/assets/ed628bab-6cce-4f47-8ca1-8fa265fce8da" />
**3. ¿Cuál es la cantidad total vendida por producto?**
<img width="921" height="453" alt="image" src="https://github.com/user-attachments/assets/fef94b9f-7557-4cfd-b890-76fa0180ae82" />
**4. ¿Cuál fue la cantidad enviada por mes de envío?**
<img width="921" height="771" alt="image" src="https://github.com/user-attachments/assets/1de1b786-cba2-472c-b095-107cce6d02b4" />
**5. ¿Cuánto se vendió por tamaño de producto y por estado civil del cliente?**
<img width="921" height="431" alt="image" src="https://github.com/user-attachments/assets/31bd8afa-5c08-4750-9bba-3da29965cc0c" />

