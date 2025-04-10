# Spatial-temporal-forest-fire-Dataset-of-Forest-land-in-China 中国林地时空森林火灾数据集

介绍：

该数据集为北京林业大学冯仲科科研团队处理。仅共享其他数据。

数据集中主要属性为：

1.day-of-year；代表燃烧开始的该火烧斑块起始燃烧时间处于该年度的第几天

2.start-data：燃烧的起始时间

3.over-time；燃烧的结束时间

4.lon：燃烧中心的经度

5.lat：燃烧中心的纬度

6.foresttype：燃烧林地中的林地类型(14：Bamboo and economic forest;111：Evergreen needleleaf forest;112：Deciduous needleleaf forest;121：Evergreen broadleaf forest;122：Deciduous broadleaf forest)

本数据集基于NASA的MCD64A1火烧迹地产品，通过与中国土地利用数据的空间叠加分析，提取中国林地范围内的历史火灾信息，并保留燃烧时间、面积及置信度等关键属性。数据交集处理旨在排除草原、农田等非林火干扰，精准反映森林生态系统火灾分布；而时间信息的保留则支持火灾季节规律分析、气候变化关联研究、林火蔓延速度研究及火后生态恢复监测。该数据集适用于林火风险评估、碳排放测算及防火政策优化等应用，具有重要的林业管理参考意义与时空分析价值。

一、基础数据源 ——MCD64A1 火烧迹地数据集​

数据内容：MCD64A1 火烧迹地数据集呈现了全球月度火烧迹地的详尽分布格局。其中，燃烧日期（Burn Date）精准记录火灾发生的时间节点，为剖析火灾季节性规律以及回溯火灾事件的发展进程提供了关键时间维度数据支撑，对揭示火灾发生的时间模式具有不可或缺的作用。燃烧面积（Burn Area）通过量化每次火灾的波及范围，为评估火灾规模及其生态与社会经济影响程度提供了核心量化指标。置信度（Confidence Level）则表征数据的可靠性，为使用者在数据应用过程中进行精度评估与不确定性分析提供依据，助力其合理判断数据的可用性与适用性。​

分辨率：该数据集具备 500m 的空间分辨率，在一定程度上能够较为清晰地展现火灾发生区域的空间分布特征，为空间尺度上的火灾分析提供了基础空间精度保障。同时，其 1 个月的时间分辨率使得可按月度时间尺度对全球火烧迹地进行系统监测与动态分析，能够有效捕捉火灾发生的时序变化规律，为时间序列分析奠定了时间精度基础。​

来源：此数据集是 NASA MODIS 卫星（Terra/Aqua）与波士顿大学协同研发的成果。借助 MODIS 卫星先进的对地观测遥感技术，可获取大面积、多光谱的地表信息，结合波士顿大学在遥感应用、火灾监测等领域的专业研究能力与深厚学术积淀，经过数据处理、算法优化等一系列复杂流程，生成了这一在全球火烧迹地监测研究领域具有重要价值的数据集。​

时间范围：自 2001 年起至今，该数据集处于持续更新状态。长期且连续的数据记录为科研人员、林业管理部门等相关主体提供了丰富的历史数据资源，便于开展长时间序列的深入分析，通过对不同时间尺度下火灾数据的挖掘，揭示火灾发生的长期趋势、周期性变化以及演变规律，为森林火灾相关的科学研究与管理决策提供了时间跨度长、数据连续性好的基础数据保障。​

算法原理：其采用基于热异常点（MODIS Active Fire）与地表反射率变化（ΔNBR 指数）的混合燃烧检测算法。热异常点探测基于 MODIS 传感器对地表热辐射的监测，能够快速识别可能存在火灾的区域，具有较高的时效性。地表反射率变化（ΔNBR 指数）则通过对比火灾前后地表植被在近红外与短波红外波段反射率的差异，利用植被在火烧前后的光谱特征变化来精确界定火烧迹地的范围。两者有机结合，充分发挥了热异常探测的及时性与光谱特征分析的优势，显著提高了火烧迹地检测的准确性与可靠性。​

