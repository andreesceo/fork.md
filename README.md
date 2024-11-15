# Difusión Migratoria
**Dessier expuesto a curado continuo**  
by @andresceo

## Introducción

El presente documento aborda las directrices de la **Difusión Migratoria**, un proceso normativo orientado a la estructuración y optimización de grandes volúmenes de código en sistemas complejos. Su principal objetivo es facilitar la legibilidad, la mantenibilidad y la bifurcación coherente de los elementos de código, asegurando que las referencias y componentes sean manipulables de manera eficiente, individual o grupal, dependiendo de las necesidades del proyecto. Esta metodología se sustenta en una nomenclatura específica para lograr una manipulación precisa de los distintos elementos del sistema, garantizando una correcta interacción entre ellos. 

El enfoque se basa en un conjunto de reglas que permiten trabajar de forma modular y escalable, haciendo posible tanto la manipulación de componentes en su totalidad como la modificación de sus partes constituyentes de manera independiente, siempre con coherencia y con un propósito claro de mantener la integridad del sistema.

## Version

**Sintaxis**: `/v`

Define la versión en la que se desea manipular un **módulo**. Este término se utiliza para identificar y distinguir las diferentes iteraciones de un módulo dentro del sistema, lo que permite trabajar con versiones específicas del mismo sin interferir con otras versiones existentes.

## General

**Sintaxis**: `/G`

Declara que el **módulo** será manipulable junto a todas sus dependencias. Este tipo de manipulación es útil cuando se desea realizar cambios a nivel global, afectando al **módulo** y a todos los elementos que dependen de él, manteniendo su integridad y funcionamiento.

## Individual

**Sintaxis**: `/I`

Declara que el **módulo** será manipulable por cada parte que lo conforma de manera individual. Esta sintaxis permite modificar o actualizar elementos específicos dentro del **módulo** sin afectar al conjunto completo, lo que facilita una mayor flexibilidad y control sobre los componentes individuales.

## System

**Sintaxis**: `/sys`

Compila el **módulo** hacia una estilización. Se utiliza cuando se desea aplicar una estructura o estilo específico al **módulo** dentro del sistema, generando un comportamiento estandarizado que afecte la presentación o el diseño de todos los elementos involucrados.

## Animation

**Sintaxis**: `/A`

Renderiza el **módulo** como animación. Esta sintaxis está destinada a aquellos casos en los que el **módulo** requiere ser representado de manera dinámica, lo que implica la generación de una animación visual que permita observar el comportamiento o la transición de elementos a lo largo del tiempo.


## Concepto Visual

A continuación, se presenta un ejemplo práctico que ilustra cómo el accesso a un elemento de tu web es intuitivo dentro de un entorno visual, aplicando las normas de la nomenclatura de **Difusión Migratoria**. Este ejemplo permite al desarrollador acceder al elemento que desea modificar de manera instántanea ya sea por razones de sostenibilidad o cambios en la directrices de diseño de la conpañia que sea propietaria de la web.

*Nota: para acceder directamente al elemento que se desea modificar el desarrollador se beneficiará de la herrameinta de búsqueda (ctrl + f) mientra se encuentra situado en la hoja de estilos declarada, sabiendo así que si desea cambiar un elemento individual de un componente solo tendrá que buscar el nombre del componente + vI o de otra forma si desea realizar cambios generales de un componente a todos sus dependencias buscará el nombre del componente + vG*

### HTML

```html
<div class="source-social">
  <div class="component-social segment-search" data-module="Search">
    <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960" width="24px" fill="#ffffff">
      <path d="M784-120 532-372q-30 24-69 38t-83 14q-109 0-184.5-75.5T120-580q0-109 75.5-184.5T380-840q109 0 184.5 75.5T640-580q0 44-14 83t-38 69l252 252-56 56ZM380-400q75 0 127.5-52.5T560-580q0-75-52.5-127.5T380-760q-75 0-127.5 52.5T200-580q0 75 52.5 127.5T380-400Z"/>
    </svg>
  </div>
  <div class="component-social segment-favorites" data-module="Favorites">
    <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960" width="24px" fill="#ffffff">
      <path d="m480-120-58-52q-101-91-167-157T150-447.5Q111-500 95.5-544T80-634q0-94 63-157t157-63q52 0 99 22t81 62q34-40 81-62t99-22q94 0 157 63t63 157q0 46-15.5 90T810-447.5Q771-395 705-329T538-172l-58 52Zm0-108q96-86 158-147.5t98-107q36-45.5 50-81t14-70.5q0-60-40-100t-100-40q-47 0-87 26.5T518-680h-76q-15-41-55-67.5T300-774q-60 0-100 40t-40 100q0 35 14 70.5t50 81q36 45.5 98 107T480-228Zm0-273Z"/>
    </svg>
  </div>
  <div class="component-social segment-menu" data-module="Menu">
    <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960" width="24px" fill="#ffffff">
      <path d="M160-360v-80h640v80H160Zm0-160v-80h640v80H160Z"/>
    </svg>
  </div>
</div>
```

### CSS

