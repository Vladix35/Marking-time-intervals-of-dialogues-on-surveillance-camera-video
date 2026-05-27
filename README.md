# Marking-time-intervals-of-dialogues-on-surveillance-camera-video

## Датасет используемый для разметки: https://www.kaggle.com/datasets/abdelrhmannile/wisenet
Видео из датасета были перекодированы из avi в MP$ с H264 (AVC) + AAC и 25 frame rate, чтобы label-studio принял данные видео для разметки

Ссылка на папку: https://drive.google.com/drive/folders/1XqDHDF8zZ1dFKPb7o_5jD8CxgH_CnN-_?usp=drive_link

## Подготовка label-studio для разметки:
### 1. Запуск ngrok для поключение модели к label-studio:
```
ngrok http 9090
```
### 2. Запуск модели [yolov8n-cls.pt](https://github.com/Vladix35/Marking-time-intervals-of-dialogues-on-surveillance-camera-video/blob/main/yolov8n-cls.pt):
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

## Получившейся после экспорта json файл: [project-1-at-2026-05-27-14-53-7e92f5d7.json](https://github.com/Vladix35/Marking-time-intervals-of-dialogues-on-surveillance-camera-video/blob/main/project-1-at-2026-05-27-14-53-7e92f5d7.json)

## XML файл используемый в Labeling Interface
```
<View>
  <Video name="video" value="$video" frameRate="25.0" timelineHeight="120"/>
  <TimelineLabels name="videoLabels" toName="video"
    model_trainable="true"
    model_classifier_epochs="1000"
    model_classifier_sequence_size="16"
    model_classifier_hidden_size="32"
    model_classifier_num_layers="1"
    model_classifier_f1_threshold="0.95"
    model_classifier_accuracy_threshold="0.99"
    model_score_threshold="0.5">
    <Label value="Dialogue" background="#44d80e"/>
    <Label value="No dialogue" background="#D4380D"/>
  </TimelineLabels>
</View>
```

## BCg


