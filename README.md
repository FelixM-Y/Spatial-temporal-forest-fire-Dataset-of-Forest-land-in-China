# Spatial-temporal-forest-fire-Dataset-of-Forest-land-in-China-

介绍：

该数据集为北京林业大学冯仲科科研团队处理。仅共享2015年数据以及部分其他数据。

数据集中主要属性为：

1.day-of-year；代表燃烧开始的该火烧斑块起始燃烧时间处于该年度的第几天

2.start-data：燃烧的起始时间

3.over-time；燃烧的结束时间

4.lon：燃烧中心的经度

5.lat：燃烧中心的纬度

6.foresttype：燃烧林地中的林地类型(14：Bamboo and economic forest;111：Evergreen needleleaf forest;112：Deciduous needleleaf forest;121：Evergreen broadleaf forest;122：Deciduous broadleaf forest)

本数据集基于NASA的MCD64A1火烧迹地产品，通过与中国土地利用数据的空间叠加分析，提取中国林地范围内的历史火灾信息，并保留燃烧时间、面积及置信度等关键属性。数据交集处理旨在排除草原、农田等非林火干扰，精准反映森林生态系统火灾分布；而时间信息的保留则支持火灾季节规律分析、气候变化关联研究、林火蔓延速度研究及火后生态恢复监测。该数据集适用于林火风险评估、碳排放测算及防火政策优化等应用，具有明确的林业管理指向性与时空分析价值。

一、基础数据源 ——MCD64A1 火烧迹地数据集​

数据内容：MCD64A1 火烧迹地数据集呈现了全球月度火烧迹地的详尽分布格局。其中，燃烧日期（Burn Date）精准记录火灾发生的时间节点，为剖析火灾季节性规律以及回溯火灾事件的发展进程提供了关键时间维度数据支撑，对揭示火灾发生的时间模式具有不可或缺的作用。燃烧面积（Burn Area）通过量化每次火灾的波及范围，为评估火灾规模及其生态与社会经济影响程度提供了核心量化指标。置信度（Confidence Level）则表征数据的可靠性，为使用者在数据应用过程中进行精度评估与不确定性分析提供依据，助力其合理判断数据的可用性与适用性。​

分辨率：该数据集具备 500m 的空间分辨率，在一定程度上能够较为清晰地展现火灾发生区域的空间分布特征，为空间尺度上的火灾分析提供了基础空间精度保障。同时，其 1 个月的时间分辨率使得可按月度时间尺度对全球火烧迹地进行系统监测与动态分析，能够有效捕捉火灾发生的时序变化规律，为时间序列分析奠定了时间精度基础。​

来源：此数据集是 NASA MODIS 卫星（Terra/Aqua）与波士顿大学协同研发的成果。借助 MODIS 卫星先进的对地观测遥感技术，可获取大面积、多光谱的地表信息，结合波士顿大学在遥感应用、火灾监测等领域的专业研究能力与深厚学术积淀，经过数据处理、算法优化等一系列复杂流程，生成了这一在全球火烧迹地监测研究领域具有重要价值的数据集。​

时间范围：自 2001 年起至今，该数据集处于持续更新状态。长期且连续的数据记录为科研人员、林业管理部门等相关主体提供了丰富的历史数据资源，便于开展长时间序列的深入分析，通过对不同时间尺度下火灾数据的挖掘，揭示火灾发生的长期趋势、周期性变化以及演变规律，为森林火灾相关的科学研究与管理决策提供了时间跨度长、数据连续性好的基础数据保障。​

算法原理：其采用基于热异常点（MODIS Active Fire）与地表反射率变化（ΔNBR 指数）的混合燃烧检测算法。热异常点探测基于 MODIS 传感器对地表热辐射的监测，能够快速识别可能存在火灾的区域，具有较高的时效性。地表反射率变化（ΔNBR 指数）则通过对比火灾前后地表植被在近红外与短波红外波段反射率的差异，利用植被在火烧前后的光谱特征变化来精确界定火烧迹地的范围。两者有机结合，充分发挥了热异常探测的及时性与光谱特征分析的精确性优势，显著提高了火烧迹地检测的准确性与可靠性。​

