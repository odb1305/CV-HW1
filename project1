import numpy as np
from matplotlib import pyplot as plt
import pylab as lb
import cv2
import sys
import PyQt5
from PyQt5 import QtWidgets, QtGui, QtCore, Qt

class MainWindow:   
    
    def __init__(self):
        self.app = QtWidgets.QApplication(sys.argv)
        self.window = QtWidgets.QMainWindow()
        
        def histogram (img, out_name): #function calculating histograms and saving chart to png file
                    
            img = cv2.imread(img, 1)
            img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
                    
            R, G, B = cv2.split(img)
                
            plt.subplot(3, 1, 1)
            hist, bins = np.histogram(R.ravel(), 256, [0,255])
            plt.xlim([0, 255])
            plt.plot(hist, color='r')
                           
            plt.subplot(3, 1, 2)
            hist, bins = np.histogram(G.ravel(), 256, [0,255])
            plt.xlim([0, 255])
            plt.plot(hist, color='g')
                         
            plt.subplot(3, 1, 3)
            hist, bins = np.histogram(B.ravel(), 256, [0,255])
            plt.xlim([0, 255])
            plt.plot(hist, color='b')
                    
            lb.savefig(out_name)
            plt.close()
                    
            
        def eqhi (im,name): #function equalizing histogram of picture
    
            img = cv2.imread(im, 1)
            img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
    
            R, G, B = cv2.split(img)
    
            output1_R = cv2.equalizeHist(R)
            output1_G = cv2.equalizeHist(G)
            output1_B = cv2.equalizeHist(B)
    
            output1 = cv2.merge((output1_R, output1_G, output1_B))
            output1 = cv2.cvtColor(output1, cv2.COLOR_BGR2RGB)
            cv2.imwrite(name,output1)
            
        #creating paths for images and histograms    
        self.imagePath1 = "color1.png"
        self.imagePath2 = "color2.png"
        histogram(self.imagePath1, "hist1.png") #calculating hist and chart
        self.imagePath11 = "hist1.png"
        histogram(self.imagePath2, "hist2.png")
        
        self.imagePath22 = "hist2.png"
        eqhi("color1.png", "pic3.png") 
        self.imagePath3 = "pic3.png"
        histogram("pic3.png", "hist3.png")
        self.imagePath33 = "hist3.png"
        
        self.initGui()
        
        self.window.setWindowTitle("My First Python Program")
        
        self.window.setGeometry(70,70,1000,700)
        #self.window.setStyleSheet("background-color:#6e6e6e")
        
        self.window.show()
        sys.exit(self.app.exec_())
        
    #create a function to initialize the GUI
    def initGui(self):
        self.displyImage1Btn = QtWidgets.QPushButton("Open Input", self.window)
        self.displyImage1Btn.setGeometry(10,10,120,30)
        self.displyImage1Btn.setStyleSheet("background-color:#4e4e4e; color:#f7f7f7;")
        self.displyImage1Btn.clicked.connect(self.displayImage1)
    
        self.displyImage2Btn = QtWidgets.QPushButton("Open Target", self.window)
        self.displyImage2Btn.setGeometry(140,10,120,30)
        self.displyImage2Btn.setStyleSheet("background-color:#4e4e4e; color:#f7f7f7") 
        self.displyImage2Btn.clicked.connect(self.displayImage2)
        
        self.displyImage3Btn = QtWidgets.QPushButton("Equalize Histogram", self.window)
        self.displyImage3Btn.setGeometry(270,10,120,30)
        self.displyImage3Btn.setStyleSheet("background-color:#4e4e4e; color:#f7f7f7")          
        self.displyImage3Btn.clicked.connect(self.displayImage3)

        #The QLabels where images will be displayed 
        #pic 1
        self.label1 = QtWidgets.QLabel(self.window)
        self.label1.setGeometry(10,50,277,427)
        self.label1.setStyleSheet("background-color:#ffffff")
        #hist1
        self.label11 = QtWidgets.QLabel(self.window)
        self.label11.setGeometry(10,480,300,200)
        self.label11.setStyleSheet("background-color:#ffffff")        
        
        self.label2 = QtWidgets.QLabel(self.window)
        self.label2.setGeometry(337,50,277,427)
        self.label2.setStyleSheet("background-color:#ffffff")
        
        self.label22 = QtWidgets.QLabel(self.window)
        self.label22.setGeometry(337,480,300,200)
        self.label22.setStyleSheet("background-color:#ffffff")        
        
        self.label3 = QtWidgets.QLabel(self.window)
        self.label3.setGeometry(664,50,277,427)
        self.label3.setStyleSheet("background-color:#ffffff") 
        
        self.label33 = QtWidgets.QLabel(self.window)
        self.label33.setGeometry(664,480,300,200)
        self.label33.setStyleSheet("background-color:#ffffff")        
        
         
    def displayImage1(self): # display image on the label
        self.image1 = QtGui.QImage(self.imagePath1)
        self.pixmapImage1 = QtGui.QPixmap.fromImage(self.image1)
        # frame image on the label
        self.label1.setPixmap(self.pixmapImage1)
        self.label1.setScaledContents(True) 
        #histogram as above
        self.image11 = QtGui.QImage(self.imagePath11)
        self.pixmapImage11 = QtGui.QPixmap.fromImage(self.image11)
        self.label11.setPixmap(self.pixmapImage11)
        self.label11.setScaledContents(True)    
        
    def displayImage2(self):
        self.image2 = QtGui.QImage(self.imagePath2)
        self.pixmapImage2 = QtGui.QPixmap.fromImage(self.image2)
        self.label2.setPixmap(self.pixmapImage2)
        self.label2.setScaledContents(True)
        self.image22 = QtGui.QImage(self.imagePath22)
        self.pixmapImage22 = QtGui.QPixmap.fromImage(self.image22)
        self.label22.setPixmap(self.pixmapImage22)
        self.label22.setScaledContents(True)         
        
    def displayImage3(self):
        self.image3 = QtGui.QImage(self.imagePath3)
        self.pixmapImage3 = QtGui.QPixmap.fromImage(self.image3)               
        self.label3.setPixmap(self.pixmapImage3)
        self.label3.setScaledContents(True)
        self.image33 = QtGui.QImage(self.imagePath33)
        self.pixmapImage33 = QtGui.QPixmap.fromImage(self.image33)
        self.label33.setPixmap(self.pixmapImage33)
        self.label33.setScaledContents(True)         
        

main = MainWindow()
