# ImageProcessing

This project is a series of assignments completed by my partner [Yinzheng Xiong](https://github.com/Mashiro-Yukino) and I when we took [CS3500: Object-Oriented Design](https://course.ccs.neu.edu/cs3500f19/) in Summer 1 Semester (May to June) in 2022 at Northeastern University. For academic integrity, we are not allowed to post code publicly. However, code is available upon request. 

# Table-of-Contents
- [Introduction](#introduction)
- [USEME](#useme)
- [Note](#note)

# Introduction 

This project is an image processing application built using the MVC design pattern. It supports interactive text-mode where a user types commands to process an image, or accepts a script file where the program would execute all the commands in it. This application also supports GUI mode built with the Java Swing library where a user can interactively load, process, save, and see the changes made to an image, while showing a histogram of the intensity, red, green, and blue values of the displayed image. 

In the GUI mode, all the operations are displayed as buttons, unlike the text-mode and script-file mode where the user needs to type every command. There is a section to display the image and a section to display the histogram. The user is able to scroll the panel. When saving an image, the application saves what the user is currently seeing. Any error will be displayed to the user through pop-up windows.

<img width="1440" alt="a-screenshot-of-our-program-with-an-image-loaded" src="https://user-images.githubusercontent.com/71456398/181701356-1f2034b6-963d-485a-96bf-e19292b2b2a8.png">

My partner and I used Model–View–Controller to separate the model from the view, and using the controller to handle the user interaction. Model, view, and controller have their own responsibilities. The model is in charged of storing images. The view is responsible for displaying information to the user. The controller is used to react to user inputs and communicate with the model and view. They are loosely-coupled so that we can easily change views and models without worrying about uncontrollable effects on each other.

# USEME 

Since our program supports text-based mode, text-files, and GUI, the user would need to choose a mode first. 

## In the command-line input, input

- `-file path-of-script-file`, the program would open the script file, execute it and shut down. The application only accepts a txt file. 
- `-text`, the program would open in an interactive text mode, allowing the user to type the script and execute it one line at a time. 
- nothing, the program would open the graphical user interface. 

## Manipulating an image

### if the user chooses text-based mode or script file mode, 
**Command must be the first input.** If the first input is invalid, the program would display the error - "X is an unrecognized command" where X is the invalid input. Command could be in whatever cases as long as it's a valid input. For the commands that require two string inputs, whichever string comes up first will be the image name and the next would be destination image name. For brightening and darkening commands, increment/decrement doesn't always have to be the second input. Our application supports partial-image-manipulation, the user is required to input mask-image-name as the last entry. The user could enter "none" if they don't want to process the image partially. 

1. To load an image: `load image-path image-name`
2. To save an image: `save image-path image-name`
3. To create a greyscale image with the red-component of the image: `red-greyscale image-name dest-image-name mask-image-name`
4. To create a greyscale image with the green-component of the image: `green-greyscale image-name dest-image-name mask-image-name`
5. To create a greyscale image with the blue-component of the image: `blue-greyscale image-name dest-image-name mask-image-name` 
6. To create a greyscale image with the value of the image: `value-greyscale image-name dest-image-name mask-image-name`
7. To create a greyscale image with the luma of the image: `luma-greyscale image-name dest-image-name mask-image-name`
8. To create a greyscale image with the intensity of the image: `intensity-greyscale image-name dest-image-name mask-image-name`
9. To flip an image horizontally: `horizontal-flip image-name dest-image-name`
10. To flip an image vertically: `vertical-flip image-name dest-image-name`
11. To brighten the image by the given increment: `brighten increment image-name dest-image-name mask-image-name`
12. To darken the image by the given decrement: `darken decrement image-name dest-image-name mask-image-name`
13. To blur an image: `blur image-name dest-image-name mask-image-name`
14. To sharpen an image: `sharpen image-name dest-image-name mask-image-name`
15. To convert an image to greyscale using luma: `greyscale image-name dest-image-name mask-image-name`
16. To convert a normal tone image to sepia tone: `sepia image-name dest-image-name mask-image-name`
17. To quit the image processor: `quit`

### if the user chooses GUI, 

Press `load` to upload an image in ppm/bmp/jpg/png format first. The image will be displayed in the top right section. The corresponding histogram of the image will be displayed in the bottom right section. Press any button to edit the image. Finally, press `save` to save the image in the ppm/bmp/jpg/png format. For more detailed user guidance, read the USEME file in this repo. 


# Note

- The GUI doesn't support partial-image manipulation. 
- This program only supports loading and saving files in ppm/bmp/jpg/png format. 



