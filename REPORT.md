# **Immersive Data Visualizations with Foodiverse**

Joyce Zhang, Matthew Komar

Human-Computer Interaction Institute and College of Fine Arts

Carnegie Mellon University

5000 Forbes Avenue, Pittsburgh, PA, 15213, USA

Introduction
##

The world of data visualization is reaching a new milestone. As reality devices become more popular and untethered, mediums for data storytelling are expanding into the virtual world. In our project, Foodiverse, we intend to explore what it means to create compelling and effective visualizations in VR. In Foodiverse, we want to visualize the relationship between food ingredients and their associated flavors in VR. On top of that, we also tried to answer questions such as: How can we visualize a data set in Virtual Reality without making it look confusing? Which methods can we employ to interact with facets in the data set?

While contemporary VR visualizations use small 3D table-sized visualizations, our technique differs in that we see the data as the environment.  Foodiverse was built with the Shneiderman Mantra: &quot;Overview first, Zoom and Filter, and details on demand&quot;. Users can manipulate the chart physically, by scaling the axis horizontally and vertically. Additionally, they are able to filter the data by food type and select data points to gain more information about them. They can also toggle an average axis view, which visualizes the average point values in an axis using a sphere. Each technique has its own strength, but we believe by giving the user the right tools, our method may overcome the existing problems in VR data visualization.

Related Work

For our work, we referenced existing guidelines on constructing Data Visualization in VR and found interesting ways to represent data in 3D. In Ana Becker&#39;s talk &quot;Designing Virtual Reality Data Visualizations&quot; at OPENVIS 2016, she proposed that the strength of VR is its ability to visualize multidimensional data, and &quot;trick your brain into thinking you&#39;re in an environment&quot;. At the same time, VR data visualization faces many roadblocks. For example, as Becker proposed, the information density presented in VR has to be &quot;kind of low&quot; because &quot;it&#39;s hard to read in VR&quot;. When presenting 3D data in VR, visualizations also have to overcome perception difficulties, as humans are not good at processing three-dimensional information.

In another research, &quot;Touch and Beyond: Comparing Physical and Virtual Reality Visualizations&quot; presented by Kurtis Danyluk and his team at IEE VIS 2021, they proposed solutions to lessen perception difficulties in VR. Danyluk gave participants virtual 3D graphs and physical graphs. The only difference is that virtual graphs were able to be filtered and annotated. It was found that participants had higher engagement and understanding of the data when using the virtual graph. We adopted similar techniques in our project, presenting virtual tools in hope to compensate for the loss of physicality.

Lastly, although not directly related to VR, a paper that inspired the design of our data visualization is &quot;Rotate or Wrap? Interactive Visualizations of Cyclical Data on Cylindrical or Toroidal Topologies&quot; by Kun-Ting Chen. In this paper, Chen presented cyclic topologies and 2D projection of 3D data. He showed that data that are unordered or cyclic in nature should adopt a cyclic data representation, which inspired the cylindrical design of our parallel coordinate system.

Methods

Data representation

We used the dataset from Foodb, one of the largest public datasets on food chemical compounds and flavor compositions. This data contains more than 790 food entries and over 70000 components that are found in foods. Each food comes with a unique ID and belongs in a food group (Vegetables, Herbs, Baby Food, etc), and the amount of each component is found in the food. Components are chemicals that are associated with either a nutrient or a flavor profile.

Our target data is a mapping between food ingredients and their flavor profile, represented by a percentage decomposition of each flavor. This seemingly simple mapping was made more difficult by the hidden problems in the data. Not all components contributed to the flavor, and not all were in the same unit; ingredient identifiers were inconsistent, and there was a lot of missing information. We chose to omit the problematic entries in our final dataset.

