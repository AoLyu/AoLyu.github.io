## springboot前端传参LocalDate等类型

如果是Post请求，是RequestBody 里的属性

在实体类对应字段上，添加注解：@JsonFormat

如：

```java
@JsonFormat(shape = JsonFormat.Shape.STRING, pattern = "yyyy-MM-dd HH:mm:ss")
private LocalDateTime updateTime;
```

如果是Get请求，

localdate 添加注解 : @DateTimeFormat

如：

```java
public TableDataInfo listByDate(@DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate startDate)
```

controller接收参数为LocalDateTime

添加注解：

```java
@DateTimeFormat(pattern = "yyyy-MM-dd HH:mm:ss")
```

