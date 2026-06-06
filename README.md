# CPC Finder Lite (Static)

静态多页面版本，包含 5 个页面：

- `首页`：查询 + 学校排行
- `选手`：按姓名筛选记录
- `学校`：学校维度汇总排行
- `比赛`：比赛维度汇总统计
- `比赛详情`：单场比赛选手排名明细

## 目录结构

```text
.
|- .github/workflows/deploy.yml
|- data/results.json
|- data/school_teams.json
|- index.html
|- players.html
|- schools.html
|- contests.html
|- contest-detail.html
|- site.js
|- styles.css
```

## 本地运行

方式 1（推荐）：

1. 用 VS Code 安装 `Live Server`
2. 右键 `index.html`
3. 点击 `Open with Live Server`

方式 2（命令行）：

```powershell
npx serve .
```

然后打开终端输出的本地地址（如 `http://localhost:3000`）。

注意：不要直接用 `file://` 打开页面，否则浏览器可能拦截 `fetch` 读取 `data/results.json`。

## 数据格式

编辑 `data/results.json`，每条记录示例：

```json
{
  "id": "r1",
  "name": "张三",
  "school": "某某学校",
  "contest": "2025 某某比赛",
  "year": 2025,
  "rank": 1,
  "award": "一等奖"
}
```

学校页面还会读取 `data/school_teams.json`（团体排名数据）：

```json
{
  "school": "某某学校",
  "teamFirst": 2,
  "teamSecond": 1,
  "teamThird": 0
}
```

## 部署到 GitHub Pages

1. 推送代码到仓库 `main` 分支
2. 在仓库 `Settings -> Pages` 里把 Source 设为 `GitHub Actions`
3. 等待 Action 执行完成后访问 Pages 链接