局限性：一方面，原始数据全域覆盖地表，这意味着其中包含大量非林地（如草原、农田）的火灾信息。这些非林地火灾数据对于专注于林地火灾研究与分析的工作而言，属于干扰信息，会影响对林地火灾特征、规律及影响的准确认知，增加数据处理与分析的复杂性，需采用适当的数据筛选与过滤方法加以排除。另一方面，modis的分辨率在面对小规模林火时存在固有局限性，例如对于面积小于 25 公顷的火场，由于分辨率相对较低，难以有效识别和区分，可能导致部分小规模火灾信息遗漏，在一定程度上影响对火灾总体情况的全面掌握。​

二、与中国土地利用数据交集的目的​

核心逻辑：通过空间掩膜（Masking）这一关键技术手段实现林地火灾的精准提取。空间掩膜技术基于地理信息系统（GIS）原理，通过构建与林地空间分布相对应的掩膜图层，对原始火灾数据进行空间筛选，从复杂的全域火灾数据中精准提取出林地范围内的火灾信息，实现目标数据的分离与提纯，提高林地火灾数据的针对性与准确性。​

步骤：​

首先，运用地理空间分析方法将 MCD64A1 数据集裁剪至中国国界范围。鉴于中国地域广袤，而研究重点聚焦国内林地火灾，对全球范围的原始数据进行国界范围内的裁剪，能够有效降低数据冗余度，减少不必要的数据存储与处理量，提升数据处理效率，同时突出研究区域，使后续分析更具针对性。​

接着，利用中国土地利用数据中的林地分类图层生成空间掩膜。这些土地利用数据集运用先进的遥感解译与地理信息分类技术，对不同土地利用类型进行了详细划分，其中的林地分类图层清晰界定了林地的空间范围，为构建空间掩膜提供了基础数据。基于该图层生成的空间掩膜，能够识别出哪些区域属于林地范畴。​

然后，对 MCD64A1 进行逐像元交集运算。在该运算过程中，依据空间掩膜所确定的林地范围，仅保留与林地像元重叠的火灾像元，将其他非林地的火灾像元予以剔除，从而实现林地火灾信息的精准提取，得到仅包含林地范围内火灾情况的数据集。​

最后，对于交集结果进行处理，通过代码和目视解译的方式将交集数据进行处理，通过时间信息和空间信息将火灾整体范围确定，最后形成带有时间信息的火烧基地数据。

科学意义：​

去除非目标干扰：草原火与林地火灾在生态系统属性上存在显著差异。草原植被以草本植物为主，生态系统结构相对简单，其火灾发生机制、燃烧特性及生态影响与以木本植物为主的林地火灾截然不同。农田秸秆焚烧则主要由人为农事活动引发，属于人为干扰因素，其火灾特征与林地自然火灾差异明显。通过与土地利用数据进行交集运算，能够有效排除这些非林业相关火灾数据，使研究能够聚焦于林地火灾的固有特性与内在规律，提高研究结果的准确性与科学性。​

支撑林业管理：聚焦森林生态系统火灾风险评估，与《森林法》中林地管理边界相契合。准确的林地火灾数据能够为林业管理部门提供关键信息，助其深入了解森林生态系统所面临的火灾风险状况，包括不同区域、不同时段的火灾发生概率与潜在影响程度，从而依据科学数据制定更具针对性、更高效的林地管理措施，有效保障森林资源的生态安全与可持续发展。​

提升分析精度：在相同分辨率条件下，林地边界掩膜能够有效减少混合像元误差。例如在森林 - 草地过渡带，由于两种土地类型相邻，在低分辨率数据中，单个像元可能同时包含森林与草地的光谱信息，导致对火灾发生区域的误判。而通过精确的林地边界掩膜，能够明确区分像元所属的土地类型，准确判断火灾是否发生在林地范围内，显著提高火灾分析在空间尺度上的精度，为后续的火灾影响评估、风险预测等工作提供更可靠的数据基础。

三、时间信息的核心价值​

