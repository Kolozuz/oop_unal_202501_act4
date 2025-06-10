## Ejercicio 8.2 (p.480)

### Enunciado

Se requiere desarrollar un programa con interfaz gráfica de usuario que
genere una ventana donde se solicite el ingreso de cinco notas obtenidas
por un estudiante.
El programa debe calcular y mostrar en la parte inferior de la ventana
los siguientes datos:
- El promedio de notas ingresadas.
- La desviación estándar de las notas ingresadas.
- La mayor nota obtenida.
- La menor nota obtenida.

##### Formula para el calculo de la desviación estándar 

$$ \sigma = \sqrt{\sum(x_i-\mu)^2 \over N} $$

- $\sigma$ = desviación estándar
- $N$ = tamaño de la lista
- $x_i$ = cada valor de la lista
- $\mu$ = media de los valores de la lista

### Diagrama de Casos de uso

![ejeruso1 drawio](https://github.com/user-attachments/assets/e729d711-f7eb-4fa4-8c5c-949ac111a9e9)

### Diagrama de Clases

```mermaid
classDiagram
    class Notas {
        listado_notas: list[float]
        «constructor»Notas()
        calcular_promedio() float
        calcular_desviacion_estandar() float
        mayor() float
        menor() float
    }
    class VentanaPrincipal {
        root: Tk
        notas: Notas
        «constructor»VentanaPrincipal()
        crear_widgets()
        calcular_notas()
    }
    VentanaPrincipal --> Notas
```

### Solución

[Click para ver código fuente](https://github.com/Kolozuz/oop_unal_202501_act4/blob/main/Ejercicio1/code.py)

#### Ejecución del programa

```python
# Se crea una instancia de la ventana principal y se inicia el bucle de eventos
my_calculator = VentanaPrincipal()
my_calculator.root.mainloop()
```

**Botón Calcular**

![image.png](Ejercicio1/media/image.png)

**Botón Limpiar**

![image-2.png](Ejercicio1/media/image-2.png)

## Ejercicio 8.3 (p.494)

### Enunciado

Se requiere desarrollar un programa con interfaz gráfica de usuario que
permita calcular el volumen y superficie de varias figuras geométricas. Las
figuras geométricas son el cilindro, la esfera y la pirámide.
- Para el cilindro se solicitan su radio y altura (en centímetros).
- Para la esfera, su radio (en centímetros).
- Para la pirámide, su base, altura y apotema (en centímetros).

Una vez ingresados estos datos, el programa calcula el volumen y
superficie de cada figura. Para desarrollar el programa se debe crear una
jerarquía de clases para las diferentes figuras geométricas requeridas.

### Diagrama de Casos de uso

![claseuso2 drawio](https://github.com/user-attachments/assets/33afd316-6b48-4d43-9f0a-4ce551198000)

### Diagrama de Clases

```mermaid
classDiagram
    class FiguraGeometrica {
        -volumen: float
        -superficie: float
        «constructor»FiguraGeometrica(volumen: float, superficie: float)
        +set_volumen(volumen: float)
        +set_superficie(superficie: float)
        +get_volumen() float
        +get_superficie() float
    }
    class Cilindro {
        -radio: float
        -altura: float
        «constructor»Cilindro(radio: float, altura: float)
        +calcular_volumen() float
        +calcular_superficie() float
    }
    class Esfera {
        -radio: float
        «constructor»Esfera(radio: float)
        +calcular_volumen() float
        +calcular_superficie() float
    }
    class Piramide {
        -base: float
        -altura: float
        -apotema: float
        «constructor»Piramide(base: float, altura: float, apotema: float)
        +calcular_volumen() float
        +calcular_superficie() float
    }
    class VentanaCilindro {
        «constructor»VentanaCilindro()
        +calcular()
    }
    class VentanaEsfera {
        «constructor»VentanaEsfera()
        +calcular()
    }
    class VentanaPiramide {
        «constructor»VentanaPiramide()
        +calcular()
    }
    class VentanaPrincipal {
        «constructor»VentanaPrincipal()
        +abrir_ventana_cilindro()
        +abrir_ventana_esfera()
        +abrir_ventana_piramide()
    }
    class Principal {
        +main()
    }

    Cilindro --|> FiguraGeometrica
    Esfera --|> FiguraGeometrica
    Piramide --|> FiguraGeometrica

    VentanaPrincipal --> VentanaCilindro : crea
    VentanaPrincipal --> VentanaEsfera : crea
    VentanaPrincipal --> VentanaPiramide : crea

    VentanaCilindro ..> Cilindro : usa
    VentanaEsfera ..> Esfera : usa
    VentanaPiramide ..> Piramide : usa

    Principal --> VentanaPrincipal : crea
```

### Solución

[Click para ver código fuente](https://github.com/Kolozuz/oop_unal_202501_act4/blob/main/Ejercicio2/code.py)

#### Ejecución del programa


```python
figuras_geometricas = Principal()
figuras_geometricas.main()
```

**Ventana principal**

![alt text](Ejercicio2/media/image-1.png)

**Cilindro**

![image-5.png](Ejercicio2/media/image-5.png)

**Esfera**

![image-3.png](Ejercicio2/media/image-3.png)

**Pirámide**

![image.png](Ejercicio2/media/image.png)
