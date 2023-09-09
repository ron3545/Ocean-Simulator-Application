
![img](https://github.com/ron3545/Ocean_Simulator/assets/86136180/fc86544d-c567-42f4-a72f-82e7a0a3e297)



The ocean simulator project described is based on Tessendorf's paper and involves several steps to generate a realistic wave simulation. First, a statistical approach is employed, utilizing random numbers called the Phillips spectrum, to calculate the amplitude and direction of each wave component. Next, Fast Fourier Transform (FFT) is applied to convert the wave components from the frequency domain to the spatial domain, resulting in a heightfield representing wave displacement on the ocean surface. The mesh representing the ocean is then updated by displacing its vertices according to the heightfield values using a displacement mapping technique. Finally, the ocean surface is rendered using OpenGL, employing shaders and textures to simulate various visual aspects such as light reflection and refraction. Overall, this project combines statistical methods, FFT, and rendering techniques to create a visually realistic ocean simulation.
