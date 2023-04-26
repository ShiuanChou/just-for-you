# API-Design
## 第一次設計
### /user-account
#### 個人帳戶資訊 
##### 單查
說明：

| General | 說明 | 
| --------------- | --- |
| Request Method  | GET |
| Request URL     | http://localhost:8080/user-account/profile |

| Headers | 說明 | 
| ------------- | ------------ |
| X-Auth-Token  | 登入者的token |

**回傳：**

| 參數名稱 | 參數型態 | 說明 | 範例 | 備註 | 
| ------ | ------- | --------- | ---- | --- |
| result | Boolean | API執行狀態 | true |    |
| errorCode | String | API執行異常代碼 | "" |    |
| message | String | API執行狀態說明 | "查詢成功" |    |
| data | Optional<Object> | 回傳資料 |   |    |
| userId | String | 使用者Google帳號 |   |    |
| userName | String | 使用者名稱 |   |    |
| userSex | String | 性別(男/女) |   | 後端需判斷 0:男/1:女 |
| department | String | 所屬科系/班級 |   |    |
| role | String | 角色/權限 |   | 對應codelist表role的desc |
| creatTime | String | DATETIME |    |     |

**範例：**
```json=
{
    "result": true,
    "errorCode": "",
    "message": "查詢成功",
    "data": {
        "userId": "10946012@ntub.edu.tw",
        "userName": "李O珊",
        "userSex": "女",
        "department": "",
        "role": "學生",
        "creatTime": "2023-04-19 03:40:20"
    }
}
```

---
