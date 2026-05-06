# AI/ML Engineer Quick Reference

A cheatsheet for the AI/ML engineer's daily workflow. Keep this handy!

---

## 🐍 Python Essentials

### NumPy Quick Syntax
```python
import numpy as np

# Create arrays
arr = np.array([1, 2, 3, 4, 5])
matrix = np.random.rand(3, 4)

# Common operations
mean = arr.mean()
std = arr.std()
sort = arr.sort()  # In-place
sorted_arr = np.sort(arr)  # Returns new array

# Matrix operations
result = matrix @ matrix.T  # @ for matrix multiplication
dot = np.dot(a, b)  # Traditional dot product
transpose = matrix.T

# Broadcasting
a = np.array([[1, 2, 3]])  # Shape (1, 3)
b = np.array([[1], [2], [3]])  # Shape (3, 1)
result = a + b  # Shape (3, 3) - broadcasting!

# Advanced
reshape = matrix.reshape(6, 2)
flatten = arr.flatten()  # or arr.ravel()
stack = np.vstack([a, b])  # Stack along rows
concat = np.hstack([a, b])  # Stack along columns
```

### Pandas Essentials
```python
import pandas as pd

# Create DataFrame
df = pd.DataFrame({'name': ['Alice', 'Bob', 'Charlie'],
                  'age': [25, 30, 35]})

# Select columns
subset = df[['name', 'age']]
just_age = df['age']

# Filter
adults = df[df['age'] > 30]
starts_with_a = df[df['name'].str.startswith('A')]

# Group by
grouped = df.groupby('name')['age'].mean()
grouped_sum = df.groupby('name').sum()

# Apply functions
doubled = df['age'] * 2
normalized = df['age'].apply(lambda x: x / 100)

# Merge/join
merged = pd.merge(df1, df2, on='key', how='inner')  # Inner, outer, left, right
joined = df1.join(df2, on='key')

# Handle missing values
no_nulls = df.dropna()  # Remove rows with any null
some_nulls = df.dropna(subset=['age'])  # Remove rows with null in specific column
filled = df.fillna(0)  # Fill with value
forward_fill = df.fillna(method='ffill')  # Forward fill

# Export
csv = df.to_csv(index=False)
json = df.to_json()
html = df.to_html()
```

---

## 🔥 PyTorch Essentials

### Tensors and Operations
```python
import torch
import torch.nn as nn
import torch.optim as optim

# Create tensors
x = torch.randn(3, 3)  # Random normal distribution
y = torch.tensor([[1.0], [2.0], [3.0]])  # Single value tensor
z = torch.zeros(2, 2)  # Zero tensor

# Operations with gradient tracking
x = torch.randn(2, 2, requires_grad=True)
y = x * 2
loss = y.sum()
loss.backward()  # Computes gradients
print(x.grad)  # Access gradient

# Tensor operations
out = x.matmul(x.T)  # Matrix multiplication
out = x + y  # Element-wise
out = torch.argmax(y, dim=0)  # Find index of max value

# Move to GPU
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
x = x.to(device)

# Reduce operations
sum = x.sum()
mean = x.mean()
max_val, max_idx = torch.max(x, dim=0)
```

### Neural Networks
```python
# Define a model
class MyModel(nn.Module):
    def __init__(self):
        super().__init__()
        self.fc1 = nn.Linear(784, 256)
        self.relu = nn.ReLU()
        self.fc2 = nn.Linear(256, 10)
    
    def forward(self, x):
        x = x.view(-1, 784)  # Flatten
        x = self.fc1(x)
        x = self.relu(x)
        x = self.fc2(x)
        return x

# Training loop
model = MyModel().to(device)
criterion = nn.CrossEntropyLoss()
optimizer = optim.Adam(model.parameters(), lr=0.001)

for epoch in range(100):
    # Forward pass
    predictions = model(inputs)
    loss = criterion(predictions, labels)
    
    # Backward pass
    optimizer.zero_grad()  # Clear gradients
    loss.backward()
    optimizer.step()  # Update weights
    
    print(f"Epoch {epoch}: Loss = {loss.item()}")
```

