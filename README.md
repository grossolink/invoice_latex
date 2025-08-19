# 发票内容格式要求

## 🚫 不能改的部分
- 所有 `\usepackage{...}` 命令
- `\geometry{...}` 参数
- `\definecolor{...}` 命令
- 所有 `\newcommand{...}` 和 `\newenvironment{...}`
- 表格列宽设置
- 页眉页脚设置
- 字体大小命令

## ✅ 可以改的部分
- 客户信息
- 发件人信息
- 项目名称
- 发票号码
- 商品内容
- 条款条件

## 📋 LaTeX语法和例子

### 客户信息
```latex
\projectname{项目名称}
\payeename{客户公司名}
\payeeaddresslineone{客户地址行1}
\payeeaddresslinetwo{客户地址行2}
\payeecontactlineone{客户邮箱}
\payeecontactlinetwo{客户网站}
```

### 发件人信息
```latex
\sendername{发件人公司名}
\senderaddresslineone{发件人地址行1}
\senderaddresslinetwo{发件人地址行2}
\sendercontactlineone{发件人邮箱}
\sendercontactlinetwo{发件人电话}
```

### 发票号码
```latex
\invoiceref{发票号码}
```

### 商品项目
```latex
\invoiceitem{1}{产品名称 \quad 型号 \\ {\fontsize{7.5}{9}\selectfont 产品详细描述 \\ Unit: 单位 \quad L/T: 交期状态}}{数量}{单价}

\rowcolor{altrowcolor}
\invoiceitem{2}{产品名称 \quad 型号 \\ {\fontsize{7.5}{9}\selectfont 产品详细描述 \\ Unit: 单位 \quad L/T: 交期状态}}{数量}{单价}
```

### 实际例子
```latex
\invoiceitem{1}{Conntek \quad EVM5700 \\ {\fontsize{7.5}{9}\selectfont EVM for Low Power, High Precision \\ Unit: SET \quad L/T: In Stock}}{1}{118.80}

\rowcolor{altrowcolor}
\invoiceitem{2}{Conntek \quad 5701AQ3QNS \\ {\fontsize{7.5}{9}\selectfont 3D Hal sensor IC, consumer grade, QFN3x3-16L \\ Unit: PCS \quad L/T: In Stock}}{5}{0.55}
```

### 条款条件
```latex
\termsandconditions{
1. Item 1 and 2 are currently in stock, ready to ship.\\
2. Item 3 and 4 are free samples.\\
3. \textbf{Payment Terms:} TT in advance\\
4. \textbf{Validity Period:} till 30th Aug 2025\\
5. \textbf{Currency:} EUR\\
6. \textbf{Warranty Period:} 12 months since delivery date
}
```
