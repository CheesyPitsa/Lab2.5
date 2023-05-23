# Лабораторная работа 5
## Развертка нейронной сети, детектирующей объекты на видео

Обработка видео покадрово с помощью импортированной модели:
```python
for i, frame in enumerate(frames):
    print('\rTracking frame: {}'.format(i + 1), end='')
    boxes, _  = mtcnn.detect(frame)
    frame_draw = frame.copy()
    draw = ImageDraw.Draw(frame_draw)
    for box in boxes:
        draw.rectangle(box.tolist(), outline=(255, 0, 0), width=6)
    frames_tracked.append(frame_draw.resize((640, 360), Image.BILINEAR))
```

Отображение результата:
```python
d = display.display(frames_tracked[0], display_id=True)
i = 1
try:
    while True:
        d.update(frames_tracked[i % len(frames_tracked)])
        i += 1
except KeyboardInterrupt:
    pass
```
![image](https://github.com/CheesyPitsa/Lab2.5/assets/113666100/b2c1aadd-7552-4f7d-ba84-fe2614e98052)
