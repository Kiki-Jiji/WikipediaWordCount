# Coursera Task - Wikipedia


1. Shared Memory Data Parallelism (SDP)와 Distributed Data Parallelism (DDP)의 공통점과 차이점
    - 필요에 따라 결과가 combine됨 
    - SDP는 데이터가 split되며 worker들이 독립적으로 병렬처리를 수행함 
    - DDP는 데이터가 여러 노드에 분산되며 각각의 노드들이 독립적으로 병렬처리를 수행함
    
2. 분산처리 프레임워크 Hadoop의 Fault Tolerance는 DDP의 어떤 문제를 해결했나요?
    - Partial Failure : crash failures of a subset of the machines involved in a distributed computation
    - Hadoop/MapReduce's ability to recover from node failure enabled: 
    computation on unthinkably large data sets to succeed to completion

3. Spark가 하둡과 달리 데이터를 메모리에 저장하면서 개선한 것 무엇이고, 왜 메모리에 저장하면 그것이 개선이 되나요?
    - Spark has been shown to be 100x more performance then Hadoop
    - Reading/Writing은 in-memory보다 100x slower
    - Network Communication은 in-memory보다 1,000,000x slower

4. val ramyons = List("신라면", "틈새라면", "너구리")val kkodulRamyons = ramyons.map(ramyon => "꼬들꼬들 " + ramyon)kkodulRamyonsList.map()을 사용하여 ramyons 리스트에서 kkodulRamyon List를 새로 만들었습니다. kkodulRamyons랑 똑같이 생긴 List를 만드는 Scala 코드를 써주세요
    - val res = List("꼬들꼬들 신라면", "꼬들꼬들 틈새라면", "꼬들꼬들 너구리")

5. val noodles = List(List("신라면", "틈새라면", "너구리"), List("짜파게티", "짜왕", "진짜장"))val flatNoodles = noodles.flatMap(list => list)flatNoodlesList.flatmap()을 사용하여 noodles 리스트에서 flatNoodles List를 새로 만들었습니다. flatNoodles랑 똑같이 생긴 List를 만드는 Scala 코드를 써주세요
    - val res = List("신라면", "틈새라면", "너구리", "짜파게티", "짜왕", "진짜장")

6. val jajangs = flatNoodles.filter(noodle => noodle.contains("짜"))jajangsList.filter()를 사용하여 flatNoodles 리스트에서 jajangs List를 새로 만들었습니다.jajangs랑 똑같이 생긴 List를 만드는 Scala 코드를 써주세요
    - val res = List("짜파게티", "짜왕", "진짜장")

7. val jajangMenu = jajangs.reduce((first, second) => first +"," + second)jajangMenuList.reduce()를 사용하여 jajangs 리스트에서 jajangMenu String을 만들었습니다.jajangMenu랑 똑같이 생긴 String을 만드는 Scala 코드를 써주세요
    - val res = "짜파게티,짜왕,진짜장"

8. Eager execution와 Lazy execution의 차이점은 무엇인가요?
    - Eager execution : Spark Actions. Compute a result based on an RDD 
    (result is immediately computed)
    - Lazy execution : Spark Transformations. Return new RDDs as results
    (result RDD is not immediately computed)
    - ** Laziness / Eagerness is how we can limit network communication using the programming model!

9. Transformation과 Action의 결과물 (Return Type)은 어떻게 다를까요?
    - RDD / not RDD

10. RDD.cache()는 어떤 작동을 하고, 언제 쓰는 것이 좋은가?
    - action에 의한 결과를 memory에 저장
    - 여러 action들에 의해 같은 연산이 반복될 

11. Lazy Execution이 Eager Execution 보다 더 빠를 수 있는 예를 얘기해주세요.
    - Eager Execution은 매번 계산이 수행되지만 Lazy Execution은 RDD들의 체인이 최초 Action함수를 
    만나는 순간 한번에 계산이 수행되므로 더 빠를 수 있음

12. 