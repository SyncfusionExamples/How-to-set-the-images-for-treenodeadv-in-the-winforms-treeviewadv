# How to set the images for TreeNodeAdv in the WinForms TreeView

This session describes how to set the images for [TreeNodeAdv](https://help.syncfusion.com/cr/windowsforms/Syncfusion.Tools.Windows~Syncfusion.Windows.Forms.Tools.TreeNodeAdv.html) in the [WinForms TreeView](https://www.syncfusion.com/winforms-ui-controls/treeview) (TreeViewAdv).

`TreeView` control can be customized with images to the Left or Right side of its `TreeNodeAdv`. The images can be set on the Left or Right by using the properties [LeftImageList](https://help.syncfusion.com/cr/windowsforms/Syncfusion.Tools.Windows~Syncfusion.Windows.Forms.Tools.TreeViewAdv~LeftImageList.html) and [RightImageList](https://help.syncfusion.com/cr/windowsforms/Syncfusion.Tools.Windows~Syncfusion.Windows.Forms.Tools.TreeViewAdv~RightImageList.html). It is also possible to specify different images for the individual nodes by using the [LeftImageIndices](https://help.syncfusion.com/cr/windowsforms/Syncfusion.Windows.Forms.Tools.TreeNodeAdv.html#Syncfusion_Windows_Forms_Tools_TreeNodeAdv_LeftImageIndices) and [RightImageIndices](https://help.syncfusion.com/cr/windowsforms/Syncfusion.Windows.Forms.Tools.TreeNodeAdv.html#Syncfusion_Windows_Forms_Tools_TreeNodeAdv_RightImageIndices) properties in the `TreeNodeAdv`.

``` csharp
//Assigns image list to the TreeNodeAdv.
this.treeViewAdv1.LeftImageList = this.imageList1;
this.treeViewAdv1.RightImageList = this.imageList1;
 
//Gets the Path of the node and AddSeparatorAtEnd property set to true.
string path = e.Node.GetPath("\\");
 
//Gets an Array of Directories from the current directory path.
ArrayList dirs = new ArrayList(Directory.GetDirectories(path));
 
//Adds the Directories as a node in the TreeViewAdv
for (int i = 0; i < dirs.Count; i++)
{
    string dir = (string)dirs[i];
    int lastIndex = dir.LastIndexOf("\\") + 1;
    TreeNodeAdv node = new TreeNodeAdv(dir.Substring(lastIndex));
    e.Node.Nodes.Add(node);
    node.RightImageIndices = new int[] { 1 };
}
 
//Sets the Left images for the TreeNodeAdv.
foreach (TreeNodeAdv node in this.treeViewAdv1.Nodes[0].Nodes)
{
    node.LeftImageIndices = new int[] { 1 };
    node.RightImageIndices = new int[] { -1 };
}
 
//Sets the Right images for the TreeNodeAdv.
foreach (TreeNodeAdv node in this.treeViewAdv1.Nodes[0].Nodes)
{
    node.RightImageIndices = new int[] { 1 };
    node.LeftImageIndices = new int[] { -1 };
}
```