# 5th Module

##  before optimization
gui test : all-student, all-student-name, highest-gpa
![image](https://github.com/user-attachments/assets/4f0a995b-5a3e-453d-9e49-fc4b8dc74470)
![image](https://github.com/user-attachments/assets/2810f9c9-600b-4fa1-a3c1-74c96efc111b)

cli test : all-student-name, highest-gpa
![image](https://github.com/user-attachments/assets/b46b0d23-c66c-4d3b-b989-fbbf99e74568)
![image](https://github.com/user-attachments/assets/9af8d883-b8c0-4b4e-8229-041d57698601)


## after optimization
cli test : highest-gpa
![image](https://github.com/user-attachments/assets/851abbf9-b088-411e-a25a-ddb057561fc9)
cli test : all-student-name
![image](https://github.com/user-attachments/assets/9dcbe6dd-9e2b-4d7e-9a02-9cd301c97489)

## h-2-h
highest-gpa ![image](https://github.com/user-attachments/assets/6d44518e-09f0-4eb1-9938-0ba0e1665b3e)
all-student-name ![image](https://github.com/user-attachments/assets/13c846d6-5b62-4f25-9667-94054e1c8210)


## reflection
1. JMeter dan profilling tools intellij adalah dua tools yang sangat bermanfaat. meskipun demikian, penggunaan jmeter dan profilling dari intellij berbeda. jmeter adalah sebuah perangkat lunak yang membantu kita untuk melakukan simulasi terhadap request (massive request) yang akan didapatkan oleh server kita. sedangkan intellij proiler digunakan untuk melakukan analisis runtime (cpu bound, memori stack, program time execution, dsb.)

2. dengan menggunakanprofiling (lebih tepatny profilling intellij idea ultimate) membantu saya untuk menganalisis bottlenecks yang ada di dalam kode saya. hal ini dapat membuat saya mengetahui apa yang membuat sebuah request begitu lama, apakah ada kode yang begitu berat (kompleksitasnya), apakah ada kode yang meretrieve information namun sangat lambat dan sebagainya. hal ini bisa dilihat dengan jelas di runtime bar yang ada di intellij profiler.

3. Yes. Bottleneck kita definisikan sebagai sebuah operasi yang sangat bereat atau sebuah kode blok atau sebuah sintaks kode (line kode) yang begitu berat jauh lebih berat daripada kompleksitas semua keseluruhan kode yang ada. dengan menggunakan profiler, kita dapat melihat saat terjadinya request, method method apa yang dipanggil dan berapa lama method tesebut dipanggil. dengan ini dapat membuat kita megngetahui apa method yang sangat berat (program kita menghabiskan waktu di method tersebut) dibanding dengan eksekusi kode kode yang lain.

4. menurut saya pada tutorial kali ini tepatnya saya mengalami kesulitan untuk melakukan simulasi massive request. sebenarnya ketika melakukan testing seharusnya kita membuat program kita utnuk dapat menangani request yang sangat besar, namun untuk membuat simulasi request yang sangat besar dibutuhkan pula komputer yang cukup untuk melakuakn simulasi request tersebut dan dibantu oleh jmeter. namun sayangnya, komputer saya tergolong murah dan tidak begitu kuat untuk melakukan simulasi request yang sangat besar, belum lagi ditambah backend springboot yang masih berjalan untuk menangani request teersebut membuat laptop saya kewalahan.

5. saya dapat melihat secara detail keseluruhan runtime program saya. hal ini dimaksudkan bila sebuah request dipanggil, fungsi apa yang akan dijalankan begitu lama (begitu berat) dibandingkan dengan fungsi fungsi yang lain. hal ini membuat saya mengetahui degnan mudah apakah terjadi bottleneck atau tidak di sebuah fungsi tertentu.

6. karena profiler tidak memberikan informasi yang konsisten kita dapat mengakalinya dengan beberapa cara serprti, melakukan pengujian dengan tolak ukur yang sama (jumlah request, request apa yang dipanggil dan sebagainy), selain itu kita juga bisa menghindari hasil test yang diberikan dengan hasil yang didapatkan dengan runtime pertama kali (penjelasan ada di modul), dengan kita menyamakan parameter saat testing, kita dapat menghindari ketidakkonsistenan yang diberikan oleh profiler

7. saya melihat bahwa pemrosesan datanya sangat buruk. banyak nested loop yang sangat tidak perlu. hal ini bisa diatasi dengan menggunakan join yang dapat diakses di realtional sql. bahkan dengan menggunakan join di relational sql performa yang berdampak sangat banyak, karena secara default join di realtional sql sudah menggunakan analisis heuristik, bahkan kita bisa melakukan heuristik yang lebih lanjut dibagian sqlnya. hal ini lebih ringan dibanding tidak melakukan heuristik sama sekali di sql dan melakukan nested loop.

## konklusi
dilihat dari elapsed time yang ada (head to head) perbedaan performa sangat sangat sangat signifikan, bahkan lebih dari 76 % hingga lebih dari 90 % lebih efisien. serta hindari nested loop (n+1) query problem dan lakukan heuristic optmization (dibahas di basdat :) )
