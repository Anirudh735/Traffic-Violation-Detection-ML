detection of vehicles 

!pip install google-colab
from IPython import get_ipython
!pip install google-colab
from IPython import get_ipython
from IPython.display import display
# %%
!pip install ultralytics opencv-python numpy
# %%
from ultralytics import YOLO
import cv2
from google.colab.patches import cv2_imshow # Import cv2_imshow

model = YOLO('yolov8n.pt')
cap = cv2.VideoCapture('/content/WhatsApp Video 2025-03-27 at 7.38.59 PM (1).mp4')
# %%
while cap.isOpened():
    ret, frame = cap.read()
    if not ret:
        break
    results = model.predict(frame)
    for result in results:
        for box in result.boxes:
            x1, y1, x2, y2 = map(int, box.xyxy[0]) 
            label = model.names[int(box.cls[0])] 
            if label in ['car', 'truck', 'bus', 'motorcycle']:
                cv2.rectangle(frame, (x1, y1), (x2, y2), (0, 255, 0), 2)
                cv2.putText(frame, label, (x1, y1 - 10), cv2.FONT_HERSHEY_SIMPLEX, 0.5, (0, 255, 0), 2)
    cv2_imshow(frame) # Use cv2_imshow instead of cv2.imshow
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break
cap.release()
cv2.destroyAllWindows()

import cv2
from google.colab.patches import cv2_imshow # Import cv2_imshow

model = YOLO('yolov8n.pt')
cap = cv2.VideoCapture('/WhatsApp Video 2025-03-27 at 7.38.59 PM (1).mp4')
# %%
while cap.isOpened():
    ret, frame = cap.read()
    if not ret:
        break
    results = model.predict(frame)
    for result in results:
        for box in result.boxes:
            x1, y1, x2, y2 = map(int, box.xyxy[0]) 
            label = model.names[int(box.cls[0])] 
            if label in ['car', 'truck', 'bus', 'motorcycle']:
                cv2.rectangle(frame, (x1, y1), (x2, y2), (0, 255, 0), 2)
                cv2.putText(frame, label, (x1, y1 - 10), cv2.FONT_HERSHEY_SIMPLEX, 0.5, (0, 255, 0), 2)
    cv2_imshow(frame) 
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break
cap.release()
cv2.destroyAllWindows()
