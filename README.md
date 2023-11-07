# Visual_task
# LuoGu-Opencv
A Record

(emmmmmm。。。。。。很抱歉一直拖到现在才把Github仓库建起来)

2023.10.10 学习C++的基础语法，和python语法大差不差，不过C++要更细致一点，语法是很好理解，但做题就不知道了。之前学的都是python，还没系统接触过C++。所以还是从最基础的开始学。

2023.10.12 在洛谷上做顺序结构和分支结构的题目，感觉还是手生，和python的撰写语法有一点不同。还需要一点时间去适应

2023.10.13 继续做题

2023.10.14 在CSDN上学习了类与对象，默认成员函数，析构函数等，脑子是读懂了，就是不知道手会不会

2023.10.15 继续在CSDN上学习C++的面向对象和其他数据结构如链表，哈希表的理论知识

2023.10.16 在洛谷刷数组的题，比较有意思的题目是个叫插火把的题目，主要要小心边界的判断。然后其他几道题都差不多一个思路，用暴力双循环（甚至三循环）都能解决

2023.10.18 尝试在洛谷上刷字符串的题目，了解了ASC码的应用，还有就是发现数据量小并且形式固定的题目的话，打表还挺方便。实现起来嘎嘎快，就是要注意index的匹配问题。还学到了一个新思路，有穷自动机，就是让代码分好几种状态，每种状态做不同的事。

2023.10.20 在洛谷刷了10到循环的题目，解题思路大都大同小异（用全排序就可以解决掉3道题，还有就是提取数位的通法也可以应用在其他题上），花费较长时间的是回文质数，这题难点在于TLE，数据量太大，在优化素数查找函数时参考了其他人的代码，还挺妙的。

2023.10.21洛谷刷函数题

2023.10.22 学习递归和递推，从最基础的斐波那契数列再到递归实现指数型枚举再到递归实现排列型枚举，有点不能理解递归的实现逻辑。特别是里面涉及到的一个恢复现场的操作，不是很能理解。好像是递归树会返回到上一个节点。             
          
          void dfs(int u)
          {
              if (u > n)  
              {
                  for (int i = 1; i <= n; i ++ ) printf("%d ", state[i]); 
                  puts("");
                  return;
              }
              for (int i = 1; i <= n; i ++ )
                  if (!used[i])
                  {
                      state[u] = i;
                      used[i] = true;
                      dfs(u + 1);
          
                      //恢复现场
                      state[u] = 0;
                      used[i] = false;
                  }
          }

2023.10.23 学习前缀和与差分

2023.10.24 想起洛谷一道题目有用到递归，连用了三个递归函数，后面通过不断设置断点去研究整个过程才总算明白递归树的执行顺序。大概是到达最小节点（不会再有分支时），又会重新回到上一个节点，再去找该节点下的分支
	
 
 void di(int x,int l,int q) 
	{
		if(x==2) 
		{
			a[l][q]=0;
			return;
		}
		for(int i=l; i<=l+x/2-1; i++)
			for(int j=q; j<=q+x/2-1; j++)
				a[i][j]=0; 
		di(x/2,l+x/2,q);
		di(x/2,l+x/2,q+x/2); 
		di(x/2,l,q+x/2); 
	}


2023.10.25 学习二分

2023.10.26 学习了一下排序算法，一个是快排，一个是归并排序。emmmm在这个边界问题上想了好久。。。。
          
          
          void quick_sort(int q[], int l, int r)
          {
              if (l >= r) return;
          
              int i = l - 1, j = r + 1, x = q[l + r >> 1];
              while (i < j)
              {
                  do i ++ ; while (q[i] < x);
                  do j -- ; while (q[j] > x);
                  if (i < j) swap(q[i], q[j]);
              }
          
              quick_sort(q, l, j);
              quick_sort(q, j + 1, r);
          }

2023.10.27学习了下双指针，一个是对撞指针，一个是快慢指针。

2023.10.28突然想到该学学opencv了，大致看了下相关的语法，感觉很抽象。

2023.10.30刚好应追光社技术部需求，在pycharm用opencv做了一个非常非常简单的小玩具：二维码识别，调库使得很多东西都很快可以实现

2023.10.31尝试用opencv去做一个物体长度测量的小项目，这个感觉就有点难了。大致的思路应该是对图像进行阈值处理，得到一个二值图（如果识别区域的辨识度不高那阈值处理的效果岂不是很差？）或者用形态学操作用erode和dilate，或者用色彩通道分割来识别有特定颜色的物体。这样可以把主体物体提取出来，然后用cv函数查找轮廓（不清楚是怎么提高轮廓检测的精度，也不知道这个储存边缘数据的形式是什么）
          
              finalCountours = []
              contours , hiearchy = cv2.findContours(imgThre,cv2.RETR_EXTERNAL,cv2.CHAIN_APPROX_SIMPLE)
              for i in contours:
                  area = cv2.contourArea(i)
                  if area > minArea:
                      peri = cv2.arcLength(i,True)
                      approx = cv2.approxPolyDP(i,0.02*peri,True)
                      bbox = cv2.boundingRect(approx)
                      if filter > 0:
                          if len(approx) == filter:
                              finalCountours.append([len(approx),area,approx,bbox,i])
                      else:
                          finalCountours.append([len(approx),area,approx,bbox,i])
          
              finalCountours = sorted(finalCountours,key = lambda x:x[1] ,reverse=True)



2023.11.1继续研究opencv
          
          if len(conts) != 0:
              biggest = conts[0][2]
           //（这是什么操作？为什么要提取了[0][2]的元素）
          if len(conts) != 0:
              for obj in conts:
                  cv2.polylines(img,[obj[2]],True,(0,255,0),3)
                  npoints = contour.reorder(obj[2])
                  nw = round((contour.find(npoints[0][0],npoints[1][0])),1)
                  nh = round((contour.find(npoints[0][0], npoints[2][0])), 1)
          // 这个是个矩阵？里面的idex又代表了什么，还是不理解。


2023.11.4尝试在VS上配置Opencv环境，花了好几个小时，然而试了好多次都不成功。。。。试过用编译好的opencv源码或者用cmake编译然后去进行配置，但最后在VS上运行测试代码，总是显示配置的json文件有问题。。。。。

2023.11.5尝试用python实现坐标的转换。通过询问gpt了解到可以使用矩阵的仿射变换来实现。然后在实际写的过程中又发现，我不知道怎么求出坐标系的旋转参数（在给定原点和xy轴数据的情况下），后面发现可以用向量点积的方式求夹角。理论可行。。。但是当代码实际跑起来时出现的bug一大堆，也不知道是不是仿射变换矩阵出了问题，把里面的数据稍微改一下坐标变换就不能正常实现。实在debug不出来，真是难受。。。。。。

2023.11.6想尝试用Github上开源的Yolo模型来训练数据然后去识别指定物体，然后用anaconda配置pytorch，发现导入时报错了，试了重装，换版本还是不行。。。