数据维度扩展：将单纯基于空间维度的火灾分布数据升级为时空立方体（Space - Time Cube）结构。时间信息的引入，为原本二维的空间数据增添了时间维度，使数据从静态的空间格局描述转变为动态的时空演变记录，拓展了数据的表达能力与分析维度，为开展多维度、深层次的火灾相关研究提供了更丰富的数据基础与分析视角。在林火蔓延研究中，时空立方体结构能够展现林火在不同时刻于空间中的位置与蔓延情况，方便研究人员分析其随时间的动态变化过程。​

关键用途：​火灾季节规律分析：借助时间信息，能够识别中国不同林区的火灾高发月份。不同林区因地理位置、气候条件、植被类型及生态系统结构等因素的差异，火灾发生的季节规律呈现出明显的地域分异特征。通过深入了解这些火灾季节规律，对于林业部门提前制定针对性的防火预案、合理调配防火资源、开展有效的火灾预防工作具有重要指导意义。在林火蔓延层面，不同季节的气候条件显著影响林火蔓延速度与方向，掌握这些规律有助于更准确地预测林火蔓延趋势。​

气候变化关联：结合气象时序数据（如 CRU TS 数据集），可量化干旱指数与林火频率的滞后相关性。气候变化对林火发生具有深刻影响，干旱作为重要的气候驱动因素，与林火发生密切相关。通过对时间序列上干旱指数与林火频率的相关性分析，能够揭示气候变化背景下干旱事件对林火发生的影响机制与时间滞后效应，为预测未来气候变化情景下林火发生趋势提供科学依据，有助于制定前瞻性的森林火灾防控与适应策略。林火蔓延也深受气候变化影响，干旱条件下，林地植被干燥，林火一旦发生，蔓延速度加快，范围更广，分析这种关联对预测林火蔓延态势在气候变化下的演变至关重要。​

火后恢复监测：通过燃烧日期标记，能够跟踪火烧迹地归一化植被指数（NDVI）在 1 - 5 年内的植被恢复轨迹。火灾发生后，植被的恢复是一个复杂的生态演替过程，受火灾强度、土壤条件、气候因素及植被自身特性等多种因素影响。借助时间信息，可以动态监测不同时间段火烧迹地植被的恢复情况，例如火灾后的第一年，通常草本植物率先恢复生长，随着时间推移，木本植物逐渐重新定居与生长，NDVI 指数也随之呈现出阶段性变化。这对于评估森林生态系统的自我修复能力、制定科学合理的生态修复措施、促进森林生态系统的恢复与重建具有重要的实践指导价值。林火蔓延强度与范围影响着火后恢复的起始条件，大面积、高强度蔓延的林火，会使植被恢复难度加大，时间延长，通过时间信息关联林火蔓延与火后恢复，能更全面地理解森林生态系统的动态变化。​

动态预测模型输入：为长短期记忆网络（LSTM）、Transformer 等先进的时序模型提供带时间戳的训练数据。这些时序模型具备强大的时间序列数据处理能力，能够学习和捕捉数据中的长期依赖关系与复杂动态模式。通过输入带有精确时间信息的林火数据，模型可以对未来林火的发生概率、时间分布、空间扩散等情况进行动态预测，为森林火灾的早期预警与防控决策提供科学的预测信息，提前做好应对准备，降低火灾损失。在林火蔓延预测中，模型可根据历史林火蔓延数据及相关环境因素数据，学习林火蔓延模式，预测未来不同时段林火可能的蔓延方向与范围，为及时采取防控措施争取时间。​

事件链重构：结合时间信息追溯火灾扩散路径。火灾发生后，往往会随着时间推移在空间上不断扩散，其扩散过程受到地形、风向、植被分布等多种因素影响。时间信息能够帮助还原火灾在不同时刻的空间位置与范围，通过对一系列时间节点上火灾位置信息的整合与分析，重构火灾扩散的完整事件链，深入理解火灾扩散的时空动态机制，为火灾扑救策略的制定、消防资源的合理调配以及火灾防控经验的总结提供详实的数据支撑与案例参考。

四、数据集典型应用场景​

