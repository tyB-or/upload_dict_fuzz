根据项目改动：https://github.com/c0ny1/upload-fuzz-dic-builder

上面项目是py2的，可以根据2to3的脚本去修改

改动是因为想轻量化字典，比如，如果过滤了大小写，其他不同位置的大小写就没有必要了。

写得去重脚本存在问题，放在这里仅作为纪念。

```
import os

dir_list = [i for i in os.listdir("./dic")]
print(dir_list)

for i in dir_list:
    file = "./dic" + "/" + i
    with open(file, "rb") as f:
        date = f.readlines()
        print(f"当前文件：{i}，存在{len(date)}个数据)")
        date = list(set(date))
        print(f"去重后，存在{len(date)}个数据)，已写入新文件。")
        # print(date)
        with open(i[:7] + '.txt', "wb") as p:
            p.writelines(date)
        

```

