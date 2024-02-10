<h1>Análisis del COVID19 😷🦠</h1>

> [!NOTE]
> Este es un proyecto que pretende analizar datos oficiales y realizar ingishts para aprender sobre lo que dejó la pandemia. <br>

> [!CAUTION]
> Utilizar con fines educativos :octocat:

<h2>Problema del negocio</h2>

<table><tr><td> 
Una entidad gubernamental responsable de la gestión de la salud en Argentina y en Colombia enfrenta el desafío de comprender y analizar la propagación del COVID-19 para tomar decisiones informadas y eficaces en la gestión de la pandemia.
Como científicos de datos, nuestra tarea es analizar los datos relacionados con el COVID-19 y presentar insights a través de visualizaciones que respondan a las siguientes cuestiones: <br>
<br>
1. La propagación del Covid-19 en Argentina y en Colombia en comparación con el resto del mundo <br>
2. Cómo fué el avance de los reporte de nuevos casos diarios lo largo de estos últimos 4 años en Argentina y Colombia. <br>
3. La evolución del índice de letatidad del Covid-19 en Colombia y en Argentina comparado con los paises con mayores índices de letalidad históricos. <br>
4. Las características mas relevantes a nivel global en el impacto del índice de letalidad desde una perspectiva demográfica.
</td></tr></table>

