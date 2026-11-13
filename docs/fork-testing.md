# Probar el fork de micasadomotica

Repositorio: https://github.com/micasadomotica/Improved-Shopping-List

Versión de prueba: **0.88.1-beta.1**, basada en la 0.88.0 del proyecto original de TitoTB. Conserva el dominio `improved_shopping_list` y el formato de los datos existentes. Sustituye la misma integración; no se instala como una segunda integración independiente.

## Instalar con HACS

1. Guarda una copia de seguridad de Home Assistant antes de sustituir la integración.
2. En HACS, elimina la descarga del repositorio original desde su menú. Esto retira sus archivos; HACS no elimina los datos asociados. **No elimines la integración desde Ajustes → Dispositivos y servicios.**
3. Antes de reiniciar, abre HACS → menú de tres puntos → Repositorios personalizados. Añade `https://github.com/micasadomotica/Improved-Shopping-List` con tipo **Integración**.
4. Abre el repositorio del fork, permite mostrar versiones beta y descarga **0.88.1-beta.1**. Comprueba el propietario `micasadomotica` para distinguirlo del original.
5. Reinicia Home Assistant después de instalar el fork y recarga el panel. La versión mostrada debe ser **0.88.1-beta.1**.

Referencias de HACS: [repositorios personalizados](https://www.hacs.dev/docs/faq/custom_repositories/) y [eliminación de una descarga y conservación de datos](https://www.hacs.dev/docs/use/repositories/dashboard/#removing-a-repository).

## Comprobaciones en tu instalación

- Pega una URL de producto y guarda sin pulsar Recuperar datos. Vuelve a abrir: la alternativa debe conservar el enlace. Debe ocurrir lo mismo si la consulta ha fallado.
- Recupera `https://tienda.mercadona.es/product/3830/aguacate-pieza` y guarda. Debe aparecer una alternativa de Mercadona identificada por la referencia `3830`, con el EAN compartido vacío.
- Añade `https://tienda.mercadona.es/product/3858/aguacates-bandeja`. Debe conservarse como otra alternativa, con referencia `3858`.
- En ambas fichas, Mercadona indicó peso aproximado en la comprobación del 13 de noviembre de 2026. Deben mostrarse como venta al peso, con el precio por kilogramo disponible, sin fijar los gramos ni inventar las piezas de la bandeja. Los precios se consultan de nuevo y pueden cambiar.
- Comprueba que la alternativa de Lidl conserva su EAN, formato y precio. Recuperar una URL de Mercadona dentro de una alternativa con EAN crea o reutiliza una alternativa independiente.
- Guarda, recarga y verifica que la lista, el catálogo, las compras y el Stock siguen disponibles.

## Volver al original

Retira la descarga del fork en HACS, añade o vuelve a descargar el repositorio de TitoTB y reinicia después de completar la instalación. No elimines la entrada de la integración ni sus datos. Las correcciones no introducen migraciones de almacenamiento.

## Trabajo con el repositorio original

La rama `codex/product-url-mercadona-fixes` contiene las correcciones y sus pruebas, sin la versión ni esta documentación del fork. La rama `codex/fork-preview` añade el empaquetado de la beta. Así se pueden enviar las correcciones al original después de probarlas, sin trasladarle cambios propios del fork.

En el fork solo se utiliza **Validate** para las comprobaciones automáticas. Los workflows de publicación y diccionarios permanecen desactivados.
