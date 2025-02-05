# Classificação de Imagens CIFAR-10 com PyTorch e TensorFlow

Este repositório contém implementações de modelos de classificação de imagens usando o conjunto de dados CIFAR-10, treinados com PyTorch e TensorFlow. O objetivo é classificar imagens em uma das 10 categorias usando técnicas de aprendizado profundo.

## 📌 O que é o CIFAR-10?
O conjunto de dados CIFAR-10 é amplamente utilizado como benchmark em visão computacional e aprendizado de máquina. Ele consiste em **60.000 imagens coloridas de 32x32 pixels**, divididas em **10 classes**, com **6.000 imagens por classe**. As classes são:

- ✈️ Avião
- 🚗 Automóvel
- 🐦 Pássaro
- 🐱 Gato
- 🦌 Cervo
- 🐶 Cachorro
- 🐸 Sapo
- 🐴 Cavalo
- 🚢 Navio
- 🚚 Caminhão

O conjunto de dados é dividido em **50.000 imagens de treinamento** e **10.000 imagens de teste**. O CIFAR-10 é útil para avaliar o desempenho de modelos de aprendizado de máquina devido à sua diversidade e complexidade.

### 🔹 Por que o CIFAR-10 é útil?
- **📊 Benchmarking:** Serve como um padrão para comparar o desempenho de diferentes modelos de aprendizado de máquina.
- **🎨 Diversidade:** Contém uma variedade de objetos, tornando-o desafiador para os modelos generalizarem.
- **⚡ Tamanho Pequeno:** As imagens são pequenas (32x32 pixels), tornando viável o treinamento em hardware padrão.

---

## 🔄 Passos de Pré-processamento
### 1️⃣ Normalização
- **Conversão para Float32:** Os valores dos pixels são convertidos para `float32` para garantir compatibilidade com os modelos.
- **Normalização:** Subtração da média e divisão pelo desvio padrão do conjunto de treinamento para garantir uma escala consistente.

### 2️⃣ One-Hot Encoding
Os rótulos das classes são convertidos em vetores *one-hot*, necessários para tarefas de classificação multiclasse.

### 3️⃣ Data Augmentation (Aumento de Dados)
**Objetivo:** Aumentar artificialmente o tamanho do conjunto de treinamento aplicando transformações como **rotações, inversões e ajustes de brilho**.

📈 **Benefícios:**
- **Evita Overfitting** ➝ Introduz variações para evitar que o modelo memorize os dados.
- **Melhora a Robustez** ➝ O modelo se adapta melhor a diferentes condições do mundo real.
- **Simula Diversidade** ➝ Aprimora a capacidade de generalização do modelo.

---

## 🏋️‍♂️ Treinamento dos Modelos

### 🔹 Implementação em TensorFlow
- **Otimizador:** Adam (`learning rate = 0.0005`)
- **Função de Perda:** Entropia Cruzada Categórica
- **Callbacks:**
  - `ReduceLROnPlateau`: Reduz a taxa de aprendizado quando a perda de validação estagna.
  - `EarlyStopping`: Interrompe o treinamento se a perda de validação não melhorar por **40 épocas**.
  - `Callback Personalizado`: Exibe métricas detalhadas de treinamento.
- **Tamanho do Lote:** 64
- **Épocas:** 150

✅ **Resultados:**
- **Acurácia no Teste:** 89.63%
- **Perda no Teste:** 0.4726

### 🔹 Implementação em PyTorch
- **Otimizador:** Adam (`learning rate = 0.0005`)
- **Função de Perda:** Entropia Cruzada
- **Loop de Treinamento:** Implementação personalizada de `EarlyStopping` e `ReduceLROnPlateau`.
- **Tamanho do Lote:** 64
- **Épocas:** 150

✅ **Resultados:**
- **Acurácia no Teste:** 84.68%
- **Perda no Teste:** 1.6145

---

## 📊 Comparação dos Resultados
| Framework  | Acurácia no Teste | Perda no Teste |
|------------|------------------|---------------|
| TensorFlow | **89.63%**        | **0.4726**    |
| PyTorch    | 84.68%            | 1.6145       |

🔎 **Observações:**
- O **TensorFlow** obteve uma **acurácia maior** e **perda menor** do que o **PyTorch**.
- A diferença no desempenho pode ser devido a **diferenças no aumento de dados, algoritmos de otimização ou arquitetura específica** usada em cada framework.

---

## 📌 Conclusão
Ambas as implementações, **TensorFlow e PyTorch**, alcançaram **resultados competitivos** no CIFAR-10. No entanto, o modelo do **TensorFlow teve um desempenho ligeiramente melhor** em termos de acurácia e perda.

### ❓ Qual Framework é Melhor?
🔹 **TensorFlow** ➝ Melhor para quem prefere uma API de **alto nível**, com **callbacks e aumento de dados** integrados.

🔹 **PyTorch** ➝ Ideal para quem busca **mais flexibilidade** e **controle sobre o treinamento**.

🚀 Independentemente do framework escolhido, ambos oferecem um ambiente robusto para **aprendizado profundo e classificação de imagens**! 🔥

---