<h2>Stack de tecnologías</h2>

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white) ![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white) ![Matplotlib](https://img.shields.io/badge/Matplotlib-%23ffffff.svg?style=for-the-badge&logo=Matplotlib&logoColor=black)

![scikit-learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)

<h2>¿De dónde obtuvimos los datos?</h2>


<picture> <img align="right" src="https://img001.prntscr.com/file/img001/bE059CK0TQOKhKqpeYo4CQ.png" width = 250px></picture>
Para que nuestras decisiones sean lo más acertadas posibles, tenemos que apoyarnos en información oficial y confiable. Nos basamos en dos organizaciones mundialmente reconocidas:

 > **World Health Organization (WHO)**: Nos proveerá información sobre la propagación del covid a nivel mundial.
 > <a href="https://www.who.int/" target="blank"> Link a la web oficial </a>. <br>
 > **United Nations (population)**: Nos proveeran información demográfica a nivel pais y a nivel mundial.
 > <a href="https://www.un.org/en/" target="blank"> Link a la web oficial </a>.

<h2>Configuración del ambiente</h2>

<h2>EDA: Análisis exploratorio de los datos</h2>

<h3>Los dataframes con los que vamos a trabajar</h3>

Definiremos los Dataframes y la información que contiene:

**df_covid:** contendrá información de la propagación del covid a nivel mundial respaldada por la WHO. <br><br>

![Captura de pantalla de 2024-02-05 07-06-55](https://github.com/pabloing93/covid19-analysis/assets/32267303/be193dca-933c-4786-baef-e7d2fb64cd6a)
<br>
![Captura de pantalla de 2024-02-05 07-07-05](https://github.com/pabloing93/covid19-analysis/assets/32267303/4146be8b-6c96-4ced-a087-f810a61e68b8)
<br><br>

**df_population:** contendrá información demográfica de todos los paises a nivel mundial, respadalda por UN.

Hacemos un filtro por las columnas de interés:

<table><tr><td> 
> df_population_limpio = df_population[<br>
 ['ISO2 Alpha-code', <br>
  'Total Population, as of 1 July (thousands)',<br>
  'Male Population, as of 1 July (thousands)',<br>
  'Female Population, as of 1 July (thousands)',<br>
  'Population Density, as of 1 July (persons per square km)',<br>
  'Life Expectancy at Birth, both sexes (years)']<br>
 ].copy() 
</td></tr></table>

![Captura de pantalla de 2024-02-05 07-10-33](https://github.com/pabloing93/covid19-analysis/assets/32267303/b4ebb79b-3a7a-4def-b6ec-e6b360d91c9d)

<h3>Análisis exploratorio y limpieza</h3>

<h4>Información del covid</h4>

> [!CAUTION]
> Encontramos unos valores extraños en la columna que nos brinda información del rate de letalidad

![Captura de pantalla de 2024-02-10 08-52-06](https://github.com/pabloing93/covid19-analysis/assets/32267303/8d4c331b-777d-43cf-bf8a-77792ef2b341)

<p>Vamos a hacer un gráfico de boxplot a ver si nos ayuda a comprender éste fenómeno</p>

![image](https://github.com/pabloing93/covid19-analysis/assets/32267303/acd4496c-59d7-4486-b82c-eb26960df379)
<br>
- [x] <b>Observación:</b> Detectamos valores muy grandes y excepcionales cuando analizamos el rate de letalidad del covid. Por lo que procederemos a hacer una limpieza y nos quedaremos con los valores de los quantiles del 0 al 99.<br>

![image](https://github.com/pabloing93/covid19-analysis/assets/32267303/2b78f6d1-ebc5-4fd4-93f3-fe01faa5d568)
- [x] <b>Resultado:</b> de la limpieza previamente aplicada al rate de letalidad lo que nos permitirá trabajar con ésta variable y obtener conclusiones más precisas.

También aplicamos otras técnicas de EDA. Por lo extenso del código los invitamos a revisarlo en detalle en el archivo COVID19_Analysis.ipynb <br>
Sin embargo listaremos en análisis y las técnicas de tratamiento aplicadas en nuestro código:
> 1. Tratamiento de NaNs y nulos.
>  2. Tratamiento de errores tipográficos
>  3. Conversión de estructuras de datos de las columnas
>  4. Eliminación de outliers
>  5. Otros 

<h2>Insights y conclusiones</h2>
<h3>Insight 1: ¿Cómo ha evolucionado el Covid-19 en Argentina y Colombia en comparación con el impacto observado a nivel global? </h3><br>

<h4>En términos relativos</h4>

![image](https://github.com/pabloing93/covid19-analysis/assets/32267303/9d02f9df-8a65-49cb-b0ae-3a6831e6fd40)
<br>
- [x] <b>Conclusión:</b> Apreciamos que la evolución del covid-19 en Argentina y Colombia fué bastante controlada en comparación a los 10 paises con mayor índice de evolución. Sin embargo, comparando Argentina y Colombia entre sí podemos apreciar que Colombia pudo mitigar mucho más la evolución de los contagios en época de pandemia en comparación a Argentina.<br>

<h4>Y en términos absolutos</h4>

![image](https://github.com/pabloing93/covid19-analysis/assets/32267303/4d28ebed-5cfd-4c25-9676-e6584a51ad5d)
<br>
- [x] <b>Conclusión:</b> En cuanto a la evolución de contagios desde el día 0 hasta 4 años después observamos que Argentina y Colombia fueron los paises con menores casos confirmados comparándolos con los TOP 5 paises a nivel mundial <br><br>

<h3>Validemos ésta información con fuentes oficiales</h3>

<p>Como científicos y profesionales de los datos también tenemos la responsabilidad de validar si nuestras conclusiones hasta el momento coinciden con fuentes oficiales</p>

<h4>Argentina</h4>

![Captura de pantalla de 2024-02-07 07-19-14](https://github.com/pabloing93/covid19-analysis/assets/32267303/1d32298c-fcfe-4e29-9d39-0127fb84a361)

Link de la fuente oficial: https://www.who.int/countries/arg/

<h4>Colombia</h4>

![Captura de pantalla de 2024-02-07 07-19-29](https://github.com/pabloing93/covid19-analysis/assets/32267303/248af2e2-8522-45f7-85ba-8f60c4c68d7c)

Link de la fuente oficial: https://www.who.int/countries/col/

- [x] <b>Conclusión:</b> ¡Hasta aquí vamos bien! En términos absolutos vemos efectivamente que para Argentina y Colombia nuestros datos coinciden con fuentes oficiales por lo que en términos relativos (en porcentajes) y en comparación a otros paises asumimos que el resultado también es verídico ya que utilizamos la misma fuente de información y el mismo método de análisis.

- [x] <b>Recomendación:</b> Argentina podría considerar analizar el procotolo de Colombia e implementar algunas medidas sugeridas por parte de su organizmo de salud.
<br><br>

<h3>Insight 2: ¿Cuál ha sido la evolución de los nuevos casos diarios reportados de Covid-19 en Argentina y Colombia a lo largo del tiempo?</h3><br><br>

![image](https://github.com/pabloing93/covid19-analysis/assets/32267303/6b87a9c2-1885-4455-af0a-2b5e00bfbe1a)<br>
- [x] <b>Conclusión:</b> En la gráfica de Colombia se puede observar un aumento notable de nuevos casos en agosto del 2020, reportando un pico de 80 mil, empezando el 2021 superó los 100 mil casos, posteriormente en el mes de marzo hubo una disminución notable de casos, por debajo de los 50 mil, para julio se reporta un pico de más de 200 mil contagios, entre el mes de septiembre de 2021 y enero de 2022 podemos observar otra disminución muy notable por debajo de los 20 mil casos. El pico más alto de contagios diarios se tiene en febrero del 2022 donde superó los 210 mil casos, posterior a esas fechas no hubo un aumento notable de casos, estuvieron por debajo de los 30 mil. <br><br>

![image](https://github.com/pabloing93/covid19-analysis/assets/32267303/96cb908f-3d7c-400f-b1c2-3f0251e0a48d)<br>

- [x] <b>Conclusión:</b> En la gráfica de Argentina se puede observar un pico de 100 mil contagios en octubre de 2020, para junio de 2021 produce un pico de 240 mil. El mayor registro de contagios diarios es entre enero y febrero de 2022 reportando un pico de 775 mil<br><br>

<h3>Insight 3: ¿Cuál es la evolución del índice de letalidad del Covid-19 en Colombia y Argentina comparado con los paises con los índices históricos más elevados?</h3><br><br>

![image](https://github.com/pabloing93/covid19-analysis/assets/32267303/dffe2e30-d02d-4865-b4b7-1326f2391b8d) <br>
![image](https://github.com/pabloing93/covid19-analysis/assets/32267303/de71eee2-1833-4bb7-a59e-e0c374e1f640)

- [x] <b>Conclusión:</b> En mayo de 2020 se reportó un pico en el lethality rate de 4.61 % para Colombia, y 7.79 % en Argentina, teniendo una diferencia entre ambos paises de 3.28 % <br><br>


<h3>Insight 4: Desde una perspectiva demográdica ¿cuáles son las características que tienen un mayor impacto en el índice de letalidad de un país?</h3><br><br>

![image](https://github.com/pabloing93/covid19-analysis/assets/32267303/4a9bf54b-d8f7-40fe-b76f-2faec888142e)
<br>
- [x] <b>Conclusión:</b> Según nuestro análisis de importancia, la densidad de la población destaca como más influyente, seguida de la población femenina con un 25% y 24% respectivamente. Esto sugiere que densidad de la población y el número de la población femenina son características relevantes en la incidencia de la letalidad de un país cuando evaluamos el covid-19.<br>
- [x] <b>Recomendaciones:</b> Con ésta información podemos predecir el índice de letalidad y tomar medidas preventivas en aquellos paises cuya densidad de población y cantidad de población femenina sea más elevado.


Comparamos a Colombia, Argentina respecto a EEUU para validar nuestra hipótesis...
