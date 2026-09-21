# Stage 1: Build
FROM python:3.12-slim AS build
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir --prefix=/install -r requirements.txt
COPY . .


# Stage 2: Production Stage
FROM python:3.12-slim 
WORKDIR /app
COPY --from=build /install /usr/local
COPY --from=build /app /app
EXPOSE 8080
CMD ["uvicorn", "src.main:app", "--host", "0.0.0.0", "--port", "8080"]