### Common Layers
```python
# Linear layer (dense)
nn.Linear(in_features, out_features)

# Activation functions
nn.ReLU()
nn.Sigmoid()
nn.Tanh()
nn.GELU()  # Good for transformers

# Pooling
nn.MaxPool2d(kernel_size=2, stride=2)
nn.AvgPool2d(kernel_size=2)

# Convolution
nn.Conv2d(in_channels, out_channels, kernel_size, stride=1, padding=0)

# Fully connected 3D (for video)
nn.Linear(27000, 100)  # Example: 30*30*3 for RGB frames

# Embedding (for NLP)
nn.Embedding(num_embeddings, embedding_dim, padding_idx=0)
```

---

## 🎯 Scikit-learn Quick Reference

### Model Training
```python
from sklearn.linear_model import LinearRegression, LogisticRegression
from sklearn.ensemble import RandomForestClassifier, GradientBoostingClassifier
from sklearn.svm import SVC
from sklearn.preprocessing import StandardScaler

# Train-Test Split
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Standardize features (IMPORTANT for distance-based models!)
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)  # Use same scaler

# Train model
model = RandomForestClassifier(n_estimators=100, random_state=42)
model.fit(X_train_scaled, y_train)

# Predict
predictions = model.predict(X_test_scaled)

# Evaluate
from sklearn.metrics import accuracy_score, precision_recall_fscore_support
accuracy = accuracy_score(y_test, predictions)
precision, recall, f1, _ = precision_recall_fscore_support(y_test, predictions)
```

### Common Preprocessors
```python
from sklearn.preprocessing import StandardScaler, OneHotEncoder
from sklearn.compose import ColumnTransformer

# For categorical variables
encoder = OneHotEncoder()
encoded = encoder.fit_transform(categorical_data)

# Pipeline with preprocessing and model
preprocessor = ColumnTransformer(
    transformers=[
        ('num', StandardScaler(), ['num_feat_1', 'num_feat_2']),
        ('cat', OneHotEncoder(), ['cat_feat_1', 'cat_feat_2'])
    ])

pipeline = Pipeline([
    ('preprocessor', preprocessor),
    ('classifier', LogisticRegression())
])

pipeline.fit(X, y)  # Auto-applies preprocessing and training
predictions = pipeline.predict(X_test)
```

### Cross-Validation
```python
from sklearn.model_selection import cross_val_score, GridSearchCV

# Simple cross-validation
scores = cross_val_score(model, X, y, cv=5, scoring='accuracy')
print(f"Mean accuracy: {scores.mean()}")
print(f"Std: {scores.std()}")

# Grid search for hyperparameters
param_grid = {
    'n_estimators': [50, 100, 200],
    'max_depth': [None, 10, 20, 30]
}

grid_search = GridSearchCV(RandomForestClassifier(), param_grid, cv=5)
grid_search.fit(X_train_scaled, y_train)

print(f"Best params: {grid_search.best_params_}")
best_model = grid_search.best_estimator_
```

---

## 🤖 Transformers & Hugging Face

### Basic Pipeline
```python
from transformers import pipeline, AutoModel, AutoTokenizer

# Quick NLP pipeline
classifier = pipeline("sentiment-analysis")
result = classifier("I love using PyTorch!")
print(result)  # [{'label': 'POSITIVE', 'score': 0.999}]

# LLM for text generation
llm = pipeline("text2text-generation", model="google/flan-t5-xl")
output = llm("Translate 'Hello World' to French:")
print(output[0]['generated_text'])

# Load model and tokenizer
model = AutoModel.from_pretrained("bert-base-uncased")
tokenizer = AutoTokenizer.from_pretrained("bert-base-uncased")

# Tokenize
input_text = "Hello, how are you?"
inputs = tokenizer(input_text, return_tensors="pt", truncation=True, padding=True)

# Generate
outputs = model.generate(**inputs, max_length=50)
decoded = tokenizer.decode(outputs[0], skip_special_tokens=True)
print(decoded)
```

### RAG with LangChain
```python
from langchain.chains import RetrievalQA
from langchain.vectorstores import Chroma
from langchain.embeddings import HuggingFaceEmbeddings

# Create vector store from documents
from langchain.document_loaders import TextLoader
loader = TextLoader("./data/document.txt")
documents = loader.load()

# Create embeddings
embeddings = HuggingFaceEmbeddings(
    model_name="sentence-transformers/all-MiniLM-L6-v2"
)

vector_store = Chroma.from_documents(documents, embeddings, persist_directory="./chroma_db")

# Create retrieval chain
retriever = vector_store.as_retriever(search_type="similarity", search_kwargs={"k": 3})
qa_chain = RetrievalQA.from_chain_type(
    llm=llm,
    retriever=retriever,
    return_source_documents=True
)

# Query
answer = qa_chain({"query": "What is the main topic?"})
print(answer['result'])
print(answer['source_documents'])  # Show where answer came from
```

