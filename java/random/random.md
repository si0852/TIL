## Random 클래스
- 의사 난수를 생성
- 초기 시드(seed) 값을 바탕으로 난수 시퀀스 생성

`Seed`
- 랜덤 숫자를 생성할 때 사용되는 초기값
- 같은 시드를 설정하면 실행할 때마다 같은 난수 패턴을 얻는다.

`주요 생성자`
- Random(): 기본 생성자, 현재 시간을 기반으로 난수 생성
- Random(long seed): 특정 시드 값을 인수로 받아 난수 시퀀스 생성

`주요 메서드`
- nextInt(), nextInt(int bound)
- nextLong()
- nextFloat()
- nextDouble()
- nextBoolean()
- nextBytes()

`예제`
~~~ java
private Random randomConstr() {
        Random random = new Random();
        return random;
    }

    private Random randomSeed(long seed) {
        return new Random(seed);
    }

    private void intMethod(Random random) {
        int randomInt = random.nextInt();
        System.out.println("intMethod : " + randomInt);
    }
    private void intMethod(Random random, int bound) {
        int randomInt = random.nextInt(bound);
        System.out.println("intMethod : " + randomInt);
    }

    private void longMethod(Random random) {
        long l = random.nextLong();
        System.out.println("longMethod : " + l);
    }

    private void floatMethod(Random random) {
        float f = random.nextFloat();
        System.out.println("floatMethod : " + f);
    }

    private void doubleMethod(Random random) {
        double d = random.nextDouble();
        System.out.println("doubleMethod : " + d);
    }

    private void booleanMethod(Random random) {
        boolean b = random.nextBoolean();
        System.out.println("booleanMethod : " + b);
    }

    private void byteMethod(Random random) {
        byte[] byteArray = new byte[10];
        random.nextBytes(byteArray);
        System.out.println("byteMethod : " + byteArray);
    }

    private void etcMethod(Random random) {
        random.ints(5).forEach(System.out::println);
        random.doubles(3, 0.0, 1.0).forEach(System.out::println);
    }

    private void generateRandomNum(Random random) {
        int i = random.nextInt(100) + 1; // 1 ~ 100 사이의 난수
        System.out.println("Random Integer between 1 and 100 : " + i);
    }

    private void randomCoin(Random random) {
        String result = random.nextBoolean() ? "Heads" : "Tails";
        System.out.println("Coin flip result: " + result);
    }

    private void generateRandomNum(Random random, int seed) {
        int[] randomArray = new int[10];
        for (int i = 0; i < randomArray.length; i++) {
            randomArray[i] = random.nextInt(seed);
        }
        System.out.println("Random array: " + Arrays.toString(randomArray));
    }
~~~
- 결과
~~~
intMethod : -1782932914
intMethod : 0
intMethod : 3
longMethod : 5744993734927456467
longMethod : -4972683369271453960
floatMethod : 0.77979183
floatMethod : 0.73043025
doubleMethod : 0.7706135175216385
doubleMethod : 0.7304302967434272
booleanMethod : true
booleanMethod : true
byteMethod : [B@85ede7b
byteMethod : [B@5674cd4d
1904686621
-1975163571
-1550062455
1880672021
693744828
0.2675165162838812
0.4410345714396201
0.8261957334720448
-1157793070
1913984760
1107254586
1773446580
254270492
0.672159466804821
0.36817039279355135
0.35676463500575895
Random Integer between 1 and 100 : 43
Random Integer between 1 and 100 : 14
Coin flip result: Tails
Coin flip result: Heads
Random array: [2, 0, 5, 2, 0, 1, 0, 6, 9, 5]
Random array: [0, 6, 6, 0, 4, 1, 1, 4, 3, 1]
~~~