After the mapping, we face another problem of categorization. We wanted to have two means to filter through the data: flavors (the axis of the parallel coordinate system), and food groups (the panel on the user&#39;s wrist). With the final 636 foods entries, there were 38 unique flavors found, and 24 food groups found. Both groups were too large to be made into effective VR data visualizations, and we had to manually merge and recategorize them. The final data contained 9 food groups: Beverages, Dairy &amp; fat, Fruits, Grains, Processed Foods, Protein, Spices, Vegetables, and Others; and the flavor compounds into 9 categories: Sweet, Floral, Fruity, Green, Animal, Smokey, Wine-like, Chemical, and Milky.

Finally, we had another data table that contained a short description of each food, url for an image, and detailed information on its components. We use this dataset to look up data when the user demands more information on data points.

Interaction design

While developing interactions in VR, we worked with Schneiderman&#39;s Mantra in mind: Overview first, Zoom and Filter, and details on demand.

To visualize the relationship between food and flavor profiles, we opted to create a cylindrical parallel coordinate system. Each axis of this parallel coordinate corresponds to one of the flavor groups. Using a cylindrical structure helps direct the user&#39;s attention, as they have a natural tendency to look around. Although projected onto a 3D shape, the parallel coordinate graph still retains its readability as a 2D graph and avoids the problems that come with 3D data points.

The user can scale the axis vertically and horizontally to zoom. Scaling on one horizon each, lets the user focus on data of one axis. Zooming in eliminates the distraction of the rest of the graph. This lets the user to filter spatially and concentrate on their area of interest.

Having the environment be a data visualization allows users to physically walk between areas of interest when the cylinder is scaled to match their room. If we had the parallel coordinates projected onto a sheet, the user would have to use teleportation to look at different parts of the graph and may easily lose track of data. Whereas, in a cylindrical layout, the user can easily learn the spatial layout of the axes. Also, turning around is just easier to do in VR than moving.

We have also created a filter tool to isolate specific food groups. By tapping the filter tool icon on their wrist, a user can open a menu asking them which food groups they would like to view. This makes it easier to view the relationship between food groups and their flavor distributions.

Finally, the user can go up to any given point and select it, which causes a display to appear with a description of the food taken from the foodb dataset.

Accessibility

Even with all the tools we&#39;ve given to the user, the data could still look visually intimidating. We tried to alleviate the visual strain by giving each genre of food a unique color. We have two forms of visualizations: line and sphere. Line visualization intends to show the relationship and trend within the data. Sphere visualization takes the axis average and displays it in the form of a sphere to remove visual clutter, thus making reading data faster. We were also careful to make the data displayed correspond to the diameter of the spheres instead of its volume, as we learned in class humans are better at comparing and estimating area instead of volumes.

We wanted to add color blind friendly palettes to add colorblind support, unfortunately we did not have enough time to do it. Having our project in VR also comes with sacrifices in accessibility, as movement in VR may induce visual discomfort or nausea -- a lot of which is caused by disorientating visuals and low framerate. We have tried to overcome these by optimizing our algorithm to keep the frame rate high and limit moving parts of the visualization to avoid feelings of false movement. Both points are discussed in the algorithm section of the Discussion.

Discussion

- What has the audience learned from your work? What new insights or practices has your system enabled? Informal observations of use (how did people use this system) that help evaluate your system are encouraged.(what worked and what didn&#39;t)

Insights

One of the insights we gained while working on this project is to use the right medium to visualize the right data. VR&#39;s strength for visualization is its ability to represent spatial data well. Theoretically, it&#39;s much better to visualize data that is inherently spatial -- such as the track of a player during a tennis match, unlike our numerical data.

We proposed two questions in the Introduction: How can we visualize a data set in Virtual Reality without making it look confusing and which methods can we employ to interact with facets in the data set? To increase visual clarity, one should choose to adopt a data representation that either a.) is highly spatial in its nature (maps, trajectories, movement predictions, etc), or b.) adapt visualization forms that are more akin to 2D representations than 3D (avoid using depth to represent data). We believe data in VR should be treated as the environment the user can immerse themselves in, instead of an object picked up to be inspected upon. This way, we&#39;re able to take full advantage of the immersive nature of VR and always direct user attention to the data itself.

In this project, we proved that the Shneiderman Mantra, &quot;Overview first, Zoom and Filter, and details on demand&quot;, still stands in VR. The interactions we built which allowed for zoom, filter, and inspection of individual points gave great user agency when exploring the data.

Doing the visualization in Virtual Reality forced us to build our own tools as there weren&#39;t any existing ones that we could find for Unreal Engine. This forced us to develop an efficient and scalable algorithm to visualize thousands of points in 3D space.

The algorithm goes as follows. In the constructor:

- Axis data gets initialized via a dictionary which maps axis names to data tables containing axis contents.
- Axis spawn location was pre-calculated using trigonometry to project the axis in the shape of a cylinder.
- Parsed a premade data table containing only Food IDs which were used to index into an array of Food Items to make look up O(1).

When the application runs:

- Spawn Axis which then spawns its Points and saves them as references to variable Point Coords.
- Go through each Point Coord and apply vertical/horizontal scaling and connect the line to each Food ID.

During any kind of event manipulation, the parallel coordinate system has to be refreshed.

On Refresh (e.g. filter added or scaled):

- Clears all lines.
- Goes through each Point Coord and applies vertical/horizontal scaling and connects the line to each Food ID. Ignores filtered out points (if possible).

Unreal Engine&#39;s built-in line function was originally used as a placeholder for a prettier looking particle system. When the particle system was implemented, we had significant performance drops regardless of how simple the particle system was. Lines are more performant because they directly draw onto the graphics buffer.

As each axis owns a localized copy of its data points, we needed to pay special attention as to how we visualized it. Representing points using 3D objects wasn&#39;t performant, so the best approach was to use sprites as they were cheaper to render.

## Future Works

More agency to filter the Data

- With our current set of tools, we&#39;re able to filter by categories. It is, however, difficult to pinpoint individual data points on the graph. In the future, we hope to add in some system to let the user search for individual ingredients, preferably via voice input. Additionally, tools that allow the user to take notes and annotate the data would also improve this experience.

Increasing Accessibility

- Currently, Foodiverse&#39;s VR form is only viewable on Oculus platforms. In the future, we hope to deploy this project on mobile VR, which makes it more accessible. This brings other challenges; for example. our current interaction system is reliant on the user having controllers. Moving to mobile calls for a redesign of all current interactions.
- There are other measures that could be taken to accommodate the motion sickness experienced in VR from the design perceptive. One example is to hide all visualized lines when the user is zooming and moving. This would negate the sense of false movement in space and potentially decrease nausea.

## Citations

Becker, A. A. (2016). Designing Virtual Reality Data Visualizations. _OPENVIS_ .

Chen, K.-T., Dwyer, T., Bach, B., &amp; Marriott, K. (2021). Rotate or wrap? interactive visualisations of cyclical data on cylindrical or toroidal topologies. _IEEE Transactions on Visualization and Computer Graphics_, 1–1. https://doi.org/10.1109/tvcg.2021.3114693

K. Danyluk, T. T. Ulusoy, W. Wei and W. Willett, &quot;Touch and Beyond:Comparing Physical and Virtual Reality Visualizations,&quot; in IEEE Transactions on Visualization and Computer Graphics, doi: 10.1109/TVCG.2020.3023336.

Shneiderman, B. (n.d.). The eyes have it: A task by data type taxonomy for information visualizations. _Proceedings 1996 IEEE Symposium on Visual Languages_. https://doi.org/10.1109/vl.1996.545307