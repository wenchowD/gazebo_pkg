使用方法：

    1.将gazebo_pkg包复制到工作空间src目录下

    2.先catkin_make编译，再source bashrc或setup.bash

        2.1 为了防止启动时编码报错，更改python2 的默认编码
            解决方案：
            打开终端输入如下指令：
            sudo gedit /usr/lib/python2.7/site.py (使用anaconda的同学要定位到自己的虚拟环境)
            找到 setencoding() 函数
            修改第 一 个 encoding="utf-8"
            重启电脑

    3.把gazebo_pkg包中的models文件夹内的东西全部复制到.gazebo/models下（.gazebo为隐藏文件，如果没有models请自行创建此文件夹）
        前提：没有打开过gazebo的同学，请在终端中输入gazebo运行一次

    4.运行比赛的仿真
        roslaunch gazebo_pkg race.launch
    
    其他情况：
        现象： 在终端出现
        Gazebo [Err] [REST.cc:205] Error in REST request
        解决方法：
        打开终端输入：
        sudo gedit ~/.ignition/fuel/config.yaml
        用 url: https://api.ignitionrobotics.org 替换 url : https://api.ignitionfuel.org



Package说明：

    .包内的models文件夹在完成了上述的操作后便不再需要
    .meshes文件夹包含模型的文件无需修改

    1.world文件夹存储仿真用的世界
        下有arena.world arena_sim1.world，分别为空场地和模拟比赛的场地

    2.urdf文件夹存储机器人描述文件
        xacro文件包含机器人的长，宽，高，颜色，传感器等信息，我已更具比赛使用的机器人做了相应的修改

    3.launch文件夹存储启动文件
        修改可选择所启动的世界，和机器人出生位置（当前为启动arena_sim1.world，出生在比赛起点）

    *.修改视觉识别任务的目标图片
        进入.gazebo/models目录，找到需要替换的类别对应的文件夹 panel_XXX（e.g. panel_person）并进入该文件夹
        替换 materials/textures目录下的 XXX.png（e.g. person.png）
        注意图片格式为png且名称保持前后一致



编辑自己的场地：

    1.终端输入以下命令来倒入一个现成的世界：
    gazebo /XXX_ws/src/gazebo_pkg/XXX.world (替换成自己的存储.world文件的地址)

    2.gazebo图形界面左上角点击Insert，再点击想要添加的模型名称可向世界添加模型

    3.gazebo图形界面上方可调整模型位置以及姿态

    *.更多操作请见参考



参考：

    画墙：https://classic.gazebosim.org/tutorials?cat=build_world&tut=building_editor

    贴图：https://www.guyuehome.com/37739
    
    URDF：略

