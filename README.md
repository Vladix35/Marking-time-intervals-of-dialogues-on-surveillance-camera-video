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
Диалог считается в том случае, если
- 


