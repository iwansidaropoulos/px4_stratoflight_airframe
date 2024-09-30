# px4_stratoflight_airframe

## Links
Voici une liste de liens utiles pour le projet :

- [Documentation PX4](https://docs.px4.io) - Documentation officielle du firmware PX4.
- [GitHub PX4](https://github.com/PX4/PX4-Autopilot) - Dépôt GitHub de PX4 Autopilot.
- [Stratoflight Mission Overview](https://stratoflight.com/mission-overview) - Détails de la mission StratoFlight.
- [QGroundControl](https://qgroundcontrol.com/) - Interface de contrôle pour le firmware PX4.
- [MAVLink Protocol](https://mavlink.io/en/) - Documentation du protocole MAVLink utilisé par PX4.

- [PAX4 Paramotor Project](https://discuss.px4.io/t/px4-paramotor-project-2-first-autonomous-mission-rtl-altitude-stabilized-flight/31125?u=junwoo0914) - Autonomous flight.
- [Paramotor Kits](https://www.opale-paramodels.com/gb/20-rc-paramotor-kits) - RC paramotor kits.
- [Paramotor Tuto](https://www.youtube.com/watch?v=-71S14kg7aU) - Paramotor flight tuto.
- [QGroundControl User Guide](https://docs.qgroundcontrol.com/master/en/qgc-user-guide/) - QGroundControl user guide.
- [QGroundControl Dev Guide](https://docs.qgroundcontrol.com/master/en/qgc-dev-guide/) - QGroundControl dev guide.


Liens d'Allan :

- [PFE parachute autonome](https://www.ensta-bretagne.fr/jaulin/rapport_pfe_kevin_bedin.pdf) - Rapport de PFE sur parachute autonome.
- [Simulateur parapente](https://liberiste.com/simulateur-parapente-gratuit/) - Simulateur de parapente.
- [Forum PX4 paramoteur](https://discuss.px4.io/c/px4/paramotor/51) - Modèles PX4 paramoteur les plus récents (airframe le plus proche => fixed wing).
- [SITL Simulation Environment](https://docs.px4.io/main/en/simulation/#sitl-simulation-environment) - Documentation pour SITL sur PX4.
- [Airframes](https://docs.px4.io/main/en/dev_airframes/) - Documentation pour les airframes sur PX4.
- [Control Allocation](https://docs.px4.io/main/en/concept/control_allocation.html) - Documentation pour control allocation sur PX4.
- [Adding a new airframe group](https://docs.px4.io/main/en/dev_airframes/adding_a_new_frame.html#adding-a-new-airframe-group) - Documentation sur l'ajout d'un nouveau airframe group sur PX4.
- [PX4 ROS 2](https://docs.px4.io/main/en/ros2/px4_ros2_interface_lib.html) - Documentation sur une librairie d'interfaçage avec ROS2.
- [Discord PX4](https://discord.gg/dronecode) - Discord PX4.
- [Video of Integrated UAV Simulation](https://www.youtube.com/live/j4EZoyoVZD8?si=WFofWvx0o-Q3I7TE) - Rediffusion de live YouTube "Integrated UAV Simulation Workflows".










### 1. **Modélisation : ROS2 vs ROS1 vs MAVSDK**
   - **ROS1** représente la version antérieure du middleware ROS, tandis que **ROS2** est une version plus moderne et améliorée. ROS2 bénéficie d'un meilleur support, offre de meilleures performances, notamment en termes de communication et de gestion réseau, et est recommandé pour les nouveaux projets.
   - **ROS2** est en effet plus complexe que **MAVSDK**, car il propose un **écosystème robotique complet**, avec de nombreuses fonctionnalités (gestion des capteurs, perception, planification, etc.), alors que MAVSDK est plus simple et spécifiquement axé sur le **contrôle des drones PX4 via MAVLink**.
   - Lors de l'utilisation de **ROS2**, il est nécessaire de recourir à **MAVROS** pour interfacer ROS2 avec PX4 via MAVLink, car MAVROS agit comme un pont entre les environnements ROS et MAVLink.

### 2. **API pour relier la modélisation à la simulation : MAVROS vs MAVSDK/MAVLink**
   - Si l'on opte pour **ROS2**, l'utilisation de **MAVROS** est essentielle pour communiquer avec **PX4**. MAVROS permet de convertir les messages MAVLink (protocole utilisé par PX4) en messages compatibles ROS, ce qui permet d’envoyer des commandes de vol depuis ROS2 et de recevoir des données de télémétrie.
   - En revanche, si **MAVSDK** est utilisé, **MAVROS** n'est pas nécessaire car MAVSDK communique directement avec PX4 via le protocole **MAVLink**. MAVSDK encapsule MAVLink dans une API simple, mais il est également possible de travailler directement avec **MAVLink** pour un contrôle plus bas niveau.

### 3. **Simulation : Gazebo vs jMAVSim**
   - Avec **ROS2**, **Gazebo** est l'option privilégiée, car il s'intègre très bien à l'écosystème ROS (grâce à des packages comme **gazebo_ros**) et permet des simulations réalistes avec des environnements et capteurs complexes.
   - Si l'on utilise **MAVSDK**, le choix peut se porter sur **Gazebo** ou **jMAVSim** pour la simulation. **Gazebo** offre plus de réalisme et de flexibilité, tandis que **jMAVSim** est plus léger et convient mieux pour des simulations simples, sans la lourdeur de Gazebo.

### **En résumé** :
- **Modélisation :** **ROS2** est plus avancé mais plus complexe que **MAVSDK**. **ROS1** est moins performant et moins recommandé aujourd'hui.
- **API :** Avec **ROS2**, l'utilisation de **MAVROS** est indispensable pour interfacer avec PX4. Avec **MAVSDK**, la communication directe avec MAVLink rend MAVROS superflu.
- **Simulation :** Avec **ROS2**, **Gazebo** est le choix recommandé. Avec **MAVSDK**, il est possible de choisir entre **Gazebo** (plus réaliste) et **jMAVSim** (plus simple).

