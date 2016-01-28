原因：在ie6下，不论绝对定位的z-index有多大，比如图中的div2，如果父层的div的z-index小于或者等于其它层的z-index，则div2会被其它的div覆盖住。
解决办法：给父层（切记是与div2同级的父级）的div指定z-index