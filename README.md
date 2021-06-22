# Pose2Carton 

EE228 课程大作业 利用3D骨架控制3D卡通人物 (https://github.com/yuzhenbo/pose2carton) 

数据组别： 25

数据类型： 10组匹配 + 5组蒙皮)


# Maya 环境配置

1. 完成Autodesk 学生认证， 下载Windows版Maya2020。

2. 安装Maya及组件，若安装路径下未成功生成安装文件，运行Maya.msi ，修复安装。

3. 进入maya2020安装目录，进入bin文件夹，将该路径添加到环境变量。通过打开cmd，输入mayapy检测是否成功添加。

4. 打开cmd，依次输入：

   ```text
   curl https://bootstrap.pypa.io/pip/2.7/get-pip.py -o get-pip.py
   mayapy get-pip.py
   mayapy -m pip install -i https://pypi.anaconda.org/carlkl/simple numpy
   ```

5.  在mayapy中检测以下命令能否顺利运行。若不报错，则maya环境配置完成。

   ```text
   import maya
   import maya.standalone
   maya.standalone.initialize(name='python')
   import maya.OpenMaya as om
   import maya.cmds as cmds
   import pymel.core as pm
   import maya.mel as mel
   import numpy as np
   import os
   import glob
   ```

   

# 匹配流程

## 代码说明

* fbx_parser.py：解析fbx文件，生成obj格式的模型，以及材质引用文件.mtl，同时产生存放模型材质贴图的.fbm文件夹，并将模型关节信息、拓扑结构和skin信息存储到txt文件中。
* transfer.py：基于fbx_parser.py生成的txt文件中的关节节点信息进行匹配，将给定人体模型的动作迁移到新模型上。生成各动作obj模型和txt信息。
* vis.py：结果可视化。

## 匹配

1. 在cmd中运行`mayapy fbx_parser.py model_name.fbx`生成obj、txt、mtl、fbm文件。
2. 运行transfer.py，得到模型关节拓扑，与SMPL进行映射，匹配关节点。将映射关系填入transfer.py中的字典中。
3. 运行transfer.py，得到匹配后的动作序列。
4. 将.fbm文件夹和.mtl文件移入obj_seq_5_3dmodel文件夹中，将mtl文件中的映射路径改为相对路径。
5. 运行vis.py，完成可视化。



xxx (如果你写了自己的脚本来处理数据或进行可视化，请在这里进行相关说明(如何使用等)； 如果没有，请忽略该模块。)



# 项目结果

![image](./img/result.png))



# 协议 

本项目在 Apache-2.0 协议下开源

所涉及代码及数据的所有权以及最终解释权归倪冰冰老师课题组所有. 

# 
