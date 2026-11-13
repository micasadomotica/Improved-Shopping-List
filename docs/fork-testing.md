# Probar el fork de micasadomotica

Repositorio: https://github.com/micasadomotica/Improved-Shopping-List

Versión de prueba: **0.88.1-beta.1**, basada en la 0.88.0 del proyecto original de TitoTB. Conserva el dominio `improved_shopping_list` y el formato de los datos existentes. Sustituye la misma integración; no se instala como una segunda integración independiente.

## Marketplace en Home Assistant 2026.11 o posterior

Marketplace sustituye a HACS y se abre desde **Ajustes → Marketplace**. El archivo técnico `hacs.json` sigue siendo necesario para los repositorios personalizados.

**Si ya tienes el original configurado, no sigas la antigua indicación de desinstalarlo.** Marketplace impide desinstalar una integración configurada sin eliminar antes su configuración. «Delete and uninstall» también elimina sus dispositivos y entidades. El cambio de origen al fork conservando la configuración todavía debe verificarse; esta guía no garantiza ese procedimiento. Guarda una copia de seguridad antes de sustituir la instalación.

Para una instalación nueva:

1. En **Ajustes → Marketplace**, pulsa **Añadir desde enlace / Add from link** e introduce `https://github.com/micasadomotica/Improved-Shopping-List`. Conecta GitHub si se solicita.
2. Añade el repositorio y abre su ficha. Marketplace detecta el tipo; selecciona **Integración** si lo solicita.
3. Para recibir betas, habilita la entidad **Pre-release** del dispositivo del repositorio en **Ajustes → Dispositivos y servicios → Marketplace** y enciende su interruptor. La entidad viene deshabilitada.
4. Selecciona **0.88.1-beta.1** al instalar. El menú de la ficha ofrece **Instalar otra versión / Install another version**.
5. Sigue la indicación de reinicio y recarga el panel. Comprueba que muestra **0.88.1-beta.1**.

Fuente: [documentación oficial de Marketplace](https://www.home-assistant.io/integrations/marketplace). La compatibilidad de la integración con Core 2026.10 se mantiene, pero estas instrucciones corresponden a Marketplace desde 2026.11.

## Comprobaciones en tu instalación

- Pega una URL de producto y guarda sin pulsar Recuperar datos. Vuelve a abrir: la alternativa debe conservar el enlace. Debe ocurrir lo mismo si la consulta ha fallado.
- Recupera `https://tienda.mercadona.es/product/3830/aguacate-pieza` y guarda. Debe aparecer una alternativa de Mercadona identificada por la referencia `3830`, con el EAN compartido vacío.
- Añade `https://tienda.mercadona.es/product/3858/aguacates-bandeja`. Debe conservarse como otra alternativa, con referencia `3858`.
- En ambas fichas, Mercadona indicó peso aproximado en la comprobación del 13 de noviembre de 2026. Deben mostrarse como venta al peso, con el precio por kilogramo disponible, sin fijar los gramos ni inventar las piezas de la bandeja. Los precios se consultan de nuevo y pueden cambiar.
- Comprueba que la alternativa de Lidl conserva su EAN, formato y precio. Recuperar una URL de Mercadona dentro de una alternativa con EAN crea o reutiliza una alternativa independiente.
- Guarda, recarga y verifica que la lista, el catálogo, las compras y el Stock siguen disponibles.

## Volver al original

Conserva una copia de seguridad anterior a la prueba para poder restaurarla. No utilices «Delete and uninstall» como una sustitución que conserve dispositivos y entidades. Las correcciones no introducen migraciones de almacenamiento, pero eso no cambia el comportamiento de desinstalación de Marketplace.

## Trabajo con el repositorio original

La rama `codex/product-url-mercadona-fixes` contiene las correcciones y sus pruebas, sin la versión ni esta documentación del fork. La rama `codex/fork-preview` añade el empaquetado de la beta. Así se pueden enviar las correcciones al original después de probarlas, sin trasladarle cambios propios del fork.

En el fork solo se utiliza **Validate** para las comprobaciones automáticas. Los workflows de publicación y diccionarios permanecen desactivados.
