# Analyzing the mental health of international students in Japan

Does going to university in a different country affect your mental health? A Japanese international university surveyed its students in 2018 and published a study the following year that was approved by several ethical and regulatory boards.

The study found that international students have a higher risk of mental health difficulties than the general population and that social connectedness (belonging to a social group) and acculturative stress (stress associated with joining a new culture) are predictive of depression.

This activity is for testing the results if staying longer period as an international student will affect mental health or not!

Data consists of the below fields. 

| Field Name    | Description                                      |
| ------------- | ------------------------------------------------ |
| `inter_dom`     | Types of students (international or domestic)   |
| `japanese_cate` | Japanese language proficiency                    |
| `english_cate`  | English language proficiency                     |
| `academic`      | Current academic level (undergraduate or graduate) |
| `age`           | Current age of student                           |
| `stay`          | Current length of stay in years                  |
| `todep`         | Total score of depression (PHQ-9 test)           |
| `tosc`          | Total score of social connectedness (SCS test)   |
| `toas`          | Total score of acculturative stress (ASISS test) |

### Analysis in SQL 

```sql
-- Run the code to view fields -- 
SELECT * 
FROM 'students.csv';
```
### Analyzing if the length of the stay impacts on the average mental health of international students.


```sql
SELECT 
	stay,
	COUNT(*) as count_int , 
	ROUND(AVG(todep),2) as average_phq, 
	ROUND(AVG(tosc),2) as average_scs,
	ROUND(AVG(toas),2) as average_as
FROM students
WHERE inter_dom = 'Inter'
GROUP BY 
	stay
ORDER BY 
	stay DESC;
```

[Data Camp project link](https://app.datacamp.com/workspace/w/a9a62112-27d1-4325-9c36-78d4408aebef/edit)
