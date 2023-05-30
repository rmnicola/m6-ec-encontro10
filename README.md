# m6-ec-encontro9

# Setar o destino do robô manualmente no RViz

# Definir sequências de pontos pela API em Python

# Mapear o TurtleBot World com SLAM

## Mapeando
Em três terminais paralelos:

```
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py

```
(abre o Turtlebot World no Gazebo)

```
ros2 launch turtlebot3_cartographer cartographer.launch.py use_sim_time:=True

```
(abre o modo de mapeamento do RViz)

```
ros2 run turtlebot3_teleop teleop_keyboard
```
(abre o tópico de controle de movimentação do robô pelo teclado)

Então, movimente o robô por todo o mundo até que o mapa esteja bem delimitado no RViz (branco nas áreas livres e escuro nos obstáculos, sem manchas cinza no meio)


## Salvando o mapa
Na raiz do sistema operacional (~):
```
mkdir maps
cd maps
```
Rode o seguinte comando para salvar o mapa:
```
ros2 run nav2_map_server map_saver_cli -f <nome-do-mapa>
```
Se tudo deu certo, é para ter um arquivo "<nome-do-mapa>.pmg" e "<nome-do-mapa>.yaml" na pasta "maps".

## Abrir um mapa para navegação no RViz
### Resolvendo bug de importação do mapa
```
sudo apt update
```
```
sudo apt install ros-humble-rmw-cyclonedds-cpp
```
```
gedit ~/.bashrc
```
Adicione a seguinte linha:
```
export RMW_IMPLEMENTATION=rmw_cyclonedds_cpp
```
Depois, vá para o seguinte caminho:
```
cd ~/opt/ros/humble/share/turtlebot3_navigation2/param
```
Altere o arquivo "waffle.yaml" pelo sudo gedit ou vim. Substitua a linha robot_model_type por:
```
robot_model_type: "nav2_amcl::DifferentialMotionModel"
```
### Abrir o mapa em si

## Construindo e mapeando um mundo novo

