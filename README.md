# BasicProg_DataViz65
รวบรวมงานวิชา SC663401 : Basic Programmimg for Data Science and Data Visualization ของ ณัฐนิช หิรัญชวโรจน์ ID6330205528

# Grading
![gradind image](Grading.jpg)

# สมาชิกในกลุ่ม
## กลุ่ม Midterm ชื่อ หวัดดีเบล
1. นายนราวิชญ์ ประทานทรัพย์ 633020445-9
2. นางสาวภรณกนก ภูผาธรรม 633020446-7
3. นางสาวณัฐนิช หิรัญชวโรจน์ 633020552-8

## กลุ่ม Project ชื่อ หยกนัทหยกนัทหยกนัทหยก
1. นางสาวภรณกนก ภูผาธรรม 633020446-7
2. นางสาวณัฐนิช หิรัญชวโรจน์ 633020552-8

## กลุ่ม Final ชื่อ หมีเรื่องแล้ว
1. นายธนภัทร โสภณ 633020444-1
2. นางสาวณัฐนิช หิรัญชวโรจน์ 633020552-8
3. นายเฉลิมเกียรติ คำชะนาม 633021013-3

# Chapter1:[Functions, print, Loop, if ](https://github.com/natthanich/BasicProg_DataViz65/blob/main/Basic_Programming_Concepts.ipynb)
## Functions ($f(x) = y$)
def function_name(input_x):
    # do something with input_x to get output_y
    return output_y
    
function มีส่วนสำคัญทั้งหมด 4 ส่วน
1. บอก python ว่าเราจะเขียนฟังก์ชั่น ชื่ออะไร  `def function_name()`: (ขาดไม่ได้)
2. กำหนดตัวแปรที่จะเป็น input  _Input_ (ขาดได้)
3. ส่วนประมวลผล do_something with _Input_ to get _Output_ (ขาดไม่ได้)
4. ส่วน output `return` _Output_(ขาดได้)

ex. :upside_down_face:
```javascript
defi function_f1(x): 
    a = x**2  
    y = a + 75  
    return y; 
```

## `print` 
ตัวอย่าง function `print` https://www.programiz.com/python-programming/methods/built-in/print
![image](https://user-images.githubusercontent.com/108257658/235455255-9d027260-771c-4d49-a89d-c999f21fdfb5.png)

print()  ใส่ input ได้หลายตัว
-   ** คือ จำเป็นต้องใส่
- = คือ ไม่จำเป็นต้องใส่ มีค่าตั้งต้นมาให้
- end คือ จบบรรทัด  \n คือด้วยการขึ้นบรรทัดใหม่
- sep คือ เว้นวรรคค่าด้วย ' ' คือ ช่องว่าง

## Looping (for)
สำหรับทำงายเยอะๆ ซ้ำๆ
```python
for member in listEx:       ## วนที่สมาชิก ใน list
    do_something()
```
for ชื่อตัวแปร in list ที่จะเอามาใช้เป็นสมาชิกใน ตัวแปร:     
    
วนซ้ำ
- วนซ้ำสมาชิกใน 
### ใช้ for loop เพิ่มสมาชิกใน list  
```
list_name = [] #นิยมสร้าง list เปล่าๆก่อน
list_id = []
list_grade = []
for each in list_name_id_grade:
    list_name.append(each[0])
    list_id.append(each[1])
    list_grade.append(each[2])
```
#### Loop ซ้อน Loop (nested loop)
```
#แม่สูตรคูณ
for mem1 in range(2,5): #แม่[2,3,4]
    print(f'now mem1 = {mem1}')
    for mem2 in range(1,13): #[1,2,3,4,5,6,7,8,9,10,11,12]ตัวมาคูณ
        print(f'{mem1} x {mem2} = {mem1*mem2}')
    print(f'end inner for mem1 = {mem1}') #จบในลูป
```
#### Loop in Function
```
def print_grade_loop(names,grades): # names,grades มีหลายสมาชิก เป็นlist
    for n,g in zip(names,grades): # The zip() function returns a zip object, which is an iterator of tuples where the first item in each passed iterator is paired together, and then the second item in each passed iterator are paired together etc.
        print(f'{n} ได้เกรด {g}')  #  zip การจับคู่ ของเเต่ละ list ในตำแหน่เดียวกัน // จับ 2 list มาร่วมกัน
```
## Conditional Statement (if)
```
if condition1:
    do_something() ## ถ้า condition1 เป็นจริง ทำ do_something()
elif condition2:
    do_another_thing()  ## ถ้า condition1 ไม่เป็นจริงแต่ condition2 เป็นจริง ทำ do_another_thing()
else:
    do_the_last_thing() ## ถ้าไม่มี condition ไหนเป็นจริงเลย ทำ do_the_last_thing()
```
#### operator ที่ใช้ตรวจสอบ condition
== (เท่ากับ) , != (ไม่เท่ากับ), >=, <=, <, >, and, or
- ผลลัพธ์มีแค่ Ture flase
