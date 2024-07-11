**创建Python名为（venv）的虚拟环境**：

```
python -m venv venv
```

**激活虚拟环境**：

- Windows:

  ```
  .\venv\Scripts\activate
  ```

- Linux/MacOS:

  ```
  source venv/bin/activate
  ```

**安装依赖库**：

- 如果你有 `requirements.txt`文件，可以直接安装：

  ```
  pip install -r requirements.txt
  ```
  
- 或者手动安装需要的库：

  ```
  pip install requests
  ```

**生成 `requirements.txt` 文件**（如果还没有）：

```
pip freeze > requirements.txt
```