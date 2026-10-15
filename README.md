# openoutreach-web

Panel web sencillo para manejar OpenOutreach: ver estado, listar leads, exportar CSV,
lanzar búsquedas y envíos, y ver el log en vivo.

Este repositorio es **independiente** del fork de OpenOutreach (`../repo`) y de la
configuración Docker (`../docker`).

## Stack previsto

- FastAPI + Uvicorn
- Jinja2 + HTMX (interfaz delgada, sin build de frontend)
- Consumo de la CLI por su contrato JSON: `openoutreach find N --json`,
  `openoutreach find 0 --json`, `openoutreach status --json`

## Reglas de diseño

- **Un solo job a la vez.** SQLite admite un único escritor; la cola interna serializa.
- **Nunca leer tablas internas.** Solo la salida JSON/CSV de la CLI.
- **Confirmación obligatoria** para acciones que gastan créditos o envían correo.
- Secretos solo por variables de entorno; jamás en la UI ni en la base.

## Estado

Sin código todavía. Pendiente el andamiaje (fases F2–F5 de `../PLAN.md`).
