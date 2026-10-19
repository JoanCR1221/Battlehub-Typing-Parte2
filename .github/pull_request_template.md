## Requisito

Closes #

<!-- Número del Issue de este requisito (el id coincide: #4 es R04). Un PR cubre un solo requisito. -->

## Descripción

<!-- Qué cambia y por qué. -->

## Cómo comprobar que cumple el «Listo cuando»

<!-- Pasos o comandos para verificarlo. Copie aquí el criterio del Issue y marque lo que se cumple. -->

## Contrato implementado

<!-- Documento y sección de battlehub-contracts que implementa este PR, si aplica.
     Ej.: 04-persistencia-y-api-juegos.md → «API REST mínima obligatoria». -->

## Evidencia de pruebas

<!-- Enlace al run de CI en verde o capturas de las pruebas. -->

## Checklist

- [ ] El PR cubre **un solo** requisito y el Issue quedó vinculado con `Closes #N`.
- [ ] El título sigue el formato semántico con el id del requisito (`feat(R04): descripción`).
- [ ] Los commits son pequeños: cada uno tiene un solo cambio coherente.
- [ ] El Issue se movió a «Se está haciendo» con su Fecha de inicio al empezar.
- [ ] El pipeline de CI está en verde (build + pruebas unitarias + pruebas de integración).
- [ ] No hay secretos en el código (contraseñas, cadenas de conexión, claves).
- [ ] Al menos 1 persona distinta del autor aprobó.
- [ ] Si modifica un contrato de `battlehub-contracts`, referencia el ADR correspondiente.
- [ ] Al fusionar: el Issue pasa a «Hecho» y se anota la Fecha de fin en el tablero.