局限性：一方面，原始数据全域覆盖地表，这意味着其中包含大量非林地（如草原、农田）的火灾信息。这些非林地火灾数据对于专注于林地火灾研究与分析的工作而言，属于干扰信息，会影响对林地火灾特征、规律及影响的准确认知，增加数据处理与分析的复杂性，需采用适当的数据筛选与过滤方法加以排除。另一方面，500m 分辨率在面对小规模林火时存在固有局限性，例如对于面积小于 25 公顷的火场，由于分辨率相对较低，难以有效识别和区分，可能导致部分小规模火灾信息遗漏，在一定程度上影响对火灾总体情况的全面掌握。​

二、与中国土地利用数据交集的目的​

核心逻辑：通过空间掩膜（Masking）这一关键技术手段实现林地火灾的精准提取。空间掩膜技术基于地理信息系统（GIS）原理，通过构建与林地空间分布相对应的掩膜图层，对原始火灾数据进行空间筛选，从复杂的全域火灾数据中精准提取出林地范围内的火灾信息，实现目标数据的分离与提纯，提高林地火灾数据的针对性与准确性。​

步骤：​

首先，运用地理空间分析方法将 MCD64A1 数据集裁剪至中国国界范围。鉴于中国地域广袤，而研究重点聚焦国内林地火灾，对全球范围的原始数据进行国界范围内的裁剪，能够有效降低数据冗余度，减少不必要的数据存储与处理量，提升数据处理效率，同时突出研究区域，使后续分析更具针对性。​

接着，利用中国土地利用数据中的林地分类图层生成空间掩膜。这些土地利用数据集运用先进的遥感解译与地理信息分类技术，对不同土地利用类型进行了详细划分，其中的林地分类图层清晰界定了林地的空间范围，为构建空间掩膜提供了准确的基础数据。基于该图层生成的空间掩膜，能够精确识别出哪些区域属于林地范畴。​

然后，对 MCD64A1 进行逐像元交集运算。在该运算过程中，依据空间掩膜所确定的林地范围，仅保留与林地像元重叠的火灾像元，将其他非林地的火灾像元予以剔除，从而实现林地火灾信息的精准提取，得到仅包含林地范围内火灾情况的数据集。​

最后，对于交集结果进行处理，通过代码和人工的方式将交集数据进行处理，通过时间信息和空间信息将火灾整体范围确定，最后形成带有时间信息的火烧基地数据。

科学意义：​

去除非目标干扰：草原火与林地火灾在生态系统属性上存在显著差异。草原植被以草本植物为主，生态系统结构相对简单，其火灾发生机制、燃烧特性及生态影响与以木本植物为主的林地火灾截然不同。农田秸秆焚烧则主要由人为农事活动引发，属于人为干扰因素，其火灾特征与林地自然火灾差异明显。通过与土地利用数据进行交集运算，能够有效排除这些非林业相关火灾数据，使研究能够聚焦于林地火灾的固有特性与内在规律，提高研究结果的准确性与科学性。​

支撑林业管理：聚焦森林生态系统火灾风险评估，与《森林法》中林地管理边界相契合。准确的林地火灾数据能够为林业管理部门提供关键信息，助其深入了解森林生态系统所面临的火灾风险状况，包括不同区域、不同时段的火灾发生概率与潜在影响程度，从而依据科学数据制定更具针对性、更高效的林地管理措施，有效保障森林资源的生态安全与可持续发展。​
提升分析精度：在相同分辨率条件下，林地边界掩膜能够有效减少混合像元误差。例如在森林 - 草地过渡带，由于两种土地类型相邻，在低分辨率数据中，单个像元可能同时包含森林与草地的光谱信息，导致对火灾发生区域的误判。而通过精确的林地边界掩膜，能够明确区分像元所属的土地类型，准确判断火灾是否发生在林地范围内，显著提高火灾分析在空间尺度上的精度，为后续的火灾影响评估、风险预测等工作提供更可靠的数据基础。

三、时间信息的核心价值​
数据维度扩展：将单纯基于空间维度的火灾分布数据升级为时空立方体（Space - Time Cube）结构。时间信息的引入，为原本二维的空间数据增添了时间维度，使数据从静态的空间格局描述转变为动态的时空演变记录，拓展了数据的表达能力与分析维度，为开展多维度、深层次的火灾相关研究提供了更丰富的数据基础与分析视角。在林火蔓延研究中，时空立方体结构能够直观展现林火在不同时刻于空间中的位置与蔓延情况，方便研究人员分析其随时间的动态变化过程。​

