# Stage 1: Build
FROM python:3.12-slim AS build
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir --prefix=/install -r requirements.txt
COPY . .


# FROM python:3.12-slim as Build
# WORKDIR /app
# COPY requirements.txt .
# RUN pip install --no-cache-dir -r requirements.txt
# COPY . .
# CMD ["uvicorn", "src.main:app", "--host", "0.0.0.0", "--port", "8080"]
# EXPOSE 8080

# Stage 2: Production Stage
FROM python:3.12-slim 
WORKDIR /app
COPY --from=Build /install /usr/local
COPY --from=Build /app /app
EXPOSE 8080
CMD ["uvicorn", "src.main:app", "--host", "0.0.0.0", "--port", "8080"]