林业部门：利用该数据集制定差异化防火期。通过对不同地区火灾数据的深入分析，分析火灾发生频次，为林业管理提供参考。基于此，林业部门可依据不同地区的火灾季节规律，在防火关键时期提前开展防火宣传教育活动，增强林区居民的防火意识；科学部署防火人员与物资，合理设置瞭望点、检查站，加强林区巡逻力度，提高防火工作的针对性与精准性，有效提升森林火灾防控能力。在林火蔓延防控方面，了解不同地区火灾高发期的林火蔓延特点，可提前规划防火隔离带位置与长度，确保在林火发生时能有效阻挡其蔓延。​

科研机构：构建中国林地火灾碳排放量估算模型。该模型构建需要综合考虑时间、面积、植被类型等多方面参数。时间信息用于精确确定火灾发生的时刻，为评估火灾碳排放的时间分布提供依据；面积数据反映火灾的规模大小，直接影响碳排放量的计算；植被类型则决定了火灾发生时的碳排放系数，不同植被类型在燃烧过程中的碳排放特性存在差异。通过利用该数据集提供的全面的数据，科研人员能够构建林地火灾碳排放量估算模型，为深入研究森林生态系统在全球碳循环中的作用以及气候变化与森林火灾的相互关系提供重要的数据支持与模型基础。林火蔓延范围与强度影响着燃烧面积与植被燃烧程度，进而影响碳排放量，分析林火蔓延情况对准确估算碳排放量至关重要。​

Introduction:

This dataset was processed by the research team of Professor Feng Zhongke from Beijing Forestry University. Only other data are shared. 

The main attributes in the dataset are: 

1.day-of-year; represents the day of the year on which the fire patch started burning. 

2. start-data: The starting time of combustion 

3. Over-time; the end time of the burning 

4. Lon: Longitude of the burning center 

5. lat: Latitude of the combustion center 

6. Forest type: The type of forest in the burned area (14: Bamboo and economic forest; 111: Evergreen needleleaf forest; 112: Deciduous needleleaf forest; 121: Evergreen broadleaf forest; 122: Deciduous broadleaf forest) 

This dataset is based on NASA's MCD64A1 burned area product. Through spatial overlay analysis with China's land use data, historical fire information within the forested areas of China was extracted, and key attributes such as the burning time, area, and confidence level were retained. The intersection processing of data aims to eliminate non-forest fire interferences such as grasslands and farmlands, accurately reflecting the distribution of forest ecosystem fires. The retention of temporal information supports the analysis of fire seasonality patterns, research on the correlation with climate change, studies on the spread speed of forest fires, and post-fire ecological recovery monitoring. This dataset is applicable to forest fire risk assessment, carbon emission calculation, and optimization of fire prevention policies, and holds significant reference value for forestry management and spatio-temporal analysis. 

I. Basic Data Source - MCD64A1 Burned Area Dataset 

The MCD64A1 Burned Area Collection 1 dataset presents a detailed global monthly distribution of burned areas. Among them, the Burn Date precisely records the time point of fire occurrence, providing crucial temporal dimension data support for analyzing the seasonal patterns of fires and retracing the development process of fire events, which is indispensable for revealing the temporal patterns of fire occurrence. The Burn Area quantifies the extent of each fire, providing a core quantitative indicator for assessing the scale of fires and their ecological and socio-economic impact. The Confidence Level characterizes the reliability of the data, providing a basis for users to conduct accuracy assessment and uncertainty analysis during data application, helping them to reasonably judge the usability and applicability of the data. 

Resolution: This dataset has a spatial resolution of 500m, which can clearly display the spatial distribution characteristics of the fire-affected areas to a certain extent, providing a basic spatial accuracy guarantee for fire analysis at the spatial scale. Meanwhile, its temporal resolution of one month enables systematic monitoring and dynamic analysis of global burn scars on a monthly time scale, effectively capturing the temporal variation patterns of fire occurrence and laying a foundation for temporal accuracy in time series analysis. 

