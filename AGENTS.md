# AGENTS.md — Mediateca MIM

## Workspace
- Contenido: `Analisis_Mediateca_MIM_Koha_OPAC-v2.md` (inventario de pantallas, hallazgos y mejoras del Koha OPAC) y una propuesta estática `index.html` + `styles.css` derivada de él.
- La propuesta usa Bootstrap 5.3.3 vía CDN (la versión del portal) + `styles.css` con las clases MIM del portal (`btn-outline-mim`, `mainTitle`, `hrMim`, footer `bg-color-purple color-beige`). El bundle JS de Bootstrap activa navbar/dropdowns. No hay manifiestos (`package.json`, etc.) ni scripts de test/lint: no los asumas ni los inventes.
- La paleta viene de `mim.cl`, no del portal: `mim-black #222222`, `mim-orange #FF7452`, `mim-yellow #FCEA03`, `mim-blue #25ABE5`, `mim-green #3DB545`, `mim-lila #9D7CE7`, `mim-magenta #E962DF`, `mim-porcelain #EFEFEF`, `mim-gray #8E8E93`.

## Convención
- Trabajar y entregar en **español** (dominio: Koha / MIM).

## Contexto que condiciona el trabajo
- El documento de análisis es la fuente de verdad para alcance, bugs y mejoras; léelo completo antes de proponer cambios.
- Login: tomar como referente el portal de cuentas MIM (Vue.js, Font Awesome, Axios, PHP Laravel).
- Navegación y colecciones: referente `mariategui.org` (WordPress, Preact, jQuery, MySQL).
- Restricción crítica: el buscador no debe aceptar `<script>`; eso ya bloqueó `mim.cl` completo vía WAF.
