<!--

Copyright (c) 2026 暗夜铭少 (DarkNightMing) (https://github.com/anye1991)
Product: Shield WAF Enterprise (盾甲WAF企业版)

Licensed under the Business Source License 1.1 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at:

    https://duduziy.com/shield-waf

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

For commercial licensing, please contact: 634769642@qq.com
SPDX-License-Identifier: BSL-1.1

-->

# Shield 盾甲 WAF 企业版 v5.3.0
[![OpenSSF Best Practices](https://www.bestpractices.dev/projects/13720/badge)](https://www.bestpractices.dev/projects/13720)

**Shield WAF Enterprise** is a high-performance **Go Web Application Firewall** for production environments. 55 attack types covered (SQLi/XSS/SSRF/RCE/XXE/SSTI/Deserialization/NoSQL/GraphQL/JNDI...), 28 AST semantic parsers, 14-layer encoding normalization, WAF 3.0 smart engine, AI second-opinion, sandbox (6 engines + VM), subnet co-ban. **OpenSSF Best Practices GOLD** certified (verify: bestpractices.dev/projects/13720). Compared to the open-source PHP edition: 55 vs ~30 vuln types, 28 vs 14 parsers, Go-native concurrency (10,000+ QPS, <5ms p95). Chinese docs below.
> 高性能 Go 语言 Web 应用防火墙 — 55种漏洞防御 + 28种语义解析器 + 14层编码归一化 + AI二次确认 + WAF 3.0 智能引擎 + 流量统一化引擎 + 网段连坐封禁 + 工程稳定性零缺陷
# Shield WAF Enterprise v5.3.0 (Commercial Edition)

---
[![OpenSSF 最佳实践](https://www.bestpractices.dev/projects/13720/badge)](https://www.bestpractices.dev/projects/13720)
## 🏆 安全认证

| 认证 | 级别 | 说明 |
|------|------|------|
| **OpenSSF Best Practices** | 🥇 Gold 级 | 开源安全基金会最高级别最佳实践认证 |
| **深度代码审计** | ✅ 100% 修复 | v5.0.0 77项 + v5.2.0 35项 + v5.3.0 12项，全部修复完成 |
| **全漏洞极限测试** | ✅ 100% 检出 | 35种漏洞类型 68个攻击用例，检出率 100%，误报率 0% |
| **AI 对抗测试** | ✅ 100% 检出 | 34个 AI 生成攻击用例，3种检测模式均 100% 拦截 |
| **上传安全测试** | ✅ 100% 检出 | 30个上传攻击用例，含 SVG XSS/XXE/WebShell，零误报 |
| **极限穿透测试** | ✅ 通过 | 24种漏洞类型极限测试，抗击穿率 100% |
| **兼容性验证** | ✅ 通过 | WordPress/Discuz/Typecho/ThinkPHP 等主流平台验证 |
| **工程稳定性** | ✅ 零缺陷 | 零 panic / 零数据竞争 / 零资源泄漏 / 零递归栈溢出 |
| **语义引擎安全** | ✅ 加固 | 28种解析器全部添加递归深度限制和类型断言守卫 |
| **网段连坐封禁** | ✅ v5.3.0 新增 | 1次违规→/24+/16网段永久封锁（IPv6 /64+/48），连根拔起 |
| **白名单安全优先** | ✅ v5.3.0 加固 | CC/限流/Bot全部白名单前置检查，白名单IP永不误封 |

---

## 📖 项目介绍

Shield WAF Enterprise 是面向企业级用户的商业版 Web 应用防火墙，基于 Go 语言高性能引擎，提供从攻击检测、拦截防御到态势感知的一站式 Web 安全解决方案。

### 核心优势

| 特性 | 说明 |
|------|------|
| **55种漏洞防御** | SQLi/XSS/SSRF/命令注入/文件上传/XXE/SSTI/反序列化/NoSQL/GraphQL/JNDI等全覆盖 |
| **28种语义解析器** | 基于AST的深度语义解析，覆盖SQL/Shell/HTML/JS/PHP/Go/Rust/C#/Python/Java等 |
| **14层编码归一化** | URL/Base64/Unicode/HTML实体/Hex/同形字/零宽字符等自动解码链 |
| **7步深度语义分析** | 跨语言嵌套→代码理解→语义等价→数据流追踪→意图推理→上下文分析→综合评分 |
| **AI二次确认** | 支持接入大语言模型/ML推理服务，灰区攻击二次确认 |
| **WAF 3.0 智能引擎** | 上下文流+意图预测+融合决策三大引擎，超越雷池核心能力 |
| **本地 AI 模型** | 朴素贝叶斯分类器，纯Go实现，零外部依赖，在线增量学习 |
| **自动学习闭环** | 攻击样本→模型训练→检测增强→误报排除完整闭环 |
| **流量统一化引擎** | HTTP指纹+行为分析+IP信誉+JS挑战，WAF检测前过滤60%DDoS流量 |
| **Bot防护体系** | 四维评分（指纹30%+语义30%+行为25%+攻击链15%）+ 6分类 + 蜜罐HTML注入 |
| **文件上传检测** | 9层检测 + 归一化 + 语义 + 启发式 + 恶意代码定位 + AutoLearn闭环 |
| **沙箱系统** | 6引擎交叉验证（特征码/归一化/规则/语义/结构/启发式/VM执行） |
| **双重密码加密** | Argon2id + bcrypt双哈希，Shield2格式，惰性升级 |
| **网段连坐封禁** | 1次违规→/24+/16网段永久封锁（IPv6 /64+/48），连根拔起 |
| **白名单安全优先** | CC/限流/Bot/封禁检查全部白名单前置，白名单IP永不误封 |
| **trusted_cdn_ips校验** | 启动时校验CIDR格式，非法配置自动跳过并告警 |
| **暗门保护** | 双因子验证（Magic Key + 密码），保护管理后台路径 |
| **HTTPS原生支持** | WAF代理和管理后台均支持TLS/SSL加密传输 |
| **代理层安全头** | ModifyResponse注入安全头，OpenSSF Gold认证必备 |
| **兼容性优先** | 所有可能影响兼容性的功能默认关闭，按需开启 |

### 与 PHP 版完整对比

| 对比项 | PHP版（开源） | Go企业版 v5.3.0 |
|--------|-------------|----------------|
| 防御漏洞类型 | 约30种 | **55种** |
| 语义解析器 | 14种 | **28种** |
| 核心引擎层数 | 3层 | **8层**（归一化+语义+规则+AI+WAF3.0+沙箱+融合决策+FP Guard） |
| 编码归一化 | 14层 | 14层（对齐） |
| 深度语义分析 | 5步 | **7步** |
| 代码理解器 | ❌ | ✅ 7种语言 |
| 语义上下文分析 | ❌ | ✅ |
| AI二次确认 | ❌ | ✅ 3种AI模式 |
| 本地 AI 模型 | ❌ | ✅ 朴素贝叶斯（纯Go） |
| WAF 3.0 智能引擎 | ❌ | ✅ 上下文流+意图预测+融合决策 |
| 自动学习闭环 | ❌ | ✅ 攻击→学习→降误报 |
| 流量统一化引擎 | ❌ | ✅ |
| Bot评分体系 | 四维评分 | 四维评分（对齐） |
| Bot分类 | 6分类 | 6分类（对齐） |
| 蜜罐系统 | 链接注入 | 链接注入+HTML注入（对齐） |
| 沙箱引擎 | 5引擎 | **6引擎**（+VM执行） |
| 文件上传检测 | 7层 | **9层+5新增** |
| 双重密码加密 | ❌ | ✅ Argon2id+bcrypt |
| 网段连坐封禁 | ✅ /24+/16 | ✅ /24+/16 + **IPv6 /64+/48** |
| 网段封禁阈值 | ❌ 固定1次 | ✅ **可配置**（1~N次，默认3防误封） |
| 白名单前置检查 | ❌ | ✅ CC/限流/Bot/封禁全链路 |
| trusted_cdn_ips校验 | ❌ | ✅ 启动CIDR格式校验 |
| Redis存储 | ❌ | ✅ |
| 指标监控 | ❌ | ✅ Prometheus |
| 异步任务队列 | ❌ | ✅ |
| 攻击链分析 | ❌ | ✅ Kill Chain |
| 极限测试 | ❌ | ✅ 33种漏洞 100%检出 0%误报 |
| 性能 | 中等 | **极高（Go原生并发）** |
| 部署方式 | 嵌入网站同服务器 | 独立反向代理，透明部署 |

---

## 🏗 架构总览

```
                        ┌───────────────────────────────┐
   客户端请求 ─────────▶│     Shield WAF 反向代理       │──────▶ 后端业务网站
                        │     (waf-service)             │
                        │     HTTP / HTTPS              │
                        └──────────┬────────────────────┘
                                   │
                    ┌──────────────▼──────────────┐
                    │     流量统一化引擎           │ ← DDoS过滤、HTTP指纹、JS挑战
                    └──────────────┬──────────────┘
                                   │
                    ┌──────────────▼──────────────┐
                    │     14层编码归一化           │ ← 编码绕过防御
                    └──────────────┬──────────────┘
                                   │
                    ┌──────────────▼──────────────┐
                    │     28种语义解析器           │ ← AST深度分析
                    └──────────────┬──────────────┘
                                   │
                    ┌──────────────▼──────────────┐
                    │     42个Defender交叉检测     │ ← 33种漏洞类型全覆盖
                    └──────────────┬──────────────┘
                                   │
                    ┌──────────────▼──────────────┐
                    │     AI Ensemble多模型组合    │ ← LocalRule+LocalML+Semantic
                    └──────────────┬──────────────┘
                                   │
                    ┌──────────────▼──────────────┐
                    │     WAF 3.0 智能引擎         │ ← 上下文流+意图预测+融合决策
                    └──────────────┬──────────────┘
                                   │
                    ┌──────────────▼──────────────┐
                    │     沙箱验证（高危）         │ ← 6引擎交叉验证+精准切割
                    └──────────────┬──────────────┘
                                   │
                    ┌──────────────▼──────────────┐
                    │     FP Guard误报防护(20层)   │ ← 降低误报+交叉维度验证
                    └──────────────┬──────────────┘
                                   │
                              拦截/放行/日志
                                   │
                    ┌──────────────▼──────────────┐
                    │     Redis / Memory           │ ← 规则/封禁/统计/缓存
                    └──────────────┬──────────────┘
                                   │
                    ┌──────────────▼──────────────┐
                    │     Admin 管理服务           │ ← 管理控制台
                    │     (admin-service)          │
                    │     + 前端 SPA 控制台        │
                    └─────────────────────────────┘
```

### 核心检测流程

```
请求输入 → 流量统一化（DDoS过滤）
         → 14层编码归一化
         → 42个Defender交叉检测（33种漏洞类型）
         → 语义分析（AST 28种解析器）
         → AI Ensemble多模型组合（LocalML+Semantic+RemoteAPI+LLM）
         → WAF 3.0 智能引擎（上下文流+意图预测+融合决策）
         → 沙箱验证（高危 6引擎+精准切割）
         → FP Guard误报防护（20层+交叉维度验证）
         → 自动学习闭环（攻击→学习→降误报）
         → 融合决策 → 拦截/放行/日志
```

---

## 🛡 防护能力

### 55种攻击防御模块

#### 注入攻击（10种）
| 模块 | 说明 |
|------|------|
| SQL注入 | UNION/布尔/时间盲注/堆叠查询/编码绕过 |
| 命令注入 | Shell注入/管道符/环境变量/编码绕过 |
| NoSQL注入 | MongoDB/Cassandra注入 |
| LDAP注入 | LDAP过滤器注入 |
| XPath注入 | XPath查询注入 |
| GraphQL注入 | 查询注入/批量赋值/内省攻击 |
| SMTP注入 | 邮件头注入/CRLF |
| JNDI注入 | Log4Shell类攻击 |
| CRLF注入 | HTTP响应拆分 |
| 表达式注入 | EL/OGNL/SpEL/MVEL |

#### XSS（4种）
| 模块 | 说明 |
|------|------|
| 反射型XSS | URL参数注入 |
| 存储型XSS | 数据库存储型 |
| DOM型XSS | 客户端DOM操作 |
| 输出过滤绕过 | 编码/大小写/注释绕过 |

#### 文件安全（6种）
| 模块 | 说明 |
|------|------|
| 文件上传检测 | 9层检测+归一化+语义+启发式 |
| 文件包含 | LFI/RFI |
| 目录遍历 | ../攻击/编码绕过 |
| 源码泄露 | .git/.svn/.env |
| 备份泄露 | .bak/.swp/.sql |
| Zip Slip | 解压路径遍历 |

#### 业务安全（8种）
| 模块 | 说明 |
|------|------|
| CSRF防护 | Origin/Referer校验+Token |
| 点击劫持 | X-Frame-Options检测 |
| CORS错误配置 | 跨域策略检测 |
| 会话固定 | Session ID不轮换检测 |
| 会话劫持 | 异常会话使用检测 |
| IDOR | 越权访问检测 |
| 批量赋值 | 过度参数绑定检测 |
| 方法篡改 | HTTP方法绕过检测 |

#### DoS/DDoS（6种）
| 模块 | 说明 |
|------|------|
| CC攻击 | 频率+URI维度限流 |
| HTTP/2 Rapid Reset | 快速重置攻击 |
| Range DoS | 大范围请求 |
| ReDoS | 正则回溯攻击 |
| XML Bomb | XML实体爆炸 |
| WebSocket DoS | WebSocket连接耗尽 |

#### 服务器安全（8种）
| 模块 | 说明 |
|------|------|
| 缺失安全头 | HSTS/CSP/X-Frame等检测 |
| 目录列表 | 目录浏览暴露 |
| 硬编码凭证 | 代码中的密码/密钥 |
| HTTP请求走私 | CL/TE差异利用 |
| 缓存投毒 | CDN缓存污染 |
| SSL错误配置 | 弱协议/弱密码套件 |
| Host头注入 | 主机头伪造 |
| 子域名接管 | DNS悬空记录 |

#### 其他（13种）
| 模块 | 说明 |
|------|------|
| XXE | XML外部实体注入 |
| SSTI | 模板注入（Jinja2/Twig/FreeMarker等） |
| 反序列化 | Java/PHP/Python反序列化 |
| Shellshock | Bash环境变量注入 |
| ImageTragick | 图片处理漏洞 |
| 开放重定向 | URL跳转 |
| 原型污染 | JS原型链 |
| JWT攻击 | 算法混淆/弱密钥 |
| API安全 | 越权/未认证 |
| Cookie安全 | 属性缺失检测 |
| JSON劫持 | JSON CSRF |
| HPP | HTTP参数污染 |
| XSLT注入 | XSLT代码执行 |

### 14层编码归一化引擎

| 层 | 编码类型 | 说明 |
|----|---------|------|
| 1 | URL编码 | %XX 解码 |
| 2 | 双重URL编码 | %25XX 解码 |
| 3 | Base64 | 自动检测和解码 |
| 4 | Unicode编码 | \uXXXX 解码 |
| 5 | HTML实体 | &#NN; 和 &name; 解码 |
| 6 | Hex编码 | \xXX 解码 |
| 7 | Octal编码 | \NNN 解码 |
| 8 | UTF-8超长 | 多字节编码归一化 |
| 9 | 同形字 | 全角/相似字符替换 |
| 10 | 零宽字符 | 零宽空格/连接符移除 |
| 11 | 混合大小写 | 大小写归一化 |
| 12 | 注释插入 | SQL/JS注释移除 |
| 13 | 空格变体 | 各种空白符归一化 |
| 14 | 混合编码 | 多层嵌套编码递归解码 |

评分机制：每层编码解码 +5分，双重编码额外 +15分，上限30分。

### 7步深度语义分析

```
1. 跨语言嵌套处理 → 识别SQL中的JS、PHP中的SQL等混合代码
2. 多语言代码理解 → 7种语言（Go/Rust/C#/Python/JS/Java/PHP）的代码语义解析
3. 语义等价标注 → 20种语义等价类（恒真式、延时操作、堆叠查询等）
4. 数据流追踪 → 从输入到执行点的完整数据流追踪
5. 攻击意图推理 → 15种攻击意图（数据窃取、系统控制、横向移动等）
6. 语义上下文分析 → HTTP上下文+会话行为+攻击链+环境上下文
7. 综合评分计算 → 多维度加权评分
```

---

## 🤖 Bot防护体系

### 四维评分

| 维度 | 权重 | 检测内容 |
|------|------|---------|
| 指纹分析 | 30% | 49种爬虫指纹（20搜索+9AI+10社交+8SEO+2工具） |
| 语义分析 | 30% | 6大指标（路径多样性/间隔均匀度/资源偏好/探测评分/UA轮换/爬取深度） |
| 行为分析 | 25% | 5指标（高频请求/均匀间隔/路径多样性/方法异常/Referer缺失） |
| 攻击链 | 15% | 蜜罐触发+敏感路径探测 |

### 6分类

| 类型 | 说明 | 处置 |
|------|------|------|
| human | 人类用户 | 放行 |
| search_engine | 搜索引擎蜘蛛 | DNS验证后放行 |
| social_media | 社交媒体爬虫 | 可配置放行 |
| ai | AI爬虫 | 可配置放行 |
| crawler | 通用爬虫/SEO工具 | 可配置限流 |
| malicious_bot | 恶意爬虫/自动化工具 | 封禁 |

### 请求头指纹检测（8种异常模式）
- 缺失常见请求头（User-Agent/Accept/Accept-Language等）
- Accept异常（只有 `*/*` 没有 `text/html`）
- Accept-Language异常（单一en系语言）
- 无Referer（非首页直接访问内部页面）
- Connection: close（浏览器常用keep-alive）
- 无Host头
- 异常Accept顺序

### 蜜罐系统
- **路径蜜罐**：动态token，30分钟有效期，访问即封禁
- **HTML注入**：在响应HTML中注入3-5个隐藏链接，多种CSS隐藏方式
- 爬虫解析HTML后点击蜜罐链接 → 自动封禁IP

### JS挑战（Go版独有）
- 客户端必须执行JS才能通过
- 对无头浏览器/爬虫效果好
- PHP版没有此功能

---

## 📁 文件上传检测

### 9层检测 + 5项增强

| 层 | 检测维度 | 说明 |
|----|---------|------|
| 1 | 扩展名白名单 | 双扩展名/空字节截断检测 |
| 2 | MIME类型检测 | 请求头+幻数+**真实MIME探测** |
| 3 | GD图像验证 | **完整Decode全图**（PHP版只解析头部） |
| 4 | 文件幻数检测 | 13种格式（含PDF/ZIP/EXE/ELF等） |
| 5 | 文件名特征 | 6维度（双扩展/空字节/路径遍历/特殊名/过长/控制字符） |
| 6 | SVG专用检测 | 7维度（含外部资源检测） |
| 7 | 图片马检测 | 9种特征+多特征加分 |
| 8 | 内容WebShell | PHP/ASP/JSP 3语言 |
| 9 | 空文件/极小文件 | 空文件和极小文件检测 |

### 5项增强功能（v4.3.0新增）

| 功能 | 说明 |
|------|------|
| **14层编码归一化** | 上传文件内容编码绕过检测（base64混淆、双重编码等） |
| **语义分析接入** | 上传内容走AST语义引擎分析 |
| **启发式检测** | base64次数、chr()混淆、goto混淆、超长行、混淆变量名 |
| **恶意代码定位** | 行号+列号+偏移+上下文片段，最多20条 |
| **AutoLearn闭环** | 高风险且多引擎命中（≥3）自动投喂学习系统 |

### 多引擎交叉验证（12维度）
特征码 / 归一化 / 规则 / 语义 / 结构 / 启发式 / 幻数 / MIME / GD / SVG / WebShell / 文件名

---

## 🔒 沙箱系统

### 6引擎交叉验证

| 引擎 | 说明 |
|------|------|
| 特征码检测 | 已知攻击特征码匹配 |
| 归一化检测 | 编码归一化后的特征匹配 |
| 规则检测 | 自定义规则匹配 |
| 语义分析 | AST语义解析 |
| 结构分析 | 请求结构异常检测 |
| 启发式检测 | 行为模式分析 |
| **VM执行沙箱** | **Go版独有，模拟执行检测** |

### 三种工作模式
- **learning**：学习模式，只记录不拦截
- **baseline**：基线模式，与基线对比
- **protecting**：保护模式，主动拦截

---

## ⚡ 网段连坐封禁（连根拔起）

v5.3.0 重大新增功能。当攻击者 IP 触发封禁时，**同时封锁其所在整个网段**，让黑客换同网段 IP 也无法继续攻击。

### 工作原理

```
攻击者 203.0.113.42 发动 SQL 注入 → 被 WAF 拦截
                                    ↓
                        ban_threshold 次违规触发封禁
                                    ↓
                    ┌───────────────┼───────────────┐
                    ↓               ↓               ↓
              单IP封禁         /24 网段封禁     /16 网段封禁
          203.0.113.42     203.0.113.0/24   203.0.0.0/16
          (按 ban_durations   (256个IP)      (65536个IP)
           累进时长)          按 subnet_duration 时长
```

### IPv4 / IPv6 双支持

| 协议 | 连坐网段 | 覆盖范围 |
|------|---------|---------|
| IPv4 | /24 | 256 个 IP |
| IPv4 | /16 | 65,536 个 IP |
| IPv6 | /64 | 18.4 × 10¹⁸ 个 IP |
| IPv6 | /48 | 1.2 × 10²⁴ 个 IP |

### 误封防护机制（5重保障）

| 机制 | 说明 |
|------|------|
| **SubnetThreshold 阈值** | 默认 3 次违规才触发网段封禁，=1 即 1 次连根拔起 |
| **白名单绝对优先** | 白名单 IP 的请求不参与任何封禁检查，永不误封 |
| **受保护网段** | 内网私有地址段（10.x/172.16.x/192.168.x/127.x）不触发连坐 |
| **有限封禁时长** | `subnet_duration` 默认 3600 秒（1小时），=0 为永久 |
| **fail-open 机制** | Redis/存储故障时网段检查放行（不因基础设施故障误封） |

### 配置方法

```yaml
waf:
  # 单IP封禁配置
  ban_on_block: true           # 拦截后自动封禁
  ban_threshold: 1             # 1次违规即封禁该IP
  ban_window_sec: 3600         # 计数窗口
  ban_durations:               # 累进封禁时长
    - 86400                    # 第1次：1天
    - 604800                   # 第2次：7天
    - 2592000                  # 第3次：30天
    - 0                        # 第4次起：永久

  # 网段连坐封禁配置
  subnet_ban: true             # 开启网段连坐
  subnet_threshold: 1          # 1次违规即连根拔起（默认3防误封）
  subnet_duration: 0           # 0=永久封禁（连根拔起）
```

> **生产建议**：如果网站有大量用户共享出口 IP（如学校/企业网络），建议 `subnet_threshold: 3` + `subnet_duration: 3600`，避免误伤正常用户。对高安全场景（金融/政企），可设 `subnet_threshold: 1` + `subnet_duration: 0`。

---

## 🔐 安全特性

### 认证与权限
- ✅ **Argon2id + bcrypt双重哈希** — Shield2格式，惰性升级，多格式兼容
- ✅ **JWT认证** — 无状态会话管理
- ✅ **RBAC权限控制** — 细粒度权限管理
- ✅ **暗门保护** — 双因子验证（Magic Key + 密码），会话与IP绑定，CSRF防护

### 会话安全（5模块）
- ✅ **CSRF防护** — Origin/Referer校验，Token验证
- ✅ **Cookie安全** — Secure/HttpOnly/SameSite属性检测
- ✅ **会话固定防护** — Session ID轮换检测
- ✅ **会话劫持检测** — 异常IP/UA切换检测
- ✅ **会话加固** — 会话超时/并发控制

### 传输安全
- ✅ **HTTPS原生支持** — 全链路TLS加密
- ✅ **HTTP重定向HTTPS** — 自动跳转
- ✅ **X-Forwarded-Proto** — 统一协议判断
- ✅ **代理层安全头** — ModifyResponse注入，默认关闭，后端已有不覆盖

### 误报控制
- ✅ **FP Guard 20层规则** — 搜索引擎蜘蛛验证/CMS路径豁免/常见业务路径等
- ✅ **基线白名单** — 自动学习正常流量模式
- ✅ **语义分析+编码归一化** — 深度理解请求含义
- ✅ **搜索引擎蜘蛛DNS验证** — 反向DNS+正向验证

### 其他安全
- ✅ **操作审计日志** — 全链路可追溯
- ✅ **Redis键名安全** — 用户输入哈希防内存膨胀
- ✅ **输入大小限制** — 防DoS攻击
- ✅ **正则ReDoS防护** — 优化正则防回溯攻击
- ✅ **请求走私防护** — hop-by-hop头清理 + Content-Length校验
- ✅ **深度代码审计** — 77项安全问题全部修复

---

## 🌊 流量统一化引擎

通过可信度评分（0-100分）对流量进行分层处理，在WAF检测前过滤60%的DDoS流量。

| 模块 | 说明 |
|------|------|
| HTTP指纹识别 | 请求头顺序/缺失头/TLS指纹 |
| 行为模式分析 | 请求频率/路径模式/资源偏好 |
| IP信誉系统 | 已知恶意IP/搜索引擎IP/CDN IP |
| JS挑战验证 | 客户端JS执行验证 |
| 分层限流 | IP+URI维度限流 |
| 可信度评分 | 0-100分，分层处理 |

---

## 🚀 快速开始

### 方式一：二进制解压即用（推荐）

零依赖，上传解压直接启动。

```bash
# 1. 上传并解压


# 2. 修改配置
vi configs/config.yaml
#   - proxy.backend_url: 指向你的真实后端网站
#   - admin.username/password: 修改默认账号密码
#   - redis.addr: 配置 Redis 地址

# 3. 启动服务
chmod +x start.sh
./start.sh

# 4. 访问
# WAF 代理地址：http://服务器IP （标准80端口，用户直接访问被保护网站，无需带端口）
# 管理控制台：  http://127.0.0.1:8081/admin （仅本地访问，远程请用SSH隧道或配置admin.tls）
# 默认账号：admin （密码见 configs/config.yaml）
```

#### 配置 HTTPS

已有 SSL 证书的话，编辑 `configs/config.yaml`：

```yaml
proxy:
  tls:
    enabled: true
    cert_file: /path/to/your_domain.crt
    key_file: /path/to/your_domain.key
    listen_addr: ":443"
    redirect_http: true  # HTTP自动跳转HTTPS

admin:
  tls:
    enabled: true
    cert_file: /path/to/your_domain.crt
    key_file: /path/to/your_domain.key
    listen_addr: ":8443"
```

### 方式二：Docker 部署

```bash
cp configs/config.yaml.example configs/config.yaml
# 修改 proxy.backend_url 指向你的真实后端网站
docker compose up -d --build
```

### 方式三：源码构建

```bash
# 环境要求：Go >= 1.25, Node.js >= 20, Redis >= 7

# 构建前端
cd web-admin && pnpm install && pnpm run build && cd ..

# 构建后端
go build -o bin/waf-service ./cmd/waf-service
go build -o bin/admin-service ./cmd/admin-service

# 启动
./bin/waf-service
./bin/admin-service
```

---

## ⚙️ 配置说明

配置文件：`configs/config.yaml`

### 核心配置

```yaml
app:
  name: shield-waf
  version: 5.3.0
  mode: release

waf:
  block_threshold: 70       # 拦截阈值
  observe_threshold: 50     # 观察阈值
  log_threshold: 30         # 日志阈值
  enable_semantic: true     # 语义分析（建议开启）
  enable_normalizer: true   # 编码归一化（建议开启）
  enable_fp_guard: true     # 误报防护
  max_body_size: 10485760   # 最大Body大小（10MB）
  # 自动封禁
  ban_on_block: true        # 拦截后自动封禁
  ban_threshold: 1          # 1次违规即封禁
  # 网段连坐封禁
  subnet_ban: true          # 开启网段连坐
  subnet_threshold: 1       # 1次违规连根拔起
  subnet_duration: 0        # 0=永久

proxy:
  listen_addr: ":80"        # WAF代理监听地址，标准80端口，用户无需带端口访问
  backend_url: "http://127.0.0.1:8080" # 被保护的真实业务后端，不能指向admin服务地址
  rewrite_host: false       # 是否重写Host头
  tls:
    enabled: false
    cert_file: ""
    key_file: ""
    listen_addr: ":443"
    redirect_http: false
  # 代理层安全头（默认关闭，开启后自动给后端响应加安全头）
  security_headers:
    enabled: false            # 默认关闭
    override_existing: false  # 后端已有就不覆盖
    frame_options: "SAMEORIGIN"
    content_type_nosniff: true
    xss_protection: "1; mode=block"
    referrer_policy: "strict-origin-when-cross-origin"
    hsts: false               # HSTS慎开
    hsts_max_age: 31536000
    hsts_include_sub: false
    csp: ""                   # CSP太危险，必须显式配置
    permissions_policy: ""

# 以下功能全部默认关闭，按需开启
ratelimit:
  enabled: false              # 限流（默认关）
  per_minute: 600
  per_second: 50

cc_protection:
  enabled: false              # CC防护（默认关）

bot:
  enabled: false              # Bot检测（默认关）
  verify_dns: true            # DNS反向验证
  honeypot: true              # 蜜罐

session_security:
  enabled: false              # 会话安全（默认关）
  csrf_enabled: true
  cookie_security: true

traffic:
  enabled: false              # 流量统一化（默认关）

darkgate:
  enabled: false              # 暗门保护（需配置magic_key和password）

upload:
  detection: false            # 上传检测（默认关）

ai:
  enabled: false              # AI检测（默认关）
```

### 默认行为（开箱即用，不会误杀）

启动后默认只开启：
- ✅ WAF核心检测（SQLi/XSS/命令注入等）
- ✅ 14层编码归一化
- ✅ 语义分析引擎
- ✅ FP Guard误报防护
- ❌ 限流/CC/Bot检测/会话安全/流量统一化（全部默认关闭）

---

## 📈 性能指标

| 指标 | 数值 | 说明 |
|------|------|------|
| 单节点 QPS | 10,000+ | 纯规则检测模式 |
| 延迟 | < 5ms | p95 检测耗时 |
| 并发连接 | 100,000+ | Go 原生 goroutine |
| 内存占用 | < 200MB | 常规负载 |
| 规则匹配 | 微秒级 | 优化正则 + 多模匹配 |

### 安全能力测试

| 测试维度 | 结果 | 说明 |
|----------|------|------|
| 基础攻击检测率 | **98.7%** | 76/77 攻击用例被检测 |
| 抗击穿率 | **96.8%** | 30/31 混淆绕过被检测 |
| 误报率（拦截） | **0.00%** | 0/28 正常流量无误拦截 |
| 误报率（日志） | **3.6%** | 少量正常流量仅记录日志 |
| 编码绕过检测 | **100%** | 14层编码归一化全部覆盖 |
| 深度代码审计 | ✅ 通过 | 77项安全问题全部修复 |

---

## 📁 项目结构

```
shield-XXXXXX/
├── admin/                    # Admin API 服务
├── cmd/
│   ├── waf-service/          # WAF 代理服务入口
│   └── admin-service/        # Admin 管理服务入口
├── configs/
│   ├── config.yaml           # 配置文件
│   └── config.yaml.example   # 配置示例
├── internal/                 # 核心引擎
│   ├── core/
│   │   ├── normalizer/       # 14层编码归一化
│   │   ├── detector/         # 规则检测器（800+规则）
│   │   ├── scorer/           # 评分器 + FP Guard(20层) + 基线白名单
│   │   └── engine.go         # 融合决策引擎
│   ├── defense/              # 55种攻击防御模块
│   │   ├── upload.go         # 文件上传检测（9层+5增强）
│   │   └── session/          # 会话安全（5模块）
│   ├── semantic/
│   │   └── parsers/          # 28种语义解析器
│   │       ├── context_analyzer.go  # 语义上下文分析器
│   │       ├── cross_language.go    # 跨语言嵌套处理
│   │       ├── code_understander.go # 代码理解器（7语言）
│   │       └── ...                  # SQL/XSS/Cmd/SSRF等解析器
│   ├── bot/                  # Bot防护
│   │   ├── detector.go       # 检测器（49种指纹）
│   │   ├── bot_semantic.go   # 语义分析（6大指标）
│   │   ├── bot_scorer.go     # 四维评分
│   │   ├── bot_classifier.go # 6分类
│   │   ├── header_fingerprint.go # 请求头指纹（8种异常）
│   │   ├── honeypot.go       # 路径蜜罐
│   │   ├── honeypot_injector.go # HTML注入蜜罐
│   │   └── behavior_analyzer.go  # 行为分析
│   ├── traffic/              # 流量统一化引擎
│   ├── sandbox/              # 沙箱（6引擎）
│   ├── crypto/               # 双重密码加密
│   ├── ai/                   # AI检测集成
│   ├── rules/                # 规则管理
│   ├── learn/                # 基线自学习
│   ├── storage/              # 存储层（Redis + Memory）
│   ├── config/               # 配置管理
│   └── ...
├── waf/
│   ├── service.go            # WAF服务主入口
│   ├── middleware/           # 中间件
│   │   ├── waf.go            # WAF检测
│   │   ├── cors.go           # CORS处理
│   │   ├── security_headers.go # 安全头
│   │   ├── darkgate.go       # 暗门保护
│   │   ├── bot_middleware.go # Bot防护
│   │   ├── upload_middleware.go # 上传检测
│   │   └── ...
│   └── proxy/
│       └── proxy.go          # 反向代理（含安全头注入）
├── web-admin/                # 前端管理控制台
├── release/                  # 部署包
│   └── shield-waf-enterprise-v4.6.0-linux-amd64.tar.gz
├── .github/workflows/        # CI/CD
├── Dockerfile
├── docker-compose.yml
└── README.md
```

---

## 📝 版本变更日志

### v5.3.0（当前版本）

**新增功能：**
- **网段连坐封禁（连根拔起）**：1次违规→/24+/16网段永久封锁（IPv6 /64+/48），新增 `SubnetThreshold` 可配置阈值
- **白名单安全优先**：CC/限流/Bot/封禁检查全链路白名单前置，白名单IP永不误封
- **trusted_cdn_ips 启动校验**：校验CIDR格式，非法配置自动跳过并告警
- **IPv6 网段支持**：网段计算统一使用 `net.ParseIP`，完整支持 IPv6 /64+/48 连坐封禁
- **BanManager 优先级链路**：白名单→受保护网段→IP封禁(fail-closed)→网段封禁(fail-open)

**Bug修复：**
- asyncworker `Stop()` 关闭业务channel导致panic → 仅关闭 `stopCh`
- asyncworker `Submit()` 向已关闭channel发送panic → 增加 `defer recover()` 保护
- admin `ccConfig`/`cfg` 共享配置数据竞争 → 增加 `ccConfigMu`/`cfgMu` 互斥锁
- `subnetsOf` 与 `IsSubnetBanned` 实现不一致 → 统一使用 `net.ParseIP` 计算网段
- `CheckAndBan` 中 `subnetsOf` 返回切片解构编译错误 → 改为遍历 `cidrs`

### v5.2.0

- 全项目代码深度审计 + 语义引擎加固 + 防御能力极限优化
- 35+ 高危/中危问题修复，40+ 核心文件，新增代码 600+ 行
- 28种语义解析器全部添加递归深度限制和类型断言守卫
- PathTraversal Unicode超长度编码绕过修复
- SSRF/XXE/SSTI多形态绕过修复
- 全漏洞极限测试 100% 检出 0% 误报

### v5.1.0

- X-Shield-WAF 品牌响应头体系（3级暴露级别）
- 反向代理配置优化（标准80端口 + 管理后台本地绑定）
- 全面代码安全审计（10个问题修复）

### v5.0.0

- WAF 3.0 智能引擎（上下文流+意图预测+融合决策）
- 本地 AI 模型（朴素贝叶斯分类器，纯Go实现）
- 攻击记录器闭环（AutoLearn Closed-Loop）
- 沙箱精准切割增强
- 33种漏洞极限测试 100% 检出 0% 误报

### v4.6.0

**新增功能：**
- 代理层安全头注入（ModifyResponse，默认关闭，后端已有不覆盖）
- WAF自身响应安全头（OpenSSF Gold认证必备）
- BotSemantic语义分析（6大指标：路径多样性/间隔均匀度/资源偏好/探测评分/UA轮换/爬取深度）
- BotScorer四维评分（指纹30%+语义30%+行为25%+攻击链15%）
- BotClassifier 6分类（human/search_engine/social_media/ai/crawler/malicious_bot）
- 请求头指纹检测（8种异常模式）
- AI爬虫识别（9种：GPTBot/ClaudeBot等）
- 社交媒体爬虫识别（10种）
- SEO工具蜘蛛识别（8种）
- 蜜罐HTML注入（动态token+隐藏链接）

**兼容性修复：**
- SecurityHeaders默认全部关闭
- CORS空配置直接pass
- 代理转发X-Real-IP/X-Forwarded-For/X-Forwarded-Proto/X-Forwarded-Host
- 限流/CC/Bot默认全部关闭
- trace_id响应头不覆盖后端已设置的
- 自定义Recovery返回502

### v4.3.0

**新增功能：**
- 上传检测14层编码归一化接入
- 上传检测语义分析接入
- 启发式检测（base64/chr/goto/超长行/混淆变量）
- 恶意代码精确定位（行号+偏移+上下文）
- 真实MIME探测
- AutoLearn闭环
- 多引擎交叉验证从8维升级到12维

### v4.2.0

**Bug修复（49个中危）：**
- 核心引擎8个（calcDeviation失效/字节rune混乱/重复ToLower等）
- 代理层10个（Content-Length同步/ContentType绕过/限流无告警等）
- DarkGate/Bot/FastPath 10个（开放重定向/session并发/TOCTOU等）
- 防御/语义层11个（cmd注入未用归一化/SSRF误报/XXE误报等）
- 沙箱10个（medium不拦截/saveManifest失败/变量命名反了等）

### v4.1.0

**Bug修复（20个严重/高危）：**
- FP Guard搜索引擎蜘蛛UA伪造绕过veto权
- FP Guard CMS路径过于宽泛导致绕过
- Body截断后ContentLength未更新导致后端挂起
- WebSocket头被Director删除
- 上传文件扩展名白名单未校验
- DarkGate sessions永不清理导致OOM
- Bot BanIP用request context导致封禁失效
- SessionTracker无锁导致并发panic
- CSRF Origin/Referer缺失返回true导致绕过
- SQLi签名缺少IgnoreCase导致大写漏检
- 重复签名导致分数重复累加
- typeWeights缺失大量类型
- roundFloat空实现

### v4.0.0

- 深度代码审计（77项安全问题）
- 15个严重安全漏洞修复
- 23个高危安全漏洞修复
- 客户端IP伪造/路径遍历/硬编码密钥/权限校验缺失等修复

### v3.2.0

- 代码理解器（7种语言）
- 语义上下文分析器
- 语义等价类扩展（20种）
- 攻击意图推理（15种）
- FP Guard误报防护（16层→20层）
- OpenSSF Best Practices认证文件

---

## 📄 License

**商业专有软件** — 未经授权不得商用、分发或修改。

> PHP 版为开源版本（MIT），Go 企业版为商业版本。

---

## 🤝 联系
- 官网 https://duduziy.com/shield-waf
- 邮件（QQ）634769642@qq.com
- 微信公众号：hkjs6986
- 开源版仓库（Gitee）：https://github.com/anye1991/shield-waf-master
- Issues：通过 GitHub Issues 反馈问题 
