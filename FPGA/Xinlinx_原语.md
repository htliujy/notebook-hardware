# Xinlinx_原语

1. FDRE:

2. LVDS:
   1. IBUFDS：This design element is an input buffer that supports low-voltage, differential signaling.
   2. IBUFGDS：This design element is a dedicated differential signaling input buffer for connection to the clock buffer (BUFG) or MMCM.
   3. 所以差别在于IBUFGDS的输出用于连接global clock相关资源，而IBUFDS是用于差分信号转成单端。但事实上，Vivado中，即使使用了IBUFGDS，综合之后的结果也会把它infer成IBUFDS。工具会在Clock Capability的信号上自动添加BUFG资源（也可手动例化）。

## 参考及引用

[1] IBUFDS和IBUFGDS之间到底有什么区别. <http://bbs.eeworld.com.cn/thread-1096247-1-1.html>
