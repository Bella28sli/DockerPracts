FROM ubuntu:22.04

# Устанавливаем зависимости + Xvfb + Fluxbox + VNC
RUN apt-get update && apt-get install -y \
    libgtk2.0-0 \
    libglu1-mesa \
    libxrandr2 \
    libxcursor1 \
    libxinerama1 \
    libxi6 \
    libglib2.0-0 \
    xvfb \
    x11vnc \
    fluxbox \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /game

# Копируем билд
COPY . /game

# Делаем бинарь исполняемым
RUN chmod +x ./NoEscape.x86_64

# Переменная дисплея
ENV DISPLAY=:1

# Запуск Xvfb, fluxbox, x11vnc и Unity с программным OpenGL
CMD Xvfb :1 -screen 0 1024x768x24 & \
    fluxbox & \
    x11vnc -display :1 -forever -nopw -shared -ncache 10 & \
    tail -f /dev/null
