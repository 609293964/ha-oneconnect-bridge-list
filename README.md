# OneConnect Bridge 映射记录

 记录 Home Assistant 实体通过 `oneconnect_bridge` 接入智慧生活后的设备映射结果。


## 映射总表



| 设备名称  | HA / 实体 | 模拟产品 | 模板 `prodId` / 型号 | 可用功能 | 未映射、不可用或待确认 | 选择原因、必要调整和状态 |
|---|---|---|---|---|---|---|
| [小米米家智能墙壁插座](https://home.miot-spec.com/p/zimi.plug.zncz01) | `zimi.plug.zncz01` | FSL 智能插座 | `2MFF` / `Z1-Z3B-101/ZK` | 开关、指示灯、功率 | 日/月用电量、电流异常报警、功率保护与充满断电未启用，卡片中电流电压无实体 | 插座品类相符；当前映射直接使用开关、指示灯和功率。 |
| [智能窗帘电机 V1-Mesh 版](https://home.miot-spec.com/p/bean.curtain.ct01) | `bean.curtain.ct01` | H1 窗帘 | `2DCY` / `H1` | 开、关、停、开合百分比、手拉启动 | 窗帘高级设置与遥控器服务未绑定；`invert: false`，方向和真实行程仍需确认 |  |
| [LS-M3 CURTAIN-Mesh](https://home.miot-spec.com/p/lonsam.curtain.ct05) | `lonsam.curtain.ct05` | H1 窗帘 | `2DCY` / `H1` | 开、关、停、百分比、手拉启动、反转、校准、故障 | 卷帘设置、场景配置、遥控器管理未接入 |  |
| [米家智能宠物喂食器 2](https://home.miot-spec.com/p/xiaomi.feeder.pi2001) | `xiaomi.feeder.pi2001` | Solo 宠物喂食器 | `A3DV` / `P571` | 出粮、童锁、余粮状态、设备状态 | 定时计划、出粮记录、称重校准、故障、干燥剂寿命、电池电量未映射 | 现有 Profile 覆盖核心喂食能力，避免引入无关功能。当前映射 |
| 美的普通滚筒洗衣机 | `TG100V87MIY` | 美的普通滚筒洗衣机 | `A1PI` / `TG100Q81Y` | 电源、开始/暂停、程序、运行状态、剩余时间 |  |  |
| 美的燃气热水器 | `JSQ30-Magic Pro` | 美的燃气热水器 | `A1BR` / `JSQ34-RX9` | 电源、当前/目标温度、状态、零冷水、进水温度 | 完整 HA 实体清单和云端字段逐项控制仍待核实 | 品类和 Profile 能力最接近。当前映射 |
| [小米米家蓝牙温湿度计 2](https://home.miot-spec.com/p/miaomiaoce.sensor_ht.t2) | `miaomiaoce.sensor_ht.t2`；HA 实体 `miaomiaoce_t2_d99f` | LifeSmart 温湿度计 | `21DJ` / `LS063WH` | 温度、湿度、电池 |  |  |
| [领普温湿度传感器](https://home.miot-spec.com/p/linp.sensor_ht.ks2bb) | `linp.sensor_ht.ks2bb`；商品型号 `KS2BB` | LifeSmart 温湿度计 | `21DJ` / `LS063WH` | 温度、湿度、电池 | 按键无法集成映射 |  |
| [米家风扇灯 42 英寸](https://home.miot-spec.com/p/xiaomi.light.cfan) | `xiaomi.light.cfan`；实体含 `xiaomi_cn_750352651_cfan` | eachone 智能风扇灯 | `2NAL` / `HJ-HM-FSD-001` | 灯开关、亮度、色温、风扇开关、6 档风速、风类模式、6 项灯光模式 | 延时、上电状态、凌动开关、勿扰、自然风曲线、遥控器管理未接入； | “用餐”“阅读”需要自定义用亮度/色温组合 |
| [米家智能香氛机](https://home.miot-spec.com/p/xiaomi.diffuser.xw002) | `xiaomi.diffuser.xw002`；`XW002` | 康美太香氛机 | `173P` / `1522YN` | 总开关、香氛开关、氛围灯开关 | 香氛浓度、出香时长、氛围灯亮度/颜色、自动出香、手动喷香、电池状态未映射 | Mynt 模板 H5 持续白屏，改用 `173P`；三组开关注册和同步成功。当前映射 |
| [平头熊人体存在传感器（顶装版）](https://home.miot-spec.com/p/090615.sensor_occupy.xw) | `090615.sensor_occupy.xw` | LifeSmart 人体存在传感器 | `21DI` / `LS062WH` | 有人/无人、照度 | 探测距离、灵敏度、生物检测、指示灯和雷达负载开关未映射 | Xiaomi Home 对应实体不可用，改用 Miot 中可用的 occupancy 和 illumination。当前映射 |
| Sagewe F2s501-GB | Tuya 集成 | FSL 智能插座 | `2MFF` / `Z1-Z3B-101/ZK` | 开关、电流、电压、累计电量、瞬时功率 | HA 侧遥测已映射；模板指示灯、童锁、故障码、定时、`netInfo`、`update` 未启用 | `electric` 和 `power` 同时覆盖插座电量实体。当前映射 |
| [情景 Mesh 色温灯 V2S 系列](https://home.miot-spec.com/p/lemesh.light.wy0c15) | `lemesh.light.wy0c15`；实体含 `wy0c15` | 松下智能灯带控制装置 | `2OE9` / `LGC90822520QT` | 开关、亮度、色温、场景模式 | 延时、渐变、上电状态、凌动开关、超过 6 个模式的 effect 未映射；色温收敛到 2702–6493K | 灯带品类准确，HA effect 可映射为 6 个模式。当前映射 |
| [情景 Lemesh 色温灯 Ultra](https://home.miot-spec.com/p/lemesh.light.wy0d02) | `lemesh.light.wy0d02`；实体含 `wy0d02` | 松下智能灯带控制装置 | `2OE9` / `LGC90822520QT` | 开关、亮度、色温、场景模式 | 渐变、延时、默认状态、节律照明、遥控器管理未接入 | 与另一条灯带能力一致，采用相同模板。当前映射 |
| 情景Lemesh色温灯Ultra | HA 组合实体；实际灯具型号待确认 | 松下智能筒射灯 | `2OE7` / `HG9S352SQT` | 开关、亮度、色温、场景模式 | 电视、阅读、呼吸、节拍等 HA effect，以及倒计时、渐变时长未映射 | 补齐 mapping 遗漏的 `brightness`；2OE7 品类和能力最准确。当前映射 |
| [松下智能吸顶灯](https://home.miot-spec.com/spec?type=urn%3Amiot-spec-v2%3Adevice%3Alight%3A0000A001%3Apmfbj-xsx340%3A2%3A0000C802)  | `light.pmfbj.light.xsx340` | 立达信护眼吸顶灯 | `2RAU` / `LC5S-G1-D50HM` | 开关、亮度、色温、6 项场景 | 通用倒计时和渐变未接入；“适悦光”等 effect 按语义映射到 2RAU 场景 | `2RDK`、`2RF1` 被 `batchBind 15013` 拒绝，恢复到可注册的 `2RAU`。当前映射 |
| [米家智能直流变频落地扇 1X](https://home.miot-spec.com/p/dmaker.fan.p5c) | `dmaker.fan.p5c`；实体含 `P5C` | eachone 智能循环扇 | `2NHB` / `HF-HM-XHS-001` | 开关、12 档风速、摇头 | 指示灯、提示音、童锁未绑定；HA `percentage_step=25`，中间档可能被取整 | 12 档风速需要自定义百分比 |
| 链路探针 | 虚拟链路探针，无实际设备 | 尊界 S800 Grand Design | `ZJ0V` | 链路探针 | 链路探针 | 用于验证子设备链路 |


## 适配调整

| 适配项 | 调整内容 | 目的 |
|---|---|---|
| 插座电量 | 电流 A 转为 mA；电压按 V；累计电量按 kWh；功率按 W | 避免单位错误导致云端数值异常 |
| 窗帘 | `action` 使用 `0=close`、`1=open`、`2=stop`；百分比对应 `opener.current/target` | 保持 HA 百分比和厂商状态一致 |
| 灯带色温 | 将色温收敛到 Profile 允许的 2702–6493K | 防止越界导致 `cct` 服务被丢弃 |
| 风扇档位 | 客厅风扇灯使用 1–6 档；小风扇使用 1–12 档并转换为 HA percentage | 让厂商档位和 HA 百分比互相转换 |
| 风扇摇头 | `angle=0/1` 对应停止摇头/摇头 | 补齐循环扇摇头能力 |
| 存在传感器 | `有人/无人` 转为 `1/0`；照度使用 lx；增加 `motionDetected` | 匹配 Profile 状态字段 |
| 灯光场景 | 使用明确的 effect 枚举；没有直接对应 effect 的场景使用亮度/色温组合 | 减少无效场景按钮 |
| 服务绑定 | 同步维护 `product.services` 和 `bindings` | 避免声明了服务却没有实体绑定 |

## 无法注册的模板和报错

| 候选模板 | 结果 | 报错或现象 | 处理 |
|---|---|---|---|
| 迈睿 MH3 Pro 人体传感器 | 失败 | `batchBind errcode 15013`；Mesh protocol 1 和 4 均拒绝 | 换用 LifeSmart `21DI` |
| 堡丽 BL5002H 人体传感器 | 失败 | `batchBind errcode 15013` | 不再使用 |
| 美的普通电风扇 `A08G` | 失败 | 新旧 child ID 都返回 `devInfoSync errcode 18002` | 判断为产品不接受当前注册方式，不是 ID 冲突；改用 `2NHB` |
| 一起玩清澈光二代雷达版 `2RDK/HF-HM-XDD-506` | 失败 | 新 child key 仍返回 `batchBind errcode 15013` | 恢复可注册的 `2RAU` |
| 一起玩清澈光二代非雷达版 `2RF1/HF-HM-XDD-502` | 失败 | 新 child key 仍返回 `batchBind errcode 15013` | 恢复可注册的 `2RAU` |
| Mynt 香氛机模板 | 页面异常 | H5 面板持续白屏 | 改用康美太 `173P` |

`15013` 表示当前网关和注册方式不接受该产品模板；`18002` 在本次测试中出现在设备信息同步阶段。更换 child key 不能解决所有产品兼容性问题。
