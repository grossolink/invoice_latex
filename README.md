# LaTeX 专业发票/报价单模板

这是一个功能完整的LaTeX发票和报价单模板，具有现代化的设计和专业的布局。

## 🚀 快速开始

### 1. 环境要求
- TeX Live 2025 或更高版本
- 支持 `pdflatex` 编译

### 2. 编译命令
```bash
pdflatex invoice._new.tex
```

## 📋 模板特性

### ✨ 核心功能
- 🎨 **现代化设计**: 红色主题头部，专业布局
- 📄 **多页支持**: 使用 `longtable` 实现表格跨页
- 🔢 **自动计算**: 自动计算小计、税费和总计
- 🌍 **多语言支持**: 支持英文内容
- 📱 **响应式布局**: 100% 表格宽度，适配不同内容

### 🎯 布局组件
- **头部**: 红色背景，白色文字，包含"INVOICE"标题和发票信息
- **发件人信息**: 公司详情和联系方式
- **收件人信息**: 客户信息和项目详情
- **商品表格**: 序号、项目描述、数量、单价、小计
- **条款条件**: 付款条件、有效期、保修等
- **页脚**: Logo和页码，垂直居中对齐

## 🔧 自定义配置

### 1. 基本信息设置
在文档开头修改以下变量：

```latex
\projectname{Sensor Components}           % 项目名称
\payeename{Sensitec GmbH}                % 客户公司名
\payeeaddresslineone{Schanzenfeldstr. 2} % 客户地址行1
\payeeaddresslinetwo{D-35578 Wetzlar}    % 客户地址行2
\payeecontactlineone{info@sensitec.com}  % 客户邮箱
\payeecontactlinetwo{www.sensitec.com}   % 客户网站
```

### 2. 发件人信息
```latex
\sendername{Grosso Link GMBH}            % 发件人公司名
\senderaddresslineone{Rue des Sugiez 18} % 发件人地址行1
\senderaddresslinetwo{2074 Marin-Epagnier} % 发件人地址行2
\sendercontactlineone{contacts@grosso.link} % 发件人邮箱
\sendercontactlinetwo{+41 788885186}     % 发件人电话
```

### 3. 发票信息
```latex
\invoiceref{1632-F}                      % 发票号码
% 日期自动使用系统当前日期
```

### 4. 颜色主题
```latex
\definecolor{highlightcolour}{HTML}{C30D23}  % 主色调（红色）
\definecolor{rulecolour}{HTML}{C30D23}       % 表格线颜色
\definecolor{altrowcolor}{gray}{0.98}        % 交替行背景色
```

## 📝 添加商品项目

### 基本语法
```latex
\invoiceitem{序号}{商品描述}{数量}{单价}
```

### 详细商品描述示例
```latex
\invoiceitem{1}{Conntek \quad EVM5700 \\ 
  {\fontsize{7.5}{9}\selectfont EVM for Low Power, High Precision \\ 
   Unit: SET \quad L/T: In Stock}}{1}{118.80}
```

### 交替行背景色
```latex
\rowcolor{altrowcolor}  % 在偶数行前添加
\invoiceitem{2}{商品描述}{数量}{单价}
```

## 🎨 样式定制

### 1. 字体大小调整
- 主标题: `\Huge` (36pt)
- 公司名: `\large` (12pt)
- 正文: `\footnotesize` (8pt)
- 商品描述第二行: `\fontsize{7.5}{9}\selectfont` (7.5pt)

### 2. 表格样式
- 表格线: 0.5pt 细线
- 交替行: 浅灰色背景 (98% 白)
- 圆角背景: 使用 `tcolorbox` 包

### 3. 页面布局
- 页边距: 左右 1cm，底部 2.5cm
- 头部高度: 3.2cm
- 第二页顶部边距: 2cm

## 📊 表格结构

### 商品表格列宽
```latex
\begin{longtable}{@{}c@{\extracolsep{\fill}}p{0.48\textwidth}@{\extracolsep{\fill}}R{0.08\textwidth}@{\extracolsep{\fill}}R{0.16\textwidth}@{\extracolsep{\fill}}R{0.16\textwidth}@{}}
```
- **NO.**: 序号列 (居中)
- **ITEM**: 商品描述列 (48% 宽度，左对齐)
- **QTY**: 数量列 (8% 宽度，右对齐)
- **UNIT PRICE**: 单价列 (16% 宽度，右对齐)
- **SUBTOTAL**: 小计列 (16% 宽度，右对齐)

## 🔄 生成新文档

