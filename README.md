<p align="Left">
  <img width=150 src="VCamLogo.png">
</p>

# VirtualCam

Виртуальная камера создается **только с использованием OpenCV и numpy**. Он имитирует камеру, где ** мы можем контролировать ** все ее параметры ** внутренние и внешние **, чтобы лучше понять, как каждый компонент в **матрице проекции камеры** влияет на окончательное изображение объекта, захваченного камерой. Его можно использовать для понимания концепций формирования изображения и понимания внутренних и внешних параметров камеры. Также предоставляется интерактивный графический интерфейс, имитирующий виртуальную камеру и самолет в трехмерном мире. Изменяя внешние параметры камеры (вращение и перемещение), вы можете имитировать изменение формируемого изображения.
8Взаимодействие с другими людьми
9
Были сделаны ссылки на стандартные книги, связанные с многовидовой геометрией и компьютерным зрением, чтобы гарантировать достоверность уравнений в коде.
10
Я также сослался на этот [блог от Learnopencv.com] (https://www.learnopencv.com/geometry-of-image-formation/), чтобы понять геометрию формирования изображения.Возможность пройти курс CS763: Computer Vision Spring 2020 в IIT Bombay также помогла мне прояснить мои фундаментальные концепции, связанные с геометрией формирования изображения и матрицей проекции камеры.

#### An interesting application of this library can be seen in [FunMirrors project](https://github.com/kaustubh-sadekar/FunMirrors/blob/master/README.md)

[Link to the post about FunMirrors](https://www.learnopencv.com/funny-mirrors-using-opencv/)

## Instructions to run the GUI

1. Install the virtual camera library using the following command
```shell
pip3 install vcam
```
2. Clone the repositoy
`git clone https://github.com/kaustubh-sadekar/VirtualCam.git`
3. Run the GUI using the following command
`python3 GUI.py`

### Camera Translation
![Camera-Translation](xyz.gif)

When you control the X, Y, Z trackerbars you are basically controlling the position of camera in the 3D world. The plane remains fixed and thus we can observe shifting of the plane as we move the camera. You can also objserve the changes in the last column of the camera projection matrix being prined in the right terminal.


### Camera Rotation
![Camera-Rotation](rot.gif)

When you control the alpha, beta, gamma trackbars you are controlling the rotations of camera in 3D world. This gives turning effect to the image.

### Camera Distortion Coefficients
![Camera-Rotation](distCoeff.gif)

When you control the k and p trackbars you are controlling the distortion coefficients. The computations performed in numpy also take into account the equation for lens distortions for a pin hole camera.

### Camera apparent pixel size and focal lenght
![Camera-apparent-pixel-size-and-focus](intrinsic.gif)

When you control the sx and sy trackbars the apparent pixel size in x and y direction changes. As Sx increases the apparent pixel width increases making the image stretch horizontally and similarly Sy increases the apparent pixel height, making the image stretch vertically. 

Basically the plane is a mesh of 3D points. We compute the camera projection matrix and thus the image coordinates corresponding to these 3D points. The projected points and the original mesh points are used to compute a map and finally a remapping function is applied on the image.

`python3 GUI.py`

## Code files
`GUI.py` is the file for GUI to play with camera parameters.
