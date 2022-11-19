#### Detect 



import cv2 
import urllib.request
cap = cv2.VideoCapture('http://192.168.1.156:40872/videostream.cgi?user=admin&pwd=888888')
urlup = 'http://192.168.1.156:40872/decoder_control.cgi?loginuse=admin&loginpas=888888&command=0&onestep=0&16665949541060.5488437026730646&_=1666594954106'
urldown ='http://192.168.1.156:40872/decoder_control.cgi?loginuse=admin&loginpas=888888&command=2&onestep=0&16665953768060.9578758702565133&_=1666595376807'
urlleft = 'http://192.168.1.156:40872/decoder_control.cgi?loginuse=admin&loginpas=888888&command=4&onestep=0&16665954389540.8104276785346785&_=1666595438954'
urlright = ' http://192.168.1.156:40872/decoder_control.cgi?loginuse=admin&loginpas=888888&command=6&onestep=0&16665954793680.14226293471168838&_=1666595479368'
urlstop = 'http://192.168.1.156:40872/decoder_control.cgi?loginuse=admin&loginpas=888888&command=5&onestep=0&16665950820350.04820711562524305&_=1666595082035'
face_detector = cv2.CascadeClassifier(cv2.data.haarcascades +"haarcascade_frontalface_default.xml")
while True:
   check,frame = cap.read()   
   gray = cv2.cvtColor(frame,cv2.COLOR_BGR2GRAY)
   faces = face_detector.detectMultiScale(gray,1.3,5)
   for (x,y,w,h) in faces:
       
       cv2.rectangle(frame,(x,y),(x+w,y+h),(102,255,178),2)
   cv2.imshow("CCTVCap",frame)

   key = cv2.waitKey(1) & 0xFF   
   if key == ord('w'):
      urllib.request.urlopen(urlup)
   if key == ord('s'):
      urllib.request.urlopen(urldown)
   if key == ord('a'):
      urllib.request.urlopen(urlleft) 
   if key == ord('d'):
      urllib.request.urlopen(urlright)
   if key == ord('r'):
      urllib.request.urlopen(urlstop)
      

*** ต้องค่อยเปลี่ยน port ทุกครั้งหลังเปิดใช้งาน ***

===================================
