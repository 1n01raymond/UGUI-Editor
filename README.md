# UGUI Development Process
Usage: Download and unzip the folder and place it in the Assets folder of your project (the folder is named UGUI-Editor, if you want to use another name, you need to modify the FolderName field in the Configure.cs file, otherwise you will get an error and cannot find it Resources). You can also use git subtree as a sub-library management, such as:

git subtree add --prefix=Assets/UGUI-Editor https://github.com/liuhaopen/UGUI-Editor.git master --squash  

Most of the functions are enabled by default.If you feel that they are not easy to use, you can turn off the corresponding functions in the Configure.cs file, set it to false and it will take effect immediately:
![image](https://github.com/liuhaopen/ReadmeResources/blob/master/UGUI-Editor/configure.png)

## PrefabWin
Generally, some common and commonly used resources will be made into prefab, such as some buttons, text styles, etc., and then used to pull it into the scene in the Project view, but the project view does not see the preview image of the prefab, all are blue The block is difficult to identify, so you can use the PrefabWin window to pull the control out. When it is pulled to the scene, it will determine which Canvas the control falls on, if it is hung on it, otherwise it will automatically generate a Canvas, and then right-click to save it as an interface prefab :

![image](https://github.com/liuhaopen/ReadmeResources/blob/master/UGUI-Editor/prefab_win.gif)  

The PrefabWin window can be opened from the menu Window-> PrefabWin
The PrefabWin window is definitely nothing at the beginning, you can pull the prefab in it, and then it will automatically generate the preview image. 2D3D prefab is all right. There is a search box at the bottom for you to quickly filter.

## Reference picture
Generally, for the interface, we press the artistic drawing, pull a button there, get a text there, and its coordinate size ratio must be adjusted strictly according to the artistic drawing. And add it as follows:

![image](https://github.com/liuhaopen/ReadmeResources/blob/master/UGUI-Editor/consult_pic.gif)  

The resources of the reference map can come from a directory outside the project, and it will be skipped when you right-click to save the interface. In addition, whenever you save the interface, UIEditor will save information such as pictures and size coordinates of all reference maps on the interface. It will load automatically when opened twice.
After adding a reference picture, you can select it and right-click the menu-> Lock so that it won't hinder you.
By the way, by the way, after selecting a node, you can use the arrow keys to adjust the node's coordinates, plus or minus 1 each time.

## Generate Image Node
In the Project view, drag the graph to the Canvas of the scene (if there is no Canvas), an Image node will be generated and the graph will be assigned to it. There is also an image that can be assigned to the graph by clicking the image in the Project view when the Image node is selected .

![image](https://github.com/liuhaopen/ReadmeResources/blob/master/UGUI-Editor/drag_pic.gif)

## Optimization level
The following picture has 8 nodes, of which 4 pictures, two pictures are from atlas 1, and two are from atlas 2.If they are arranged consecutively according to the atlas, they can be combined into the same batch, but they are merged by other graphs. If the set is interrupted, it cannot be combined.The other 4 texts are the same.The same font can also be combined into a batch.This function is to automatically arrange the order to optimize the batch:

![image](https://github.com/liuhaopen/ReadmeResources/blob/master/UGUI-Editor/optimize_depth_for_batch_draw.gif)  

## Find resource references
Sometimes some old resources want to delete but dare not delete them, for fear they are used elsewhere. At this time, you can find out which prefab uses the resource in the entire project in the Project right-click menu:

![image](https://github.com/liuhaopen/ReadmeResources/blob/master/UGUI-Editor/find_references.gif)  

## Open the prefab interface in the entire folder
![image](https://github.com/liuhaopen/ReadmeResources/blob/master/UGUI-Editor/open_folder.gif)  

## Merge groups and disintegrate
Sometimes it is necessary to combine several nodes into a group.

![image](https://github.com/liuhaopen/ReadmeResources/blob/master/UGUI-Editor/make_group.gif)  

## Arrange and clean all interfaces
![image](https://github.com/liuhaopen/ReadmeResources/blob/master/UGUI-Editor/sort_and_clean.gif)

## Alignment tool
![image](https://github.com/liuhaopen/ReadmeResources/blob/master/UGUI-Editor/align_menu.png)
![image](https://github.com/liuhaopen/ReadmeResources/blob/master/UGUI-Editor/align_tool.gif)  

## Modify anti-reset at runtime
You can safely modify and save the prefab when running, and reload to the latest when you finish running (by default, Unity will reset to the state before running)

![image](https://github.com/liuhaopen/ReadmeResources/blob/master/UGUI-Editor/reload_after_exit.gif)   

## Display interface name
Press Ctrl + E to show or hide all interface names

![image](https://github.com/liuhaopen/ReadmeResources/blob/master/UGUI-Editor/show_layout_name.gif)   

## other functions
-Reload all the interfaces being edited after running (because the changes during running will be reset after running)
The interface opened at runtime, Unity will automatically clear it when exiting, so we have to record it and reopen it when exiting
- Record the reference picture information of each interface (now it is too much trouble to add a reference picture every time you reopen the interface)
- Add right-click menu: optimize the level, put the text together, put the same atlas together
- Press ctrl + shift + c to copy the selected node name to the clipboard, and the resulting string is with path:
  
![image](https://github.com/liuhaopen/ReadmeResources/blob/master/UGUI-Editor/copy_nodes.png)

## TODO  
)界面优化大全:选中某界面后遍历其所有子节点并在一个window列出优化建议(比如Text别用bestfix,用到了其它图集的小图等等)  
)支持大部分操作的Undo(在操作前用Undo这个工具类记录)(30%)  
)右键显示颜色框(有时代码要设置颜色值可以用的)  
)Hierarchy界面也要显示我们的右键菜单  


