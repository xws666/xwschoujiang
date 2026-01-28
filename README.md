# 小稳神抽奖应用

## 功能说明

1. **用户登录**：首次进入需要输入用户名
2. **抽奖系统**：每天5次抽奖机会
3. **奖品概率**：
   - 520元：0.00000001%
   - 100元：0.00001%
   - 50元：0.00001%（假设值，如需调整请修改代码）
   - 10元：0.0001%
   - 0.1元：0.1%
   - 0.01元：30%
   - 谢谢参与：剩余概率
4. **记录管理**：
   - 我的记录：显示当前用户的抽奖记录
   - 其他人的记录：显示所有用户的抽奖记录
5. **数据存储**：使用LeanCloud存储所有抽奖记录

## LeanCloud 配置步骤

### 1. 注册并创建应用

1. 访问 [LeanCloud官网](https://www.leancloud.cn/)
2. 注册账号并登录
3. 进入控制台，创建新应用
4. 记录下 **AppID** 和 **AppKey**

### 2. 创建数据表

在LeanCloud控制台中，需要创建一个名为 `DrawRecord` 的数据表，包含以下字段：

- `username` (String) - 用户名
- `prize` (String) - 奖品名称
- `drawDate` (String) - 抽奖日期（格式：YYYY-MM-DD）
- `drawTime` (Date) - 抽奖时间

### 3. 配置应用

打开 `index.html` 文件，找到以下代码：

```javascript
const APP_ID = 'YOUR_APP_ID';
const APP_KEY = 'YOUR_APP_KEY';
```

将 `YOUR_APP_ID` 和 `YOUR_APP_KEY` 替换为您在LeanCloud控制台中获取的实际值。

如果使用国际版LeanCloud，还需要设置 `serverURL`：

```javascript
AV.init({
  appId: APP_ID,
  appKey: APP_KEY,
  serverURL: 'https://YOUR_SERVER_URL' // 国际版需要此参数
});
```

### 4. 设置数据表权限

在LeanCloud控制台的 `DrawRecord` 数据表中：
- 设置 **写权限**：允许所有用户写入
- 设置 **读权限**：允许所有用户读取（用于查看所有记录）

## 使用说明

1. 打开 `index.html` 文件
2. 首次使用输入用户名
3. 点击"开始抽奖"按钮进行抽奖
4. 每天最多可抽奖5次
5. 在"我的记录"中查看自己的抽奖历史
6. 在"其他人的记录"中查看所有用户的抽奖记录

## 注意事项

- 请确保已正确配置LeanCloud的AppID和AppKey
- 数据表名称必须为 `DrawRecord`
- 建议在生产环境中设置适当的数据表权限
- 50元的概率设置为0.00001%（假设值），如需调整请修改代码中的 `PRIZES` 数组
