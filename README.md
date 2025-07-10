
# 缺陷图片显示流程总结

### 1. 缺陷检测触发流程
```
图像采集 → 检测引擎 → 检测结果 
```

### 2. 缺陷信息处理流程  
```
DefectImageSaver.onDecisionResult() → 
  ├─ 解析DecideResult
  ├─ 查找关键帧
  ├─ 计算最高置信度
  ├─ 绘制缺陷框
  ├─ 保存缺陷图片
  └─ 启动DefectStopActivity
```

### 3. 数据传递流程
```
DefectImageSaver → Intent → DefectStopActivity
传递数据:
  ├─ defect_image_uri: 缺陷图片URI
  ├─ defect_type: 缺陷类型中文名称（断针/飞根/破洞/小缺陷）
  ├─ defect_confidence: 置信度
  ├─ defect_timestamp: 检测时间戳
  ├─ defect_x/y/width/height: 缺陷位置
  └─ 各种缺陷统计: duanzhen_count, feigen_count等
```

### 4. 界面显示流程
```
DefectStopActivity.onCreate() →
  ├─ initViews(): 初始化UI组件
  └─ loadDefectInfo(): 加载并显示缺陷信息
      ├─ 显示缺陷图片
      ├─ 显示缺陷类型和统计
      ├─ 显示置信度
      ├─ 显示缺陷位置
      └─ 显示检测时间
```



