# 轻松玩转书生·浦语大模型趣味 Demo

## InternLM2-Chat-7B 智能对话 Demo
1. 创建开发机、搭建环境
```
studio-conda -o internlm-base -t demo
# 与 studio-conda 等效的配置方案
# conda create -n demo python==3.10 -y
# conda activate demo
# conda install pytorch==2.0.1 torchvision==0.15.2 torchaudio==2.0.2 pytorch-cuda=11.7 -c pytorch -c nvidia
```
2. 下载 InternLM2-Chat-1.8B 模型  
在`/root/demo/download_mini.py `文件写入
```
import os
from modelscope.hub.snapshot_download import snapshot_download

# 创建保存模型目录
os.system("mkdir /root/models")

# save_dir是模型保存到本地的目录
save_dir="/root/models"

snapshot_download("Shanghai_AI_Laboratory/internlm2-chat-1_8b", 
                  cache_dir=save_dir, 
                  revision='v1.1.0')
```
并执行`python /root/demo/download_mini.py` 

3. 运行 cli_demo  
运行`python /root/demo/cli_demo.py`  
等待模型加载完成，键入内容示例：  
`请创作一个 300 字的小故事`  
效果如下：
![image](https://github.com/ZiyingHuang/InternLM/assets/140309330/87bee27f-8974-4ecd-8c71-52b802130840)

### 实战：部署实战营优秀作品 八戒-Chat-1.8B 模型
1. 配置及下载八戒模型
   使用 git 命令来获得仓库内的 Demo 文件：    
   `git clone https://gitee.com/InternLM/Tutorial -b camp2`
   
   下载运行 Chat-八戒 Demo  
   `python /root/Tutorial/helloworld/bajie_download.py`
   
2. 待程序下载完成后，输入运行命令：  
   `streamlit run /root/Tutorial/helloworld/bajie_chat.py --server.address 127.0.0.1 --server.port 6006`
   ![image](https://github.com/ZiyingHuang/InternLM/assets/140309330/9f5262e5-4d9b-4197-8127-adda77842a1e)

    用ssh进行本地连接，映射到web：  
    ```
    # 从本地使用 ssh 连接 studio 端口
    # 将下方端口号 38374 替换成自己的端口号
    ssh -CNg -L 6006:127.0.0.1:6006 root@ssh.intern-ai.org.cn -p 38374
    ```
   打开 `http://127.0.0.1:6006` 后，等待加载完成即可进行对话:    
   ![image](https://github.com/ZiyingHuang/InternLM/assets/140309330/6efb8ca8-1643-4511-a5e7-6ac76130ee18)

