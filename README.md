name: 📰 Actualizar actividad reciente

on:
  schedule:
    - cron: '0 * * * *' # Ejecuta cada hora
  workflow_dispatch:     # Permite ejecución manual

jobs:
  update-recent-activity:
    runs-on: ubuntu-latest
    steps:
      - name: Clonar el repositorio
        uses: actions/checkout@v3

      - name: Actualizar actividad reciente
        uses: Readme-Workflows/recent-activity@v2.4.1

      - name: Hacer commit si hay cambios
        run: |
          git config user.name "github-actions[bot]"
          git config user.email "41898282+github-actions[bot]@users.noreply.github.com"
          git add README.md
          git commit -m "📝 Actualiza actividad reciente" || echo "No hay cambios para hacer commit"
          git push


user: wilfridoh
repo: miPrimerReport
commitMessage: "📝 Actualiza actividad reciente"
maxLines: 5
readmePath: "README.md"

## 📌 Actividad reciente

<!--RECENT_ACTIVITY:start-->
<!--RECENT_ACTIVITY:end-->
