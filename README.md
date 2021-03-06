# my-driver-demo
# 用户管理——管理员

## 1、获取所有管理员信息

接口：/api/admins/search/all

请求方式：get

请求参数：无

返回数据：

状态码：200

```json
{
    admins:[{
        userId,
        username,
        creatTime,
        updataTime
    }]
}
```

## 2、通过用户名获取管理员信息

接口：/api/admins/search/:username

请求方式：get

请求参数：

```json
username
```

返回数据：

状态码：200

```json
{
    admin:{
        userId,
        username,
        creatTime,
        updataTime
    }
}
```

## 3、修改管理员信息

接口：/api/admins/update

请求方式：put

请求参数：

```json
{
    admin:{
        userId,
        username,
        password
    }
}
```

返回数据：

状态码：204

## 4、通过用户ID删除管理员信息

接口：/api/admins/delete/:userId

请求方式：delete

请求参数：

```json
userId
```

返回数据：

状态码：204

## 5、添加管理员信息

接口：/api/admins/add

请求方式：post

请求参数：

```json
{
    admin:{
        username,
        password
    }
}
```

返回数据：

状态码：204

## 6、管理员登陆

接口：/api/admins/login

请求方式：post

请求参数：

```json
{
    login:{
        username,
        password
    }
}
```

返回数据：

```json
{
    userType,
    token
}
```

状态码：200

## 7、获取已登陆管理员个人信息

接口：/api/admins/myself

请求方式：get

请求参数：无

返回数据：

状态码：200

```json
{
    admin:{
        userId,
        username,
        creatTime,
        updataTime
    }
}
```



# 用户管理——学员

## 1、获取所有学员信息

接口：/api/students/search/all

请求方式：get

请求参数：无

返回数据：

状态码：200

```json
{
    students:[{
        userId,
        username,
        courses:[{
            course,
            courseState
        }]
        creatTime,
        updataTime
    }]
}
```

## 2、通过用户名获取学员信息

接口：/api/students/search/:username

请求方式：get

请求参数：无

返回数据：

状态码：200

```json
{
    student:{
        userId,
        username,
        courses:[{
            course,
            courseState
        }]
        creatTime,
        updataTime
    }
}
```

## 3、添加学员信息

接口：/api/students/add

请求方式：post

请求参数：

```json
{
    student:{
        username,
        password,
        imageBase64
    }
}
```

返回数据：

状态码：204

## 4、通过用户ID删除学员信息

接口：/api/students/delete/:userId

请求方式：delete

请求参数：

```json
userId
```

返回数据：

状态码：204

## 5、修改学员信息

接口：/api/students/update

请求方式：put

请求参数：

```json
{
    student:{
        userId,
        username,
        password
    }
}
```

返回数据：

状态码：204

## 6、学员登陆

接口：/api/admins/login

请求方式：post

请求参数：

```json
{
    login:{
        username,
        password，
        imageBase64
    }
}
```

返回数据：

```json
{
    userType,
    token
}
```

状态码：200

## 7、获取已登陆学员的个人信息

接口：/api/students/myself

请求方式：get

请求参数：无

返回数据：

状态码：200

```json
{
    student:{
        userId,
        username,
        courses:[{
            course,
            courseState
        }]
        creatTime,
        updataTime
    }
}
```



# 考试管理

## 1、获取所有考试信息

接口：/api/examinations/search/all

请求方式：get

请求参数：无

返回数据：

状态码：200

```json
{
    examinations:[{
        examinationId,
        roomId
        roomName,
        courseId,
        courseName,
        startTime,
        reservationNum, //已预约人数
        maxNum	//最大可预约人数
    }]
}
```

## 2、获取学员能够预约的考试信息

接口：/api/examinations/search/student/:userId

请求方式：get

请求参数：

```json
userId
```

返回数据：

状态码：200

```json
{
    examinations:[{
        examinationId,
        roomId,
        roomName,
        courseId,
        courseName,
        startTime,
        reservationNum,
        maxNum
    }]
}
```

## 3、获取学员已预约/完成的考试信息

接口：/api/examinations/search/studentDo/:userId

请求方式：get

请求参数：userId

返回数据：

```js
{
    examinationDetail:[{
        examinationId,
        roomId,
       	roomName,
        courseId,
        courseName,
        startTime,
        examinationState //考试状态：未开始、正在考试、已结束
    }]
}
```

状态码：204

## 4、获取特定科目的考试信息

接口：/api/examinations/search/course/:courseId

请求方式：get

请求参数：

```
courseId 
```

返回数据：

状态码：200

```json
{
    examinations:[{
        examinationId,
        roomId,
        roomName,
        courseId,
        courseName,
        startTime,
        reservationNum,
        maxNum
    }]
}
```

