# API-Design
## 第一次設計
## /user-account
### 個人帳戶資訊 
#### 單查
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
| data | Optional<Object> | 回傳資料 |  |    |
| userId | String | 使用者Google帳號 |  |    |
| userName | String | 使用者名稱 |  |    |
| userSex | String | 性別(男/女) |  | 後端需判斷 0:男/1:女 |
| department | String | 所屬科系/班級 |  |    |
| role | String | 角色/權限 |  | 對應codelist表role的desc |
| creatTime | String | DATETIME |  |    |

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

#### 修改個人資訊
說明：

| General | 說明 | 
| --------------- | --- |
| Request Method  | PATCH |
| Request URL     | http://localhost:8080/user-account/profile |

| Headers | 說明 | 
| ------------- | ------------ |
| X-Auth-Token  | 登入者的token |

**JSON：**

| 參數名稱 | 參數型態 | 說明 | 範例 | 備註 |
| -------- | -------- | -------- | -------- | -------- |
| userId | String | 使用者Google帳號 | 10946011@ntub.edu.tw | 必填 |
| userSex | int | 性別(男:0/女:1) | 1 | 非必填 |
| department | String | 所屬科系/班級 | 資管系 | 非必填 |

**範例：**
```json=
{
    "userId":"10946011@ntub.edu.tw",
    "userSex":"1",
    "department":"資管系"
}
```

**回傳：**

| 參數名稱 | 參數型態 | 說明 | 範例 | 備註 | 
| ------ | ------- | --------- | ---- | --- |
| result | Boolean | API執行狀態 | true |    |
| errorCode | String | API執行異常代碼 | "" |    |
| message | String | API執行狀態說明 | "修改成功" |    |
| data | Optional<Object> |  |  |    |

**範例：**
```json=
{
    "result": true,
    "errorCode": "",
    "message": "修改成功",
    "data": {}
}
```

---

### 人員管理 
#### 全查
說明：查詢全部使用者帳號

| General | 說明 | 
| --------------- | --- |
| Request Method  | GET |
| Request URL     | http://localhost:8080/user-account?page= |

| Headers | 說明 | 
| ------------- | ------------ |
| X-Auth-Token  | 登入者的token |

**Params**

| 參數名稱 | 參數型態 | 說明 | 範例 | 備註 |
| -------- | -------- | -------- | -------- | -------- |
| page     | INT     | 頁碼     | 1     | 後端會設定一頁查詢幾筆     |

**回傳**

| 參數名稱 | 參數型態 | 說明 | 範例 | 備註 |
| -------- | -------- | -------- | -------- | -------- |
| result     | Boolean | API執行狀態 | true |      |
| errorCode     | String | API執行異常代碼 | "" |      |
| message     | String | API執行狀態說明 | 查詢成功 |      |
| data    | List<Object> | 回傳資料 |      |      |
| userId  | String | 使用者Google帳號 |      |      |
| userName | String | 使用者名稱 |    |      |
| userSex | String | 性別(男/女) |    |  後端需判斷 0:男/1:女    |
| department | String     | 所屬科系/班級 |     |      |
| role | String | 角色/權限 |      |  對應codelist表role的desc    |
| available | Boolean | 啟用狀態(啟用:1/不啟用:0) |      |      |

**範例：**
```json=
{
    "result": true,
    "errorCode": "",
    "message": "查詢成功",
    "data": [
     {
            "userId": "10946038@ntub.edu.tw",
            "userName": "李冠賢",
            "userSex": "男",
            "department": null,
            "role": "學生",
            "available": true
        },
     {
            "userId": "10946012@ntub.edu.tw",
            "userName": "李姍珊",
            "userSex": "女",
            "department": "四技資管三甲",
            "role": "學生",
            "available": true
        },
 {
            "userId": "10946008@ntub.edu.tw",
            "userName": "楊玉珊",
            "userSex": "女",
            "department": "四技資管三甲",
            "role": "學生",
            "available": true
        }
    ]
}
```

---

#### 單查
說明：查詢單一使用者帳號

| General | 說明 | 
| --------------- | --- |
| Request Method  | GET |
| Request URL     | http://localhost:8080/user-account/{{Id}}  |

| Headers | 說明 | 
| ------------- | ------------ |
| X-Auth-Token  | 登入者的token |
    
**Params**

| 參數名稱 | 參數型態 | 說明 | 範例 | 備註 |
| -------- | -------- | -------- | -------- | -------- |
| id     | String     | 使用者Google帳號     | 10946008@ntub.edu.tw |      |

**回傳**

| 參數名稱 | 參數型態 | 說明 | 範例 | 備註 |
| -------- | -------- | -------- | -------- | -------- |
| result     | Boolean | API執行狀態 | true |      |
| errorCode     | String | API執行異常代碼 | "" |      |
| message     | String | API執行狀態說明 | 查詢成功 |      |
| data    | Optional < Object > | 回傳資料 |      |      |
| userId  | String | 使用者Google帳號 |      |  |
| userName | String | 使用者名稱 |    |  |
| userSex | String | 性別(男/女) |    |  |
| department | String     | 所屬科系/班級 |     |  |
| role | String | 角色/權限 |      |      |
| available | Boolean | 啟用狀態(啟用:1/不啟用:0) |      |      |

**範例：**
```json=
{
    "result": true,
    "errorCode": "",
    "message": "查詢成功",
    "data": {
        "userId": "10946011@ntub.edu.tw",
        "userName": "周珮宣",
        "userSex": "女",
        "department": "四技資管三甲",
        "role": "學生",
        "available": true
    }
}
```

---

#### 總頁數查詢
說明：查詢人員管理總頁數

| General | 說明 | 
| --------------- | --- |
| Request Method  | GET |
| Request URL     | http://localhost:8080/user-account/count |

| Headers | 說明 | 
| ------------- | ------------ |
| X-Auth-Token  | 登入者的token |

**回傳**

| 參數名稱 | 參數型態 | 說明 | 範例 | 備註 |
| -------- | -------- | -------- | -------- | -------- |
| result     | Boolean | API執行狀態 | true |      |
| errorCode     | String | API執行異常代碼 | "" |      |
| message     | String | API執行狀態說明 | 查詢成功 |      |
| data    | Optional < Object > | 回傳資料 |      |      |
| totalPage  | INT | 總頁數 |      |   |

**範例：**
```json=
{
    "result": true,
    "errorCode": "",
    "message": "查詢成功",
    "data": {
        "totalPage": 1
    }
}
```

---