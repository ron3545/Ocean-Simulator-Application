# OCEAN SIMULATOR
![Capture](https://github.com/ron3545/Ocean_Simulator/assets/86136180/497930a2-295c-4575-a38f-141f9cc94621)

https://github.com/ron3545/Ocean_Simulator/assets/86136180/ba420826-2e95-4b7e-acdc-1358726c4923


#### Introduction
The ocean simulator project described herein is a comprehensive implementation based on the groundbreaking work of Jerry Tessendorf. The primary goal is to generate a visually realistic wave simulation that accurately mimics the dynamic behavior of ocean surfaces. This documentation provides an overview of the key steps involved in the project, highlighting the techniques employed and the underlying principles.

#### Wave Generation
The foundation of the simulation lies in the statistical approach to wave generation. The Phillips spectrum, utilizing random numbers, is employed to calculate the amplitude and direction of each wave component. This statistical method is crucial for generating a diverse and realistic range of wave patterns, capturing the complexity of natural ocean surfaces.

#### Frequency Domain to Spatial Domain Conversion
To translate the wave components from the frequency domain to the spatial domain, the Fast Fourier Transform (FFT) is applied. This step is pivotal in obtaining a heightfield that accurately represents the displacement of waves on the ocean surface. The FFT allows for an efficient and realistic conversion, ensuring that the spatial representation captures the intricate details of wave interactions.

#### Mesh Displacement
The mesh representing the ocean is dynamically updated based on the calculated heightfield values. A displacement mapping technique is employed to alter the vertices of the mesh, accurately reflecting the wave patterns present in the heightfield. This step ensures that the physical representation of the ocean surface aligns with the calculated wave dynamics, providing a realistic visual output.

#### Rendering with OpenGL
The final stage involves rendering the ocean surface using OpenGL. Shaders and textures are utilized to simulate various visual aspects, including light reflection and refraction. These techniques enhance the realism of the simulation, making it visually compelling and immersive for the observer.

#### Problem Addressed
Prior to the implementation of this ocean simulation project, creating realistic and dynamic ocean surfaces in computer graphics posed significant challenges. Traditional methods often fell short in capturing the complexity and diversity of natural wave patterns. Tessendorf's approach, as implemented in this project, addresses this problem by combining statistical methods, FFT, and rendering techniques to produce a visually accurate and captivating ocean simulation.

#### Benefits of the Project
- Visual Realism: The project achieves a high level of visual realism by accurately simulating the dynamic behavior of ocean waves, making it suitable for applications such as gaming, virtual reality, and simulation environments.

- Versatility: The statistical approach and FFT-based frequency to spatial domain conversion allow for a wide range of wave patterns, making the simulation adaptable to different oceanic conditions and scenarios.

- Educational Value: The project serves as an educational resource by demonstrating the application of statistical methods, FFT, and rendering techniques in creating realistic simulations, helping students and enthusiasts understand the intricacies of computer graphics and oceanography.

- Scientific Exploration: The realistic representation of ocean surfaces provides a valuable tool for scientific exploration and analysis, allowing researchers to study wave dynamics and their impact on various phenomena.

