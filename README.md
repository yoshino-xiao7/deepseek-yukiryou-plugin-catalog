# DeepSeek YukiRyou Plugin Catalog

这是 DeepSeek YukiRyou 的开发者实机验证插件目录。桌面应用会动态读取
[`catalog-v1.json`](./catalog-v1.json)，因此目录内容可以独立于应用版本更新。

目录中的条目仅表示：YukiRyou 在所标注的平台上安装并冒烟测试过该**精确版本**。
它不是代码审计、未来版本背书或绝对安全保证。安装前，桌面应用仍会执行 npm 身份、
仓库回链、生命周期脚本、SHA-512、平台约束、依赖图、Peer 兼容性和实际包体检查。

## 收录条件

- 必须是精确、稳定的 npm 版本，不能使用版本范围或 prerelease。
- 必须填写规范的 GitHub 仓库地址，且与 npm 包身份一致。
- 必须通过 DeepSeek YukiRyou 的受管安装流程并在真实设备上完成冒烟测试。
- `verification.platforms` 只能包含 `darwin-arm64` 和 `win32-x64`。
- 每次修改必须更新顶层 `revision`，并记录 UTC 格式的 `testedAt`。
- 不得提交凭据、安装命令、任意下载地址或未经测试的安全结论。

初始目录为空；只有完成真实安装验收后才会加入条目。

## Entry shape

```json
{
  "id": "plugin-id",
  "displayName": "Plugin name",
  "summary": "What was verified.",
  "repository": "https://github.com/owner/repository",
  "categories": ["agent"],
  "publisher": { "name": "publisher" },
  "package": { "name": "npm-package", "version": "1.2.3" },
  "verification": {
    "status": "installed",
    "testedAt": "2026-08-23T03:00:00.000Z",
    "harnessVersion": "0.1.1-rc.2",
    "platforms": ["darwin-arm64", "win32-x64"],
    "notes": "Managed install and product smoke test passed."
  }
}
```
