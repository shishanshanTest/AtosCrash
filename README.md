### 符号表

---
- 符号表:就是指在Xcode项目编译后，在编译生成的二进制文件.app的同级目录下生成的同名的.dSYM文件。.dSYM文件其实是一个目录，在子目录中包含了一个16进制的保存函数地址映射信息的中转文件，所有Debug的symbols都在这个文件中(包括文件名、函数名、行号等)，所以也称之为调试符号信息文件。
- 作用:在Xcode开发调试App时，一旦遇到崩溃问题，开发者可以直接使用Xcode的调试器定位分析。
但如果App发布上线，开发者不可能进行调试，只能通过分析系统记录的崩溃日志来定位问题，在这份崩溃日志文件中，会指出App出错的函数内存地址，而这些函数地址是可以在.dSYM文件中找到具体的文件名、函数名和行号信息的，这正是符号表的重要作用所在，也是为什么要进行符号表进行管理，并纪录这是哪个版本的符号表。
---

### atos 命令行工具

---
- atos命令来符号化某个特定模块加载地址 atos [-arch 架构名] [-o 符号表] [-l 模块地址] [方法地址]
---

### 使用方法

---

- 1 git clone 此地址
- 2 终端输入: python3 atoscrash.py xxx.app.dYSM xxx.crash
- 3 会在当前的文件夹下生成一个 xxxresult.crash 的文件
```PYTHON
    # dsym_dir_path = sys.argv[1]  # .app.dSYM符号表的文件路径
    # crash_file_path = sys.argv[2]  # crash文件路径(可以是导出的 crash 文件路径,也可是待解析的原始堆栈)
    # arm_str = sys.argv[3]  # 架构名
```
---