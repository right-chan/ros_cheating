# ros_cheating

```bash
catkin_create_pkg <패키지 이름> <의존성1> <의존성2> roscpp std_msgs ...
```


# 커스텀 메시지 만들기
```bash
catkin_create_pkg <메시지 패키지 이름> message_generation std_msgs ...
```

CMakeLists.txt에 추가할 메시지 선언, 의존하는 메시지 설정
```make
add_message_files(
  FILES
  SensorData.msg
)
generate_messages(
  DEPENDENCIES
  std_msgs
)
```

package.xml에 실행할 때 의존성 추가
```xml
<exec_depend>message_runtime</exec_depend>
```
# 메시지 사용하기
```cmake
find_package(catkin REQUIRED COMPONENTS
    roscpp
    my_msgs
)
```
```c++
#include <my_msgs/SensorData.h>
my_msgs::SensorData count;
ros::Publisher pub_number = nh.advertise<my_msgs::SensorData>("/topic", 10);
```
