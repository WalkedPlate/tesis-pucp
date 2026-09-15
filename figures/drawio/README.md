# Diagramas draw.io de la tesis

Diagramas editables para explicar el contexto, el problema, la propuesta y la validación
de la tesis sobre realizabilidad relativa al PEP de *intents* de contención selectiva en
5G Core SBA.

## Contenido

| Archivo | Qué explica | Dónde encaja |
|---|---|---|
| `01-contexto-5gc-sba.drawio` | Arquitectura 5G Core, plano de control SBA, RAN y plano de usuario. Marca el ámbito de la tesis. | Introducción / Cap. 1, área académica |
| `02-comunicacion-directa-indirecta.drawio` | Comunicación directa frente a indirecta vía SCP; dónde ocurre la selección de la instancia. | Cap. 1, contexto del problema |
| `03-problema-contencion-selectiva.drawio` | El problema central: intent selectivo, PEP antes y después del SCP, qué observa cada punto y las cuatro condiciones. | Cap. 1, §problema de investigación (reemplaza a `figures/chapter1/problema_contencion_selectiva.tex`) |
| `04-perfil-de-ejecucion.drawio` | El formalismo: entradas del perfil Π, evaluación y veredictos R / U con causas F1, F2, F3. | Cap. 1, visión de la solución |
| `05-verificador-cuatro-condiciones.drawio` | El verificador: materialización → visibilidad → confianza → acción, con la causa asociada a cada fallo. | Cap. 1, enfoque técnico / Cap. 3 |
| `06-efecto-del-binding.drawio` | Petición no ligada frente a ligada con todo lo demás constante, y matriz estado × capa del PEP. | Hallazgos |
| `07-modelo-de-amenaza-y-confianza.drawio` | NF comprometida, cabecera autoafirmada, escala de confianza T0–T3 y distinción funcional / segura. | Cap. 1, consideraciones de seguridad / Hallazgos |
| `08-banco-de-pruebas.drawio` | Entorno experimental: K3s, Cilium, Open5GS, UERANSIM y los PEP antes y después del SCP. | Cap. 1, validación / Cap. 3 |
| `09-mapa-de-la-tesis.drawio` | Problema → propuesta → validación → resultado, con la pregunta de investigación. | Presentación / cierre de capítulo |

## Editar

Abrirlos en <https://app.diagrams.net> (Archivo → Abrir desde → Dispositivo) o con la
aplicación de escritorio draw.io. El XML no está comprimido, así que también se puede
editar a mano y versionar con git.

Cada archivo tiene dos capas (Extras → Editar diagrama → o menú Ver → Capas):

- **Diagrama**: el contenido.
- **Titulo**: el título y el subtítulo. Conviene **ocultarla** al exportar figuras para la
  tesis, porque el título ya lo aporta el `\caption` de LaTeX. Para diapositivas, dejarla
  visible.

## Exportar para LaTeX

En draw.io: **Archivo → Exportar como → PDF**, con `Recortar` (crop) activado y
`Fondo transparente`. Guardar en `figures/chapter1/` con el mismo nombre base.

Alternativa por línea de comandos, si se instala draw.io de escritorio:

```bash
drawio --export --format pdf --crop --transparent --output figures/chapter1/03-problema-contencion-selectiva.pdf figures/drawio/03-problema-contencion-selectiva.drawio
```

## Insertar en el documento

```latex
\begin{figure}[H]
    \centering
    \includegraphics[width=\textwidth]{chapter1/03-problema-contencion-selectiva.pdf}
    \caption{Problema de contención selectiva y puntos de ejecución de la política en un trayecto SBA indirecto.}
    \label{fig:problema-contencion-selectiva}
    \notafuente{Elaboración propia con base en la arquitectura SBA de 3GPP~\cite{ETSI_TS_123501_R16,ETSI_TS_129500_R16}.}
\end{figure}
```

`\graphicspath` ya incluye `figures/`, por lo que basta la ruta relativa a esa carpeta.

## Convenciones de estilo

- Azul (`#4A6D96`): funciones de red 5G.
- Gris (`#7A7A7A`): infraestructura e intermediarios (SCP, NRF, UPF, RAN).
- Ámbar (`#B58133`): puntos de ejecución de políticas (PEP).
- Rojo (`#B03A2E`): denegación, actor comprometido, veredicto no realizable.
- Verde (`#3B7A57`): permiso y veredicto realizable.
- Línea discontinua: relación auxiliar, descubrimiento o elemento aún no materializado.
