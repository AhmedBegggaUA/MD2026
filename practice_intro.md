# Introduction to the practical part of MD2025


## Welcome to the practice material of MD2025

Welcome to the practice part of MD2025. In this part we will learn the main libraries of Python for Machine Learning and Data Science. We will review the main libraries for solving Machine Learning problems, such as Numpy, NetworkX, Matplotlib, Scikit-Learn, etc. We will also learn how to use Jupyter Notebook, a web application that allows you to create and share documents that contain live code, equations, visualizations and explanatory text. The notebooks can be used to perform data cleaning and transformation, numerical simulation, statistical modeling, data visualization, machine learning, etc. In the following code, we will see an example of how to these libraries can work together.

```{code-block} python
---
linenos: true
---
import numpy as np 
import matplotlib.pyplot as plt
import networkx as nx

np.random.seed(42) # Fijar semilla para reproducibilidad

# Crear una matriz de adyacencia aleatoria de 10 x 10
A = np.random.randint(0, 2, size=(8, 8))

# Crear un grafo a partir de la matriz
G = nx.Graph(A)
pos = nx.spring_layout(G, seed=42) # Posiciones para graficar [opcional]
# Dibujar el grafo con matplotlib
plt.figure(figsize=(10, 8)) # Tamaño del gráfico (ancho, alto)
plt.title(label='Grafo de ejemplo', # Título
            fontsize=15, # Tamaño de fuente
            fontweight='bold', # Tipo de letra
            color='skyblue', # Color de letra
            loc='left') # Posición del título

nx.draw(G, with_labels=True, # Mostrar etiquetas
            pos=pos, # Posiciones
            node_color='skyblue', # Color de nodos
            edge_cmap=plt.cm.Blues, # Color de aristas
            node_size=700,# Tamaño de nodos
            arrowsize=10, # Tamaño de flechas
            linewidths=2, # Ancho de aristas
            font_size=10, # Tamaño de letra de nodos
            font_weight='bold', # Tipo de letra de nodos
            font_color='black', # Color de letra de nodos 
            alpha=0.9, # Transparencia
            width=1) # Ancho de aristas
plt.show() # Mostrar gráfico
```
```{figure} ./images/practices/grafo_ejemplo.png
---
name: Integration between libraries
width: 700px
align: center
height: 500px
---
Integration between libraries
```

But before we start, we need to set up our environment. For this, we will use Anaconda, a free and open source distribution of the Python and R programming languages for scientific computing, that aims to simplify package management and deployment. Anaconda comes with more than 1,500 packages and a package manager called conda. We will use conda to install the libraries we need for this course.