The source: This dataset is the result of collaborative research and development between NASA's MODIS satellites (Terra/Aqua) and Boston University. By leveraging the advanced earth observation remote sensing technology of the MODIS satellites, large-scale, multi-spectral surface information can be obtained. Combined with Boston University's professional research capabilities and profound academic accumulation in the fields of remote sensing applications and fire monitoring, after a series of complex processes such as data processing and algorithm optimization, this dataset of significant value in the global study of burned area monitoring was generated. 

The time range: Since 2001 to the present, this dataset has been in a continuous state of update. Long-term and continuous data records provide rich historical data resources for researchers, forestry management departments and other relevant entities, facilitating in-depth analysis over a long time series. Through the mining of fire data at different time scales, the long-term trends, periodic changes and evolution patterns of fire occurrence can be revealed, providing a long time span and good data continuity for the basic data guarantee of scientific research and management decisions related to forest fires. 

Algorithm principle: It adopts a hybrid combustion detection algorithm based on thermal anomaly points (MODIS Active Fire) and changes in surface reflectance (ΔNBR index). Thermal anomaly detection is based on the MODIS sensor's monitoring of surface thermal radiation, which can quickly identify areas that may have fires and has high timeliness. The ΔNBR index, on the other hand, compares the differences in surface vegetation reflectance in the near-infrared and short-wave infrared bands before and after the fire, and uses the spectral feature changes of vegetation before and after the fire to precisely define the extent of the burned area. The combination of the two fully leverages the timeliness of thermal anomaly detection and the advantages of spectral feature analysis, significantly improving the accuracy and reliability of burned area detection. 

Limitations: On the one hand, the original data covers the entire surface of the earth, which means it contains a large amount of fire information from non-forest areas (such as grasslands and farmlands). These non-forest fire data are interfering information for work focused on forest fire research and analysis, which can affect the accurate understanding of the characteristics, patterns and impacts of forest fires, and increase the complexity of data processing and analysis. Appropriate data screening and filtering methods need to be adopted to exclude them. On the other hand, MODIS has inherent limitations in resolution when dealing with small-scale forest fires. For example, for fire areas smaller than 25 hectares, due to the relatively low resolution, it is difficult to effectively identify and distinguish them, which may lead to the omission of some small-scale fire information and to some extent affect the comprehensive understanding of the overall fire situation. 

II. The Purpose of the Intersection with China's Land Use Data 

The core logic is to precisely extract forest fire information through the key technical means of spatial masking. Spatial masking technology, based on the principles of Geographic Information System (GIS), constructs a mask layer corresponding to the spatial distribution of forest land. It spatially filters the original fire data to accurately extract fire information within the forest land area from the complex global fire data, achieving the separation and purification of target data and enhancing the specificity and accuracy of forest fire data. 

Steps: 

Firstly, the MCD64A1 dataset was clipped to the boundaries of China using geographic spatial analysis methods. Given the vast territory of China and the focus of the study on domestic forest fires, clipping the global raw data to the national boundaries can effectively reduce data redundancy, decrease unnecessary data storage and processing volume, enhance data processing efficiency, and highlight the study area, making subsequent analyses more targeted. 

Then, a spatial mask was generated using the forest land classification layer from China's land use data. These land use datasets employ advanced remote sensing interpretation and geographic information classification techniques to make detailed distinctions among different land use types. The forest land classification layer clearly defines the spatial extent of forest land, providing the basic data for constructing the spatial mask. The spatial mask generated based on this layer can identify which areas fall within the category of forest land. 

Then, a pixel-by-pixel intersection operation is performed on MCD64A1. During this operation, based on the forest area determined by the spatial mask, only the fire pixels that overlap with the forest pixels are retained, while the fire pixels in non-forest areas are excluded. This process enables the precise extraction of forest fire information and results in a dataset that only contains fire conditions within the forest area. 

Finally, the intersection results are processed. The intersection data is processed through both code and visual interpretation. The overall range of the fire is determined based on temporal and spatial information. Eventually, the data of the burned area with temporal information is formed. 

Scientific significance: 

