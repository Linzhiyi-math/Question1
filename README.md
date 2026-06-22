# 第一题：LIF + OU 突触电流神经元模型

## 作业说明

本作业实现了 **LIF（Leaky Integrate-and-Fire）神经元模型** 结合 **OU（Ornstein-Uhlenbeck）突触电流** 的参数反解与数值验证。

给定目标 ISI 的均值与方差，通过白噪声极限理论（Ricciardi 公式）反解模型参数，并用 2 维 SDE 数值模拟验证其有效性。

---

## 环境要求

- **开发环境**：Python 3.14.4
- **运行环境**：Jupyter Notebook
- **依赖库**：numpy, scipy
- （版本见 requirements.txt）

安装第三方依赖：

```bash
pip install -r requirements.txt
```
---

## 运行方法

使用 Jupyter Notebook

```bash
jupyter notebook 第一题.ipynb
```

打开后，点击菜单栏 **Cell → Run All** 运行全部代码。


---

## 模型说明

**数学模型：**

$$\frac{dV}{dt} = -g_L V + g_{syn} I_{syn}$$

$$\tau \, dI_{syn} = (-I_{syn} + \mu) \, dt + \sigma \, dW$$

**主要参数（固定常数）：**

| 参数 | 值 | 说明 |
|------|----|------|
| `gL` | 1.0 | 泄漏电导 |
| `Vth` | 1.0 | 发放阈值 |
| `Vr` | 0.0 | 复位电位 |
| `tau_ref` | 0.0 | 不应期 |

**目标 ISI 统计量：**

| 参数 | 值 |
|------|----|
| `E[T]`（均值） | 0.6 |
| `Var(T)`（方差） | 0.08 |

---

## 预期输出

程序将输出：
1. 反解得到的模型参数 `g_syn`、`mu`、`sigma`
2. 理论自洽性检验结果
3. 不同 `tau` 值下数值模拟的误差对比表，验证白噪声极限的有效性
