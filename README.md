# 时空体质 · 五运六气与八字节气分析网页

这是一个可部署的静态网页原型，支持输入出生日期时间、性别、出生地经度/时区等信息，返回八字、节气、真太阳时、起运岁数、五运六气、十神、藏干、旺衰、格局、用神忌神与体质/疾病易感性研究性提示。

> 重要声明：本项目仅用于传统文化/中医运气理论研究与学习，不构成医学诊断、治疗建议或命理断语。

## 本地运行

```bash
python3 -m http.server 8765
# 浏览器打开 http://127.0.0.1:8765
```

## GitHub Pages 部署

1. 新建 GitHub 仓库，例如 `spacetime-yunqi-web`。
2. 将本目录内容推送到仓库 `main` 分支。
3. 在 GitHub 仓库 Settings → Pages 中选择 GitHub Actions。
4. Actions 自动完成后访问：

```text
https://<你的GitHub用户名>.github.io/spacetime-yunqi-web/
```

## Netlify 部署

- Build command 留空或填 `echo static`
- Publish directory 填 `.`

## Vercel 部署

- Framework Preset 选择 Other
- Output Directory 填 `.`

## 后续接入权威万年历接口建议

当前前端含天文近似算法。若做正式版，建议后端接入权威历算库/API，例如：

- `sxtwl`/寿星天文历算法作后端历算；
- 商业万年历 API；
- 自建节气时刻表数据库；
- 城市经纬度/时区 API；
- 历史气象 API。

接口建议：

```http
POST /api/calculate
Content-Type: application/json

{
  "birthDatetime": "1990-03-21T08:30:00",
  "gender": "male",
  "longitude": 116.4074,
  "timezone": 8
}
```

返回：四柱、节气、真太阳时、起运、五运六气、十神、藏干、旺衰、格局、用神忌神等。
