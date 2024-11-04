# QViT_FIRE298
Experimentation for QViT technology. Goal is to reproduce results, and expand upon the original quantum circuit to observe higher accuracies/speedups in computation.

Based on https://github.com/EyupBunlu/QViT_HEP_ML4Sci


# CIRCUITS INFO
The script installs necessary quantum computing libraries using the commands !pip install tensorcircuit and !pip install pennylane, which are essential for implementing quantum machine learning functions. It imports the QViT (Quantum Vision Transformer) module from the cloned repository in Google Colab or from a local path, depending on the execution environment. These components set up the groundwork for integrating quantum circuits into the machine learning workflows.

# ML FUNCTIONS INFO
Data preparation begins with downloading and preparing the MNIST dataset using mnist_trainset = MNIST(root='./data', train=True, download=True). The dataset is then transformed, applying resizing and normalization to the images through a composed transformation pipeline. Two different models, a classical model and a hybrid model, are initialized with specific configurations, using the command classical_model = HViT(...).to(device) and hybrid2_model = HViT(...).to(device).

Training configurations are set up with optimization algorithms using Adam and a cross-entropy loss function specified by loss_fn = nn.CrossEntropyLoss(reduction='none'). The training procedure is encapsulated in a function defined as def train(model, tr_dl, val_dl, loss_fn, optim, n_epochs, device='cuda'), which manages forward passes, loss calculation, and parameter updates. The training function is executed for both models, capturing their performance histories.

Finally, the script visualizes the training results by plotting the training and validation loss and accuracy for both models, allowing for a clear comparison of their performances over the training epochs.

# OBSERVATIONS WHILE PRODUCING RESULTS
- n/a
# POTENTIAL AREAS OF QUANTUM CIRCUIT TO BE IMPROVED
- n/a
