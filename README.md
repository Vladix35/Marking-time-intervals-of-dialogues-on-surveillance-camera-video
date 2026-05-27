# Marking-time-intervals-of-dialogues-on-surveillance-camera-video

## Датасет используемый для разметки: https://www.kaggle.com/datasets/abdelrhmannile/wisenet
Видео из датасета были перекодированы из avi в MP$ с H264 (AVC) + AAC и 25 frame rate, чтобы label-studio принял данные видео для разметки

## Подготовка label-studio для разметки:
### 1. Запуск ngrok для поключение модели к label-studio:
```
ngrok http 9090
```
### 2. Запуск модели yolov8n-cls.pt:
```
git clone https://github.com/HumanSignal/label-studio-ml-backend.git
cd label-studio-ml-backend/label_studio_ml/examples/yolo
docker compose up --build
```
### 3. Подключение модели в label-studio через этот URL: https://overload-drown-baton.ngrok-free.dev

## Инструкциия для разметчиков:
Цель разметки: классификация кадров диалога или его отсутствия на видео

Технические требования:

Разметка - классами: Dialogue - диалог, No dialogue - отсутствие диалога

Диалог считается в том случае, если выполнены данные условия:

- смотрят друг на друга два и более людей;

- стоят на расстояние максимум 2 метра друг от друга.
<img width="1203" height="759" alt="image" src="https://github.com/user-attachments/assets/32c2c176-afb9-4012-ad7d-f1ab96261f3b" />


В противном случае, отсуствие диалога.
<img width="1203" height="759" alt="image" src="https://github.com/user-attachments/assets/8ff16956-bfb3-4783-84f4-138c0953aaf3" />

Допустимо задание 3-5 кадров Dialogue при частичном обороте от собеседника после приличной по количеству кадров беседы, а все остальные - No dialogue.



