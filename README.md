# Generación de texto con RNN


El proyecto que escogi fue la generación de texto. Cuando escuché que compañeros habían generado letras de canciones para su proyecto o elementos de la biblia me gustó la idea. Pero no se me ocurría qué textos podían ser tan interesantes como esos, quizás no escogí uno tan bueno pero al fin de cuentas tenía hambre y pensé en recetas de cocina.
No encontré un data set con recetas de cocina en español por lo que creé uno propio recopilando recetas de comida Mexicana en internet.

La página original a la que se le atribuye este proyecto es la siguiente: https://github.com/spiglerg/RNN_Text_Generation_Tensorflow/blob/master/rnn_tf.py
La red consiste en una RNN con capas LSTM y una capa de salida completamente conectada, con funciones de activación softmax y función de costo cross entropy.


## Requerimientos
- Python3
- numpy
- [TensorFlow](https://www.tensorflow.org/)


## Generando los datos de entrenamiento

La estructura de los datos es la siguiente.
```
Ingredientes

    3 cucharadas de jugo de limón
    1/2 cucharadita de consomé de pollo
    6 cucharadas de aceite de oliva
    1 pepinillo en rebanadas delgadas
    1/2 taza de jitomates cherry partidos en cuartos
    4 tazas de verdolagas
    4 tazas de verdolagas t
    1/4 de cebolla morada en tiras delgadas
    3/4 taza de queso doblecrema desmoronado
    1 1/3 tazas de garbanzos cocidos

Instrucciones

    Mezcla el jugo de limón con el consomé de pollo; agrega el aceite de oliva y salpimienta.
    En un tazón grande mezcla el resto de los ingredientes; añade el aderezo, salpimienta y llévalo a la mesa.

```
Junté aproximadamente más de 70 recetas.

## Entrenando los datos

```
python rnn_tf.py --input_file=data/recetasMexicanas.txt --ckpt_file="saved/model.ckpt" --mode=train
```

Input:

- `input_file` Archivo de texto para entrenar.
- `test_prefix` El prefijo para comenzar a generar texto
- `ckpt_fil` checkpoint 
- `mode` Modo de ejecución: talk or train (generar texto o entrenar).



## Ejecutando el resultado

```
ppython rnn_tf.py --input_file=data/recetasMexicanas.txt --ckpt_file="saved/model.ckpt" --test_prefix="salsa de  " --mode=talk
```


## Resultado
Con 100 batches:

Iniciando con la palabra "pelar"
  ```
    pelar cocinar por 20 minutos más dejhados.
    agrega sal de licuamos, consincuresínsecús lás semilla picados con un poco de sal y pimienta.
    sirve la lechuga de agua
    550 g de puldito de to: 3 tazas vesdea se vecave)
    2 zanahorias ralladas du por el vinao de á trebollas firamlsmente
    2 chiles serranos s mpoutes destro s
    3 vinogre corresa a tecos
    1 pequeña de jitomates cuedas de carne se in retínas
    1 ramitu de pisilno molodos
    sal y pimienta al certro de la piel de tomate: 

  ```

-Iniciando con la palabra "Instrucciones"
```
  instrucciones s
        lovar los jitomates, los chiles y los ingredientes, pechegarlo suficiente para granse. 


    ingredientes

        2 cucharadas de jugo de limón.
        remorve las tallates.
        trozos de maíe parandaro
        1/2 taza de harina de tergo
        1/4 de taza de azúcar 

        sal y pimienta al gusto

    instrucciones

        precuenerorfinte los checorrlas harna enteriorve hace de papel un pocio. deshebra cade manecio.
        agrega de chocolate picay de manzana. recuradila es paresiona con sufuccir. compie de cocer
```
Iniciando con la palabra "3 cucharadas"
```
  3 cucharadas de aceite de oliva
      1 pica de consimó

  instrucciones 
      cebolla
      2 dientes de ajo
      1 cebolla cortade en ruesto
      8 bojas de maíz
      2 cucharadas de mantequilla
      sal y pimienta

  preporación

      fremer por una bota las semillas de sétaro y un papo encerdonte que vierve. sa se vuelvan sobre una toza.
      1 pepine pequante 
  0    sal de topate de la mezcla de cebolla, licór,alos cun tomatemo. 

  ingredientes


      1 kilo de jitomate
      cebolla
      1 cebolla
      una vez de semovervo
      1 litro de jitomazo picado: 1  calitas de olla
      1 cebolla cortadia desmanitados refrigas de malea, los tomates, el pimiento en la cardi tos que se quila lícepa, queda la verdura, y pesar al muchoradas de comienta al gusto, sucerge sal.
      calienta unos monte: 3 la hierbay una pica de pollo deshebrada
      una rama de lapoy tepararso.
      lemojes verde: 3 piezas de harina en pimiento mojra de vidoble. vagete la mesal, se vuélvela.
      disponer la rallada: la piel. distente de la tazo del
```
Con 5000 batches.

Iniciando con la palabra "3 cucharadas"
```
3 cucharadas del guiso y el pimiento verde; saltea hasta que el pimiento cambie de color. 
    agrega el chorizo desmenuzado y deja que se cueza. finalmente agrega el jitomate picado. 
    incorpora la pasta, mezcla y sazona con sal y pimienta al gusto.


ingredientes

    2 cucharadas de vinagre 
    1 cucharadita de azúcar 
    2 zanahorias ralladas 
    6 salchichas de pavo 
    6 panes para hot dogs 
    1 pepino rebanado 
    chiles jalapeños 
    2 cucharadas de cilantro finamente picado 
    cacahuates en trocitos 
    salsa picante 

preparación 

    mezcla el vinagre y el azúcar en un tazón. 
    sumerge las zanahorias ralladas durante 10 minutos para que absirlo. el pal y cortar en trozos el queso.
    una vez cocida la carne, agrega sal y pimienta al gusto. mezcla todo el guiso y prueba. corrige la sazón, si hace falta.
    calienta muy ligeramente cada tortilla sobre una plancha a baja intensidad (se recomienda engrasar ligeramente la plancha para que no se peguen o se ennegrezcan). 
```

Iniciando con la palabra "calienta"

```
calienta una parcir a la mitad los limones restantes y esparcir algunas gotas sobre cada tostada para condimer a de comino
    1 cucharadita de pimienta blanca o negra
    10 rábanos rebanados
    12 limones partidos a la mitad
    1 lechuga finamente picada, lavada y desarande un pol horica y desmenuzada             
    sal de ajo
    comino
    pimienta negra
    sal
    ½ taza de salsa de tomate
    1 jitomate
    3 chiles verdes picados
    ½ de cebolla picada
    1 cucharada de polvo para hornear
    1/2 litro de aceite 1 cucharadita para la masa y el resto para freír
    1 cucharada de canela
    1 taza de fresa sin rabito, para la salsa
    1/2 taza de frambuesa ,para la salsa
    1/2 taza de mora azul ,para la salsa
    1/2 taza de zarzamora ,para la salsa
    1/4 de taza de azúcar ,para la salsa
    1/3 de taza de agua para la salsa


preparación
    en una ollita a fuego medio, hierve el agua con la vainilla, la sal, una cucharada de azúcar y una cucharadita de aceite.
    agrega de
```

  Iniciando con la palabra "salsa"
```
  salsa de  viénal y mecetar en horra 1 2 cuchoradas de aceite.
    agrega de golpe la harina y cocina a fuego bajo por 5 minutos sin dejar de manue, para servir. 



ingredientes

    2 kilos de costilla cortado en trozos
    1 kilo de diezmillo cortado en trozos
    2 huesos de tuétano
    4 litros de agua
    6 dientes de ajo
    1 cebolla cortada en cuartos
    3 cucharaditas de sal
    3 ramas de hierbabuena
    2 elotes cortados en trozos
    200 gramos de ejotes limpios
    1 papa cortada en trozos
    ¼ jícama pelada cortada en trozos
    1 col finamente picada
    1 chiyeguto de oliva
    1 pepino picado en cubos
    queso fresco al gusto
    aceite de oliva

inshrucciones

    corta los jitomates, la cebolla y el chile finamente; reserva. 
    bate los huevos con la leche y sazona. coloca en un sartén un chorrito de aceite, deja que se caliente e integra la mezcla de huevo, al igual que el los jitomates, la cebolla y el chile. mueve con una palita de madera de forma envolvente hasta que 
```
## Conclusión

Hice varios intentos modificando el numero de neuronas por capa, el número de pasos, la taza de aprendizaje. El número de capas la conserve como 2. Tuve resultados muy malos, como mezclas aleatorias de letras, palabras sin sentido. Hasta que me concentré en modificar el número de batches, por el tiempo que consumia la ejecucion. Y obtuve resultados como los de arriba. Los primeros de 100 batches, me parecieron bastante buenos, algunos cientos mas donde los resultados no cambiaron mucho hasta que llegué a los de 5000 batches y era un sobreaprendizaje.
Pero en general salvo por formar bien o casi bien las palabras, las estructuras de las recetas se mantuvieron y aunque hubo recetas nuevas eran muy parecidas a algunas en particular. Lo que me llevo a pensar que mis datos eran muy escasos y no tan parecidos entre si como lo seria la musica de reguetón.








