# layuiUse
layui使用小结

１.　从父页面中弹出弹窗，
２.在弹窗中通过点击确定按钮关闭弹窗的同时，使用
 //关闭弹窗
      var index = parent.layer.getFrameIndex(window.name);
      parent.layer.close(index);
               刷新父页面中的表格,　type:2的形式弹窗
      parent.layui.table.reload('testReload');

 ３.　type:1的形式弹窗，使用此　语句　layui.table.reload('testReload');刷新父页表格数据
		