## 5、获取特定时间段内的特定科目的考试信息

接口：/api/examinations/search/courseTime/:courseId/:startTime/:endTime

请求方式：get

请求参数：

```
courseId 
startTime //开始时间 由Date.parse()返回的毫秒数
endTime //结束时间 由Date.parse()返回的毫秒数
```

返回数据：

状态码：200

```json
{
    examinations:[{
        examinationId,
        roomId,
        roomName,
        courseId,
        courseName,
        startTime,
        reservationNum,
        maxNum
    }]
}
```

## 6、添加考试信息

接口：/api/examinations/add

请求方式：post

请求参数：

```
{
	examination:{
		roomId,
		courseId,
		startTime
	}
}
```

返回数据：

状态码：204

## 7、删除考试信息

接口：/api/examinations/delete/:examinationId

请求方式：delete

请求参数：

```
examinationId
```

返回数据：

状态码：204

## 8、修改考试信息

接口：/api/examinations/update

请求方式：put

请求参数：

```
{
	examination:{
		examinationId,
		roomId,
		courseId,
		startTime
	}
}
```

返回数据：

状态码：204

## 9、预约考试

接口：/api/examinations/reservation

请求方式：put

请求参数：

```json
{
    reservation:{
        userId,
        examinationId
    }
}
```

返回数据：

状态码：204

# 考场管理

## 1、获取所有考场信息

接口：/api/rooms/search/all

请求方式：get

请求参数：无

返回数据：

状态码：200

```json
{
    rooms:[{
        roomId,
        roomName,
        maxNum,
        creatTime,
        updateTime
    }]
}
```

## 2、通过考场ID获取考场信息

接口：/api/rooms/search/:roomId

请求方式：get

请求参数：

```
roomId
```

返回数据：

状态码：200

```json
{
    room:{
        roomId,
        roomName,
        maxNum,
        creatTime,
        updateTime
    }
}
```

## 3、通过考场ID获取考场状态信息

接口：/api/rooms/state/:roomId

请求方式：get

请求参数：

```
roomId
```

返回数据：

状态码：200

```json
{
    roomState:{
        reservationNum,
        examiningNum,
        maxNum
    }
}
```

## 4、添加考场信息

接口：/api/rooms/add

请求方式：post

请求参数：

```
{
	room:{
		roomName,
		maxNum
	}
}
```

返回数据：

状态码：204

## 5、删除考场信息

接口：/api/rooms/delete/:roomId

请求方式：delete

请求参数：

```
roomId
```

返回数据：

状态码：204

## 6、修改考场信息

接口：/api/rooms/update

请求方式：put

请求参数：

```
{
	room:{
		roomId,
		roomName,
		maxNum
	}
}
```

返回数据：

状态码：204

# 试题管理

## 1、获取所有选择题

接口：/api/questions/search/choice/all

请求方式：get

请求参数：无

返回数据：

状态码：200

```json
{
    choices:[{
        id,
        content,
        createTime,
        updateTime,
        options:[{
            key,		//选项的key 正确为1 错误为0
            content,	//选项的内容
            flag	//选项的对错标识符
        }]
    }]
}
```

## 2、获取所有判断题

接口：/api/questions/search/judge/all

请求方式：get

请求参数：无

返回数据：

状态码：200

```json
{
    judges:[{
        id,
        content,
        createTime,
        updateTime,
        options:[{
            key,
            content,
            flag
        }]
    }]
}
```

## 3、获取所有多选题

接口：/api/questions/search/multiple/all

请求方式：get

请求参数：无

返回数据：

状态码：200

```json
{
    multiples:[{
        id,
        content,
        createTime,
        updateTime,
        options:[{
            key,
            content,
            flag
        }]
    }]
}
```

## 4、添加选择题

接口：/api/questions/add/choice

请求方式：post

请求参数：

```json
{
    choice:{
        content,
        options:[{
            key,
            content,
            flag
        }]
    }
}
```

返回数据：

状态码：204

## 5、添加判断题

接口：/api/questions/add/judge

请求方式：post

请求参数：

```json
{
    judge:{
        content,
        options:[{
            key,
            content,
            flag
        }]
    }
}
```

返回数据：

状态码：204

## 6、添加多选题

接口：/api/questions/add/multiple

请求方式：post

请求参数：

```json
{
    multiple:{
        content,
        options:[{
            key,
            content,
            flag
        }]
    }
}
```

返回数据：

状态码：204

## 7、修改选择题

接口：/api/questions/update/choice

请求方式：put

请求参数：

```json
{
    choice:{
        id,
        content,
        options:[{
            key,
            content,
            flag
        }]
    }
}
```

返回数据：

状态码：204

## 8、修改判断题

接口：/api/questions/update/judge

请求方式：put