关键用途：​

火灾季节规律分析：借助时间信息，能够识别中国不同林区（如东北针叶林、西南季雨林）的火灾高发月份。不同林区因地理位置、气候条件、植被类型及生态系统结构等因素的差异，火灾发生的季节规律呈现出明显的地域分异特征。例如东北针叶林地区冬季漫长寒冷，林下积雪覆盖，春季气温回升后，积雪融化，林下植被逐渐干燥，可燃物积累，4 - 6 月受春季风影响，气候干燥且多风，成为火灾高发期。而西南季雨林地区受季风气候控制，干湿季分明，干季（如 3 - 5 月）降水稀少，空气湿度低，植被含水量下降，易燃性增强，火灾发生概率显著增加。深入了解这些火灾季节规律，对于林业部门提前制定针对性的防火预案、合理调配防火资源、开展有效的火灾预防工作具有重要指导意义。在林火蔓延层面，不同季节的气候条件显著影响林火蔓延速度与方向，如在多风季节，林火易顺风快速蔓延，掌握这些规律有助于更准确地预测林火蔓延趋势。​

气候变化关联：结合气象时序数据（如 CRU TS 数据集），可量化干旱指数与林火频率的滞后相关性。气候变化对林火发生具有深刻影响，干旱作为重要的气候驱动因素，与林火发生密切相关。通过对时间序列上干旱指数与林火频率的相关性分析，能够揭示气候变化背景下干旱事件对林火发生的影响机制与时间滞后效应，为预测未来气候变化情景下林火发生趋势提供科学依据，有助于制定前瞻性的森林火灾防控与适应策略。林火蔓延也深受气候变化影响，干旱条件下，林地植被干燥，林火一旦发生，蔓延速度加快，范围更广，分析这种关联对预测林火蔓延态势在气候变化下的演变至关重要。​

火后恢复监测：通过燃烧日期标记，能够跟踪火烧迹地归一化植被指数（NDVI）在 1 - 5 年内的植被恢复轨迹。火灾发生后，植被的恢复是一个复杂的生态演替过程，受火灾强度、土壤条件、气候因素及植被自身特性等多种因素影响。借助时间信息，可以动态监测不同时间段火烧迹地植被的恢复情况，例如火灾后的第一年，通常草本植物率先恢复生长，随着时间推移，木本植物逐渐重新定居与生长，NDVI 指数也随之呈现出阶段性变化。这对于评估森林生态系统的自我修复能力、制定科学合理的生态修复措施、促进森林生态系统的恢复与重建具有重要的实践指导价值。林火蔓延强度与范围影响着火后恢复的起始条件，大面积、高强度蔓延的林火，会使植被恢复难度加大，时间延长，通过时间信息关联林火蔓延与火后恢复，能更全面地理解森林生态系统的动态变化。​

技术优势：​
动态预测模型输入：为长短期记忆网络（LSTM）、Transformer 等先进的时序模型提供带时间戳的训练数据。这些时序模型具备强大的时间序列数据处理能力，能够学习和捕捉数据中的长期依赖关系与复杂动态模式。通过输入带有精确时间信息的林火数据，模型可以对未来林火的发生概率、时间分布、空间扩散等情况进行动态预测，为森林火灾的早期预警与防控决策提供科学的预测信息，提前做好应对准备，降低火灾损失。在林火蔓延预测中，模型可根据历史林火蔓延数据及相关环境因素数据，学习林火蔓延模式，预测未来不同时段林火可能的蔓延方向与范围，为及时采取防控措施争取时间。​

事件链重构：结合时间信息追溯火灾扩散路径（如 2022 年重庆山火的多日蔓延过程）。火灾发生后，往往会随着时间推移在空间上不断扩散，其扩散过程受到地形、风向、植被分布等多种因素影响。时间信息能够帮助还原火灾在不同时刻的空间位置与范围，通过对一系列时间节点上火灾位置信息的整合与分析，重构火灾扩散的完整事件链，深入理解火灾扩散的时空动态机制，为火灾扑救策略的制定、消防资源的合理调配以及火灾防控经验的总结提供详实的数据支撑与案例参考。

