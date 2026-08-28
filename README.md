-基于 HslCommunication的西门子 S7 系列 PLC 的数据采集监控上位机展示，支持设备管理、PLC 连接与心跳检测、地址表配置化采集、实时折线图可视化、历史数据存储、操作日志回溯功能<br>
-1  添加设备（参数配置 + Ping 连通性测试）
填写设备名称、型号、IP、端口、心跳地址、读写地址表路径；点击「连接测试」可快速 Ping 目标 IP；设备保存到数据库
<img width="898" height="636" alt="添加设备1 1-添加设备控件界面" src="https://github.com/user-attachments/assets/8713ace7-aa1b-411d-99d2-1c87ac06f381" />
<img width="898" height="630" alt="添加设备1 2-添加设备网络连接测试" src="https://github.com/user-attachments/assets/1c02ae73-e355-435b-b60d-6524f77a6ac4" />
<img width="1307" height="445" alt="添加设备1 3-添加设备数据库持久化" src="https://github.com/user-attachments/assets/511bb30f-9126-4d06-8d8d-2708ab6c0899" />

-2  单设备采集（连接 PLC + 启动心跳）
选中一台设备后点击「单设备采集」，系统建立与 PLC 的通信链路，并启动后台心跳检测。连接成功后设备卡片左上角的状态灯切换为绿色常亮，并弹出成功提示。右侧日志也可看到在线客户端接入
<img width="1700" height="663" alt="单设备采集2 1-PLC连接成功" src="https://github.com/user-attachments/assets/0867173e-7911-478b-a958-37346401fdfe" />

-3  异常场景友好提示（PLC 离线 / 拒绝连接）
当目标 PLC 未启动或网络不通时，系统不会崩溃闪退，而是弹出可读的错误说明，明确告知用户「目标计算机积极拒绝」「地址不存在」等原因，便于快速定位现场问题
<img width="1707" height="655" alt="单设备采集2 2-PLC连接失败" src="https://github.com/user-attachments/assets/d01c7b44-a47d-4876-a157-dc77a6e67929" />

-4  勾行启动实时采集 + 多变量实时折线图
勾选读地址表中的一行或多行，系统立即启动对应地址的独立采集循环，将每 200ms 采集到的浮点数以不同颜色的折线画在同一张图表上，每条折线对应图例可清晰区分。X 轴自动滚动（最近 100 个采集点），长时间采集不会挤爆画面；Y 轴随采集到的数据范围自动伸缩，不用手动配置量程。
<img width="1707" height="652" alt="单设备采集2 3-单设备采集展示" src="https://github.com/user-attachments/assets/997c6e99-7cf4-4f29-ace4-6c7b4429a558" />
<img width="1651" height="630" alt="单设备采集2 4-单设备采集断开" src="https://github.com/user-attachments/assets/58b8f553-6bf1-4329-af0e-02371968bca2" />

-5  数据库存储与查询（设备表 / 采集记录 / 系统日志 三位一体）
所有操作和数据可在 SQL Server 中追溯：
Devices 表：列出已入库的设备基础信息（名称、IP、端口、创建时间）
DataRecords 表：每条采集值都会插入一条新记录，含地址、数值、质量（成功/失败）、采集时间，可按设备筛选导出
SystemLogs 表：Info（启动/停止采集、添加/删除设备）、Warning（读失败/校验异常）、Error（未预期异常）三级日志完整留痕
 三表联合查询结果
 <img width="865" height="816" alt="单设备采集2 5-单设备采集信息数据展示" src="https://github.com/user-attachments/assets/bf738b96-8dfd-40f8-9c31-85977b7c5a66" />
<img width="769" height="613" alt="单设备采集2 6-设备HSL通信信息数据展示" src="https://github.com/user-attachments/assets/f6c5ef12-4496-4506-a5ba-9cafcce7269c" />
-6  删除设备
<img width="896" height="625" alt="删除设备3 1-删除设备展示1" src="https://github.com/user-attachments/assets/ecfb4aa1-c9de-4a32-9755-15ed5eb3df02" />
<img width="896" height="629" alt="删除设备3 2-删除设备展示2" src="https://github.com/user-attachments/assets/421ce95e-4013-4223-9522-0e501b4efaf6" />
