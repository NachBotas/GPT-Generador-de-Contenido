# Contrato de diseño para Codex
No se pide al motor de copy que finja generar un diseño final. El entregable es una especificación reproducible. Si usuario pide interfaz de diseños, implementar selector con tarjetas de familia D01–D08 y miniaturas de referencias reales autorizadas, opción «usar mi referencia», modo automático que explica elección y modo manual. Separar copy de plantilla y activos. El usuario debe poder cambiar colores, fuente, imágenes, texto, tamaño, posiciones y orden sin reescribir el contenido. No subir imágenes privadas ni referencias de terceros a repos públicos sin permiso.
## Modelo de datos mínimo (ejemplo, no datos medidos)
```json
{"schemaVersion":1,"canvas":{"width":1080,"height":1350},"styleId":"D01","referenceFiles":["referencias/growin_agencia_DdHbigijble_1.jpg"],"tokens":{"background":"#101010","text":"#ffffff","accent":"#f6d34a","fontFamily":"Inter","margin":72},"slides":[{"id":"01","role":"cover","layers":[{"type":"image","asset":"hero.png","box":[0,0,1,0.64],"fit":"cover","alt":"Metáfora visual"},{"type":"text","role":"headline","text":"Titular aprobado","box":[0.06,0.63,0.88,0.25],"fontSize":84,"lineHeight":1.03,"align":"center","weight":800}],"assetsRequired":["hero.png"],"notes":"Ejemplo de coordenadas, adaptar tras observar la referencia"}]}
```
Coordenadas x,y,w,h normalizadas respecto del canvas. Orden de capas = z-index; declarar padding, fill, opacity, border, radius, rotation, shadow, crop y focal point cuando aplique. Texto editable separado de imagen; usar runs con estilos para palabras destacadas. Registrar fallback de tipografía y licencias; nunca compartir archivos de fuentes sin autorización. Si se usan fuentes de sistema, revisar métricas y reflow. Render a PNG/JPG por slide; nombrar 01, 02...; exportar ZIP y manifest; no aplanar originales si se requiere edición. Si se usan videos, tratarlos como un tipo separado con duración, poster, transcripción y safe areas; no asumir contenido de video no inspeccionado.
## Flujo de interfaz sugerido
1. Brief y activos. 2. Elegir referencia narrativa y visual (o subir una propia). 3. Propuestas de portada y preview en miniatura. 4. Aprobar copy completo. 5. Render de slides, edición por capas y preview del conjunto. 6. Exportar. Mantener versiones y permitir regenerar un solo slide sin cambiar los demás. Si referencia sube con un texto propio, no copiarlo automáticamente a la marca.
## Pruebas de aceptación
- Exportación 1080×1350 por defecto o dimensiones elegidas, consistente en todo el carrusel.
- Texto sin overflow, truncamiento, clipping involuntario, solapamientos; medir bounding boxes del renderer.
- CTA y titular legibles a 360px de ancho; inspección visual de cada slide y contact sheet.
- Cajas y jerarquía comparadas con referencia; justificar diferencias por copy/activo.
- Orden numérico correcto, nombres únicos, activos resueltos, no rutas rotas; mantener fuentes y logos permitidos.
- No cambiar valores de pruebas ni inventar capturas; marcar placeholder visible antes de aprobar.
- No prometer que un render fue probado si no se ejecutó. No convertir una propuesta de integración en evidencia de que funciona.
## Rúbrica editorial (0–2 cada criterio, sugerida)
Relevancia avatar, impacto portada, especificidad, cumplimiento de promesa, continuidad, valor útil, evidencia, densidad, jerarquía, legibilidad, fidelidad visual, coherencia CTA. Total 24; objetivo 20, pero cualquier falsedad, activo faltante esencial o texto ilegible bloquea publicación aunque puntúe alto. Evaluación humana final.