Eliminating non-target interference: There are significant differences in ecosystem attributes between grassland fires and forest fires. Grassland vegetation is mainly composed of herbaceous plants, and the ecosystem structure is relatively simple. The fire occurrence mechanism, combustion characteristics, and ecological impacts of grassland fires are completely different from those of forest fires, which are dominated by woody plants. The burning of crop residues in farmland is mainly caused by human agricultural activities and is a human-induced disturbance factor. Its fire characteristics are significantly different from those of natural forest fires. By performing intersection operations with land use data, these non-forest-related fire data can be effectively excluded, allowing the research to focus on the inherent characteristics and internal laws of forest fires and improving the accuracy and scientific nature of the research results. 

Supporting forestry management: Focusing on the assessment of fire risks in forest ecosystems, in line with the boundaries of forest land management stipulated in the Forest Law. Accurate data on forest land fires can provide key information for forestry management departments, enabling them to gain a deeper understanding of the fire risk conditions faced by forest ecosystems, including the probability and potential impact of fires in different regions and at different times. This allows for the formulation of more targeted and efficient forest land management measures based on scientific data, effectively ensuring the ecological security and sustainable development of forest resources. 

Improving Analytical Accuracy: Under the same resolution conditions, the forest land boundary mask can effectively reduce the error of mixed pixels. For instance, in the forest-grassland transition zone, due to the adjacency of the two land types, in low-resolution data, a single pixel may simultaneously contain the spectral information of both forest and grassland, leading to misjudgment of the fire occurrence area. However, through precise forest land boundary masking, the land type to which each pixel belongs can be clearly distinguished, accurately determining whether the fire occurs within the forest land, significantly enhancing the spatial accuracy of fire analysis and providing a more reliable data foundation for subsequent fire impact assessment, risk prediction, and other work. 

III. The Core Value of Time Information 

Data dimension expansion: Upgrade the fire distribution data based solely on spatial dimensions to the Space-Time Cube structure. The introduction of time information adds a temporal dimension to the original two-dimensional spatial data, transforming the data from a static spatial pattern description to a dynamic spatio-temporal evolution record. This expands the data's expression capacity and analysis dimensions, providing a richer data foundation and analysis perspective for conducting multi-dimensional and in-depth fire-related research. In the study of forest fire spread, the Space-Time Cube structure can display the position and spread of forest fires at different times in space, facilitating researchers' analysis of their dynamic changes over time. 

Key application: Analysis of fire seasonality patterns: By leveraging temporal information, it is possible to identify the months with high fire incidence in different forest areas of China. Due to differences in geographical location, climatic conditions, vegetation types, and ecosystem structures, the seasonal patterns of fire occurrence exhibit distinct regional variations. A thorough understanding of these fire seasonality patterns is of significant guiding importance for forestry departments to formulate targeted fire prevention plans in advance, rationally allocate fire prevention resources, and carry out effective fire prevention work. At the level of forest fire spread, climatic conditions in different seasons significantly influence the speed and direction of forest fire spread. Mastering these patterns helps to more accurately predict the trend of forest fire spread. 

Climate change correlation: By integrating meteorological time series data (such as the CRU TS dataset), the lagged correlation between drought indices and forest fire frequency can be quantified. Climate change has a profound impact on forest fires, and drought, as an important climatic driver, is closely related to the occurrence of forest fires. Through the analysis of the correlation between drought indices and forest fire frequency in time series, the influence mechanism and time lag effect of drought events on forest fires under the background of climate change can be revealed, providing a scientific basis for predicting the trend of forest fires in future climate change scenarios and helping to formulate forward-looking forest fire prevention and adaptation strategies. Forest fire spread is also deeply affected by climate change. Under drought conditions, the vegetation in forest areas becomes dry, and once a forest fire occurs, its spread speed increases and the affected area becomes larger. Analyzing this correlation is crucial for predicting the evolution of forest fire spread trends under climate change. 

