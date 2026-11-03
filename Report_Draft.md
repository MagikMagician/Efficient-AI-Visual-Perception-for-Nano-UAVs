# Draft Report

Report will be unstructured without grammar and will slowly be cleaned up.

_Please Note: UWE(University of the West of England) has imposed a 4,000 word limit of the report._

Note from UWE Marking PDF just to remind me - In line with UWE Bristol’s [Assessment Content Limit Policy](https://www.uwe.ac.uk/about/structure-and-governance/policies) (formerly the Word Count Policy), word
count includes all text, including (but not limited to): the main body of text (including headings), all
citations (both in and out of brackets), text boxes, tables and graphs, figures and diagrams, quotes,
lists. The Bibliography for references is not included in the word count.

# Efficient AI-Based Visual Perception for Autonomous Nano-UAVs

### MagikMagician(Change to real name for submission just dont want to dox myself)

### Student ID: Insert Here

### Github Link - https://github.com/MagikMagician/Efficient-AI-Visual-Perception-for-Nano-UAVs

## UXCFXK-30-3 Digital Systems Project

## Abstract

My Abstract

## Acknowledgements

My Acknowledgements

## Table of Contents

| Section                                                     | Page |
| :---------------------------------------------------------- | :--: |
| [Abstract](#abstract)                                       |  1   |
| [Acknowledgements](#acknowledgements)                       |  2   |
| [Table of Contents](#table-of-contents)                     |  3   |
| [Table of Figures](#table-of-figures)                       |  4   |
| [Introduction](#introduction)                               |  5   |
| [Literature Review](#literature-review)                     |  6   |
| [Methodology](#methodology)                                 |  7   |
| [Results and Analysis](#results-and-analysis)               |  8   |
| [Project Evaluation](#project-evaluation)                   |  9   |
| [Further Work and Conclusion](#further-work-and-conclusion) |  10  |
| [Glossary](#glossary)                                       |  11  |
| [Table of Abbreviations](#table-of-abbreviations)           |  12  |
| [References / Bibliography](#references--bibliography)      |  13  |
| [Appendix A: First Appendix](#appendix-a-first-appendix)    |  14  |

## Table of Figures

No table of figures entries found.

## Introduction

lorem ipsum dolor sit amet consectetur adipiscing elit quibusdam facilis qui excepturi assumenda similique pariatur eiusmod minus minus cum culpa cillum quos dolorem consequat qui ullamco ex facilis dolore minus nisi officia similique in labore qui nisi quidem et eligendi repellendus cupidatat dolor temporibus ex ut id ut atque nisi

### Background and Research Context

Autonomous unmanned aerial vehicles (UAVs) are increasingly used in agriculture, inspection, logistics and emergency response (Bhat *et al.*, 2024; Hashim, 2025; Bialas *et al.*, 2026), enabled by advances in computer vision and deep learning (Carrio *et al.*, 2017). Deploying these capabilities is hardest on nano-UAVs, which typically measure under 10 cm, weigh under 40 g and have less than 100 mW available for computation (Cereda *et al.*, 2023). Such limits on payload, battery endurance and processing restrict onboard complexity (Boroujerdian *et al.*, 2021), so perception accuracy, computational efficiency and autonomous performance must be balanced. This is particularly important where perception directly informs control, as inaccurate visual information can compromise the safety of the wider system (Hsu, Hu and Fisac, 2024).

### AI-Based Visual Perception in Autonomous UAVs

Visual perception enables UAVs to identify objects and estimate spatial relationships from camera images (Kanellakis and Nikolakopoulos, 2017), supporting applications such as agricultural monitoring (Ronzhin *et al.*, 2026). However, neural networks add computational demand that competes with flight systems for limited power and payload (Boroujerdian *et al.*, 2021).

Neural perception can nevertheless operate within these constraints. Palossi *et al.* (2019) achieved closed-loop visual navigation using a deep neural network aboard a 27 g nano-UAV, with processing consuming only 64 mW. Palossi *et al.* (2022) estimated relative human–drone pose entirely onboard for closed-loop control, although median positional error rose from 26 cm with ideal sensing to 41 cm. These results establish feasibility but remain specific to their tasks, architectures and hardware. Perception also cannot be evaluated in isolation: Falanga, Kim and Scaramuzza (2019) showed that perception latency limits the maximum speed at which a quadrotor can navigate safely. Prediction quality must therefore be evaluated through task performance.

### Computational Efficiency of Neural Networks

Algorithmic efficiency has improved rapidly: Hernandez and Brown (2020) found that the training compute needed to reach AlexNet-level ImageNet accuracy fell 44-fold between 2012 and 2019. MobileNet replaced standard convolutions with depthwise separable convolutions (Howard *et al.*, 2017), and MobileNetV2 added inverted residuals and linear bottlenecks, further improving the accuracy–cost trade-off (Sandler *et al.*, 2018), as Figure 5 illustrates. Nano-UAV networks such as PULP-Frontnet (14.7 million multiply-accumulates; Cereda *et al.*, 2023) would sit at the plot’s far left, where accuracy falls most steeply.

![Figure 5](/Figure_5-LitReview.png)

*Figure 5: ImageNet top-1 accuracy against multiply-adds (log scale); coloured squares show MobileNetV2 at different input resolutions. Source: Sandler et al. (2018, p. 4515).*

Quantisation offers further savings: Jacob *et al.* (2018) demonstrated integer-only 8-bit inference that reduces computation and storage while largely preserving accuracy. For nano-UAVs, Niculescu *et al.* (2021) automated CNN optimisation and deployment, halving memory footprint and accelerating inference 1.6-fold. Prediction accuracy was unchanged, yet in-field flight behaviour improved significantly: a benefit invisible to offline accuracy metrics.

However, parameter and operation counts do not necessarily reflect latency, memory use or energy consumption on specific hardware (Sze *et al.*, 2017; Hanafy, Molom-Ochir and Shenoy, 2021). Gains on image-classification benchmarks also cannot be assumed to transfer to continuous regression tasks such as position estimation. Architecture, numerical precision and execution characteristics should therefore be evaluated alongside task-specific performance.

### The Role of Simulation in Autonomous Systems

Simulation allows autonomous systems to be evaluated before physical deployment, with environmental conditions, sensor characteristics and system parameters varied systematically and repeatably (Kaur *et al.*, 2021). NVIDIA Isaac Sim, used in this project, underpins UAV frameworks for photorealistic multi-vehicle simulation (Jacinto *et al.*, 2024) and GPU-parallelised reinforcement learning with a Crazyflie model (Xu *et al.*, 2024).

However, simulation only approximates reality: differences in sensor behaviour, appearance and dynamics create a ‘reality gap’ between simulated and real-world performance (Muratore *et al.*, 2022; Aljalbout *et al.*, 2026). Domain randomisation mitigates this by varying simulated conditions during training (Tobin *et al.*, 2017), and has enabled a drone-racing CNN trained entirely in simulation to transfer to a physical quadrotor without fine-tuning (Loquercio *et al.*, 2020). Its effectiveness nevertheless depends on whether simulated variation adequately represents real-world uncertainty.

Simulation is therefore a controlled experimental environment rather than definitive evidence of real-world performance, and formal verification remains important where safety is critical (Luckcuck *et al.*, 2019). This project accordingly uses simulation to compare perception configurations repeatably, not to claim physical flight capability.

### Research Gap

Efficient models and embedded deployments are commonly evaluated using accuracy, operation counts, latency and memory (Sze *et al.*, 2017; Jacob *et al.*, 2018; Hernandez and Brown, 2020). However, these measures do not establish whether a perception model enables an autonomous system to complete its task reliably. Because perception feeds control, its errors and delays can alter behaviour in ways offline evaluation may not reveal. Codevilla *et al.* (2018) demonstrated this in simulated autonomous driving: models with similar offline error could drive very differently, although better-chosen validation data and metrics made offline results more predictive.

A systematic review identifies continuing challenges in developing rigorous, domain-specific evaluation measures for robotic systems (Araujo, Mousavi and Varshosaz, 2023). Proposed measures include the PERFORM metric for marine testbeds (Dalpe, Thein and Renken, 2021), task-relevant object-detection metrics (Badithela *et al.*, 2025) and holistic robotic assessment frameworks (Muepu, Watanobe and Naruse, 2025), but none of these addresses perception under nano-UAV resource constraints. Closest to this project, Cereda *et al.* (2023) flew several CNNs found by neural architecture search aboard a nano-UAV. Their best model reduced in-field control error by 32% against the baseline, yet a faster variant with roughly equivalent test error completed on average only 35% of a test path in an unseen environment, echoing Codevilla *et al.* (2018). However, all four nano-UAV studies reviewed here share authors and Crazyflie hardware. It therefore remains unclear how accuracy and efficiency jointly determine closed-loop nano-UAV performance across systematically varied models.

This project addresses that gap by evaluating CNN configurations of differing accuracy and efficiency within a repeatable simulated target-approach task under nano-UAV constraints. It investigates whether better model-level metrics translate into better closed-loop performance, measured through mission success, tracking error and target loss.


## Methodology

lorem ipsum dolor sit amet consectetur adipiscing elit quibusdam facilis qui excepturi assumenda similique pariatur eiusmod minus minus cum culpa cillum quos dolorem consequat qui ullamco ex facilis dolore minus nisi officia similique in labore qui nisi quidem et eligendi repellendus cupidatat dolor temporibus ex ut id ut atque nisi

## Results and Analysis

lorem ipsum dolor sit amet consectetur adipiscing elit quibusdam facilis qui excepturi assumenda similique pariatur eiusmod minus minus cum culpa cillum quos dolorem consequat qui ullamco ex facilis dolore minus nisi officia similique in labore qui nisi quidem et eligendi repellendus cupidatat dolor temporibus ex ut id ut atque nisi

## Project Evaluation

lorem ipsum dolor sit amet consectetur adipiscing elit quibusdam facilis qui excepturi assumenda similique pariatur eiusmod minus minus cum culpa cillum quos dolorem consequat qui ullamco ex facilis dolore minus nisi officia similique in labore qui nisi quidem et eligendi repellendus cupidatat dolor temporibus ex ut id ut atque nisi

## Further Work and Conclusion

lorem ipsum dolor sit amet consectetur adipiscing elit quibusdam facilis qui excepturi assumenda similique pariatur eiusmod minus minus cum culpa cillum quos dolorem consequat qui ullamco ex facilis dolore minus nisi officia similique in labore qui nisi quidem et eligendi repellendus cupidatat dolor temporibus ex ut id ut atque nisi

## Glossary

lorem ipsum dolor sit amet consectetur adipiscing elit quibusdam facilis qui excepturi assumenda similique pariatur eiusmod minus minus cum culpa cillum quos dolorem consequat qui ullamco ex facilis dolore minus nisi officia similique in labore qui nisi quidem et eligendi repellendus cupidatat dolor temporibus ex ut id ut atque nisi

## Table of Abbreviations

lorem ipsum dolor sit amet consectetur adipiscing elit quibusdam facilis qui excepturi assumenda similique pariatur eiusmod minus minus cum culpa cillum quos dolorem consequat qui ullamco ex facilis dolore minus nisi officia similique in labore qui nisi quidem et eligendi repellendus cupidatat dolor temporibus ex ut id ut atque nisi

## References / Bibliography

### Note for later self these are inside Lit Review

Aljalbout, E. *et al.* (2026) ‘The reality gap in robotics: Challenges, solutions, and best practices’, *Annual Review of Control, Robotics, and Autonomous Systems*, 9(1), pp. 403–432. Available at: https://doi.org/10.1146/annurev-control-031924-100130.

Araujo, H., Mousavi, M.R. and Varshosaz, M. (2023) ‘Testing, validation, and verification of robotic and autonomous systems: A systematic review’, *ACM Transactions on Software Engineering and Methodology*, 32(2), pp. 1–61. Available at: https://doi.org/10.1145/3542945.

Badithela, A., Srivastav, R., Wongpiromsarn, T. and Murray, R. (2025) ‘Task-relevant evaluation metrics of object detection for quantitative system-level analysis of safety-critical autonomous systems’, *ACM Transactions on Cyber-Physical Systems* [Online first]. Available at: https://doi.org/10.1145/3771284.

Bhat, G.R. *et al.* (2024) ‘Autonomous drones and their influence on standardization of rules and regulations for operating – A brief overview’, *Results in Control and Optimization*, 14, p. 100401. Available at: https://doi.org/10.1016/j.rico.2024.100401.

Bialas, J., Mohebbi, M.R., van Veelen, M.J., Mejia-Aguilar, A., Kathrein, R. and Döller, M. (2026) ‘From human teams to autonomous swarms: A reinforcement learning-based benchmarking framework for unmanned aerial vehicle search and rescue missions’, *Drones*, 10(2), p. 79. Available at: https://doi.org/10.3390/drones10020079.

Boroujerdian, B. *et al.* (2021) ‘The role of compute in autonomous micro aerial vehicles: Optimizing for mission time and energy efficiency’, *ACM Transactions on Computer Systems*, 39(1–4), pp. 1–44. Available at: https://doi.org/10.1145/3511210.

Carrio, A., Sampedro, C., Rodriguez-Ramos, A. and Campoy, P. (2017) ‘A review of deep learning methods and applications for unmanned aerial vehicles’, *Journal of Sensors*, 2017, p. 3296874. Available at: https://doi.org/10.1155/2017/3296874.

Cereda, E., Crupi, L., Risso, M., Burrello, A., Benini, L., Giusti, A., Jahier Pagliari, D. and Palossi, D. (2023) ‘Deep neural network architecture search for accurate visual pose estimation aboard nano-UAVs’, in *2023 IEEE International Conference on Robotics and Automation (ICRA)*. Piscataway, NJ: IEEE, pp. 6065–6071. Available at: https://doi.org/10.1109/ICRA48891.2023.10160369.

Codevilla, F., López, A.M., Koltun, V. and Dosovitskiy, A. (2018) ‘On offline evaluation of vision-based driving models’, in Ferrari, V., Hebert, M., Sminchisescu, C. and Weiss, Y. (eds) *Computer Vision – ECCV 2018*. Cham: Springer (Lecture Notes in Computer Science, 11219), pp. 246–262. Available at: https://doi.org/10.1007/978-3-030-01267-0_15.

Dalpe, A.J., Thein, M.-W.L. and Renken, M. (2021) ‘PERFORM: A metric for evaluating autonomous system performance in marine testbed environments using interval Type-2 fuzzy logic’, *Applied Sciences*, 11(24), p. 11940. Available at: https://doi.org/10.3390/app112411940.

Falanga, D., Kim, S. and Scaramuzza, D. (2019) ‘How fast is too fast? The role of perception latency in high-speed sense and avoid’, *IEEE Robotics and Automation Letters*, 4(2), pp. 1884–1891. Available at: https://doi.org/10.1109/LRA.2019.2898117.

Hanafy, W.A., Molom-Ochir, T. and Shenoy, R. (2021) ‘Design considerations for energy-efficient inference on edge devices’, in *Proceedings of the Twelfth ACM International Conference on Future Energy Systems*. New York, NY: ACM, pp. 302–308. Available at: https://doi.org/10.1145/3447555.3465326.

Hashim, H.A. (2025) ‘Advances in UAV avionics systems architecture, classification and integration: A comprehensive review and future perspectives’, *Results in Engineering*, 25, p. 103786. Available at: https://doi.org/10.1016/j.rineng.2024.103786.

Hernandez, D. and Brown, T.B. (2020) ‘Measuring the algorithmic efficiency of neural networks’, *arXiv* [Preprint]. Available at: https://arxiv.org/abs/2005.04305v1 (Accessed: 2 November 2026).

Howard, A.G., Zhu, M., Chen, B., Kalenichenko, D., Wang, W., Weyand, T., Andreetto, M. and Adam, H. (2017) ‘MobileNets: Efficient convolutional neural networks for mobile vision applications’, *arXiv* [Preprint]. Available at: https://arxiv.org/abs/1704.04861v1 (Accessed: 2 November 2026).

Hsu, K.-C., Hu, H. and Fisac, J.F. (2024) ‘The safety filter: A unified view of safety-critical control in autonomous systems’, *Annual Review of Control, Robotics, and Autonomous Systems*, 7(1), pp. 47–72. Available at: https://doi.org/10.1146/annurev-control-071723-102940.

Jacinto, M., Pinto, J., Patrikar, J., Keller, J., Cunha, R., Scherer, S. and Pascoal, A. (2024) ‘Pegasus Simulator: An Isaac Sim framework for multiple aerial vehicles simulation’, in *2024 International Conference on Unmanned Aircraft Systems (ICUAS)*. Piscataway, NJ: IEEE, pp. 917–922. Available at: https://doi.org/10.1109/ICUAS60882.2024.10556959.

Jacob, B., Kligys, S., Chen, B., Zhu, M., Tang, M., Howard, A., Adam, H. and Kalenichenko, D. (2018) ‘Quantization and training of neural networks for efficient integer-arithmetic-only inference’, in *2018 IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)*. Piscataway, NJ: IEEE, pp. 2704–2713. Available at: https://doi.org/10.1109/cvpr.2018.00286.

Kanellakis, C. and Nikolakopoulos, G. (2017) ‘Survey on computer vision for UAVs: Current developments and trends’, *Journal of Intelligent & Robotic Systems*, 87(1), pp. 141–168. Available at: https://doi.org/10.1007/s10846-017-0483-z.

Kaur, P., Taghavi, S., Tian, Z. and Shi, W. (2021) ‘A survey on simulators for testing self-driving cars’, in *2021 Fourth International Conference on Connected and Autonomous Driving (MetroCAD)*. Piscataway, NJ: IEEE, pp. 62–70. Available at: https://doi.org/10.1109/MetroCAD51599.2021.00018.

Loquercio, A., Kaufmann, E., Ranftl, R., Dosovitskiy, A., Koltun, V. and Scaramuzza, D. (2020) ‘Deep drone racing: From simulation to reality with domain randomization’, *IEEE Transactions on Robotics*, 36(1), pp. 1–14. Available at: https://doi.org/10.1109/TRO.2019.2942989.

Luckcuck, M., Farrell, M., Dennis, L.A., Dixon, C. and Fisher, M. (2019) ‘Formal specification and verification of autonomous robotic systems: A survey’, *ACM Computing Surveys*, 52(5), pp. 1–41. Available at: https://doi.org/10.1145/3342355.

Muepu, D.M., Watanobe, Y. and Naruse, K. (2025) ‘Toward a holistic framework for robotic assessment: A survey on performance, software, and environmental adaptability’, *IEEE Access*, 13, pp. 136996–137011. Available at: https://doi.org/10.1109/access.2025.3595386.

Muratore, F., Ramos, F., Turk, G., Yu, W., Gienger, M. and Peters, J. (2022) ‘Robot learning from randomized simulations: A review’, *Frontiers in Robotics and AI*, 9, p. 799893. Available at: https://doi.org/10.3389/frobt.2022.799893.

Niculescu, V., Lamberti, L., Conti, F., Benini, L. and Palossi, D. (2021) ‘Improving autonomous nano-drones performance via automated end-to-end optimization and deployment of DNNs’, *IEEE Journal on Emerging and Selected Topics in Circuits and Systems*, 11(4), pp. 548–562. Available at: https://doi.org/10.1109/JETCAS.2021.3126259.

Palossi, D., Loquercio, A., Conti, F., Flamand, E., Scaramuzza, D. and Benini, L. (2019) ‘A 64-mW DNN-based visual navigation engine for autonomous nano-drones’, *IEEE Internet of Things Journal*, 6(5), pp. 8357–8371. Available at: https://doi.org/10.1109/jiot.2019.2917066.

Palossi, D., Zimmerman, N., Burrello, A., Conti, F., Muller, H., Gambardella, L.M., Benini, L., Giusti, A. and Guzzi, J. (2022) ‘Fully onboard AI-powered human-drone pose estimation on ultralow-power autonomous flying nano-UAVs’, *IEEE Internet of Things Journal*, 9(3), pp. 1913–1929. Available at: https://doi.org/10.1109/jiot.2021.3091643.

Ronzhin, A., Ryabinov, A., Shkodina, E., Saveliev, A., Cherskikh, E. and Figurek, A. (2026) ‘UAV-assisted pesticide application in potato cultivation under waterlogged soil conditions: Orthophotomap-based monitoring and field assessment’, *Sustainability*, 18(9), p. 4567. Available at: https://doi.org/10.3390/su18094567.

Sandler, M., Howard, A., Zhu, M., Zhmoginov, A. and Chen, L.-C. (2018) ‘MobileNetV2: Inverted residuals and linear bottlenecks’, in *2018 IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)*. Piscataway, NJ: IEEE, pp. 4510–4520. Available at: https://doi.org/10.1109/cvpr.2018.00474.

Sze, V., Chen, Y.-H., Yang, T.-J. and Emer, J.S. (2017) ‘Efficient processing of deep neural networks: A tutorial and survey’, *Proceedings of the IEEE*, 105(12), pp. 2295–2329. Available at: https://doi.org/10.1109/jproc.2017.2761740.

Tobin, J., Fong, R., Ray, A., Schneider, J., Zaremba, W. and Abbeel, P. (2017) ‘Domain randomization for transferring deep neural networks from simulation to the real world’, in *2017 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)*. Piscataway, NJ: IEEE, pp. 23–30. Available at: https://doi.org/10.1109/iros.2017.8202133.

Xu, B., Gao, F., Yu, C., Zhang, R., Wu, Y. and Wang, Y. (2024) ‘OmniDrones: An efficient and flexible platform for reinforcement learning in drone control’, *IEEE Robotics and Automation Letters*, 9(3), pp. 2838–2844. Available at: https://doi.org/10.1109/LRA.2024.3356168.

## Appendix A: First Appendix

## Appendix A – Supervisor Meeting Notes

### Meeting 1 – 22 October 2026

| **Detail**        | **Information**                                               |
| :---------------- | :------------------------------------------------------------ |
| **Module**        | UFCFXK-30-3: Digital Systems Project                          |
| **Project Title** | Efficient AI-Based Visual Perception for Autonomous Nano-UAVs |
| **Student**       | Oliver Mercer                                                 |
| **Supervisor**    | Mark Rhodes                                                   |
| **Meeting Date**  | 22 October 2026                                               |

### Discussion Points

The following topics were discussed during the meeting:

1. **Drone Convolutional Neural Networks (CNNs):** Discussion surrounding the application of convolutional neural networks within autonomous drone systems.

2. **Python Development:** Considerations regarding Python programming and its role in the development of the project.

3. **Drone Human Avoidance:** Discussion of obstacle and human avoidance capabilities within autonomous UAV systems.

4. **Flight Controller Development:** Investigating the possibility of training and testing the flight controller using the student rather than other human participants, taking ethical considerations into account.

5. **Postgraduate Opportunities:** Discussion of potential references for future Master's programme applications following completion of the undergraduate degree.

### Agreed Actions

| **Responsible Party** | **Action**                                                                                                                                                         | **Target Date**   |
| :-------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---------------- |
| Student               | Investigate the ArduDeck platform, particularly its capabilities for sending instructions to a UAV and integrating custom Python scripts with a flight controller. | Not specified     |
| Student               | Begin background research to support the literature review.                                                                                                        | Ongoing           |
| Student               | Begin drafting the literature review and introduction sections of the project report, providing draft copies to the supervisor for feedback before submission.     | Before submission |
| Supervisor            | Review and sign off the project proposal.                                                                                                                          | 26 October 2026   |
| Supervisor            | Complete the project's Ethical Checklist.                                                                                                                          | 26 October 2026   |

---
