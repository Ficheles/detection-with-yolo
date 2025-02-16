# 🚀 Projeto de Detecção de Gestos com Mãos usando YOLO ✋🤖

Este projeto utiliza a rede neural YOLO (You Only Look Once) para detectar gestos feitos com as mãos em imagens. O objetivo é treinar o modelo YOLO para identificar e classificar diferentes gestos realizados com as mãos, aplicando-o em uma base de dados de imagens de sinais manuais. O modelo pode ser usado em sistemas de reconhecimento de gestos em tempo real.

## 📋 Funcionalidades

- **Detecção de Gestos Manuais**: Detecte gestos feitos com as mãos em imagens estáticas utilizando o modelo YOLO.
- **Modelo Pré-Treinado**: Utiliza o modelo YOLOv5 pré-treinado para detectar objetos e pode ser adaptado para detectar gestos manuais.
- **Treinamento Personalizado**: Possibilidade de treinar o modelo com sua própria base de dados de gestos manuais.

## 🗃 Base de Dados

Para este projeto, utilizamos a base de dados **Sign Language MNIST** como exemplo. Esta base contém imagens de gestos das letras do alfabeto em linguagem de sinais americana. A base é simples e serve para fins de teste e demonstração.

Alternativamente, você pode usar outras bases de dados como:

- **HAND GESTURE RECOGNITION DATABASE**: Contém gestos mais dinâmicos e complexos.
- **Custom Data**: Você pode criar sua própria base de dados de gestos manuais e rotulá-la para o treinamento.

## 🔧 Tecnologias

- **YOLO (You Only Look Once)**: Rede neural eficiente para detecção de objetos em tempo real.
- **OpenCV**: Biblioteca para manipulação e exibição de imagens.
- **PyTorch**: Framework utilizado para carregar e treinar o modelo YOLO.
- **LabelImg**: Ferramenta para rotulação de dados (opcional).

## 🚀 Como Usar

### 1. Instalar Dependências

Instale as dependências necessárias usando o `pip`:

```bash
pip install opencv-python opencv-python-headless torch torchvision matplotlib
```

### 2. Carregar e Exibir Imagens

Carregue uma imagem e visualize o gesto manual:

```python
import torch
import torchvision
import cv2
import matplotlib.pyplot as plt

# Carregar uma imagem da base de dados
train_set = torchvision.datasets.FashionMNIST(root='./data', train=True, download=True)
img, label = train_set[0]
plt.imshow(img, cmap='gray')
plt.title(f'Label: {label}')
plt.show()
```

### 3. Detectar Gestos com YOLO

Carregue um modelo pré-treinado YOLOv5 e faça a detecção de gestos em uma imagem.

```python
# Carregar o modelo YOLOv5 pré-treinado
model = torch.hub.load('ultralytics/yolov5', 'yolov5s')

# Carregar uma imagem de gesto manual
img_path = 'path/to/hand_gesture_image.jpg'
img = cv2.imread(img_path)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Realizar a detecção
results = model(img_rgb)

# Exibir a imagem com a caixa delimitadora
results.show()
```

### 4. Treinamento Personalizado

Se você tiver sua própria base de dados de gestos, crie anotações no formato YOLO e treine o modelo com o seguinte comando:

```bash
python train.py --data custom_data.yaml --cfg yolov5s.yaml --weights '' --batch-size 16 --img-size 640 --epochs 50
```

O arquivo `custom_data.yaml` deve conter o caminho para as imagens e as anotações das classes de gestos.

## 🗂 Estrutura do Projeto

Aqui está a estrutura básica do diretório:

```
.
├── data/
│   ├── train/          # Imagens de treinamento
│   ├── test/           # Imagens de teste
│   └── annotations/    # Arquivos de anotações (no formato YOLO)
├── models/             # Arquivos do modelo treinado
├── train.py            # Script para treinar o modelo
├── detect.py           # Script para realizar a detecção de gestos
├── README.md           # Este arquivo
└── requirements.txt    # Dependências do projeto
```

## 🤝 Contribuições

Contribuições para o projeto são **bem-vindas**! Sinta-se à vontade para abrir **issues** ou enviar **pull requests** com melhorias, correções ou sugestões. Vamos construir algo incrível juntos! 💻

## 📜 Licença

Este projeto está licenciado sob a Licença MIT - consulte o arquivo [LICENSE](LICENSE) para mais detalhes. 

---

🎉 **Obrigado por contribuir ou utilizar este projeto!** 🎉


### Melhorias com Emojis:
1. **Cabeçalhos e Títulos**: Emojis ajudam a destacar os principais tópicos, como o uso do modelo YOLO, as funcionalidades e a licença.
2. **Exemplos de Código**: Não alterei o código, mas acrescentei emojis para torná-lo mais fácil de seguir visualmente.
3. **Títulos e Seções**: Emojis são usados em seções como "Tecnologias", "Como Usar", "Contribuições", etc., para tornar o arquivo mais atraente.
4. **Contribuições e Licença**: Adição de emojis para engajar mais o usuário na ideia de colaboração e para tornar o final do README mais positivo.

Esse formato torna o arquivo mais amigável e visualmente interessante! 😄
