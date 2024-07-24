# Baking and UVs Overview

<p><iframe src="https://www.youtube.com/embed/TJfHWDVjwHE?rel=0" width="800" height="450" allowfullscreen="allowfullscreen" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"></iframe></p>
<hr>
<h2>Objective</h2>
<p>In this handout, we’re going to explore the baking process a little more to understand how it is going to help us later in the texturing phase.</p>
<p><img src="https://vertexschool.instructure.com/courses/204/files/26513/preview?verifier=ZJfZLg5xkXpOx3c9ojFQNfCcYJchci2gCIMbLjAk" alt="image1.png" width="1920" height="1080" data-api-endpoint="https://vertexschool.instructure.com/api/v1/courses/204/files/26513" data-api-returntype="File"></p>
<hr>
<h2>Baked Maps in 3D Art</h2>
<h3>What is Baking?</h3>
<p>Baking is the process of extracting information from the high poly mesh and mapping it to the UV space of the low poly mesh. Through the baking process, we transfer the details from the high poly to the low poly.</p>
<p>The core map resulting from this process is the Normal Map. This very important map is what fakes lighting information to give the illusion that the low poly has more geometry than it actually does.</p>
<p>But the Normal Map is only one of the many maps that gets baked. There are several other maps generated in the process that contribute to the texturing phase.</p>
<p>&nbsp;</p>
<p><img src="https://vertexschool.instructure.com/courses/204/files/26517/preview?verifier=xhCD7HZO2pQtMPk0VotAbCX7I1mAseDrwDu5ZuQi" alt="image8.png" width="900" height="506" data-api-endpoint="https://vertexschool.instructure.com/api/v1/courses/204/files/26517" data-api-returntype="File"></p>
<p>&nbsp;</p>
<h3>The Baked Maps</h3>
<p><span>During the baking process, several maps are generated. Each one contributes to the texturing process in a different way, but they are all important for successful texturing.</span></p>
<p>&nbsp;</p>
<p><strong>Normal</strong><span> - Map that fakes lighting to show high poly details on the low poly. Responsible for making the low poly look like it has more geometry than it does.&nbsp;</span></p>
<p><span><img src="https://vertexschool.instructure.com/courses/204/files/26512/preview?verifier=a08Xh8CckYxJMQvo2ElzMrlcwN9Vlr6H7A4NwSyS" alt="image6.png" width="640" height="360" data-api-endpoint="https://vertexschool.instructure.com/api/v1/courses/204/files/26512" data-api-returntype="File"></span></p>
<p><span>&nbsp;</span></p>
<p><strong>Curvature</strong><span> - Map that defines the edges and cavities of the mesh. This is useful for generating edge highlights and controlling areas for dirt and dust.</span></p>
<p><span><img src="https://vertexschool.instructure.com/courses/204/files/26510/preview?verifier=UBr4jOA6rf7cFJfo19RoObiUd0vPcykjrWdgfpqm" alt="image7.png" width="640" height="360" data-api-endpoint="https://vertexschool.instructure.com/api/v1/courses/204/files/26510" data-api-returntype="File"></span></p>
<p>&nbsp;</p>
<p><strong>Ambient Occlusion</strong><span> - Map that defines the shadowy areas of the mesh. This map is responsible for the shadows you see in the cracks and crevices, as well as contributing to the control of dust and dirt.</span></p>
<p><strong>Position</strong><span> - Map that stores the position in 3D space as a gradient. This map is important for procedurally generating gradients in your texture work.</span></p>
<p><span><img src="https://vertexschool.instructure.com/courses/204/files/26518/preview?verifier=KGPiB2WstvoFZ0foMH2YVXawqEmgA2PsEg8m6U8b" alt="image3.png" width="640" height="360" data-api-endpoint="https://vertexschool.instructure.com/api/v1/courses/204/files/26518" data-api-returntype="File"></span></p>
<p>&nbsp;</p>
<p><strong>Thickness Map</strong><span> - Simulates the thickness of the model. This map is useful for things like SubSurface Scattering.</span></p>
<p><span><img src="https://vertexschool.instructure.com/courses/204/files/26511/preview?verifier=1697yA7o5ARdvin1UVa8XEQevF7MiEiCnmNzXbWm" alt="image2.png" width="640" height="360" data-api-endpoint="https://vertexschool.instructure.com/api/v1/courses/204/files/26511" data-api-returntype="File"></span></p>
<p>&nbsp;</p>
<p><strong>Material ID</strong><span> - Color map that masks different areas meant for different materials. Another very important map that helps organize the physical materials into groups.</span></p>
<p><span><img src="https://vertexschool.instructure.com/courses/204/files/26515/preview?verifier=1k885c9YENyA8fDB38LC0lFzG8l6x6sVoefNW6Im" alt="image4.png" width="640" height="360" data-api-endpoint="https://vertexschool.instructure.com/api/v1/courses/204/files/26515" data-api-returntype="File"></span></p>
<p>&nbsp;</p>
<h3>THEY ALL WORK TOGETHER</h3>
<p>&nbsp;</p>
<p><img src="https://vertexschool.instructure.com/courses/204/files/26516/preview?verifier=XBzbdUWhI0Uli2OK6STTx8w52ds6Kc8DH8OpCNr6" alt="image5.png" width="640" height="360" data-api-endpoint="https://vertexschool.instructure.com/api/v1/courses/204/files/26516" data-api-returntype="File"></p>
<hr>
<h2>How Does Projection Work When Baking?</h2>
<p><span>To bake texture maps, the geometry from the high poly source mesh is projected (ray traced) onto the low poly mesh. The best way to visualize this is to imagine a camera looking at the high poly and capturing the direction of the surface for every pixel in the normal map. To make sure the projection does not hit the wrong elements, a cage, or projection mesh must be set up to limit the distance of the projection. For each pixel, the angle of the camera is set by the normal direction of the cage.</span></p>
<p><img src="https://vertexschool.instructure.com/courses/204/files/26514/preview?verifier=JE15GzOjLJiIU34svA7hugmmf6jDCW90VeZbCv3l" alt="cagedisplay-1.gif" width="900" height="432" data-api-endpoint="https://vertexschool.instructure.com/api/v1/courses/204/files/26514" data-api-returntype="File">&nbsp;&nbsp;</p>