四、数据集典型应用场景​

林业部门：利用该数据集制定差异化防火期。通过对不同地区火灾数据的深入分析，例如对云南地区历史火灾数据的时间序列分析发现，3 - 5 月火灾发生频次显著高于其他月份，而东北林区在 4 - 6 月火灾风险处于高位。基于此，林业部门可依据不同地区的火灾季节规律，在防火关键时期提前开展防火宣传教育活动，增强林区居民的防火意识；科学部署防火人员与物资，合理设置瞭望点、检查站，加强林区巡逻力度，提高防火工作的针对性与精准性，有效提升森林火灾防控能力。在林火蔓延防控方面，了解不同地区火灾高发期的林火蔓延特点，可提前规划防火隔离带位置与长度，确保在林火发生时能有效阻挡其蔓延。​

科研机构：构建中国林地火灾碳排放量估算模型。该模型构建需要综合考虑时间、面积、植被类型等多方面参数。时间信息用于精确确定火灾发生的时刻，为评估火灾碳排放的时间分布提供依据；面积数据反映火灾的规模大小，直接影响碳排放量的计算；植被类型则决定了火灾发生时的碳排放系数，不同植被类型在燃烧过程中的碳排放特性存在差异。通过利用该数据集提供的准确、全面的数据，科研人员能够构建更为精确的林地火灾碳排放量估算模型，为深入研究森林生态系统在全球碳循环中的作用以及气候变化与森林火灾的相互关系提供重要的数据支持与模型基础。林火蔓延范围与强度影响着燃烧面积与植被燃烧程度，进而影响碳排放量，精确分析林火蔓延情况对准确估算碳排放量至关重要。​

Introduction

This dataset is processed by Feng Zhongke's research team at Beijing Forestry University. Only the 2015 data and some other data are shared.

The main attributes in the dataset are:

1. day-of-year; represents the day of the year when the burning of the burnt patch started

2.start-data: the start time of burning

3.over-time; end time of burning

4.lon: longitude of the combustion center

5.lat: latitude of the burning center

6. foresttype: forest type in the burned forest (14: Bamboo and economic forest; 111: Evergreen needleleaf forest; 112: Deciduous needleleaf forest; 121: Evergreen broadleaf forest; 122: Deciduous broadleaf forest)

This dataset is based on NASA's MCD64A1 burnt area product. Through spatial overlay analysis with China's land use data, it extracts historical fire information within China's forest land and retains key attributes such as burning time, area, and confidence. Data intersection processing aims to eliminate non-forest fire interference such as grassland and farmland, and accurately reflect the distribution of forest ecosystem fires; while the retention of time information supports the analysis of fire season patterns, climate change correlation research, forest fire spread speed research, and post-fire ecological recovery monitoring. This dataset is suitable for applications such as forest fire risk assessment, carbon emission calculation, and fire prevention policy optimization, and has clear forestry management orientation and spatiotemporal analysis value.

1. Basic data source - MCD64A1 burnt area dataset

Data content: The MCD64A1 burnt area dataset presents a detailed distribution pattern of global monthly burnt areas. Among them, the Burn Date accurately records the time node of the fire, providing key time dimension data support for analyzing the seasonality of fires and tracing the development process of fire events, and plays an indispensable role in revealing the time pattern of fire occurrence. The Burn Area quantifies the scope of each fire, providing a core quantitative indicator for assessing the scale of fires and their ecological and socio-economic impacts. The Confidence Level characterizes the reliability of the data, provides a basis for users to conduct accuracy assessment and uncertainty analysis in the process of data application, and helps them to reasonably judge the availability and applicability of the data. ​

Resolution: The dataset has a spatial resolution of 500m, which can clearly show the spatial distribution characteristics of the fire area to a certain extent, and provide basic spatial accuracy guarantee for fire analysis on a spatial scale. At the same time, its 1-month temporal resolution enables systematic monitoring and dynamic analysis of global fire scars on a monthly time scale, which can effectively capture the temporal changes of fire occurrence and lay a foundation for temporal accuracy for time series analysis. ​

