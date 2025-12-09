#--- Base python ---
FROM python:3.9-slim-bullseye as base

ENV PYTHONUNBUFFERED 1
ENV PYTHONDONTWRITEBYTECODE 1

# [NEW] Silence the root warning
ENV PIP_ROOT_USER_ACTION=ignore 

# Create app directory
WORKDIR /src
COPY requirements.txt .

# [NEW] Update pip to the latest version before installing requirements
RUN pip install --upgrade pip

RUN pip install --no-cache-dir -r requirements.txt

# --- Copy Files/Build ---
FROM base

WORKDIR /src

COPY . /src

# (You can remove the chmod line if you want, but it's fine to keep)
RUN chmod -R 777 /src

# Start the application on port 8080
CMD ["python", "manage.py", "runserver", "0.0.0.0:8080"]