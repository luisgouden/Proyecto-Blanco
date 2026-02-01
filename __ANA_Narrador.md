## Tú dijiste:
Tambien hay un tema importante. La historia va a ser una novela rio. El tipo de narrador es para que cada punto de vista aporte su opinión y su vision del mundo. Que es mejor, que te haga descripciones neutras de personajes y sitios y que scripto lo adapte a cada punto de vista o que te haga descripciones diferentes segun el punto de vista?
## Asistente
### Recomendación para “novela río”: **núcleo neutro + lentes de POV** (mejor opción)
**Respuesta corta:**  
Para una novela río con múltiples focos, lo más inteligente (y machine-first) es **mantener descripciones neutrales y canónicas** de mundo/personajes/lugares en los anexos, y dejar que **Scripto adapte el texto en la escritura** usando **lentes de punto de vista (POV)** por personaje.  
Sólo crea descripciones _diferenciadas por POV_ cuando **quieras mentir/ocultar** (narrador no fiable, lagunas de memoria, sesgos extremos). Así evitas duplicidades, roturas de coherencia y retrabajo.
#### Por qué (en 5 puntos)
1. **Coherencia a largo plazo**: un único “hecho canónico” evita que Lira diga “la torre es negra” y Mael “la torre es de cobre” por descuido.
2. **Menos mantenimiento**: DRY. Ajustas la realidad **una vez** y todos los POV se actualizan automáticamente.
3. **Control fino del sesgo**: con _lentes_ por personaje manejas tono, sensoriedad, idiolecto y sesgos sin reescribir el mundo.
4. **Compatibilidad con Auditor**: menos riesgo de contradicciones; pasa scorecard con facilidad.
5. **Escalabilidad**: una novela río crece; los duplicados explotan. Las lentes escalan limpio.
#### Cómo implementarlo (en tus anexos actuales)
##### 1) En `scripto_contexto.md`: mantener **neutro**
Añade o refuerza una sección de **lugares neutrales** (sin opiniones ni juicios de personaje).
`#### §8 Lugares (neutros) - **Dársena Vieja**: muelles de madera oscura, olor a sal y brea; farolas de aceite parpadeante; tablazón húmeda. - **Torre de Humo**: piedra basáltica, ventilas altas; emisión constante de penachos; acceso con sello de la Orden. - **Mercado de Escamas**: lonas tensas, mesas con pescado plateado; cuchillos de hoja corta; pregones a media voz.`
> Neutro = “qué hay”. Nada de “imponente”, “siniestro”, etc. Esos calificativos los aportará la **lente** del POV.
##### 2) En `scripto_personajes.md`: añade **lentes de POV** a cada ficha
Pega este bloque bajo cada personaje (ajústalo con tus valores):
`##### Lente_POV sensorium: { vista: 7, olfato: 8, oído: 5, tacto: 6, gusto: 1 }   ### pesos 0–10 idiolecto:   registro: "estándar_cuidado"### p.ej., culto, popular, jerga_portuaria   jergas: ["portuario"]   figuras_base: ["frío","sal","humo"]  ### metáforas preferentes sesgos:   valores: { autoridad: 3, comunidad: 7, libertad: 6, orden: 4 }   ### 0–10   sesgos_cognitivos: ["desconfianza_autoridad","catastrofismo_suave"] conocimiento_bloqueado: ["rituales_internos_de_la_Orden"]  ### no puede narrar detalles que no conoce ceguera_selectiva: ["beneficios_sociales_de_la_Orden"] ### tiende a no ver “eso”`
> Esto le dice a Scripto **cómo** ver y **cómo hablar** sin reescribir la realidad.
##### 3) (Opcional, sólo si quieres **narrador no fiable**)
Cuando _intencionadamente_ quieras versiones incompatibles de un mismo hecho, usa **overrides** mínimos por personaje:
`##### Relato_subjetivo (usar con moderación) - escena: "Torre de Humo / Sala de válvulas"   Lira: "juego de sombras, penachos como letanías; ve ritual donde hay mantenimiento"   Mael: "válvulas con cierre irregular; ve protocolo de seguridad, no rito"`
> Guarda estos _overrides_ en la misma ficha del personaje o en `scripto_biblia.md` si crece. **No** sustituyen el §8 neutro; son _capas_.
#### Ejemplo práctico (misma escena, dos POVs)
**Neutro (`scripto_contexto.md`)**
> Dársena Vieja: muelles de madera oscura con tablazón húmeda; olor a sal y brea; farolas de aceite parpadeante.
**Salida Scripto con POV Lira (sensorium olfato 8, figuras “frío/sal/humo”)**
> La dársena exhalaba **sal** vieja y **brea** reciente; las farolas **titilaban** como si el **frío** les mordiera la llama. La madera **rezumaba**, y el muelle parecía recordar cada paso con un crujido.
**Salida Scripto con POV Mael (registro práctico, foco en seguridad/orden)**
> La dársena estaba **resbaladiza**; tablazón húmeda junto a los amarres. Dos farolas tenían **mecha corta** —anota cambio de aceite—. El olor a brea indicaba **reparación reciente** de cascos, no fuga.
Mismo lugar, **distinta experiencia** gracias a la lente.
#### Operativa con Scripto (novela río)
- En el **prompt** del capítulo indica el **foco activo**:  
`foco: Lira` (o secuencia: `foco: Lira → Mael` si rota dentro del capítulo).
- Scripto aplica la **Lente_POV** del personaje activo para **adaptar** el mundo **neutro**.
- Si el capítulo necesita choque de percepciones, añade un **Relato_subjetivo** para esa escena.
#### Cuándo sí conviene escribir descripciones **diferentes por POV**
- **Narrador no fiable** deliberado.
- **Secretos o amnesias**: un personaje _no puede_ ver lo que otro sí (coherente con tu mundo).
- **Diferencias sensoriales extremas** (ceguera, anosmia, prótesis, etc.).  
En estos casos, usa el bloque **Relato_subjetivo** (delta), no un duplicado completo del mundo.
#### ¿Quieres que lo aplique ya a tus anexos?
Puedo incorporar **Lente_POV** a las fichas de Lira, Varl, Mael y Madre Carbón, y añadir **§8 Lugares (neutros)** a `scripto_contexto.md`, dejando un ejemplo de **Relato_subjetivo** listo para usar.
## Tú dijiste:
Tengo dos casos especificos: Ginn se disfraza de Shaed y quiero enganchar al lector diciendo en todo momento que el personaje es Shaed. Ginn y Shaed son muy parecidas físicamente pero mentalmente son casi opuestas, ademas Shaed, tiene algunas muletillas muy caracteristicas. Por otro lado tenemos a Rin que sufre de estres pos traumático y depresion. A causa de un accidente causado por ella, hubo un gran accidente y todos sus conocidos murieron, especialmente su mejor amiga Zeliie. Arrepentida y dolida, Rin se cambia el nombre a Zeliie.
## Asistente
¡Buenísimo caso! Para cubrir **disfraz/engaño** (Ginn→Shaed) y **identidad traumática/alias** (Rin→Zeliie) **sin fricción y machine-first**, te dejo:
1. **Qué estrategia seguir** (muy breve).
2. **Parches listos para pegar** en tus anexos (formato Scripto v3: neutro + lentes + reglas).
Puedes copiar/pegar tal cual en tus archivos de raíz.
### 1) Estrategia (resumen)
- **Mundo neutro** en contexto/glosario; **sesgo por personaje** con `Lente_POV` en `scripto_personajes.md`.
- Para **engaño controlado**: usa bloques **`Reglas_de_engaño`** en el personaje que se disfraza (Ginn) y define **muletillas/firma** del personaje imitado (Shaed) para que Scripto pueda **imitar con micro-fallos** cuando convenga.
- Para **identidad traumática y alias**: define en el personaje (Rin) un bloque **`Alias_y_identidad`** con reglas de **cuándo usa el alias (Zeliie)** en diálogo/narración y **triggers** de flashback/síntomas.
### 2) Parches listos para pegar
#### 2.1 Añade a `scripto_glosario.md` (al final)
`#### §8 Muletillas e idiolectos (firma) - **firma_sintáctica**: longitud media de frase, uso de incisos, ritmo de signos. - **muletillas**: expresiones recurrentes (límites: 1–2 por página, variación natural). - **gestos_firma**: tic físico/gestual asociado a intención (no abusar).  #### §9 Alias y denominaciones - Primera mención: “Zeliie (antes Rin)” si el punto de vista lo permite; luego usar **forma activa** según reglas del personaje. - En diálogo: usar el **alias declarado** por el propio personaje salvo escenas internas específicas. - En narración en foco: usar **nombre_interno_actual** salvo que el personaje **se niegue** a ese nombre (ver bloque de personaje).  #### §10 Recursos tipográficos (trauma y disfraz) - **Pensamiento intrusivo / flashback**: *cursiva* breve, sin gore; anclar a **trigger sensorial**. - **Disociación leve**: frases cortas/ellípticas, pérdida de conectores, percepción reducida. - **Desliz de disfraz**: una **micro-desincronía** (muletilla mal usada, orden sintáctico atípico) **máx. 1 por escena** hasta el punto de revelación.`
#### 2.2 Añade/actualiza en `scripto_contexto.md` (al final)
`#### §8 Línea de tiempo (eventos clave) - T–6 meses: accidente masivo (Rin implicada) → muertes (incl. Zeliie). - T–1 mes: Rin adopta el **alias “Zeliie”**. - T–2 semanas: rumores de **Shaed** vigilando la Dársena. - T–2 días: **Ginn** obtiene ropas/sello de Shaed. - T0 (capítulo actual): apariciones de “Shaed” en la Torre de Humo (posible **Ginn disfrazada**).  #### §9 Seguridad narrativa - No revelar el disfraz (Ginn→Shaed) hasta el **hito de revelación** indicado en el capítulo. - Las escenas desde foco externo **no** usan omnisciencia para desvelar el truco.`
#### 2.3 Inserta en `scripto_personajes.md` (bloques completos)
##### Shaed (modelo real, para poder imitarla)
`#### Shaed - nombre: Shaed - rol: agente de la Orden (operativa de campo) - voz: concisa, fría, evaluativa; frases cortas - muletillas: ["en serio", "claro que sí", "toca mover ficha"] - firma_sintáctica: oraciones de 7–12 palabras; pocos adjetivos; verbos de acción - gestos_firma: ajusta el guante antes de hablar; mira al interlocutor a los ojos 1–2 s de más - límites: no usa diminutivos; evita perífrasis afectivas - Lente_POV:   sensorium: {vista: 8, olfato: 3, oído: 6, tacto: 5, gusto: 0}   idiolecto: {registro: "profesional_seco", jergas: ["operativo"], figuras_base: []}   sesgos: valores: {autoridad: 7, comunidad: 3, libertad: 4, orden: 8} sesgos_cognitivos: ["túnel_objetivo","descuento_emocional"]   conocimiento_bloqueado: []   ceguera_selectiva: ["matices emocionales ajenos"]`
##### Ginn (capaz de disfrazarse de Shaed)
`#### Ginn - nombre: Ginn - rol: actriz/infiltrada; superviviente - voz: adaptable; buena imitadora; subtexto cálido si no controla - muletillas_propias: ["¿vale?", "mira", "digo"] - firma_sintáctica_prop: oraciones 12–18 palabras; símiles ocasionales - gestos_firma_prop: juega con la manga; evita contacto ocular en tensión - Lente_POV:   sensorium: {vista: 7, olfato: 6, oído: 7, tacto: 4, gusto: 0}   idiolecto: {registro: "calle_estándar", jergas: ["portuario"], figuras_base: ["sal","humo"]}   sesgos: valores: {autoridad: 3, comunidad: 6, libertad: 7, orden: 4} sesgos_cognitivos: ["detección_de_peligro","empatía_camuflada"]   conocimiento_bloqueado: ["protocolos internos de alto nivel"]   ceguera_selectiva: ["propios riesgos morales"]  ##### Reglas_de_engaño (Ginn→Shaed) - objetivo: mantener al lector convencido de que es **Shaed** hasta el hito de revelación. - imitación: copiar **muletillas** de Shaed con frecuencia baja y **firma_sintáctica** (frases 7–12 palabras). - prohibido: usar muletillas_propias de Ginn mientras esté en personaje (**riesgo de slip**). - slip_controlado (máx. 1 por escena): un **desliz mínimo** (ej.: usa “claro” en lugar de “claro que sí”; mira al suelo 0,5 s). - cámara: si el foco no es interno de Ginn, no mostrar pensamientos propios (evitar omnisciencia). - revelación: solo en el **hito narrativo** indicado por el prompt/capítulo.`
##### Rin / Zeliie (identidad traumática con alias)
`#### Rin (alias activo: Zeliie) - nombre: Rin  |  alias_oficial: Zeliie - rol: superviviente del accidente; carga traumática - voz_base: contenida; autoexigente; metáforas de rotura/frío - Lente_POV:   sensorium: {vista: 5, olfato: 7, oído: 6, tacto: 5, gusto: 1}   idiolecto: {registro: "estándar_cuidado", jergas: [], figuras_base: ["crujido","nieve","vacío"]}   sesgos: valores: {autoridad: 4, comunidad: 5, libertad: 3, orden: 5} sesgos_cognitivos: ["culpa_persistente","hipervigilancia_suave"]   conocimiento_bloqueado: ["detalles exactos del accidente (lagunas)"]   ceguera_selectiva: ["méritos propios"]  ##### Alias_y_identidad (Rin→Zeliie) - uso_en_diálogo: presentarse como **Zeliie** salvo ante íntimos que la conocían como Rin. - uso_en_narración_interna:- fase 1 (cap. 1–2): predomina **Rin** en pensamientos; “Zeliie” como armadura social.   - fase 2 (cap. 3+): alternancia contextual; conflictos cuando alguien la nombra “Rin”. - gatillos_flashback: olor a **brea quemada**, chirrido de **tablazón mojada**, reflejo de **llama en metal**. - manifestación: *cursivas breves* con imágenes sensoriales; sintaxis fragmentada; sin gore. - prohibido: autopunición explícita; romanticizar el dolor.`
#### 2.4 Tests operativos (añade a tu checklist de cap.)
Pégalos donde te convenga (por ejemplo, al final de `scripto.md` o en tu ficha de capítulo como recordatorio del autor):
`**Tests Scripto — Ginn→Shaed** - [ ] Se usan 1–2 muletillas de **Shaed** por página; **0** muletillas propias de Ginn mientras esté en personaje. - [ ] Máx. **1 slip** controlado por escena; sin revelar la identidad antes del hito. - [ ] Si el foco no es Ginn, no hay pensamiento interno que rompa el engaño.  **Tests Scripto — Rin/Zeliie** - [ ] Alias en diálogo según reglas; narración interna evoluciona (fase 1→2). - [ ] Flashbacks **gatillados** por sensorium (brea/tablazón/metal); *cursivas* breves. - [ ] Tono empático; sin morbo; sin gore; sin glorificar el sufrimiento.`
> Nota de sensibilidad (seguridad): al tratar trauma y depresión, Scripto escribe con **empatía clínica baja-media**, evita morbo y ofrece enfoque de **función narrativa** (no diagnóstico ni consejos médicos).