### 步骤1: 复制模板
```bash
cp invoice._new.tex my_invoice.tex
```

### 步骤2: 修改基本信息
- 更新客户信息
- 修改项目名称
- 调整发票号码

### 步骤3: 添加商品项目
- 使用 `\invoiceitem` 命令
- 根据需要添加 `\rowcolor{altrowcolor}`

### 步骤4: 编译生成
```bash
pdflatex my_invoice.tex
```

## 📋 条款条件模板

### 标准条款
```latex
\termsandconditions{
1. Item 1 and 2 are currently in stock, ready to ship.\\
2. Item 3 and 4 are free samples.\\
3. Payment Terms: TT in advance\\
4. Validity Period: till 30th Aug 2025\\
5. Delivery cost: The price does not include freight insurance.\\
6. Currency: EUR\\
7. Warranty Period: 12 months since delivery date\\
8. Date Code: within 6 months\\
9. Remarks: L/T can be shorter when ordering small quantities
}
```

## 🎯 使用GPT生成新发票

### 提示词模板
```
请使用以下LaTeX发票模板生成一个新的发票：

[粘贴 invoice._new.tex 的完整内容]

要求：
1. 客户公司：[公司名称]
2. 项目名称：[项目描述]
3. 发票号码：[发票号]
4. 商品项目：[详细商品列表，包括名称、描述、数量、单价]
5. 条款条件：[具体条款要求]

请保持模板的样式和布局不变，只更新内容信息。
```

## ⚠️ 重要：以下内容绝对不能修改

### 🚫 禁止修改的部分
- **包引用部分**: 所有 `\usepackage{...}` 命令
- **页面设置**: `\geometry{...}` 参数
- **颜色定义**: `\definecolor{...}` 命令
- **命令定义**: 所有 `\newcommand{...}` 和 `\newenvironment{...}`
- **表格结构**: `\begin{longtable}{...}` 的列宽设置
- **页眉页脚**: `\fancyfoot{...}` 和 `\fancyhf{...}` 设置
- **头部样式**: `\invoiceheader` 命令的实现
- **字体大小**: 所有 `\fontsize{...}{...}\selectfont` 命令

### ✅ 允许修改的部分
- 客户信息变量值
- 发件人信息变量值
- 项目名称
- 发票号码
- 商品项目内容
- 条款条件内容
- 商品数量（保持数字格式）

## 📋 发票内容整理要求

### 🎯 商品描述格式规范
```
第一行：产品名称 + 型号（保持原字体大小）
第二行：产品详细描述（字体缩小到75%）
第三行：Unit: [单位] + L/T: [交期状态]（如果有内容）
```

### 📝 商品信息示例
```
Conntek \quad EVM5700
{\fontsize{7.5}{9}\selectfont EVM for Low Power, High Precision}
Unit: SET \quad L/T: In Stock
```

### 🔢 数量格式
- 使用纯数字，如：`1`, `5`, `10`
- 不要添加单位或符号

### 💰 价格格式
- 使用欧元符号：`EUR`
- 价格数字保持两位小数：`118.80`
- 免费样品使用：`0.00`

### 📋 条款条件格式
- 每条条款单独一行
- 使用 `\\` 换行
- 保持编号格式：`1.`, `2.`, `3.`
- 重要信息加粗：`\textbf{Payment Terms:} TT in advance`

## 🐛 常见问题

### 1. 编译错误
- 确保使用 `pdflatex` 编译
- 检查所有必需包是否安装
- 验证图片文件路径

### 2. 表格跨页问题
- 使用 `longtable` 环境
- 在 `\endhead` 中添加 `\vspace{2cm}` 控制第二页顶部边距

### 3. 字体显示问题
- 确保 TeX Live 包含所需字体
- 检查字体包是否正确加载

## 📚 技术细节

### 使用的LaTeX包
- `geometry`: 页面布局控制
- `longtable`: 跨页表格支持
- `fancyhdr`: 页眉页脚定制
- `tikz`: 图形绘制和定位
- `tcolorbox`: 圆角背景框
- `colortbl`: 表格颜色支持
- `siunitx`: 数字格式化

### 关键命令
- `\invoiceheader`: 创建红色头部
- `\contactdetails`: 发件人信息表格
- `\invoicedtotable`: 收件人信息表格
- `\invoicetable`: 商品表格环境
- `\amountdue`: 金额和条款表格

## 🤝 贡献

欢迎提交改进建议和bug报告！

## �� 许可证

此模板可自由使用和修改。