Source: This dataset is the result of collaborative research between NASA MODIS satellites (Terra/Aqua) and Boston University. With the help of MODIS satellite's advanced earth observation remote sensing technology, large-area, multi-spectral surface information can be obtained. Combined with Boston University's professional research capabilities and profound academic accumulation in the fields of remote sensing applications and fire monitoring, this dataset with important value in the field of global burn site monitoring research has been generated through a series of complex processes such as data processing and algorithm optimization. ​

Time range: Since 2001, the dataset has been continuously updated. Long-term and continuous data records provide a wealth of historical data resources for relevant entities such as scientific researchers and forestry management departments, facilitating in-depth analysis of long time series. By mining fire data at different time scales, the long-term trends, periodic changes and evolution laws of fire occurrence are revealed, providing a basic data guarantee with a long time span and good data continuity for scientific research and management decisions related to forest fires. ​

Algorithm principle: It adopts a hybrid combustion detection algorithm based on thermal anomaly points (MODIS Active Fire) and surface reflectivity changes (ΔNBR index). Thermal anomaly point detection is based on the monitoring of surface thermal radiation by MODIS sensors, which can quickly identify areas where fires may exist and has high timeliness. The surface reflectivity change (ΔNBR index) compares the difference in reflectivity of surface vegetation in the near-infrared and short-wave infrared bands before and after the fire, and uses the changes in the spectral characteristics of vegetation before and after the fire to accurately define the scope of the burn site. The organic combination of the two gives full play to the timeliness of thermal anomaly detection and the accuracy of spectral feature analysis, significantly improving the accuracy and reliability of burn site detection. ​

Limitations: On the one hand, the original data covers the entire surface, which means that it contains a large amount of fire information on non-forest land (such as grassland and farmland). These non-forest fire data are interference information for work focused on forest fire research and analysis, which will affect the accurate understanding of the characteristics, laws and impacts of forest fires, increase the complexity of data processing and analysis, and need to be eliminated by appropriate data screening and filtering methods. On the other hand, the 500m resolution has inherent limitations when facing small-scale forest fires. For example, for fires with an area of ​​less than 25 hectares, due to the relatively low resolution, it is difficult to effectively identify and distinguish, which may lead to the omission of some small-scale fire information, which to a certain extent affects the overall grasp of the fire situation. ​

2. Purpose of Intersection with Chinese Land Use Data

Core logic: The key technical means of spatial masking is to achieve accurate extraction of forest fires. Spatial masking technology is based on the principle of geographic information system (GIS). By constructing a mask layer corresponding to the spatial distribution of forests, the original fire data is spatially screened, and the fire information within the forest range is accurately extracted from the complex global fire data, so as to separate and purify the target data and improve the pertinence and accuracy of forest fire data. ​

Steps:​

First, the MCD64A1 dataset was clipped to the national border of China using geospatial analysis methods. Given the vast territory of China and the focus of the study on domestic forest fires, clipping the original global data to the national border can effectively reduce data redundancy, reduce unnecessary data storage and processing, improve data processing efficiency, and highlight the research area, making subsequent analysis more targeted. ​

Next, we used the forest classification layer in China's land use data to generate a spatial mask. These land use data sets use advanced remote sensing interpretation and geographic information classification technology to make detailed divisions of different land use types. The forest classification layer clearly defines the spatial range of forest land, providing accurate basic data for constructing spatial masks. The spatial mask generated based on this layer can accurately identify which areas belong to the forest land category. ​

Then, a pixel-by-pixel intersection operation is performed on MCD64A1. In this operation, according to the forest range determined by the spatial mask, only the fire pixels overlapping with the forest pixels are retained, and other non-forest fire pixels are removed, so as to achieve accurate extraction of forest fire information and obtain a data set containing only fire conditions within the forest range. ​

Finally, the intersection results are processed by code and manual methods, the overall scope of the fire is determined by time and space information, and finally the fire base data with time information is formed.

Scientific significance:

