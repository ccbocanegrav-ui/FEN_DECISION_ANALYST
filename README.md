# Termómetro BCRP + El Niño (borrador de la fase 1)

> README provisional. El README final de 9 partes se redacta al final.

Chat analista sobre datos oficiales del BCRP, con una capa de El Niño, un semáforo
de exposición para negocios y un modo periodista.

## Fase 1: datos

```bash
python -m venv .venv && .venv\Scripts\activate      # Mac/Linux: source .venv/bin/activate
pip install -r requirements.txt pytest
pytest -q                                           # deben pasar las 18 pruebas
python scripts/fetch_bcrp.py --check                # prueba el formato de la API con una serie (IPC)
python scripts/fetch_bcrp.py                         # descarga todas las series del catálogo
```

Las series quedan en `data/series/`. El catálogo cerrado está en `data/catalog.json`:
cada serie tiene `verificada` (true si se abrió su página en BCRPData y se confirmó el nombre y la unidad).

Si la API falla o responde con otro formato, usa el plan B: exporta la serie desde BCRPData a CSV y ejecuta
`python scripts/fetch_bcrp.py --from-csv ipc_lima ruta/export.csv`.

## Privacidad y honestidad de los datos

Solo datos públicos agregados. Los números que ve el usuario los calcula el código (`app/transform.py`);
el modelo de lenguaje solo redacta.
