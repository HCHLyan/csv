# 1. Construir la imagen Docker de la API de catálogo
docker build -t datamart-catalog-api -f api_extension/Dockerfile.api api_extension/

# 2. Iniciar el contenedor conectado a la misma red del Data Warehouse
"""
docker run -d \
  --name datamart_catalog_api \
  --network datamart-etl_datamart_net \
  -e DW_POSTGRES_HOST=postgres-dw \
  -e DW_POSTGRES_PORT=5432 \
  -e DW_POSTGRES_DB=datamart_dw \
  -e DW_POSTGRES_USER=datamart_user \
  -e DW_POSTGRES_PASSWORD=datamart_dw_pass \
  -p 8000:8000 \
  datamart-catalog-api
  """