```css
/*socialvG*/
.source-social {
    height: max-content;
    width: max-content;
    margin: 0 auto;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 12px;
    border-radius: 32rem;
    > .component-social {
        padding: 6px;
        display: inherit;
        justify-content: inherit;
        align-items: inherit;
        position: relative;
        cursor: pointer;
        background: #8683D5;
        border-radius: inherit;
        &::after {
            padding: 4px 10px;
            display: none;
            content: attr(data-module);
            position: absolute;
            top: calc(100% + 12px);
            left: 50%;
            color: #ffffff;
            background: inherit;
            border-radius: inherit;
            transform: translateX(-50%);
        }
        &:hover::after {
            display: block;
        }
    }
}

/*socialvI*/
.source-social {
    > .segment-search:hover {
        background: #3874C7;
    }
    > .segment-favorites:hover {
        background: #FF5A5A;
    }
    > .segment-menu:hover {
        background: #30BA5D;
    }
}
```
Ver ejemplo en: [Codepen]([https.codepen.io/andresceo](https://codepen.io/andresceo/pen/vYoPaeP))

## Potencial & Bifurcación de Código

Cada una de las abreviaturas utilizadas en la nomenclatura **Difusión Migratoria** ofrece un beneficio único y especializado que, al ser aplicada correctamente, permite a los desarrolladores trabajar con mayor claridad, flexibilidad y control sobre el código. A continuación, explicamos cómo cada uno de estos elementos facilita el proceso de desarrollo y bifurcación del código web.

### 1. **Versión (/v)**: Control Total de Iteraciones y Compatibilidad

La sintaxis **/v** tiene el poder de definir y controlar versiones específicas de un **módulo**. Esto permite a los desarrolladores trabajar con distintas iteraciones de un mismo componente o módulo, sin interferir con otras versiones existentes. Este enfoque es particularmente útil cuando se realizan pruebas, mejoras o cambios en el código sin afectar el funcionamiento global del sistema.

**Beneficio**: Los desarrolladores pueden aislar y gestionar diferentes versiones de los mismos elementos, permitiendo actualizaciones y pruebas sin miedo a romper la compatibilidad con versiones anteriores. Esto da un control preciso sobre el ciclo de vida de cada módulo.

### 2. **General (/G)**: Manipulación Global y Consistente

**/G** ofrece la capacidad de aplicar cambios a nivel global, lo que impacta tanto al **módulo** principal como a todas sus dependencias. Esto ayuda a los desarrolladores a implementar cambios de forma consistente en toda la aplicación, asegurando que todos los elementos relacionados se ajusten a una misma directriz o estilo sin necesidad de modificar cada componente individualmente.

**Beneficio**: Los cambios globales son más fáciles de implementar y mantener, ya que se aplican a todos los elementos vinculados al **módulo**, sin la necesidad de duplicar esfuerzos. Esto mejora la eficiencia y la consistencia a lo largo del desarrollo del proyecto.

### 3. **Individual (/I)**: Flexibilidad y Precisión en Modificaciones Específicas

Cuando un desarrollador necesita ajustar solo una parte del **módulo** sin alterar su totalidad, la sintaxis **/I** permite intervenir solo en los elementos individuales dentro de un módulo. Esto ofrece una gran flexibilidad para realizar ajustes mínimos o específicos en componentes sin afectar la integridad general del sistema.

**Beneficio**: **/I** otorga al desarrollador la capacidad de ser preciso en sus intervenciones, modificando solo los elementos necesarios. Esto es ideal cuando se trabaja en proyectos grandes o cuando se necesita personalizar una funcionalidad sin comprometer la estructura general del módulo.

### 4. **System (/sys)**: Coherencia Estética y Funcional

La sintaxis **/sys** es fundamental cuando se busca aplicar una estructura y estilo uniforme a lo largo de todo el sistema. Mediante el uso de **/sys**, los desarrolladores pueden definir estilos y comportamientos estandarizados para un **módulo**, garantizando que todos los elementos dentro de este módulo sigan una misma convención en cuanto a presentación y disposición.

**Beneficio**: Este enfoque facilita la creación de interfaces consistentes y estéticamente agradables, mientras se mantiene la flexibilidad en el diseño. Los desarrolladores pueden asegurarse de que todos los elementos de un módulo compartan una base común, sin tener que escribir reglas repetitivas, lo que ahorra tiempo y esfuerzo.

### 5. **Animation (/A)**: Dinamismo y Experiencia Interactiva

La sintaxis **/A** se aplica a los **módulos** que requieren animación, permitiendo que los desarrolladores incluyan comportamientos dinámicos y transiciones visuales. Este elemento es esencial cuando se busca mejorar la experiencia de usuario mediante interacciones suaves y atractivas.

**Beneficio**: **/A** ofrece a los desarrolladores una forma sencilla de implementar animaciones sin que estas interfieran con el diseño estático. Las animaciones se gestionan de manera independiente, lo que permite que los cambios visuales sean fáciles de aplicar y modificar sin afectar otros aspectos del código. Además, mejora la experiencia del usuario al agregar dinamismo a la interfaz.

---

### Conclusión: Un Código Organizado, Flexible y Escalable

El uso adecuado de las abreviaturas de **Difusión Migratoria** proporciona una forma de organizar el código que optimiza tanto el desarrollo como la bifurcación de proyectos web. Cada elemento, con su propósito específico, ayuda a los desarrolladores a controlar versiones, aplicar cambios globales o individuales, mantener coherencia en el diseño y añadir interactividad, todo sin perder la claridad ni la flexibilidad necesarias para escalar el proyecto.

Con esta metodología, se asegura que el código sea no solo más limpio y legible, sino también más fácil de modificar y bifurcar de forma eficiente, sabiendo que cada regla y cada módulo tiene su lugar y función dentro del sistema. Esto permite a los equipos de desarrollo gestionar proyectos complejos con mayor facilidad, garantizando un flujo de trabajo más ordenado y optimizado.
