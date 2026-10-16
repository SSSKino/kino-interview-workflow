# Kino Interview Workflow

把多机位采访剪成逻辑完整的长片，再产出适合小红书、抖音的竖屏话题切片。

这是供支持本地 Skill 的 AI Agent 执行的工作流包。编辑需要已连接的 ChatCut Desktop；它不是独立运行的视频剪辑软件，也不是 GitHub Actions 自动剪辑服务。

## 能做什么

- 多机位按声音同步，统一使用选定的清晰主音轨。
- 长片保留开场、人物介绍、多个话题和结尾；删除口癖、重复和卡壳。
- 中英双语字幕、拼贴纸片风格的讲解动画、相关空镜。
- 在明确授权后，用已有克隆声音修正必要的对白或制作结尾旁白。
- 从已确认的长片按话题剪出 30–120 秒竖屏切片。
- 快闪人物介绍、按话题定制的总结与产品引导，以及最终项目归属检查。

## 使用

1. 安装并登录 ChatCut Desktop，为你的 Agent 连接 ChatCut 工具。功能和付费生成能力以当前账号为准。
2. 克隆本仓库：`gh repo clone SSSKino/kino-interview-workflow`。
3. 将 `skills/kino-interview-workflow/` 复制到你的 Agent 支持的技能目录。Codex 可使用 `~/.codex/skills/`；重启会话后检查技能是否被发现。其他宿主按其 Skill 安装方式操作。
4. 复制 `templates/job-brief.md` 填写新任务，素材保留在本机的私有任务目录。
5. 向 Agent 发出以下请求：

> 使用 $kino-interview-workflow。按这份任务说明处理我已导入的采访。先核对目标项目和主音轨，完成逻辑完整的长片粗剪；我确认后，再做双语字幕、动画和竖屏切片。

已完成长片时，可以直接说：

> 使用 $kino-interview-workflow，从已确认的最新长片按话题生成切片。沿用人物卡和动画风格；只处理任务说明里选定的片段，逐条核对内容闭环、字幕、声音和项目归属。

## 文件

- [SKILL.md](skills/kino-interview-workflow/SKILL.md)：Agent 入口与阶段流程。
- [剪辑与视觉规范](skills/kino-interview-workflow/references/editorial.md)：双机位、内容逻辑、竖屏和品牌结尾。
- [交付与修订](skills/kino-interview-workflow/references/delivery.md)：项目防误写、版本和验证。
- [任务说明](templates/job-brief.md)：每个新项目的输入。
- [交付清单模板](templates/delivery-manifest.example.json)：关联视频、项目、版本和审核结果。

## 执行边界

需要 Agent 的判断和可用工具，不能保证无人干预完成。缺少素材、转录、授权声音或项目连接时，报告具体阻塞，不虚构结果。使用 FFmpeg/FFprobe 或本地动画渲染器时检查当前环境；不把某次任务的机器路径、参数或内部 ID 当作通用配置。

此仓库只包含新编写的流程文档和模板，不包含采访素材、转录、声纹、生成音频、账户凭据、内网地址或第三方插件源代码。它受到 [cut-motion](https://github.com/Endless1936/cut-motion) 的工作流组织方式启发，可配合该项目使用，但并非其官方插件。没有附带第三方字体或素材授权。
