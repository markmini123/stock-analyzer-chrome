# 雪球AI投资伴侣（Chrome / Edge / Firefox）

在雪球股票页（`https://xueqiu.com/S/...`）中，用户只需在页面任意位置左键点击，即可触发：

1. 识别当前股票代码
2. 读取雪球登录态（cookie/token）
3. 拉取基本面与财务指标
4. 调用大模型按巴菲特价值投资框架生成分析
5. 在浮层展示并支持导出（JSON/TXT）

## 功能

- 任意左键触发分析（雪球股票页）
- 自动从浏览器 Cookie 读取雪球 token（可手动刷新）
- 参考 `pysnowball` 的接口路径获取雪球数据
- 巴菲特六维价值分析模板（护城河/管理层/财务质量/估值安全边际等）
- 结果缓存（默认 5 分钟）
- 分析结果导出：`JSON`、`TXT`

## 浏览器版本

仓库内置三份清单：

- `manifests/manifest.chrome.json`
- `manifests/manifest.edge.json`
- `manifests/manifest.firefox.json`

通过脚本切换当前 `manifest.json`：

```bash
bash scripts/use-manifest.sh chrome
bash scripts/use-manifest.sh edge
bash scripts/use-manifest.sh firefox
```

## 安装

### Chrome

1. 执行 `bash scripts/use-manifest.sh chrome`
2. 打开 `chrome://extensions/`
3. 开启开发者模式
4. 点击“加载已解压的扩展程序”
5. 选择当前项目目录

### Edge

1. 执行 `bash scripts/use-manifest.sh edge`
2. 打开 `edge://extensions/`
3. 开启开发人员模式
4. 点击“加载解压缩的扩展”
5. 选择当前项目目录

### Firefox

1. 执行 `bash scripts/use-manifest.sh firefox`
2. 打开 `about:debugging#/runtime/this-firefox`
3. 点击“临时载入附加组件”
4. 选择项目目录下的 `manifest.json`

## 配置

点击扩展图标打开设置页，填写：

- `LLM API Key`
- `LLM API Base URL`（OpenAI 兼容接口）
- `模型名称`

可选：

- 开启 `自动从雪球 Cookies 读取 token`
- 手动填写 `xq_a_token/xq_r_token/device_id`
- 调整缓存时长 `cacheTtlMs`

## 使用

1. 登录雪球
2. 打开任意股票页面，例如：`https://xueqiu.com/S/SH600519`
3. 在页面任意位置点击鼠标左键
4. 右上角浮层出现分析结果
5. 可点击浮层按钮：`重跑`、`强刷`、`导出JSON`、`导出TXT`

## 说明

- 本插件仅用于研究与学习，不构成投资建议。
- 如果提示“无法获取雪球数据”，请确认雪球处于登录状态并刷新页面重试。
