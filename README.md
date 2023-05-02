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

# เชื่อมต่อไดร์ฟ
```
from google.colab import drive
drive.mount('/content/drive')
```
# เรียกอ่านไฟล์ 
## .CSV
```
unit = pd.read_csv('/content/drive/MyDrive/BPDV65/opendata_unittype.csv') # path drive ที่ไฟล์ .csv ต้องการอ่าน
unit.head()
--------------------------------------------------------------------------------------------------------
df = pd.read_csv('https://raw.github.com/pandas-dev/pandas/master/pandas/tests/io/data/csv/iris.csv')
df # read csv บน web ได้เลย
```
## excel
```
pd.read_excel('/content/drive/MyDrive/BPDV65/myunit.xlsx',sheet_name='unit1') # sheet_name='unit1' ชีทที่ชื่อ
```

# บันทึกตารางเป็นไฟล์
##  save ตาราง
   *   .csv
  ```
  unit.to_csv('myunit.csv') # save(ชื่อไฟล์)  
  unit.to_csv('/content/drive/MyDrive/BPDV65/myunit.csv') #save ลงไดร์ฟ
  ```
  * excel
  ```
  unit.to_excel('/content/drive/MyDrive/BPDV65/myunit.xlsx',sheet_name='unit') # save excel ตั้งชื่อชีทแล้ว
  ```