Removing non-target interference: There are significant differences in the ecosystem properties between grassland fires and forest fires. Grassland vegetation is mainly herbaceous plants, and the ecosystem structure is relatively simple. Its fire mechanism, combustion characteristics and ecological impact are completely different from those of forest fires dominated by woody plants. Farmland straw burning is mainly caused by human agricultural activities and is a human interference factor. Its fire characteristics are significantly different from natural forest fires. By performing intersection operations with land use data, these non-forestry related fire data can be effectively excluded, so that the research can focus on the inherent characteristics and internal laws of forest fires, and improve the accuracy and scientificity of the research results. ​

Supporting forestry management: Focusing on the fire risk assessment of forest ecosystems, it is consistent with the forest management boundaries in the Forest Law. Accurate forest fire data can provide key information for forestry management departments, helping them to gain an in-depth understanding of the fire risk conditions faced by forest ecosystems, including the probability of fires and the potential impact in different regions and at different times, so as to formulate more targeted and efficient forest management measures based on scientific data, and effectively ensure the ecological security and sustainable development of forest resources. Improve analysis accuracy: Under the same resolution conditions, forest boundary masks can effectively reduce mixed pixel errors. For example, in the forest-grassland transition zone, due to the proximity of the two land types, in low-resolution data, a single pixel may contain spectral information of both forest and grassland, leading to misjudgment of the fire area. Through accurate forest boundary masks, it is possible to clearly distinguish the land type to which the pixel belongs, accurately determine whether the fire occurs within the forest, significantly improve the accuracy of fire analysis at a spatial scale, and provide a more reliable data basis for subsequent fire impact assessment, risk prediction and other work.

3. The core value of time information​Data dimension expansion: Upgrading fire distribution data based solely on spatial dimensions to a space-time cube structure. The introduction of time information adds a time dimension to the original two-dimensional spatial data, transforming the data from a static description of spatial patterns to a dynamic record of space-time evolution, expanding the data's expressive power and analysis dimensions, and providing a richer data foundation and analysis perspective for conducting multi-dimensional, in-depth fire-related research. In forest fire spread research, the space-time cube structure can intuitively display the location and spread of forest fires in space at different times, making it easier for researchers to analyze their dynamic changes over time. ​

Key Uses:​

Analysis of seasonal patterns of fires: With the help of time information, it is possible to identify the high-incidence months of fires in different forest areas in China (such as the northeastern coniferous forests and the southwestern monsoon forests). Due to differences in geographical location, climate conditions, vegetation types, and ecosystem structure, the seasonal patterns of fires in different forest areas show obvious regional differences. For example, the northeastern coniferous forest area has a long and cold winter, with snow covering the forest floor. After the temperature rises in spring, the snow melts, the vegetation under the forest gradually dries, and combustibles accumulate. From April to June, affected by the spring wind, the climate is dry and windy, making it a high-incidence period for fires. The southwestern monsoon forest area is controlled by the monsoon climate, with distinct dry and wet seasons. In the dry season (such as March to May), precipitation is scarce, air humidity is low, vegetation moisture content decreases, flammability increases, and the probability of fire increases significantly. A deep understanding of these seasonal patterns of fires is of great guiding significance for forestry departments to formulate targeted fire prevention plans in advance, rationally allocate fire prevention resources, and carry out effective fire prevention work. In terms of forest fire spread, climate conditions in different seasons significantly affect the speed and direction of forest fire spread. For example, in windy seasons, forest fires tend to spread quickly with the wind. Understanding these laws will help to more accurately predict the trend of forest fire spread. ​

Climate change association: Combined with meteorological time series data (such as the CRU TS dataset), the lagged correlation between the drought index and forest fire frequency can be quantified. Climate change has a profound impact on the occurrence of forest fires. Drought, as an important climate driver, is closely related to the occurrence of forest fires. By analyzing the correlation between the drought index and forest fire frequency in the time series, we can reveal the impact mechanism and time lag effect of drought events on forest fires under the background of climate change, provide a scientific basis for predicting the trend of forest fires under future climate change scenarios, and help to formulate forward-looking forest fire prevention and control and adaptation strategies. The spread of forest fires is also deeply affected by climate change. Under drought conditions, forest vegetation is dry. Once a forest fire occurs, it spreads faster and covers a wider range. Analyzing this association is crucial to predicting the evolution of forest fire spread under climate change. ​

