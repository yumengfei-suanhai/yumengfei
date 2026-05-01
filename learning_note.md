# 预培训第 2 周学习笔记

## 一、Git 命令解析（主要功能 + 示例）
| 命令 | 主要功能 | 示例 |
|------|----------|------|
| `git clone` | 将远程仓库完整克隆到本地电脑 | `git clone git@github.com:suanhaitech-undergrad/training-2026.git` |
| `git checkout` | 切换/创建分支 | 1. 切换分支：`git checkout develop`<br>2. 创建并切换分支：`git checkout -b develop` |
| `git branch` | 查看本地所有分支（当前分支前带 `*` 标记） | 示例输出：<br>`* develop`<br>`  main` |
| `git pull` | 拉取远程仓库对应分支的最新代码到本地（保证代码同步） | `git pull origin develop` |
| `git add` | 将修改后的文件添加到 Git 暂存区（为提交做准备） | `git add .` |
| `git commit` | 将暂存区的修改提交到本地仓库（生成版本记录） | `git commit -m "week_2/yumengfei/learning_note.md"` |
| `git push` | 将本地提交推送到远程 GitHub 仓库 | `git push origin develop` |
| `mkdir -p` | 递归创建指定层级的文件夹（不存在则创建） | `mkdir -p weekly_outputs/week_2/yumengfei` |
| `touch` | 创建空文件 | `touch weekly_outputs/week_2/yumengfei/learning_note.md` |

---

## 二、学习收获与问题
### 收获
1. 学会使用 SSH 方式克隆仓库。
2. 掌握 Git 从克隆 → 切换分支 → 添加 → 提交 → 推送的完整流程。
3. 学会按指定目录结构创建文件夹和文件。
4. 理解 Git 分支的作用，能在 develop 分支上完成任务。

### 遇到的问题与解决
- 问题：执行 `git clone git@github.com:suanhaitech-undergrad/training-2026.git` 出现 `Could not read from remote repository` 错误。
- 解决：加速器暂停加速。
- 问题：执行 `git push origin develop` 出现 `Write access to repository not granted.` 错误。
- 解决：仓库权限设置有问题，联系学长学姐处理。

## 三、完整操作流程
```bash
# 1. 克隆远程仓库到本地
git clone git@github.com:suanhaitech-undergrad/training-2026.git

# 2. 进入仓库目录
cd training-2026

# 3. 切换到 develop 分支
git checkout develop

# 4. 拉取远程 develop 分支最新代码
git pull origin develop

# 5. 创建个人目录
mkdir -p weekly_outputs/week_2/yumengfei

# 6. 创建学习笔记文件
touch weekly_outputs/week_2/yumengfei/learning_note.md

# 7. 添加所有修改到暂存区
git add .

# 8. 提交到本地仓库
git commit -m "week_2/yumengfei/learning_note.md"

# 9. 推送到远程 develop 分支
git push origin develop