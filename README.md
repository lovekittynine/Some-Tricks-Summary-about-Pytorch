# Some-Tricks-Summary-about-Pytorch
Keep Recording Some Tricks about Pytorch
## 2020.6.16
1.不使用的变量最好的delete释放缓存，relu使用inplace=True

2.加载数据的时候，dataloader设定了pin_memory=True时，要和non_blocking=True搭配使用，e.g. imgs = imgs.cuda(non_blocking=True)(知乎上据说可以提速～50%)

3.使用nn.DataParallel()做单机多卡并行训练时候，现将模型转换到gpu上，在使用nn.DataParallel()包装：
      model = model.cuda()
      model = nn.DataParallel(model, device_ids=[0,1,2,3], output_device=[0]) # ouput_device用于汇总所有gpu上的梯度计算
      
4.python3字符串输出，简便用法: 
      name='hello' 
      string = f"name is : {name}" # f开头的字符串支持{}内python运算
      string = 'name is : {}'.format(name)(等价)
