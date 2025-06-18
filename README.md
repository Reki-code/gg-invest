# 龟龟投资法计算器

*基于龟龟投资法理念的A股投资分析工具*

[![Deployed on Vercel](https://img.shields.io/badge/Deployed%20on-Vercel-black?style=for-the-badge&logo=vercel)](https://vercel.com/tianyangtys-projects/v0-next-js-community-starter)
[![Built with v0](https://img.shields.io/badge/Built%20with-v0.dev-black?style=for-the-badge)](https://v0.dev/chat/projects/eiPZ2uT7eec)

## 项目简介

龟龟投资法计算器是一个基于B站UP主"史诗级韭菜"的龟龟投资法系列视频制作的纯前端投资分析工具。该工具专注于A股上市公司的股息投资分析，通过科学的计算公式帮助投资者评估股票的投资价值。

## 核心功能

### 📊 单股分析

- **股票信息展示**：显示公司基本信息，包括股价、市值、净利润等关键数据
- **参数调整**：可自定义净利润增长系数和目标股息率
- **智能计算**：自动计算预估综合收益率和可接受价格
- **价格分析**：直观显示当前股价是否被低估或高估

### 🧮 计算公式

#### 预估综合收益率

```
预估综合收益率 = (去年净利润 × 增长系数 × 股息支付率 + 注销式回购) ÷ 总市值
```

#### 可接受价格

```
可接受价格 = (去年净利润 × 增长系数 × 股息支付率 + 注销式回购) ÷ 目标股息率 ÷ 总股本
```

### 💡 特色功能

- **注销式回购支持**：计算中包含公司回购对股东收益的影响
- **综合收益分析**：同时考虑现金分红和股票回购收益
- **响应式设计**：支持桌面端和移动端访问
- **深色模式**：支持明暗主题切换

## 数据结构

### 股票数据字段

```typescript
interface StockData {
  code: string                    // 股票代码
  name: string                    // 公司名称
  lastYearNetProfit: number       // 去年净利润（亿元）
  minDividendPayoutRatio: number  // 最低股息支付率（0-1）
  defaultGrowthRate: number       // 默认增长系数
  currentMarketCap: number        // 当前总市值（亿元）
  totalShares: number             // 总股本（亿股）
  currentPrice: number            // 当前股价（元）
  defaultTargetDividendRate: number // 默认目标股息率（0-1）
  cancellationBuyback: number     // 注销式回购（亿元）
  lastUpdated: string             // 最后更新时间
}
```

## 项目结构

```
├── app/                    # Next.js App Router
│   ├── globals.css        # 全局样式
│   ├── layout.tsx         # 根布局
│   └── page.tsx           # 主页面
├── components/            # React组件
│   ├── ui/               # shadcn/ui组件
│   ├── calculation-results.tsx
│   ├── parameter-inputs.tsx
│   ├── stock-info.tsx
│   ├── stock-selector.tsx
│   └── theme-toggle.tsx
├── data/                 # 数据文件
│   └── stocks.json       # 股票数据
├── types/                # TypeScript类型定义
│   └── stock.ts
├── utils/                # 工具函数
│   └── calculations.ts   # 计算逻辑
└── lib/                  # 库文件
    └── utils.ts
```

## 本地开发

### 环境要求

- Node.js 18+
- npm/yarn/pnpm

### 安装依赖

```bash
npm install
# 或
yarn install
# 或
pnpm install
```

### 启动开发服务器

```bash
npm run dev
# 或
yarn dev
# 或
pnpm dev
```

访问 [http://localhost:3000](http://localhost:3000) 查看应用。

### 构建生产版本

```bash
npm run build
# 或
yarn build
# 或
pnpm build
```

## 数据维护

股票数据存储在 `data/stocks.json` 文件中，包含以下信息：
- 公司基本信息（代码、名称）
- 财务数据（净利润、市值、股本等）
- 股息政策（支付率、回购金额）
- 默认参数设置

### 添加新股票
在 `data/stocks.json` 的 `stocks` 数组中添加新的股票对象：

```json
{
  "code": "000001.SZ",
  "name": "平安银行",
  "lastYearNetProfit": 400.5,
  "minDividendPayoutRatio": 0.3,
  "defaultGrowthRate": 1.0,
  "currentMarketCap": 2500,
  "totalShares": 19.4,
  "currentPrice": 12.85,
  "defaultTargetDividendRate": 0.05,
  "cancellationBuyback": 20.0,
  "lastUpdated": "2024-01-15"
}
```

## 投资理念

本工具基于龟龟投资法的核心理念：
- **长期价值投资**：关注公司的长期盈利能力
- **股息投资策略**：重视现金分红和股东回报
- **安全边际**：通过计算合理价格避免高估风险
- **综合收益考量**：同时考虑分红和回购对股东的价值

## 免责声明

⚠️ **重要提示**：
- 本工具仅供投资参考，不构成投资建议
- 投资有风险，入市需谨慎
- 数据来源于公开信息，请以官方公告为准
- 计算结果基于历史数据和假设，实际情况可能存在差异

## 相关链接

- **投资理念来源**：[史诗级韭菜 - B站主页](https://space.bilibili.com/322005137)
- **龟龟投资法视频**：[点击观看](https://www.bilibili.com/video/BV1EDJWzNEXn)

## 贡献

欢迎提交Issue和Pull Request来改进这个项目。

## 许可证

本项目仅供学习和参考使用。
