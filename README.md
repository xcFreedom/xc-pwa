## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/xcFreedom/xiaocheng.github.io/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/xcFreedom/xiaocheng.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.


# Aurora 小工具介绍

# Setup
Step0. create env
如果你的电脑上已经存在了比较复杂的python依赖，可能会导致 Step1. 安装失败，建议创建一个干净的虚拟环境，安装aurora.
```
conda create --name aurora_env python=3.10
conda activate aurora_env
```

Step1. Install Aurora Package
```
git clone <repo> && cd <repo>
pip3 install ./
```

Step 2. In ~/.bashrc or ~/.zshrc, add

```
export AURORA_BASE=/home/bytedance/data/Aurora
```
这个路径将是aurora本地存放数据路径，可以修改这个路径至任意其它本地路径。

## 1. 日志
```
»aurora log -f 01-12 -f抖超 -f '!local' -f '|7RTPB1EB0233600021' -f '|7RTPB1EB0233600011' -p -w -n10
```
-f 表示filter, 可以筛选需要的日志，支持 and，or, not\
  具体的，"-f 01-12 -f 抖超" 表示结果必须包含01-12当日且在抖超仓库抓取的日志（and）,\
  "-f !local" 表示结果不能包含本地已经下载过的日志（not）,\
  "-f |7RTPB1EB0233600021 -f |7RTPB1EB0233600011" 表示结果需要包含7RTPB1EB0233600021或者7RTPB1EB0233600011\

-p 表示pull, 会自动下载日志到本地\
-w 表示wait, 如果日志还未抓取完成，会死等\
-n 表示显示10条结果\

## 2. debug
```
» aurora debug 7322733733499930668
0: all
1: localization_log_20240116_095205.rec
2: localization_log_20240116_102202.rec
```
传入日志id， 如果本地没有，则自动下载（下载前会询问），然后读取相关文件夹下的文件，人工选择需要跑的debug日志即可。\

## 3. snapshot
```
» aurora snapshot 7322733733499930668
>>>STEP 1: Avaliable Executable Version
0. relocalization_bugfix  2024-01-17_10-40-37
Choose an test_load_snapshot version: 0
>>>STEP 2: Download Log
Already exist, /media/buenos/seagate/Aurora/logs/raw_data/233500001_all_S_101600_104600_1705373194
>>>STEP 3: Download Map
Already exist, 7304922127102494764_7306704318412032044_1704859423053509357
>>>STEP 4: Prepare Cmd File
2024-01-16_10-32-21;start;
2024-01-16_10-32-21;load_snapshot;/media/buenos/seagate/Aurora/maps/raw_data/7304922127102494764_7306704318412032044_1704859423053509357
2024-01-16_10-39-00;end;
Do you want to edit cmd.txt? [y/N]:
Error: invalid input
No change.
>>>STEP 5: Config Done. Run the cmd undermentioned.
         aurora snapshot 7322733733499930668 --version crash --play_speed 1 --run
```
自动下载日志（本地有就跳过），地图文件，配置文件（含在日志里），自动根据当前日志所处时间，\
生成一份简易版的cmd_file, 并询问是否需要修改，最后给出运行指令，拷贝运行即可

## 4. oncall
```
» aurora oncall BCT -n 2
description:    14:50 EVT02 原地持续旋转
type:           算法-感知
date:           2024-01-17T14:54:38
robot_sn:       7RTPB1EB0233600003
warehouse:      GS
primary:        ['zhouhao.999', 'lj']
oncall_tags:    ['误报']
log_url:
oncall_flow:    https://oncall.bytedance.net/chats/user/userCase?cross_oncall_flow_id=43969777
=+==+===+====+=====+======
description:    15：31 9/11号机器人目标点并未被占用，却停在多机等待点长时间等待
type:           算法-多机
date:           2024-01-17T15:34:32
robot_sn:       7RTPB3HA0230100002 7RTPB3HA0230100004
warehouse:      GS
primary:        ['wangyansheng', 'zhouhao.999']
oncall_tags:    []
log_url:
oncall_flow:    https://oncall.bytedance.net/chats/user/userCase?cross_oncall_flow_id=43974302
=+==+===+====+=====+======
Total: 2
```
查询当前平台的oncall记录，点击链接可以跳转 也支持-f指令，具体使用方法参考log，\
同样如果oncall的描述里含有日志id, 使用-p指令可以直接批量下载

## 5. robot
```
 » aurora robot  -n 2
name:   BCT-P60L-EVT2-02
sn:     7RTPB1EB0233600011
build:  GREAT_BYD
ip:     10.33.212.152 / 10.8.0.238 / 0.0.0.0
=+==+===+====+=====+======
name:   BCT-P60L-EVT2-01
sn:     7RTPB1EB0233600015
build:  GREAT_BYD
ip:     10.31.250.84 / 10.8.0.78 / 0.0.0.0
=+==+===+====+=====+======
Total: 2
```
查询机器人的相关信息 也支持-f指令，具体使用方法参考log

## 6. map
snapshot可以自动化下载日志，此功能不太需要了

## 7. history
```
aurora history
```
显示之前的查询结果，这是个测试功能

## 8. test case
```
aurora test_case create {log_id}
```
上述命令将用log_id以及其对应的cmd file创建一个slam benchmark test case。请保证该日志数据已经在本地再运行该命令。

```
aurora test_case download {test_case_name}
```
上述命令将下载test_case_name的测试数据。如果对应的日志本地还为下载，会先下载日志，并用test case中的cmd文件覆盖对应日志的cmd文件。


# Usage
```
aurora --help
```

# TODO
2.log time order
