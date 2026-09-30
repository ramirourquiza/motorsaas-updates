# motorsaas-updates

Metadata **pública y firmada** de las versiones de MotorSaaS, publicada con GitHub Pages:

- Sitio: <https://ramirourquiza.github.io/motorsaas-updates/>
- Índice de versiones: <https://ramirourquiza.github.io/motorsaas-updates/motorsaas-updates.json> (se publica con la
  primera versión oficial; hasta entonces no existe)

MotorSaaS y su mecanismo de actualización son de uso **interno**: las aplicaciones que lo consultan viven en
repositorios controlados por el mismo propietario.

## Qué contiene

- `motorsaas-updates.json`: índice firmado con Ed25519 (formato `motorsaas.signed/1`, schema `motorsaas.updates/1`).
  Solo informa versiones, fechas, compatibilidad, cambios incompatibles, requisitos y notas públicas.
- `index.html`, `.nojekyll` y este README.

**Nunca** contiene código, artefactos (`.tgz`), manifests de release, el registro técnico de cambios, claves privadas,
tokens ni secretos.

## Por qué es seguro que sea público

El índice solo **informa**: cada aplicación verifica su firma con las claves públicas que trae consigo y lo ignora si no
es válida. Preparar una actualización nunca usa este índice: el Updater descarga la release del repositorio privado con
un token temporal de solo lectura y exige su manifest firmado y el SHA-256 del artefacto. Alterar este sitio no permite
ejecutar código en ninguna aplicación.

## Cómo se actualiza

Solo al publicar una versión de MotorSaaS: el índice se firma **offline** junto con la release y se sube tal cual (sin
editarlo a mano). GitHub Pages y la caché de cada aplicación (15 minutos) pueden demorar su visibilidad unos minutos.
