# Cómo trabajamos

Cada requisito de la parte 2 se hace **uno por uno**, nunca varios de golpe. Esto aplica también a las migraciones: cada paso es su propio requisito y su propio PR.

> **Un requisito = un Issue = una rama = un PR pequeño, hecho con commits pequeños.**

El tablero está en Proyectos → «Typing Battle parte 2» y la lista completa de requisitos son los Issues del repositorio (el número del Issue coincide con el del requisito: `#4` es `R04`).

## El tablero

| Columna | Qué significa | Cuándo se mueve |
|---|---|---|
| **Pendiente** | Nadie ha empezado | Estado inicial de todos los Issues |
| **Se está haciendo** | Hay rama y trabajo en curso | Al crear la rama. **Se anota la Fecha de inicio** |
| **Hecho** | El PR se fusionó y el requisito cumple su «Listo cuando» | Al fusionar el PR. **Se anota la Fecha de fin** |

Un requisito solo se mueve a **Hecho** si se cumple lo que dice su sección **Listo cuando**. Las fechas son lo que se muestra en la presentación, así que se anotan el mismo día.

## Paso a paso para cada requisito

1. **Elegir** el siguiente Issue en el orden sugerido (el orden está en el Issue y en el Excel).
2. **Mover** el Issue a «Se está haciendo» y poner la Fecha de inicio.
3. **Crear la rama** desde `main` actualizado, con este formato:

   ```bash
   git checkout main
   git pull
   git checkout -b req/R04-quitar-auth0
   ```

   El nombre es `req/` + el id del requisito + 2 a 4 palabras que lo describan.
4. **Trabajar en commits pequeños** (ver «Commits pequeños»), con formato semántico.
5. **Abrir el PR** hacia `main`. El título lleva el id del requisito y la descripción incluye `Closes #N` (el número del Issue), para que al fusionar el Issue se cierre solo.
6. **Esperar** a que el CI esté en verde y a que **otra persona** apruebe. Nadie aprueba su propio PR.
7. **Fusionar** con el mismo método que acuerde el equipo (siempre el mismo), borrar la rama y anotar la Fecha de fin.

## Qué es «un solo requisito»

- Si el PR toca cosas que no pertenecen al Issue, se divide.
- Si el Issue es demasiado grande para un PR revisable en pocos minutos, se divide en varios Issues y se registra en el tablero.
- **Migraciones:** cada cambio de esquema o de motor va en su propio PR (por ejemplo: proveedor de MySQL, llaves primarias, largos de texto y migraciones de EF Core son cuatro PRs distintos, no uno).
- Un PR no mezcla código nuevo con reformateo ni con renombres masivos.

## Commits pequeños

Un PR no es un solo commit con todos los cambios: es una serie de commits pequeños, cada uno con **un cambio coherente** que se puede entender y revisar por sí solo. Lo ideal es que cada commit compile y pase las pruebas.

- Un commit = una idea: quitar un archivo, cambiar una firma, actualizar la documentación de un tema.
- Las pruebas de un cambio van junto con el cambio, o en el commit siguiente si cuestan un paso aparte.
- La documentación va en commits propios, separados del código.

## Commits semánticos

Formato: `<tipo>(<alcance>): <descripción corta en imperativo>`. El alcance es el id del requisito.

| Tipo | Uso |
|---|---|
| `feat` | Funcionalidad nueva |
| `fix` | Corrección de un bug |
| `refactor` | Cambio interno que no altera el comportamiento |
| `test` | Pruebas |
| `docs` | Documentación |
| `ci` | Pipeline de CI |
| `chore` | Mantenimiento |
| `perf` | Rendimiento |

Ejemplos: `refactor(R04): quitar la autenticación de Auth0 de la API`, `docs(R32): agregar ejemplos curl de los endpoints`.

## Reglas de `main`

- Está protegida: no se sube nada directo; todo entra por PR.
- Cada PR necesita **1 aprobación**, que las conversaciones estén resueltas y que pasen los checks del CI (`Backend (.NET 10)` y `Frontend (Aurelia)`).
- Nunca se hace `force push` sobre `main`.

## Lo que no se versiona

Ningún secreto en el código ni en archivos del repositorio: contraseñas, cadenas de conexión y claves viven en variables de entorno. Si algo se subió por error, se avisa de inmediato para cambiarlo, no basta con borrarlo en un commit nuevo.