## create ตาราง
![image](https://user-images.githubusercontent.com/108257658/235647639-047f889c-7b00-4968-8932-bd51a69bc2b0.png)
### Dictionary_RowOriented
```
sales = [{'accout':'Jones LLC','Jan':150,'Feb':200,'Mar':140},
         {'accout':'Alpha Co','Jan':200,'Feb':210,'Mar':215},
         {'accout':'Blue Inc','Jan':50,'Feb':90,'Mar':95}]
df = pd.DataFrame(sales)
df 
```
![image](https://user-images.githubusercontent.com/108257658/235647990-5cf7c237-a431-4040-930c-4d04576f5ad8.png)         

### Dictionary_ColumnOriented
```
sales = {'account':['Jones LLC', 'Alpha Co', 'Blue Inc'],
         'Jan': [150,200,50],
         'Feb': [200,210,90],
         'Mar': [140,215,95]}
df = pd.DataFrame.from_dict(sales)
df
```
![image](https://user-images.githubusercontent.com/108257658/235648255-e6321585-314c-49f2-9c32-91ea36af192f.png)
### List-RowOriented
```
sales = [['Jones LLC', 150, 200,	140],
         ['Alpha Co',	 200,	210,	215],
         ['Blue Inc', 	50,	 90,	95]]
columnname = ['account','Jan','Feb','Mar']
df = pd.DataFrame.from_records(sales,columns=columnname)
df
```
![image](https://user-images.githubusercontent.com/108257658/235648415-b71048b1-0391-406b-9fb3-d754caf1087e.png)

# Chapter1:[Functions, print, Loop, if ](https://github.com/natthanich/BasicProg_DataViz65/blob/main/Basic_Programming_Concepts.ipynb):point_left:	
## Functions ($f(x) = y$) :dog:
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

## `print` :cat:
ตัวอย่าง function `print` https://www.programiz.com/python-programming/methods/built-in/print
![image](https://user-images.githubusercontent.com/108257658/235455255-9d027260-771c-4d49-a89d-c999f21fdfb5.png)

print()  ใส่ input ได้หลายตัว
-   ** คือ จำเป็นต้องใส่
- = คือ ไม่จำเป็นต้องใส่ มีค่าตั้งต้นมาให้
- end คือ จบบรรทัด  \n คือด้วยการขึ้นบรรทัดใหม่
- sep คือ เว้นวรรคค่าด้วย ' ' คือ ช่องว่าง

## Looping (for):tiger:
สำหรับทำงายเยอะๆ ซ้ำๆ
```python
for member in listEx:       ## วนที่สมาชิก ใน list
    do_something()
```
for ชื่อตัวแปร in list ที่จะเอามาใช้เป็นสมาชิกใน ตัวแปร:     
    
วนซ้ำ
- วนซ้ำสมาชิกใน 
### ใช้ for loop เพิ่มสมาชิกใน list :pig:
```
list_name = [] #นิยมสร้าง list เปล่าๆก่อน
list_id = []
list_grade = []
for each in list_name_id_grade:
    list_name.append(each[0])
    list_id.append(each[1])
    list_grade.append(each[2])
```
#### Loop ซ้อน Loop (nested loop):cow:
```
#แม่สูตรคูณ
for mem1 in range(2,5): #แม่[2,3,4]
    print(f'now mem1 = {mem1}')
    for mem2 in range(1,13): #[1,2,3,4,5,6,7,8,9,10,11,12]ตัวมาคูณ
        print(f'{mem1} x {mem2} = {mem1*mem2}')
    print(f'end inner for mem1 = {mem1}') #จบในลูป
```
#### Loop in Function :unicorn:
```
def print_grade_loop(names,grades): # names,grades มีหลายสมาชิก เป็นlist
    for n,g in zip(names,grades): # The zip() function returns a zip object, which is an iterator of tuples where the first item in each passed iterator is paired together, and then the second item in each passed iterator are paired together etc.
        print(f'{n} ได้เกรด {g}')  #  zip การจับคู่ ของเเต่ละ list ในตำแหน่เดียวกัน // จับ 2 list มาร่วมกัน
```
## Conditional Statement (if) :rabbit2:
```
if condition1:
    do_something() ## ถ้า condition1 เป็นจริง ทำ do_something()
elif condition2:
    do_another_thing()  ## ถ้า condition1 ไม่เป็นจริงแต่ condition2 เป็นจริง ทำ do_another_thing()
else:
    do_the_last_thing() ## ถ้าไม่มี condition ไหนเป็นจริงเลย ทำ do_the_last_thing()
```
#### operator ที่ใช้ตรวจสอบ condition :polar_bear:
== (เท่ากับ) , != (ไม่เท่ากับ), >=, <=, <, >, and, or
- ผลลัพธ์มีแค่ Ture flase

# Chapter2:[Data Structure (โครงสร้างข้อมูล)](https://github.com/natthanich/BasicProg_DataViz65/blob/main/Data_Structure.ipynb) :skull:
##  ```list()``` :alien:
- เอาข้อมูลมาต่อๆ กัน
- เก็บอะไรก็ได้ (ไม่จำเป็นต้องชนิดเดียวกัน)
- ลำดับในการเก็บ มีความสำคัญ

### Indexing การชี้สมาชิกใน list ด้วย เลขลำดับของ list :robot:
index = ตัวชี้
```
list_a[3] #เลือกสมาชิกลำดับที่ 3 ของ list_a
```
```
list_b[3][4] #เลือกสมาชิกลำดับที่ 4 ในสมาชิกลำดับที่ 3 ของ list_b
```
```
list_a[-1] #index -1 คือเลือกตัวสุดท้ายของ list (ลำดับ) วัตถุประสงค์การใช้ 1. listมีขนาดใหญ่ 2. list มีการเปลี่ยนแปลง
```
```
list_a[-4] # นับจากท้ายมา 4 ตัว
```
### การสร้าง `list` :panda_face:
```
list_x1 = [] #แบบที่ 1
list_x2 = list() #แบบที่ 2
```
### เพิ่มสมาชิกเข้าไปใน list ด้วย `append()`:otter:
```
list_x1.append(2) # เพิ่ม 2 เข้าไปใน list
```
### ลบสมาชิกจาก list    /// .pop() :bear:
```
list_x1.pop() #ลบออกจากท้ายสุด ||  ไม่นิยมเพราะอาจผิดพลาดได้
```
### `len()` ตรวจสอบจำนวนสมาชิกของ list 	:hedgehog:
### String is a list of characters  (ข้อความคือ ilst ของตัวอักษร) :bat:
```
st_stat = 'Department of Statistics, Faculty of Science'
st_stat[10] # เรียกดูสมาชิกตัวที่ 10
len(st_stat) # จำนวน
```
### List Slicing `:` :chicken:

สามารถเลือกสมาชิก ออกมาแสดงได้หลายๆ ตัว
> `list [จุดเริ่มต้น(ทึบ):จุดสุดท้าย(โปร่ง)]` ## เอาตัวเริ่มต้น ไม่เอาตัวสุดท้าย

> `list [จุดเริ่มต้น(ทึบ:จุดสุดท้าย(โปร่ง):step]`  # step คือ ข้ามไปกี่ตัว
![image](https://user-images.githubusercontent.com/108257658/235480100-91994909-3c1f-4bff-b52d-dfa4bdbeec1c.png)

#### `:` colon :penguin:
```
list_a[-3:]  # : colon  อันนี้คือ เริ่มตั้งเเต่ -3 ไปจนถึงตัวสุดท้าย
list_a[:4]  # : colon # เริ่มตั้งเเต่ตัวที่ 0 จนถึง ก่อน 4
list_a[1:4] #เริ่มตัวที่ 1 จบ ตัวที่ 3
list_a[:] #เอาทุกตัว
```
#### step  ( เพิ่มครั้งละ...) :flamingo:
```
list_c[:10:] #ดู 10 ตัวแรก นับจาก 0
--> [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```
```
list_c[:10:2] #กรณี step = 2   เริ่มจากตัวที่ 0 เว้นระยะห่างครั้งละ 2 จนถึงก่อน 10
--> [1, 3, 5, 7, 9]
```
```
list_c[::-1] #เอาทุกตัว แต่เริ่มจากด้านหลัง
--> [13, 12, 11, 10, 9, 8, 7, 6, 5, 4, 3, 2, 1]
```
### `range()`  สร้าง list ตั้งแต่ นี่ ถึง นี่ :dove:
ได้ลำดับเลขโดยที่ไม่ต้องพิมพ์
- `range(จุดเริ่ม(ทึบ),จุดจบ(โปร่ง))`
```
range(21) #ต้องการ 21 ตัว
range(0, 21)
a = list(range(21))
a
--> [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20]
list(range(1,21))
--> [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20]
```
## Dictionary :face_in_clouds:
- คล้าย lits() (เก็บอะไรก็ได้)
- index เป็นอะไรก็ได้ ไม่จำเป็นต้องเป็นตัวเลขลำดับ (ตัวชี้)
- ลำดับไม่มีความสำคัญ
- ยืดหยุ่นกว่า list เพราะเอาอะไรเป็น index ก็ได้
### สร้าง Dictionary :frog:
dict_a = {1:'Happy','N': 'New','2022':'Year'} #{} curly brackets //ก็คือ index ที่ชี้happyคือ 1 ถ้าพิมพ์ 1 ลงไปจะเเสดงhappy
### การชี้สมาชิกใน Dictionary
```
dict_a[1]
--> 'Happy'
```
```
dict_a['N']
--> 'New'
```
```
dict_a.keys() #ดูว่าใน dict มี key = index อะไรบ้าง
dict_a.values() # เรียกดูว่ามีค่าอะไรในdict บ้าง
```
### การเพิ่มสมาชิกลงไปใน Dictionary :dragon_face:
dict_a[ ที่มีindexเป็น] =  จะมีค่า่เท่ากับ
```
dict_a[7] = 3.14
dict_a
--> {1: 'Happy', 'N': 'New', '2022': 'Year', 7: 3.14}
```
```
dict_a['N'] = 'NNNNEEEEWWWW' #มันจะไปอัปเดตอันเก่าให้เป็นตัวที่เราตั้งใหม่
dict_a
--> {1: 'Happy', 'N': 'NNNNEEEEWWWW', '2022': 'Year', 7: 3.14}
```
## Numpy Array :whale:
เป็นdata structure อย่างหนึ่ง ที่เก็บข้อมูลได้หลายมิติ
- เก็บได้แค่ตัวเลข
- อ้างอิงโดยใช้ พิกัด (2 มิติ ก็มองเป็น matrix)
- มิติมีความสำคัญ ข้อมุลมากขึ้น มิติก็มากขึ้น
![image](https://user-images.githubusercontent.com/108257658/235482167-02065fc8-e943-46f4-9942-92b6c16b5067.png)
### 1D array (n,) :octopus:
```
import numpy #import package ของคนอื่นมา
list_A = [1,2,3,4,5]
arr_a = numpy.array(list_A) #แปลงจาก listไปเป็น array  /// เหมือน arr_a = numpy.array([1,2,3,4,5])
arr_a
--> array([1, 2, 3, 4, 5])
arr_a[0] #เรียกดูสมาชิกแต่ละตัวเหมือน list
--> 1
```
### Matrix (Scalar multiplication) array มีคุณสมบัติเหมือน matrix :shell:
```
5 * arr_a
--> array([ 5, 10, 15, 20, 25])
```
```
5 * list_A #ซ้ำกัน 5 รอบ
--> [1, 2, 3, 4, 5, 1, 2, 3, 4, 5, 1, 2, 3, 4, 5, 1, 2, 3, 4, 5, 1, 2, 3, 4, 5]
```
```
arr_b = numpy.array([10,20,30,40,50])
arr_a + arr_b #ตัวที่อยู่ตำแหน่งเดียวกันมาบวกกัน
--> array([11, 22, 33, 44, 55])
```
### 2D array :thinking:
 array 2 มิติ
 ```
import numpy as np  #   เรียก numpy มาใช้ แต่เปลี่ยนชื่อเป็น np
arr2_z = np.array([[1,2,3],[4,5,6]]) # สมาชิกลำดับที่ 1 เป็นแถว ลำดับที่ 2 เป็นหลัก
arr2_z
--> array([[1, 2, 3],
          [4, 5, 6]])
arr2_z.shape #ดูว่ามีกี่แถวกี่หลัก อันนี้คือมี 2 แถว 3 หลัก
--> (2, 3)
```
### `np.zeros()` :shushing_face:
สร้าง array ว่างๆ ขึ้นมา
```
arr2_3_5_0 = np.zeros((3,5)) #สร้าง array ที่ตั้งต้นด้วย 0 แบบ 3 แถว 5 หลัก ค่อยเพิ่มค่าทีหลังได้
arr2_3_5_0 #เราต้องกำหนดขนาดของ array ขยายไม่ได้
--> array([[0., 0., 0., 0., 0.],
           [0., 0., 0., 0., 0.],
           [0., 0., 0., 0., 0.]])
 ```
 ```
 arr2_3_5_0[1,2] = 9 #กำหนดค่าแถวที่ 1 หลักที่ 2 ให้เป็นเลข 9
 arr2_3_5_0
 --> array([[0., 0., 0., 0., 0.],
            [0., 0., 9., 0., 0.],
            [0., 0., 0., 0., 0.]])
```
```
arr2_3_5_0[1,2] #ชี้
--> 9.0
```
```
#เปลี่ยนค่าใน list() :seal:
print(list_A) # เรียกดู list ก่อน
list_A[-1] = 'Christmas' #เปลี่ยนค่าใน list()
print(list_A)
-->  [1, 2, 3, 4, 5]
     [1, 2, 3, 4, 'Christmas']
```
### `np.ones()`:woozy_face:
- เริ่มต้นมาค่าเป็น 1 หมด
- ทำให้สามารถกำหนดค่าเริ่มต้นเป็นค่าอื่นๆ ได้
```
arr_2_4_5_1 = np.ones((4,5))  # 4 แถว 5หลัก
--> array([[1., 1., 1., 1., 1.],
           [1., 1., 1., 1., 1.],
           [1., 1., 1., 1., 1.],
           [1., 1., 1., 1., 1.]])
```
```
arr_2_4_5_200 = 200 * np.ones((4,5))
--> array([[200., 200., 200., 200., 200.],
           [200., 200., 200., 200., 200.],
           [200., 200., 200., 200., 200.],
           [200., 200., 200., 200., 200.]])
```
### Matrix operations	:monocle_face:
-  การบวก ลบ matrix $M ± N$ บวกลบตัวที่อยู่ตำแหน่งเดียวกัน และ matrix shape ต้องเท่ากัน
- การคูณ matrix
  - Scalar คูณ Matrix   $aM$ (คูณกระจายเข้าไปทุกตัว)
  - Matrix คูณ Matrix   $M\times N$ (แถวคูณหลัก)
    - $M×N$ (dot product)
    - (m,n) × (n,o) = (m,o) (Shape)
    -  ตัวหน้า ตัวหลังมีความสำคัญ
    ![image](https://user-images.githubusercontent.com/108257658/235487153-1470da26-bdb4-4507-9fe3-82f1f590072a.png)
    ```
    mat_a = np.array([[2,3,5],[4,6,7]])
    mat_b = np.array([[1,2,5],[2,4,-7]])
    mat_c = np.array([[2,3],[4,6],[7,9]])
    ```
    ```
    np.dot(mat_a,mat_c)
    --> array([[ 51,  69],
               [ 81, 111]])
    ```
    ```
    np.dot(mat_c,mat_a)
    --> array([[16, 24, 31],
               [32, 48, 62],
               [50, 75, 98]])
    ```
    ```
    mat_a * mat_b #คูณตัวตำแหน่งเดียวกัน ไม่เป็นไปตามสมบัติ matrix
    --> array([[  2,   6,  25],
               [  8,  24, -49]])
### Matrix Slicing :muscle:
```
mat_X = np.dot(mat_c,mat_b)
print(mat_X)
--> [[  8  16 -11]
     [ 16  32 -22]
     [ 25  50 -28]]
mat_X[:2,:2]  #เลือกตั้งแต่แถวที่ 0- ก่อน 2 , เลือก หลักที่ 0-ก่อน2
--> array([[ 8, 16],
           [16, 32]])
```           
# Chapter3:[pandas101](https://github.com/natthanich/BasicProg_DataViz65/blob/main/pandas101.ipynb):zipper_mouth_face:
## ดูข้อมูลคร่าว ๆ :smirk:
 ```
 .head() # ดูข้อมูล 10 แถวแรก
 .shape #ดูว่าข้อมูลมีกี่แถวกี่หลัก
 .describe()
![image](https://user-images.githubusercontent.com/108257658/235627228-f10c1f48-4eaf-4162-bdf9-4526e23466d7.png)
```
## ตรวจสอบ Missing (isnull) 	:face_exhaling:
```
.isnull() # ตรวจสอบว่าค่านั้นเป็นค่า missingหรือไม่
.isnull().any()  #.any( )คือการเอาค่าความจริง ใน column มา  or กัน ///False คือไม่มี missing  เลย /// True ต้องจัดการ || ปกติดูอันนี้
.isnull().all()  #.all( )คือการเอาค่าความจริง ใน column มา  and กัน
.isnull().any().any() -> True
```
## ลบ Missing :relieved:
missing ->  null, na(not autorized, NaN (not a number)
![image](https://user-images.githubusercontent.com/108257658/235631202-b1a7dcb3-8623-46f5-bdf1-c039e78fcd89.png)
- axis =0 พิจารณาแนวแถว/ 1 พิจารณา ตามหลัก  //ตัดทุกๆ ข้อมูล ที่มี missing ออก // 1 = ลบทั้งเเถววววว // 0 = ลบทั้งคอลัมน์
- how = 'any' / มี 1 missing ก็จะโดนตัดเลย เเต่ถ้า = 'all'  ก็ต้องเป็นทุกอันที่มีค่าว่าง ถึงตัด
- thresh กรอกเป็น int*** เก็บเฉพาะแถวที่ มี missnig อย่างน้อย  .... (int) ตัว แนวนอน
-  thresh แนวตั้ง //  int ใส่จำนวนที่มีค่า missing เกินกี่ค่า ถึงจะลบ
- subset ตัดเฉพาะ คอลัมที่เรากำหนด คอลัมน์ที่เรากำหนดจะไม่มี missing แน่นอน
- inplace, deFault False แทนค่าลงไปในตัวแปร fl = ไม่เเทนค่าลงในตัวแปร /True = แทนค่าลงในตัวแปรเดิม
```
## dropna() 
.dropna()  # axis =0 พิจารณาแนวแถว/ 1 พิจารณา ตามหลัก  //ตัดทุกๆ ข้อมูล ที่มี missing ออก // ลบทั้งเเถววววว
.dropna(axis=1) # เอาเเค่คอลัมที่ไม่มีmissing เลย
```
how = 'any' / มี 1  missing ก็จะโดนตัดเลย เเต่ถ้า = 'all' ก็ต้องเป็นทุกอันที่มีค่าว่าง ถึงตัด
```
.dropna(how = 'all') # ตัดทุกแถวที่เป็น missing หมด
```
thresh : int ใส่จำนวนที่มีค่า missing เกินกี่ค่า ถึงจะลบ
```
.dropna(axis=1, thresh=42000) # แนวตั้ง //  int ใส่จำนวนที่มีค่า missing เกินกี่ค่า ถึงจะลบ
```
### subset ตัดเฉพาะ คอลัมที่เรากำหนด :drooling_face:
```
.dropna(subset=['propertytype_name_en','price_min','area_usable_min']) # 3columnนี้จะไม่มี missingแน่นอน
```
### inplace แทนค่าลงไปในตัวแปร fl = ไม่เเทนค่าลงในตัวแปร  /True   = แทนค่าลงในตัวแปรเดิม :face_with_thermometer:
```
.dropna(subset=['propertytype_name_en','price_min','area_usable_min'], inplace = True) # True = แทนค่าลงในตัวแปรเดิม
```
## แทนค่า missing ด้วยค่าที่เราต้องการ (fillan()) :neutral_face:
- value ใส่เป็น dict ว่า เราจะใส่ค่าใน คอลัมน์ไหน เป็นค่าของอะไร  #dic {}  
![image](https://user-images.githubusercontent.com/108257658/235638976-843a9cb8-07c2-4b82-93d0-3f93f97eb8ce.png)
![image](https://user-images.githubusercontent.com/108257658/235639056-c6869e2a-dc59-45bc-956f-5fd082e96a1f.png)
```
.fillna(0) # ทุกค่าที่เป็น missing จะถูกแทนด้วย 0  // ไม่ควรทำ
.fillna(value={'count_room_utility':0,'area_total_min_wa':unit['area_total_min_wa'].mean()})  #dic {}
```
##  วนลูป record ในตาราง (iterrows):lying_face:
วิ่งไปทีละเเถวว
```
for row in unit.head(20).iterrows():
    if 'project_' not in row[1]['project_id']:   #  สนใจที่ไม่มี project ขึ้นต้น ถ้าไม่มีก็แสดงออกมา // /row[1] ในสมาชิกตัวที่ 1
      print(row)
```
```
for row in unit.iterrows():
    if 'สตูดิโอ' in row[1]['url_unittype']:   #  สนใจที่มี สตูดิโอ ขึ้นต้น ถ้ามีก็แสดงออกมา // [1]['url_unittype'] สมาชิกตัวที่ 1 คอลัมน์[]
      print(row[1]['url_unittype'])
```
## Groupby   จัดกลุ่มแล้วจึงคำนวนค่าที่ต้องการ :hugs:
```
.groupby(['propertytype_name_en']).mean()   # จัดกลุ่มข้อมูลด้วย []  แล้วหา mean() ของเเต่ละกลุ่ม
.groupby(['propertytype_name_en']).count() 
.groupby('propertytype_name_en').mean().reset_index() #.reset_index() ทำให้ตารางเป็นตาราง 2 มิติ
.groupby('propertytype_name_en').mean().reset_index()[['propertytype_name_en','price_min']]  # แสดงแค่คอลัมน์ ['propertytype_name_en','price_min']
```
```
.max()= หา มากสุดของเเต่ละคอลัมน์
.min() 
```
# ต่อตาราง :face_with_thermometer:
![image](https://user-images.githubusercontent.com/108257658/235645015-4117cb53-64d5-4f1c-975a-bb413e68d6c0.png)

- obj list ของตารางที่อยากเอามาต่อกัน 
- axis ตามแถว 0 // 1 ตามหลัก
- join inner เอาเเค่ที่key ซ้ำ //outer เอาหมด
- sort เรียงตาราง
## ต่อตารางแกน Y (เพิ่มปริมาณข้อมูล) :mask:
```
.iloc[:,:]
pd.concat()
```
## ต่อตารางแกน X (เพิ่มรายละเอียด ข้อมูล) :vomiting_face:
### ต่อแบบเอาตารางมาต่อกันเลย  // merge() :hot_face:
```
.merge(project, left_on='project_id', right_on='project_id') # จะต่อด้วยKey อะไร   // ซ้ายของ unit
```
```
this[this['province_name_th']=='ขอนแก่น'] #หาบ้านที่อยู่ในจังหวัดขอนแก่น
```
### ต่อแบบเลือกมาเฉพาะบาง column (map)  // แกน x  ได้คอลัมน์ที่ต้องการจริงๆ  :face_with_spiral_eyes:	
```
#คีย์หลักซ้ำได้ คีย์รองซ้ำไม่ได้
project_nodup = project.drop_duplicates(subset=['project_id']) #drop อันซ้ำออกกก่อน
unit['pricemin'] = unit['project_id'].map(project_nodup.set_index('project_id')['price_min'])  #เอา  price_min ของตาราง โปรเจค มาใส่ในตาราง unit 
```
# ------- Visualization --------------
# Chapter4:[DataViz01_Table_Data](https://github.com/natthanich/BasicProg_DataViz65/blob/main/DataViz01_Table_Data.ipynb):point_left:	
https://datavizcatalogue.com
* ดูว่ามีค่า/อักษรที่ไม่ซ้ำ กี่ค่า
## data 	:sleepy:
![image](https://user-images.githubusercontent.com/108257658/235694685-aa99d59d-54ce-4bd5-8bed-f17770716847.png)
```
set(df['Name']
df['Name'].unique() # pd  หาค่าที่ ไม่ซ้ำของคอลัมน์ชื่อ
```
## Parallel Coordinates	:hot_face:
```
pd.plotting.parallel_coordinates(df, 'Name') #python  pd.plotting.parallel_coordinates(จากตาราง, 'จัดกลุ่มโดย')
# จากกราฟ เขียวสด กับม่วง คล้ายกัย ส่วนเขียวอ่อน จะเล็กต่างจากเพื่อน
```
![image](https://user-images.githubusercontent.com/108257658/235693558-2cd90cfd-1e89-4cfa-94be-a010609e1d22.png)
### select columns to show :cold_face:
```
pd.plotting.parallel_coordinates(df, 'Name',cols = ['SepalLength','PetalLength','SepalWidth','PetalWidth']) 
```
![image](https://user-images.githubusercontent.com/108257658/235693959-5100712f-5016-4d94-9deb-ed49d193d3e3.png)
```
pd.plotting.parallel_coordinates(df, 'Name',cols = ['SepalLength','PetalLength']) # cols = ['SepalLength','PetalLength'] เลือกเฉพาะ คอลัมน์ที่อยากทำมาเเสดง
#กลีบดอกกับกลีบเลี้ยง มีขนาดต่างกันมั้ย
```
![image](https://user-images.githubusercontent.com/108257658/235694191-96ab0d72-4974-4dbb-ace5-01d7feb9417a.png)

### change color	:disguised_face:
https://matplotlib.org/stable/tutorials/colors/colors.html
rgbcmyk
```
pd.plotting.parallel_coordinates(df, 'Name', color=['c','m','y'])
```
![image](https://user-images.githubusercontent.com/108257658/235695499-fed51e47-6ff6-43e9-a0e7-955e4d6234a6.png)
```
pd.plotting.parallel_coordinates(df, 'Name', color=[[0.6,0,0],[0,0,0.8],[0.2,0.4,0.7]]) # ใช้ค่า RGB สีผสม
```
![image](https://user-images.githubusercontent.com/108257658/235695703-e1321d0a-7127-426a-badd-f8373dd4183c.png)
```
pd.plotting.parallel_coordinates(df, 'Name', color=['#a73b24', '#F98EC5', '#88B46C']) # web color // html color
```
![image](https://user-images.githubusercontent.com/108257658/235695826-f702b0d3-9c6e-4fa5-88ac-4fe7993bbbc9.png)

#### Specify color by colormap  // เซตของสี่ที่เข้ากัน :sunglasses:
**https://matplotlib.org/stable/tutorials/colors/colormaps.html**
```
pd.plotting.parallel_coordinates(df, 'Name', colormap='magma')
```
![image](https://user-images.githubusercontent.com/108257658/235696610-de0281bd-b737-4ec7-87de-fc167d99b908.png)

# Matplotlib	:confused:
```
from matplotlib import pyplot as plt #เพื่อ plot graph
import matplotlib #เพื่อปรับแต่งขนาดของกราฟ
```
## Heatmap matrix:astonished:
```
plt.imshow(df.iloc[:,:-1],interpolation='nearest') # -1 ไม่เอาคอลัมน์สุดท้าย  // เข้ม มาก  สว่างน้อย
plt.imshow(df.iloc[:,:-1],interpolation='nearest',cmap = 'hot')
plt.imshow(df.iloc[50:100,:-1],interpolation='nearest',alpha = 0.8) # alpha ความเข้มจางของเส้นกราฟ
```
# ปรับขนาดภาพ :cold_sweat:
```
matplotlib.rcParams['figure.figsize']=[30,30] #กำหนดขนาดของ figure
plt.subplot(1,3,1)  # subplot(มีกี่แถว, มีกี่หลัก, เป็นตัวที่เท่าไหร่)
```
# Chapter5:[DataViz02_Data_Distribution_](https://github.com/natthanich/BasicProg_DataViz65/blob/main/DataViz02_Data_Distribution_.ipynb):cry:
## Scatter Plot
ดูการกระจายของข้อมูล  // เอาข้อมูลมาพอตเป็นจุด โดยตำแหน่งแต่ละค่า ค่าในคอลัมน์
![image](https://user-images.githubusercontent.com/108257658/235701372-45b1a5f1-47f4-45b5-b788-d9bb852a8162.png)
```
from matplotlib import pyplot as plt
plt.scatter([1,-1],[2,-1]) # ( x,y)  ([จุดแรกในแกน x = 1, จุดสอง ค่าในแกน x = -1],[จุดแรกค่าในแกน y=2,จุดสองค่าในแกน y= -1 ])
plt.scatter(df['PetalLength'],df['SepalLength']) #ความยาวกลีบดอก เทียบกับ ความยาวกลีบเลี้ยง
```
## เปลี่ยนสี 
c = arr -like or list of col / col เลยก็ได้  // list กำหนดสีเเต่ละประเภทได้
```
plt.scatter(df['PetalLength'],df['SepalLength'],c='r')
```
### ระบุสีให้แต่ละจุด
* แทนค่าชื่อดอกไม้ด้วยตัวอักษรแทนสี (r g b c m y k w)
```
df2 = df.replace({'Iris-setosa':'r', 'Iris-versicolor':'g', 'Iris-virginica':'b'})
plt.scatter(df2['PetalLength'],df2['SepalLength'],c=df2['Name']) # ความยาวกลีบเลี้ยง กลีบดอก #จำนวนสมาชิก ของ x y c ต้องเท่ากัน len()
```
![image](https://user-images.githubusercontent.com/108257658/235702315-0dc2eef4-4ae1-482d-a626-c6a49b16aebe.png)

## เพิ่มรายละเอียดกราฟ
### ชื่อแกน
```
plt.xlabel('PetalLength') #ชื่อเเกน x
plt.ylabel('SepalLength') # ชื่อแกน y
```
### ชื่อ marker
```
plt.scatter(df2['PetalLength'][:50],df2['SepalLength'][:50],c=df2['Name'][:50],label='setosa')
plt.scatter(df2['PetalLength'][50:100],df2['SepalLength'][50:100],c=df2['Name'][50:100],label='versicolor')
plt.scatter(df2['PetalLength'][100:],df2['SepalLength'][100:],c=df2['Name'][100:],label='verginiga')
plt.legend()  #โชว์ // ให้วางตรงไหนของกราฟ
```
![image](https://user-images.githubusercontent.com/108257658/235704242-f81b6e4b-2b90-4d5e-aafe-dfac3f2c871e.png)

### ชื่อกราฟ
```
plt.title('Comparing petal&sepal length of different iris flowers'); #ชื่อกราฟ
```
![image](https://user-images.githubusercontent.com/108257658/235704520-b63387ee-b045-490b-9a1f-698979efaa6c.png)

## ใช้ ขนาดของ marker ในการแสดงค่าใน column
s =  size เอาความกว้างของกลีบดอกมาเป็น size
![image](https://user-images.githubusercontent.com/108257658/235705179-d3ad0883-454e-463f-adf5-5c41d1f22179.png)
```
plt.scatter(df2['PetalLength'][:50],df2['SepalLength'][:50],c=df2['Name'][:50],label='setosa',s=df2['PetalWidth'][:50])
plt.scatter(df2['PetalLength'][50:100],df2['SepalLength'][50:100],c=df2['Name'][50:100],label='versicolor',s=df2['PetalWidth'][50:100])
plt.scatter(df2['PetalLength'][100:],df2['SepalLength'][100:],c=df2['Name'][100:],label='verginiga',s=df2['PetalWidth'][100:])
plt.legend()
plt.xlabel('PetalLength')
plt.ylabel('SepalLength')
plt.title('comparing petal&sepal length of different iris flowers');
```
![image](https://user-images.githubusercontent.com/108257658/235705369-654f2525-0a50-4ca4-a258-468c9c7bf7fa.png)

*ขยายของขนาด marker ที่เล็กเกินไป
```
plt.scatter(df2['PetalLength'][:50],df2['SepalLength'][:50],c=df2['Name'][:50],label='setosa',s=40*df2['PetalWidth'][:50])
plt.scatter(df2['PetalLength'][50:100],df2['SepalLength'][50:100],c=df2['Name'][50:100],label='versicolor',s=40*df2['PetalWidth'][50:100])
plt.scatter(df2['PetalLength'][100:],df2['SepalLength'][100:],c=df2['Name'][100:],label='verginiga',s=40*df2['PetalWidth'][100:])
plt.legend()
plt.xlabel('PetalLength')
plt.ylabel('SepalLength')
plt.title('comparing petal&sepal length of different iris flowers');
```
![image](https://user-images.githubusercontent.com/108257658/235705617-c0a4efa0-0cf4-4c27-80f1-16925846dee0.png)
## ปรับความโปรงใสของ marker เพื่อให้มองเห็นจุดที่ถูกบัง (Bubble Chart)
alpha 
```
plt.scatter(df2['PetalLength'][:50],df2['SepalLength'][:50],alpha=0.5,c=df2['Name'][:50],label='setosa',s=40*df2['PetalWidth'][:50])
plt.scatter(df2['PetalLength'][50:100],df2['SepalLength'][50:100],alpha=0.5,c=df2['Name'][50:100],label='versicolor',s=40*df2['PetalWidth'][50:100])
plt.scatter(df2['PetalLength'][100:],df2['SepalLength'][100:],alpha=0.5,c=df2['Name'][100:],label='verginiga',s=40*df2['PetalWidth'][100:])
plt.legend()
plt.xlabel('PetalLength')
plt.ylabel('SepalLength')
plt.title('comparing petal&sepal length of different iris flowers \n (sizes of the circle determine petal widths of the flowers)');
```
![image](https://user-images.githubusercontent.com/108257658/235705898-3d5c51b2-7210-428a-991d-4e734f78d2db.png)

## เปลี่ยน หน้าตาของ Marker เพื่อความสวยงาม
marker =  $c$ $ พอตตัวนส$
```
plt.scatter(df2['PetalLength'][:50],df2['SepalLength'][:50],alpha=0.5,c=df2['Name'][:50],label='setosa',s=40*df2['PetalWidth'][:50],marker='X')
plt.scatter(df2['PetalLength'][50:100],df2['SepalLength'][50:100],alpha=0.5,c=df2['Name'][50:100],label='versicolor',s=40*df2['PetalWidth'][50:100],marker='X')
plt.scatter(df2['PetalLength'][100:],df2['SepalLength'][100:],alpha=0.5,c=df2['Name'][100:],label='verginiga',s=40*df2['PetalWidth'][100:],marker='X')
plt.legend()
plt.xlabel('PetalLength')
plt.ylabel('SepalLength')
plt.title('comparing petal&sepal length of different iris flowers');
```
![image](https://user-images.githubusercontent.com/108257658/235706193-431719a3-02c9-4a51-8113-3988cacd0997.png)

## แสดงแบบ 3 มิติ
```
plt.axes(projection = "3d")
```
# Boxplot

![image](https://user-images.githubusercontent.com/108257658/235707886-ac6fb645-52b1-4a92-8473-744a5b36e097.png)
![image](https://user-images.githubusercontent.com/108257658/235707945-832872ce-5cc9-4f53-b917-4f01f343de7c.png)

```
plt.boxplot(df['SepalLength']); #วาดการกระจายของความยาวกลีบเลี้ยง  // ; ปิด output ที่เป็นtext
```
![image](https://user-images.githubusercontent.com/108257658/235708373-36b4d76b-6aa2-4884-b73c-0b7d441de00b.png)

```
plt.boxplot(df['SepalLength'],vert=False) # defult = Ture
```
![image](https://user-images.githubusercontent.com/108257658/235708488-6fd5a99d-1409-4d06-8ab6-ad7537351a51.png)

## median
```
ybp['medians'][0].get_xdata() #  xdata() ค่าในแนวแกน x
ybp['medians'][0].get_ydata()  
```
## min
```
min(ybp['whiskers'][0].get_xdata()) #min หลังจาก ลบout liner
```
## max
```
max(ybp['whiskers'][1].get_xdata())
```
## q1
```
max(ybp['whiskers'][0].get_xdata())
```
## outlier
```
plt.boxplot(df['SepalLength'],vert=False,meanline=True,showmeans=True)
plt.boxplot(df['SepalLength'],vert=False,showmeans=True,meanprops={'marker':'o'})
```
![image](https://user-images.githubusercontent.com/108257658/235710413-0c4c7895-4164-48dc-997e-7f1da8b1a219.png)