## Installing Conda
There are lots of ways to install conda, but we recommend you to install Anaconda. There are lots of tutorials on how to install Anaconda in Youtube or websites. Here are some of them, but again, you can choose the one you like the most.
To install Anaconda, you can follow the instructions in the following link: [https://docs.anaconda.com/anaconda/install/](https://docs.anaconda.com/anaconda/install/). Once you have installed Anaconda, you can open the Anaconda Navigator and install the libraries we will use in this course. To do this, you can follow the instructions in the following link: [https://docs.anaconda.com/anaconda/navigator/getting-started/](https://docs.anaconda.com/anaconda/navigator/getting-started/).
```{warning}
After trying your best and spent 2 or 3 hours, if you have any problems installing Anaconda,, you can ask for help by sending an email to the following address: ahmed.begga@ua.es. Please, include the error message you are getting and the steps you have followed to install Anaconda. And do not send trivial questions, please.
```
### Other resources for installing Anaconda

[Anaconda for windows](https://youtu.be/5mDYijMfSzs?si=IUoeUcX3v33rNmwy)


[Anaconda for Mac (M1, M2, etc)](https://youtu.be/6-i9pY2n2FU?si=-pWth1et98XTsRWF)

## IDEs for Python

You can use any IDE you want to write your code. However, we recommend you to use Jupyter Notebook, a web application that allows you to create and share documents that contain live code, equations, visualizations and explanatory text. The notebooks can be used to perform data cleaning and transformation, numerical simulation, statistical modeling, data visualization, machine learning, etc. To install Jupyter Notebook, you can follow the instructions in the following link: [https://jupyter.org/install](https://jupyter.org/install).
```{note}
In this course, we will use Jupyter Notebook to write our practical reports. You can use any other IDE you want, but we recommend you to use Jupyter Notebook.
```
### Jupyter Notebook

Jupyter Notebook is an user-friendly IDE that allows you to write code in Python and Markdown. It is very useful for writing reports, as you can write code and text in the same document. Here we are going to give you few commands to learn how to use markdown in Jupyter Notebook. For more information, you can check the following link: [jupyter tutorial](https://www.datacamp.com/tutorial/markdown-in-jupyter-notebook).

#### Headers
To create a header, you can use the following syntax:
```md
# Header 1
## Header 2
### Header 3
#### Header 4
##### Header 5
###### Header 6
```
#### Emphasis
To create emphasis, you can use the following syntax:
```md
*italic*
**bold**
***bold and italic***
~~strikethrough~~
```
#### Lists
To create lists, you can use the following syntax:
```md
- Item 1
- Item 2
- Item 3
```
Giving as a result:
- Item 1
- Item 2
- Item 3

You can also create ordered lists:
```md
1. Item 1
2. Item 2
3. Item 3
```
Giving as a result:
1. Item 1
2. Item 2
3. Item 3

#### Math
To create math expressions, you can use the following syntax:
```md
$y = x^2$
```
Giving as a result:
$y = x^2$
##### Math blocks
To create math blocks, you can use the following syntax:
```md
$$
y = x^2
$$
```
Giving as a result:
$$
y = x^2
$$
##### Math symbols
To create math symbols, you can use the following syntax:
```md
$\alpha$
$\beta$
$\gamma$
$\delta$
$\epsilon$
$\zeta$
$\eta$
$\theta$
$\iota$
$\kappa$
$\lambda$
$\mu$
$\nu$
$\xi$
$\pi$
$\rho$
$\sigma$
$\tau$
$\phi$
```
Giving as a result:
$\alpha, \beta,\gamma ,\delta ,\epsilon ,\zeta ,\eta ,\theta ,\iota ,\kappa ,\lambda ,\mu ,\nu ,\xi ,\pi ,\rho ,\sigma ,\tau ,\phi$
##### Matrices
To create matrices, you can use the following syntax:
```md
$
\begin{bmatrix}
1 & 2 & 3 \\
4 & 5 & 6 \\
7 & 8 & 9
\end{bmatrix}
$
```
Giving as a result:
$
\begin{bmatrix}
1 & 2 & 3 \\
4 & 5 & 6 \\
7 & 8 & 9
\end{bmatrix}
$
##### Derivatives
To create derivatives, you can use the following syntax:
```md
$
\frac{dy}{dx}
$
```
Giving as a result:
$
\frac{dy}{dx}
$
##### Integrals
To create integrals, you can use the following syntax:
```md
$
\int_{a}^{b} x^2 dx
$
```
Giving as a result:
$
\int_{a}^{b} x^2 dx
$
##### Limits
To create limits, you can use the following syntax:
```md
$
\lim_{x \to \infty} x^2
$
```
Giving as a result:
$
\lim_{x \to \infty} x^2
$
##### Sums
To create sums, you can use the following syntax:
```md
$
\sum_{i=1}^{n} x_i
$
```
Giving as a result:

$
\sum_{i=1}^{n} x_i
$

##### Products
To create products, you can use the following syntax:
```md
$
\prod_{i=1}^{n} x_i
$
```
Giving as a result:
$
\prod_{i=1}^{n} x_i
$
##### Roots
To create roots, you can use the following syntax:
```md
$
\sqrt{x}
$
```
Giving as a result:
$
\sqrt{x}
$
##### Fractions
To create fractions, you can use the following syntax:
```md
$
\frac{1}{2}
$
```
Giving as a result:
$
\frac{1}{2}
$
#### Tables
To create tables, you can use the following syntax:
```md
| Header 1 | Header 2 |
| -------- | -------- |
| Cell 1   | Cell 2   |
| Cell 3   | Cell 4   |
```
Giving as a result:
| Header 1 | Header 2 |
| -------- | -------- |
| Cell 1   | Cell 2   |
| Cell 3   | Cell 4   |

#### Images
To add an image, you can use the following syntax:
```md
![alt text](image_path)
```
#### Links
To add a link, you can use the following syntax:
```md
[link text](url)
```
#### Citations
We have agreed to add them by hand with bullets like this:
```md
- [1] Author, Title, Year
- [2] Author, Title, Year
```