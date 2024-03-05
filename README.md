# Solar-System-Silumation
This project was implemented as a project in the coontext of the course "Graphics I" at the Department of Informatics and Telecommunications of the National and Kapodistrian University of Athens using the following libraries:

1. **Glad**: for managing OpenGL functions
2. **GLFW**: for window creation and input handling
3. **GLM**: for mathematical operations and transformations
4. **STB**: for loading textures
5. **Assimp**: for loading scene models

A total of 5 classes were implemented:

1. **SunModel**: for representing the Sun
2. **EarthModel**: for representing the Earth
3. **MoonModel**: for representing the Moon
4. **PlanetModel**: for representing planets and stars in random positions
5. **Camera**: for managing camera movement on the x and y axes

All model classes implement the functions `loadModel()`, `processMesh()`, `setupBuffers()`, `setupMatrices()`, `compileShaders()`, `loadTexture()`, and `render()`, whose functionalities are described below:

- **loadModel()**: Using an Assimp Importer, loads the appropriate object file, then, after finding the file's mesh, calls the `processMesh()` function, and finally the `setupBuffers()` function.
- **processMesh()**: Given a mesh, this function sequentially stores the coordinates of each point, texture coordinates, normals, and the total number of edges, which is necessary for the subsequent execution of the `render()` function.
- **setupBuffers()**: This function creates a VBO for transferring model data to the GPU and finally sets how this data should be interpreted by the GPU using the `glVertexAttribPointer()` function.
- **setupMatrices()**: This function places the model in the appropriate initial positions and modifies its initial size.
- **compileShaders()**: This function creates a vertex and fragment shader for each model, and then links them to create the model's pipeline.
- **loadTexture()**: This function loads the appropriate texture for each model and specifies how it should be wrapped on the model.
- **render()**: This function is called to render a model on the screen.

The main functions of the camera class are `processKeyboardInput()` and `updateCameraVectors()`, whose functionalities are described below:

- **processKeyboardInput()**: This function reads user input from the keyboard and calculates the appropriate angle for camera rotation.
- **updateCameraVectors()**: This function rotates the camera at the angle calculated in the previous step by `processKeyboardInput()`.

## Scene Design

1. At the center of the scene is the Sun, which remains stationary.
2. The Earth rotates around itself and around the Sun.
3. The Moon rotates around the Earth.
4. Planets and stars are initialized with random sizes and positions around the solar system, as well as random textures taken from the additional textures in the Earth's directory. The stars remain stationary.

## Main Program Operation

1. Initially, GLFW and GLAD are initialized, and the main application window is created.
2. Then, the models of the Sun, Earth, Moon, and planets are loaded.
3. Next, within the main loop, the models are rendered.
4. Pausing and resuming the movement of scene models is done with the SPACE key.
5. For rotating the camera on the x-axis, the left or right arrow keys are used for left or right rotation, respectively. For rotating the camera on the y-axis, the up and down arrow keys are used for upward or downward rotation, respectively.
6. If the user presses the ESC button, the program flow exits from the render loop, resources are released, and the program terminates.
