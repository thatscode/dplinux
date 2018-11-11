# Bash数组-判断某个元素是否在数组内的几种方法

## 声明一个数组array，一个待测试元素var

```
array=(
element1
element2
element3
)

var="element1"
```

## 接下来用几种方法来分别测试var是否是array中的元素

### 判断方法1：
```
echo "${array[@]}" | grep -wq "$var" &&  echo "Yes" || echo "No"
```

### 判断方法2：
```
for i in ${array[@]}
do
   [ "$i" == "$var" ] && echo "yes"
done
```

### 判断方法3：这是个人感觉最巧妙的一种测试方法，使用了bash数组的内置方法。
```
[[ ${array[@]/${var}/} != ${array[@]} ]] && echo "Yes" || echo "No"
```

## 测试演示

```
# 声明数组array、变量var
[root(0)@dplinux ~]# array=(
> element1
> element2
> element3
> )
[root(0)@dplinux ~]#
[root(0)@dplinux ~]# var="element1"
# 确认数组和变量值
[root(0)@dplinux ~]# echo ${array[@]}
element1 element2 element3
[root(0)@dplinux ~]# echo $var
element1
[root(0)@dplinux ~]#
# 判断方法1
[root(0)@dplinux ~]# echo "${array[@]}" | grep -wq "$var" &&  echo "Yes" || echo "No"
Yes
[root(0)@dplinux ~]#
# 判断方法2
[root(0)@dplinux ~]# for i in ${array[@]}
> do
>    [ "$i" == "$var" ] && echo "yes"
> done
yes
[root(0)@dplinux ~]#
# 判断方法3
[root(0)@dplinux ~]# [[ ${array[@]/${var}/} != ${array[@]} ]] && echo "Yes" || echo "No"
Yes
[root(0)@dplinux ~]#
```