---

## 📊 Common ML Metrics

```python
from sklearn.metrics import confusion_matrix, classification_report, roc_auc_score

# Confusion Matrix
cm = confusion_matrix(y_true, y_pred)
# Interpret:
# - True Positives: cm[1, 1] (diagonal for class 1)
# - False Positives: cm[0, 1] (predicted 1, actual 0)
# - True Negatives: cm[0, 0]
# - False Negatives: cm[1, 0]

# Classification Report (detailed)
print(classification_report(y_true, y_pred))
# Shows: precision, recall, f1-score for each class

# ROC-AUC for binary classification
auc = roc_auc_score(y_true_binary, y_pred_proba[:, 1])
print(f"ROC-AUC: {auc}")  # 1.0 = perfect, 0.5 = random
```

---

## 🚀 Model Deployment (FastAPI)

```python
from fastapi import FastAPI
from pydantic import BaseModel
import joblib

app = FastAPI()
model = joblib.load("model.pkl")

class PredictionInput(BaseModel):
    features: list[float]  # or use a dict structure

@app.post("/predict")
def predict(input_data: PredictionInput):
    prediction = model.predict(input_data.features)
    probability = model.predict_proba(input_data.features)
    
    return {
        "prediction": int(prediction[0]),
        "probability": probability[0].tolist(),
        "metadata": {
            "model_version": "v1.0",
            "timestamp": "2024-01-01"
        }
    }

# Run with:
# uvicorn main:app --host 0.0.0.0 --port 8000
```

---

## 🐳 Docker Quick Commands

### Create Dockerfile
```dockerfile
FROM python:3.11-slim

WORKDIR /app

# Copy requirements and install
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy code
COPY . .

# Run application
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
```

### Build and Run
```bash
# Build
docker build -t my-ml-app .

# Run
docker run -p 8000:8000 --gpus all my-ml-app

# Interactive session
docker run -it --rm --gpus all my-ml-app bash

# View logs
docker logs <container_id>

# Stop
docker stop <container_id>

# Pull image
docker pull <image_name>
```

---

## 💡 Pro Tips

### Debugging PyTorch
```python
# Check tensor shapes
print(f"Shape: {tensor.shape}")

# Check gradients
if tensor.requires_grad:
    tensor.retain_grad()  # Keep gradients

# Manual grad check
out = torch.mm(x, w)
out.backward(torch.ones_like(out))
print(f"Grad norm: {w.grad.norm()}")

# Memory profiling
import torch.cuda as cuda
cuda.memory_allocated()
cuda.memory_reserved()
```

### Debugging Transformers
```python
from transformers import AutoModel

model = AutoModel.from_pretrained("model-name")

# Check parameter counts
print(f"Model params: {sum(p.numel() for p in model.parameters())}")

# Check device placement
for name, param in model.named_parameters():
    if param.requires_grad:
        print(f"{name}: device={param.device}")
```

---

## 📖 Further Reading

- **Math**: [Khan Academy Linear Algebra](https://www.khanacademy.org/math/linear-algebra), [3Blue1Brown](https://www.3blue1brown.com/)
- **ML Theory**: [Elements of Statistical Learning](https://hastie.swmed.edu/ElemStatLearn.pdf), [Pattern Recognition](https://web.stanford.edu/~hastie/ElemStatLearn/)
- **Practical ML**: [Hands-On ML](https://www.oreilly.com/library/view/hands-on-machine-learning/9781492032632/)
- **Production ML**: [Designing ML Systems](https://www.manning.com/books/designing-machine-learning-systems), [MLOps Zoomcamp](https://github.com/Quviqq/mlops_zoomcamp)
- **LLMs**: [The Annotated Transformer](https://nlp.seas.harvard.edu/2018/04/03/annotated-transformer.html), [Hugging Face Course](https://huggingface.co/learn)

---

**Keep practicing, keep building, keep failing, keep learning!** 🚀
