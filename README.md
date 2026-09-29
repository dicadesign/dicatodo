# dicaToDo

Lista de tareas en alemán, capturada como **mindmap** (estilo XMind) y conectada con dicaKalendar. Funciona en PC y móvil.

## Cómo funciona
- **El centro del mapa es la fecha** de la lista (o «Ohne Datum»). Las tareas del día salen como ramas principales; las subtareas, como ramas secundarias (sin límite de niveles).
- Barra de días arriba para cambiar de fecha; `‹ Heute ›` y selector de fecha.
- **Captura rápida**: tocar la fecha → «＋ Aufgabe» → escribir. `Enter` = siguiente tarea, `Tab` = subtarea, `F2` = renombrar, `Espacio` = hecho, `Supr` = borrar. En el móvil: barra de acciones al seleccionar un tema. Se entiende «Miete 850 €» y «Zahnarzt 10:00-11:00».
- **Subtareas secuenciales o paralelas**: en «Details → Reihenfolge» se marca de qué tarea depende otra. Sin dependencia = paralelo. Los números verdes son el paso (1, 2, 3…; mismo número = en paralelo); «🔒 wartet» avisa si falta un paso previo. El botón «Nacheinander/Parallel» de la barra lo ajusta de golpe.
- **Fecha, hora, periodo** (Von/Bis, varios días), repetición (diaria, días de la semana, cada 2 semanas, mensual, anual) y recordatorios.
- **Dinero**: al llenar «Betrag» aparece la **Art der Ausgabe** (categoría); en la mindmap se abre sola al escribir un importe. Categorías: crear, renombrar, cambiar color y borrar (⋯ → Ausgaben-Kategorien). Pestaña «Zahlungen»: totales del mes, abierto/pagado y por categoría.
- **Termine**: las citas de dicaKalendar del día aparecen (solo lectura) como rama «📅 Termine» en la mindmap y como sección en la lista, con hora, persona, lugar y categoría de color.
- **dicaKalendar**: cada tarea con fecha aparece allí como cita (`todo-<id>`), con hora, repetición y avisos push. Si la mueves o la borras en el calendario, dicaToDo lo recoge. Las tareas con importe van a la categoría «Zahlungen».

## Uso
- **Local**: abrir `index.html` (necesita la carpeta `dicaKalendar` al lado; comparte el navegador con el calendario local).
- **Servidor** (PC + móvil sincronizados): el servidor de dicaKalendar sirve dicaToDo en **`/todo/`** con el mismo login y sincronización, y así lee también las citas del calendario online. En el móvil: abrir `https://kalendar.dicakultur.com/todo/` → Compartir → Zum Home-Bildschirm.

## Instalación en el VPS (junto a dicaKalendar)
```bash
sudo git clone <URL-del-repositorio-dicaToDo> /opt/dicatodo
sudo chown -R dicakalender:dicakalender /opt/dicatodo
# dicakalender.service ya trae TODO_DIR=/opt/dicatodo
sudo cp /opt/dicakalender/deploy/dicakalender.service /etc/systemd/system/
sudo systemctl daemon-reload
sudo /opt/dicakalender/deploy/update.sh
```
Después, `update.sh` actualiza también dicaToDo.
