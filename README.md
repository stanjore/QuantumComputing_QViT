# QViT_FIRE298
Experimentation for QViT technology. Goal is to reproduce results, and expand upon the original quantum circuit to observe higher accuracies/speedups in computation.

Based on https://github.com/EyupBunlu/QViT_HEP_ML4Sci


## circuits.py functions

| Function              | Description |
| :---------------- | :------ |
| compute_attention(alphas,norms,compute_element)        |   Computes attention weights by iterating through a set of norms and alphas, applying a computation function, and generating normalized interaction matrices.  |
| encode_token(circuit,data,nqubits)           |   Initializes a quantum circuit by applying Hadamard gates and parameterized rotations (Rx) based on input data.   |
| qk_ansatz(circuit,data,parameters,nqubits)    |  Implements a quantum circuit ansatz for query-key computation, involving parameterized rotations (Rx, Ry) and entanglement layers using CNOT gates.  |
| v_ansatz(circuits,data,parameters,nqubits) |  Implements a quantum circuit ansatz for value computation, similar to qk_ansatz, but for values rather than query-key pairs.   |
| measure_query_key(data,parameters,nqubits) | Measures the query-key interactions by encoding input data into a quantum circuit, applying the qk_ansatz, and computing the expectation value on a specific qubit.|
| measure_value(data,parameters,nqubits)|  Measures the value representation by encoding input data into a quantum circuit, applying the v_ansatz, and computing expectation values across multiple qubits. |

## ml_functions.py functions

| Function              | Description |
| :---------------- | :------ |
| (CLASS) simple_dataset        |   a custom dataset class from pytorch, contains 3 functions: init - intializes dataset with target array, len - returns length of dataset, getitem - retrieves the sample from a given index |
| patcher(data,sh)          |   splits input data tensor (data) into patches with specified shpe, these shapes are specified in a tuple (sh), returns the split tensor    |
| patcher_with_color(data,sh)    |   similar to patcher, but accounts for data with an additional color dimention, splits tensor with color dimention (data) into patches based on specified shape tuple (sh)  |
| train(model,tr_dl,val_dl,loss_fn,optim,n_epochs,device='cuda') |   trains the NN (model) based on the training data via the loader (tr_dl) and compares it to the validation data via loader (val_dl), runs for n_epochs epochs and uses the given optimizer (optim) and loss function (loss_fn) to adjust the weights through each epoch to adjust model predictions and accuracy 

## Paper image descriptions
| Image | Description |
| :----------------: | :------ |
| <img src="img/figure_3.png" width="500" /> | Input images are divided into patches of equal area and processed into a matrix. This matrix is processed by encoder layers, with outputs passed sequentially. The final encoder layer's first row is sent to a classifier for probabilities (Figure 3b). In the column-pooling variant, the matrix is reduced via mean or max pooling per column, producing a vector input for the classifier (Figure 3a). |
| <img src="img/figure_4.png" width="200" /> | The multi-head attention layer splits the input matrix into submatrices by dividing its columns. Each submatrix is processed by an attention head, which then resizes it to the original input.|