Post-fire recovery monitoring: By marking the date of the burn, the trajectory of vegetation recovery in the burned area can be tracked through the Normalized Difference Vegetation Index (NDVI) within 1 to 5 years. After a fire, the recovery of vegetation is a complex ecological succession process, influenced by various factors such as fire intensity, soil conditions, climatic factors, and the characteristics of the vegetation itself. With the help of time information, the recovery of vegetation in the burned area at different time periods can be dynamically monitored. For example, in the first year after a fire, herbaceous plants usually recover and grow first. As time goes by, woody plants gradually re-settle and grow, and the NDVI index also shows phased changes. This is of significant practical guiding value for assessing the self-repairing capacity of forest ecosystems, formulating scientific and reasonable ecological restoration measures, and promoting the recovery and reconstruction of forest ecosystems. The intensity and extent of forest fire spread affect the initial conditions of post-fire recovery. Large-scale and high-intensity forest fires will increase the difficulty and extend the time of vegetation recovery. By correlating the spread of forest fires with post-fire recovery through time information, a more comprehensive understanding of the dynamic changes in forest ecosystems can be achieved. 

The dynamic prediction model input: It provides timestamped training data for advanced time series models such as Long Short-Term Memory networks (LSTM) and Transformer. These time series models have strong capabilities in processing time series data and can learn and capture long-term dependencies and complex dynamic patterns in the data. By inputting forest fire data with precise time information, the model can dynamically predict the occurrence probability, time distribution, and spatial spread of future forest fires, providing scientific prediction information for early warning and prevention and control decision-making of forest fires, allowing for early preparations and reducing fire losses. In the prediction of forest fire spread, the model can learn the fire spread patterns based on historical forest fire spread data and related environmental factor data, and predict the possible spread direction and range of forest fires at different times in the future, thus buying time for timely prevention and control measures. 

Event chain reconstruction: Tracing the fire spread path by integrating temporal information. After a fire breaks out, it often spreads over space over time, and its spread process is influenced by various factors such as terrain, wind direction, and vegetation distribution. Temporal information can help restore the spatial location and extent of the fire at different moments. By integrating and analyzing the fire location information at a series of time nodes, the complete event chain of fire spread can be reconstructed, providing a detailed data support and case reference for understanding the spatio-temporal dynamic mechanism of fire spread, formulating fire suppression strategies, rationally allocating fire-fighting resources, and summarizing fire prevention and control experience. 

IV. Typical Application Scenarios of the Dataset 

The forestry department: Utilize this dataset to establish differentiated fire prevention periods. Through in-depth analysis of fire data in different regions, analyze the frequency of fire occurrence to provide references for forestry management. Based on this, the forestry department can, in accordance with the fire season patterns of different regions, carry out fire prevention publicity and education activities in advance during key fire prevention periods, enhancing the fire prevention awareness of residents in forest areas; scientifically deploy fire prevention personnel and materials, reasonably set up lookout points and inspection stations, and strengthen forest area patrols to improve the targeted and precise nature of fire prevention work, effectively enhancing the forest fire prevention and control capabilities. In terms of forest fire spread prevention and control, understanding the characteristics of forest fire spread during high-incidence periods in different regions can help plan the location and length of firebreaks in advance, ensuring that they can effectively prevent the spread of forest fires when they occur. 

Research institutions: Establish a model for estimating carbon emissions from forest fires in China. The construction of this model requires comprehensive consideration of multiple parameters such as time, area, and vegetation type. Time information is used to precisely determine the moment when the fire occurs, providing a basis for assessing the temporal distribution of carbon emissions from the fire; area data reflects the scale of the fire and directly affects the calculation of carbon emissions; vegetation type determines the carbon emission coefficient when the fire occurs, and different vegetation types have different carbon emission characteristics during the burning process. By using the accurate and comprehensive data provided by this dataset, researchers can build a more accurate model to estimate carbon emissions from forest fires, providing important data support and model basis for in-depth research on the role of forest ecosystems in the global carbon cycle and the relationship between climate change and forest fires. The spread and intensity of forest fires affect the burning area and the degree of vegetation burning, which in turn affects carbon emissions. Accurate analysis of the spread of forest fires is crucial to accurately estimate carbon emissions. ​