请求参数：

```json
{
    judge:{
        id,
        content,
        options:[{
            key,
            content,
            flag
        }]
    }
}
```

返回数据：

状态码：204

## 9、修改多选题

接口：/api/questions/update/multiple

请求方式：put

请求参数：

```json
{
    multiple:{
        id,
        content,
        options:[{
            key,
            content,
            flag
        }]
    }
}
```

返回数据：

状态码：204

## 10、删除选择题

接口：/api/questions/delete/choice/:questionId

请求方式：delete

请求参数：

```json
questionId
```

返回数据：

状态码：204

## 10、删除判断题

接口：/api/questions/delete/judge/:questionId

请求方式：delete

请求参数：

```json
questionId
```

返回数据：

状态码：204

## 10、删除多选题

接口：/api/questions/delete/multiple/:questionId

请求方式：delete

请求参数：

```json
questionId
```

返回数据：

状态码：204

## 11、通过用户ID和科目ID获取试卷

接口：/api/questions/search/paper/:userId/:courseId

请求方式：get

请求参数：

```json
userId
courseId
```

返回数据：

状态码：200

```json
{
    questions:{
        choices:[{
            id,
            content,
            options:[{
                key,
                content,
                flag  //正确为1 错误为0
            }],
            studentChoice:
        }],
        judges:[{
            id,
            content,
            options:[{
                key,
            	content,
                flag
            }],
            studentChoice:
        }],
        multiples:[{
            id,
            content,
            options:[{
                key,
                content,
                flag
            }],
            studentChoice:
        }]
    }
}
```

## 12、获取试卷

接口：/api/questions/paper/:examinationId

请求方式：get

请求参数：

```json
examinationId
```



返回数据：

状态码：200

```json
{
    questions:{
        choices:[{
            id,
            content,
            options:[{
                key,
                content,
                flag
            }]
        }],
        judges:[{
            id,
            content,
            options:[{
                key,
                content,
                flag
            }]
        }],
        multiples:[{
            id,
            content,
            options:[{
                key,
                content,
                flag
            }]
        }]
    }
}
```

## 12、提交答案

接口：/api/questions/submit

请求方式：post

请求参数：

```json
{
    submit:{
        userId,
        examinationId,
        answer:{
        	choice:[{
            	questionId,
            	optionChoice:	//学员所选选项，内容为选项的key值
        	}],
            judge:[{
            	questionId,
            	optionChoice:	//学员所选选项，内容为选项的key值
            }],
            multiple:[{
                questionId,
            	optionChoice:	//学员所选选项，内容为选项的key值
            }]
        }
    }
}
```

返回数据：

状态码：204

# 成绩管理

## 1、通过科目ID获取所有学员成绩

接口：/api/scores/search/:courseId

请求方式：get

请求参数：

```json
courseId
```

返回数据：

```json
{
    scores:[{
        userId,
        username,
        score,
        roomId,
        roomName,
        startTime
    }]
}
```

状态码：200

## 2、通过学员ID和科目ID获取学员成绩

接口：/api/scores/search/usercourse/:userId/:courseId

请求方式：get

请求参数：

```json
userId
courseId
```

返回数据：

```json
{
    score:{
        userId,
        username,
        score,
        scoreState,
        roomId,
        roomName,
        startTime
    }
}
```

状态码：200

## 3、通过科目ID和分数限制获取所有学员成绩

接口：/api/scores/search/courselimit/:userId/:courseId

请求方式：get

请求参数：

```json
courseId
largerThen	//大于某个分数
```

返回数据：

```json
{
    scores:[{
        userId,
        username,
        score,
        scoreState,
        roomId,
        roomName,
        startTime
    }]
}
```

状态码：200

## 4、修改学员成绩

接口：/api/scores/update

请求方式：put

请求参数：

```json
{
    score:{
        userId,
        courseId,
        score
    }
}
```

返回数据：

状态码：204

# 审核管理

## 1、提交注册信息

接口：/api/audits/register

请求方式：post

请求参数：

```json
{
    student:{
        username,
        password,
        imageBase64,
        identityNumber
    }
}
```

返回数据：

状态码：204

## 2、获取待审核列表

接口：/api/audits/list

请求方式：get

请求参数：无

返回数据：

状态码：200

```json
{
    students:[{
        username,
        password,
        imageBase64,
        identityNumber
    }]
}
```

## 3、拒绝通过

接口：/api/audits/reject/:username

请求方式：delete

请求参数：

```
username
```

返回数据：

状态码：200

## 4、查询审核状态

接口：/api/audits/status/:identityNumber

请求方式：get

请求参数：

```
identityNumber
```

返回数据：

状态码：200

```json
{
    status //0代表未注册或未通过，1代表待审核，2代表已通过
}
```

