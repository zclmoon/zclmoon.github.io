---
layout: post
title:  "Does ChatGPT has common sense?"
date:   2023-04-07 13:54:55 +0800
categories: ChatGPT
---


# Ask ChatGPT this question

### Prompt: Does ChatGPT has common sense?

### Answer by ChatGPT
As an AI language model, ChatGPT is capable of learning patterns and relationships between words and phrases from the vast amount of text data it has been trained on. However, whether it has common sense or not depends on how we define and measure "common sense". 

In general, "common sense" refers to the ability to make judgments and decisions based on our understanding of the world and our experiences. While ChatGPT can generate text that appears to be coherent and logical, it may not have the same level of understanding and awareness of the world that humans possess. It lacks the capability to experience and interact with the world in the same way that humans do, which is an important aspect of developing common sense.

Therefore, while ChatGPT can provide useful information and insights, it may not always have the same level of common sense as a human being.


# But it does surprised me for it's Comprehension & common sense

### Prompt
有2个数据库表: student (id, name, grade); student_score(student_id, course, score); 写mysql SQL，查询每个年级总分最高的学生

### Anwser by ChatGPT

可以使用INNER JOIN将两个表连接在一起，并使用GROUP BY和SUM函数计算每个学生的总分。然后，可以使用子查询和MAX函数找到每个年级的最高总分，最后使用INNER JOIN将这些最高总分和学生表连接起来，找到每个年级总分最高的学生。以下是示例代码：

```
SELECT s.id, s.name, s.grade, SUM(sc.score) AS total_score
FROM student s
INNER JOIN student_score sc ON s.id = sc.student_id
GROUP BY s.id, s.grade
HAVING SUM(sc.score) = (
  SELECT MAX(total_score)
  FROM (
    SELECT s1.grade, SUM(sc1.score) AS total_score
    FROM student s1
    INNER JOIN student_score sc1 ON s1.id = sc1.student_id
    GROUP BY s1.id, s1.grade
  ) t
  WHERE t.grade = s.grade
)
```

这个SQL语句首先将两个表student和student_score连接起来，并使用GROUP BY计算每个学生的总分。然后，使用子查询找到每个年级的最高总分，并将这些最高总分和学生表连接起来，找到每个年级总分最高的学生。最后，使用HAVING子句过滤出总分最高的学生。