Post-fire recovery monitoring: By marking the burning date, the vegetation recovery trajectory of the normalized difference vegetation index (NDVI) in the burned area can be tracked within 1-5 years. After a fire, the recovery of vegetation is a complex ecological succession process, which is affected by many factors such as fire intensity, soil conditions, climate factors and vegetation characteristics. With the help of time information, the recovery of vegetation in the burned area in different time periods can be dynamically monitored. For example, in the first year after the fire, herbaceous plants usually resume growth first. As time goes by, woody plants gradually resettle and grow, and the NDVI index also shows a phased change. This has important practical guiding value for evaluating the self-repair ability of forest ecosystems, formulating scientific and reasonable ecological restoration measures, and promoting the recovery and reconstruction of forest ecosystems. The intensity and scope of forest fire spread affect the starting conditions for post-fire recovery. Large-scale, high-intensity forest fires will make vegetation recovery more difficult and prolong the time. By associating forest fire spread with post-fire recovery through time information, we can have a more comprehensive understanding of the dynamic changes of forest ecosystems. ​

Technical advantages: Dynamic prediction model input: Provides time-stamped training data for advanced time series models such as long short-term memory networks (LSTM) and Transformer. These time series models have powerful time series data processing capabilities and can learn and capture long-term dependencies and complex dynamic patterns in data. By inputting forest fire data with precise time information, the model can dynamically predict the probability of occurrence, time distribution, spatial diffusion, etc. of future forest fires, provide scientific prediction information for early warning and prevention and control decisions of forest fires, make preparations in advance, and reduce fire losses. In the prediction of forest fire spread, the model can learn forest fire spread patterns based on historical forest fire spread data and related environmental factors data, predict the possible spread direction and range of forest fires in different periods in the future, and buy time for timely prevention and control measures. ​

Event chain reconstruction: Combine time information to trace the path of fire spread (such as the multi-day spread of the Chongqing wildfire in 2022). After a fire occurs, it often continues to spread in space over time, and its spread process is affected by multiple factors such as terrain, wind direction, and vegetation distribution. Time information can help restore the spatial location and scope of the fire at different times. By integrating and analyzing the fire location information at a series of time nodes, the complete event chain of fire spread can be reconstructed, and the spatiotemporal dynamic mechanism of fire spread can be deeply understood, providing detailed data support and case references for the formulation of fire fighting strategies, the rational allocation of fire resources, and the summary of fire prevention and control experience.

4. Typical application scenarios of the dataset

Forestry Department: Use this data set to develop differentiated fire prevention periods. Through in-depth analysis of fire data in different regions, for example, time series analysis of historical fire data in Yunnan found that the frequency of fires in March-May was significantly higher than in other months, while the fire risk in the Northeast Forest Region was high in April-June. Based on this, the forestry department can carry out fire prevention publicity and education activities in advance during the critical period of fire prevention according to the seasonal patterns of fires in different regions to enhance the fire prevention awareness of residents in forest areas; scientifically deploy fire prevention personnel and materials, reasonably set up lookout points and checkpoints, strengthen patrols in forest areas, improve the pertinence and accuracy of fire prevention work, and effectively enhance forest fire prevention and control capabilities. In terms of forest fire spread prevention and control, understanding the characteristics of forest fire spread during the high-incidence period of fires in different regions can plan the location and length of fire isolation belts in advance to ensure that they can effectively prevent the spread of forest fires when they occur. ​

Scientific research institutions: Construct a model to estimate carbon emissions from forest fires in China. The construction of this model requires comprehensive consideration of multiple parameters such as time, area, and vegetation type. Time information is used to accurately determine the moment when the fire occurs, providing a basis for evaluating the temporal distribution of carbon emissions from fires; area data reflects the scale of the fire and directly affects the calculation of carbon emissions; vegetation type determines the carbon emission coefficient when the fire occurs, and different vegetation types have different carbon emission characteristics during the burning process. By using the accurate and comprehensive data provided by this dataset, researchers can build a more accurate model to estimate carbon emissions from forest fires, providing important data support and model basis for in-depth research on the role of forest ecosystems in the global carbon cycle and the relationship between climate change and forest fires. The spread and intensity of forest fires affect the burning area and the degree of vegetation burning, which in turn affects carbon emissions. Accurate analysis of the spread of forest fires is crucial to accurately estimate carbon emissions. ​
