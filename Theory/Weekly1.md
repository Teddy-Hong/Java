## JAVA
- Java TEST (PC에 자바가 설치되어 있어야 동작)
 - 임의의 폴더를 생성한 후 메모장이나 에디터를 사용해서 HelloWorld.java 생성
 - 명령프로프트 or powershell 실행
 - 생성한 폴더 찾아가서 생성한 파일있는지 확인
 - 파일로 돌아가 아래와 같이 타이핑

 ```java
class HelloWorld {
	public static void main(String[] args) {
    	System.out.print("Hello World!!");
    }
} 
```
 - 컴파일은 javac HelloWorld.c
 - 실행은 java HelloWorld

- java의 실행과정 
 - 참조 : http://www.slideshare.net/ssuser4ff81c/java-56998433

- 코드 작성 규칙
 - 주석
```java
	; //세미콜론
    { } //블럭
	//  한줄주석처리
	/*  .....  */ 다중 주석처리
    /**
     *
     */ //javadoc
```
 - 식별자 - 변수명, 상수명, 클래스명, 패키지명 등을 선언할 때 붙이는 이름. ex)main
 - 예약어 - 자료형 이름 같은걸 말함.ex) char int
 - 변수와 상수 (상수는 변수 앞에 final을 붙이면 됨. 변경 안됨)
  - 변수 상수 참조 : http://ding9.tistory.com/88
 - 기본자료형 - 논리형, 문자형, 정수형, 실수형,문자형2(string, 기본자료형은 아님)
 - 문자형 타입 적용 - 작은따옴표 적용 '글' 이런식으로 2byte

 - 정수형 타입 적용 - byte(1 byte), short(2 byte), int(4 byte), long(8 byte)
 - 실수형 타입 적용 - float(4 byte), double( 8byte)
 - 실수형 연산 오류 원인
   - a= 0.1515 * 10e1 = 1.515
   - b= 0.55 * 10e-5 =  0.0000055
   - 풀어쓰면 a + b = 1.5150055 = 0.15150055 * 10e1
   - 저장되는 지수가수법으로 변경하면 0.1515006 * 10e1
   - 따라서 정확한 계산이 필요하다면 대안이 필요.

 - 자료형 변환 - 계산 형태에 따라 자동으로 형변환, byte + int 이면 결과가 int로 변하는 걸 말함.
   - 참조 : https://opentutorials.org/module/516/5330

 - 문자 <-> 숫자 (함수로 정의되어 있음.)
 - 연산자 우선순위 - 참조 : https://msdn.microsoft.com/ko-kr/library/2bxt6kc4.aspx
 - 쉬프트 연산자 >> 과 >>> 의 차이는 >>의 경우, 부호가 바뀌지 않으나 >>>의 경우 무조건 0이 채워짐.
   - 0100 1111 이란 값이 있고 이것을 2만큼 쉬프트하는 경우..
   |연산자|기준값|변환1|변환2|설명|
   |:-----|:--|:--|:--|:--|
   |>>|01001111|**11**010011~~11~~|11010011|새로 추가되는 값은 1<br>오른쪽 끝 2개는 삭제<br>이경우 값이 signed라면 값이 (-)로 바뀜|
   |>>>|01001111|**00**010011~~11~~|00010011|새로 추가되는 값은 0<br>오른쪽 끝 2개는 삭제|
 - 반복문 - break, continue.

### 실습
- BigDecimal 큰수 계산할때 사용 3,333,333,333 이런수..

```java
import java.math.BigDecimal; //BigDecimal을 사용하기 위해 필요.

	BigDecimal testVar = new BigDecimal(0);

	testVar = result.add(new BigDecimal(10));

	testVar = result.multiply(new BigDecimal(5));

	testVar = result.divide(new BigDecimal(10));
```

### 함수 구현하기
```java
    /** count와 unit을 입력받아서
     * 
     * ex) count = 3, unit = A
     * 
     * A
     * AA
     * AAA
     * 
     * @param int count
     * @param String unit
     */
    public void showRectTri(int count, String unit) {
        int i = 0;
        int j = 0;

        for ( i = 0; i < count; i++) { //줄수
            for ( j = 0; j <= i; j++) {//1줄은 1개 2줄은 2개...count줄은 count개 이므로 j<=i
                System.out.print(unit);
            }
            System.out.println(""); //라인변경
        }
    }

    /** count와 unit을 입력받아서
     * 
     * ex) count = 3, unit = A
     * 
     *   A
     *  AA
     * AAA
     * 
     * @param int count
     * @param String unit
     */
    public void showRevTri(int count, String unit) {
        int i = 0;
        int j = 0;

        for ( i = 0; i < count; i++) { //줄수
            for ( j = 0; j < count; j++) {// 공백의 수는 count -1 -줄수 , 줄수 만큼 문자 표시
                if ( (count-(j+1)) > i) { //공백은 count -(1+줄수) > i
                    System.out.print(" ");
                }
                else {                  //문자 표시
                    System.out.print(unit);
                }
            }
            System.out.println("");
        }
    }
```
- 퀴즈 - 예제를 이용하여 아래 문제 풀어보기
```java
    /** Quiz1. count와 unit을 입력받아서
     * 
     * ex) count = 3, unit = A
     * 
     *   A
     *  AAA
     * AAAAA
     * 
     * @param int count
     * @param String unit

     //이런 문제를 풀때는 모양을 사각형으로 자르는 것이 좋다.
     * |---|
     * |  A|
     * | AA|A
     * |AAA|AA
     * |---|
     * 이렇게 나눠보면 1줄에서는 사각형 뒤에 찍는것이 없고.
     * 둘째줄 1개, 셋째줄 2개 이런식이다.
     * 먼저 사각형 부분을 구현하고 그 뒤에 남는 부분은 for문을 추가해서 하면 좋다.
     * */
    public void showTri(int count, String unit) {
        int i = 0;
        int j = 0;

        for ( i = 0; i < count; i++) { //줄수
            for ( j = 0; j < count; j++) {//공백의 수는 count -1 -줄수 , 줄수 만큼 문자 표시
                if ( (count-(j+1)) > i) { //공백은 count -(1+줄수) > i
                    System.out.print(" ");
                }
                else { //unit 표시
                    System.out.print(unit);
                }
            }
            //사각형 영역 제외 나머지 부분 인쇄 구문.
            for ( j = 0; j < i; j++) { //첫줄은 표시하지 않기때문에 조건 설정 중요.
                System.out.print(unit); 
                // i = 0 , 통과
                // i = 1 , unit 한번 표시
            }
            System.out.println("");
        }
    }
```
```java
    /** Quiz2. count와 unit을 입력받아서
     * 
     * ex) count = 3, unit = A
     * 
     * @param int count
     * @param String unit
     * 
     *   A
     *  A A
     * A   A
     * 
     * 이 문제도 사각형 모양으로 나눠서 하면 좋음.
     * |---|
     * |  A|
     * | A |A
     * |A  | A
     * |---|
     */
    public void showTriEmpty(int count, String unit) {
        int i = 0;
        int j = 0;

        for ( i = 0; i < count; i++) { //줄수
            for ( j = 0; j < count; j++) {//unit이 각 줄에 1번씩만 찍여야함.
                if ( count-i == j+1) { //unit이 슬래시 모양으로만 찍혀야함.
                    System.out.print(unit);
                }
                else { //공백표시
                    System.out.print(" ");
                }
            }
            for ( j = 0; j < i; j++) { //사각형 뒷 부분출력.
                if ( i == j + 1) { // 역슬래시 모양으로 출력해야함.
                    System.out.print(unit);
                } else { // 공백 표시
                    System.out.print(" ");
                }
            }
            System.out.println("");
        }
    }
```
```java
    /** Quiz3. count와 unit을 입력받아서
     * 
     * ex) count = 3, unit = A
     * 
     *   A
     *  A A
     * AAAAA
     * 
     * @param int count
     * @param String unit
     */
    public void showTriEmpty1(int count, String unit) {
        int i = 0;
        int j = 0;

        for ( i = 0; i < count; i++) { 
            for ( j = 0; j < count; j++) {
                if ( count-i == j+1) { //슬래시 모양 출력
                    System.out.print(unit);
                }
                else if ( count - 1 == i) { //맨 아래는 공백대신 unit으로 채움.
                    System.out.print(unit);
                }
                else {
                    System.out.print(" ");
                }
            }
            for ( j = 0; j < i; j++) { //사각형 뒷부분 출력
                if ( i == j + 1) { // 역슬래시 모양 출력
                    System.out.print(unit);
                }
                else if ( count - 1 == i) { //맨 아래는 unit출력
                    System.out.print(unit);
                }
                else {
                    System.out.print(" ");
                }
            }
            System.out.println("");
        }
    }
```
```java
    /** Quiz4. count와 unit을 입력받아서
     * 
     * ex) count = 3, unit = A
     * 
     *   A
     *  AAA
     * AAAAA
     *  AAA
     *   A
     * 
     * @param int count
     * @param String unit
     * 

     //이것도 사각형으로 잘라서 보는 것이 좋다.
     *  |---|---|
     * 1|  A|   |2
     *  | AA|A  |
     *  |AAA|AA |
     *  |---|---|
     *  | AA|A  |
     * 3|  A|   |4
     *  |---|---|
     */
    public void showRhombus(int count, String unit) {
        int i = 0;
        int j = 0;

        for ( i = 0; i < count; i++) { //1, 2번 출력
            for ( j = 0; j < count; j++) { //1번 사각형 출력
                if ( (count-(j+1)) > i) {
                    System.out.print(" ");
                }
                else {
                    System.out.print(unit);
                }
            }
            for ( j = 0; j < i; j++) { //2번 사각형 출력
                System.out.print(unit);
            }
            System.out.println("");
        }

        for ( i = count-1; i > 0; i--) { //3,4 출력
            for ( j = count-1; j > 0; j--) {// 3번 출력
                if ( j < i) {
                    System.out.print(unit);
                }
                else {
                    System.out.print(" ");
                }
            }
            for ( j = 0; j < i; j++) { //4번 출력
                System.out.print(unit);
            }
            System.out.println("");
        }
    }
```
```java
    /** Quiz5. count와 unit을 입력받아서
     * 
     * ex) count = 3, unit = A
     * 
     *   A
     *  A A
     * A A A
     *  AAA
     *   A 
     * 
     * @param int count
     * @param String unit
     * 이것도 위에 처럼 사각형으로 나눠서 생각을 하면 됨.
     */
    public void showRhombus1(int count, String unit) {
        int i = 0;
        int j = 0;

        for ( i = 0; i < count; i++) {
            for ( j = 0; j < count; j++) {
                if ( count-i == j+1 || ((j > (count -i)) && ((j-(count-i))%2 == 1))) {
// count-i == j+1 슬래시 출력 조건문
// ((j > (count -i)) && ((j-(count-i))%2 == 1)) 대각선 내부 출력 조건
// 두가지 모두 동작해야하므로 OR 연산자 적용
                    System.out.print(unit);
                }
                else {
                    System.out.print(" ");
                }
            }
            for ( j = 0; j < i; j++) {
                if ( i == j+1 || ((i > 2) && ((i -j) % 2 == 1))) {
//i == j+1 역슬래시 출력 조건문
//((i > 2) && ((i -j) % 2 == 1)) 역슬래시 내부 출력 조건
// 두가지 모두 동작해야하므로 OR 연산자 적용
                    System.out.print(unit);
                } else {
                    System.out.print(" ");
                }
            }
            System.out.println("");
        }

        for ( i = count-1; i > 0; i--) {
            for ( j = count-1; j > 0; j--) {
                if ( j < i) { //3번째 사각형 출력 조건
                    System.out.print(unit);
                }
                else {
                    System.out.print(" ");
                }
            }
            for ( j = 0; j < i; j++) { //4번째 사각형 출력
                System.out.print(unit);
            }
            System.out.println("");
        }
    }
```
```java
    /** Quiz6. count와 unit을 입력받아서
     * 
     * ex) count = 3, unit = A
     * 
     *   A
     *  A A
     * A   A
     *  A A
     *   A 
     * 
     * @param int count
     * @param String unit
     */
    public void showRhombus2(int count, String unit) {
        int i = 0;
        int j = 0;

        for ( i = 0; i < count; i++) {
            for ( j = 0; j < count; j++) { // 1번 사각형
                if ( count-i == j+1 ) { //슬래시모양 출력
                    System.out.print(unit);
                }
                else {
                    System.out.print(" ");
                }
            }
            for ( j = 0; j < i; j++) { // 2번 사각형
                if ( i == j+1 ) { //역슬래시 모양 출력
                    System.out.print(unit);
                } else {
                    System.out.print(" ");
                }
            }
            System.out.println("");
        }

        for ( i = count-1; i > 0; i--) {
            for ( j = count-1; j > 0; j--) { //3번 사각형 출력
                if ( j == i -1) { //역슬래시 모양출력
                    System.out.print(unit);
                }
                else {
                    System.out.print(" ");
                }
            }
            for ( j = 0; j < i; j++) { //4번 사각형 출력
                if ( j == i-1){//슬래시 모양 출력
                    System.out.print(unit);
                }
                else {
                    System.out.print(" ");
                }
            }
            System.out.println("");
        }
    }
```
```java
    /** Quiz7. count와 unit을 입력받아서
     * 
     * ex) count = 3, unit = A
     * 
     * A   A
     *  A A
     *   A
     *  A A
     * A   A 
     * 
     * @param int count
     * @param String unit
     */
    public void showX(int count, String unit) {
        int i = 0;
        int j = 0;
        for ( i = count; i > 0; i--) { 
            for ( j = count; j > 0; j--) { // 1번 사각형
                if ( j == i) { // 역슬래시 모양 출력
                    System.out.print(unit);
                }
                else {
                    System.out.print(" ");
                }
            }
            for ( j = 1; j < i; j++) { // 2번 사각형
                if ( j == i-1){ // 슬래시 모양 출력
                    System.out.print(unit);
                }
                else {
                    System.out.print(" ");
                }
            }
            System.out.println("");
        }
        for ( i = 1; i < count-1; i++) {
            for ( j = 0; j < count-1; j++) { // 3번 사각형
                if ( count-i == j+1) { // 슬래시 모양 출력
                    System.out.print(unit);
                }
                else {
                    System.out.print(" ");
                }
            }
            for ( j = 0; j <= i; j++) { // 4번 사각형
                if ( i == j) { // 역슬래시 모양 출력
                    System.out.print(unit);
                } 
                else {
                    System.out.print(" ");
                }
            }
            System.out.println("");
        }
    }
```
```java
    /** Quiz8. count와 unit을 입력받아서
     * 
     * ex) count = 3, unit = A
     * 
     * AAAAA
     * A   A
     * A   A
     * A   A
     * AAAAA 
     * 
     * @param int count
     * @param String unit
     * 
     * 이번 문제는 사각형을 2개로 나눠도 되고, 4개로 나눠도 되고 구역도 맘대로 정할수 있으나.
     * 연속성을 위해서 기존 위에 처럼 나눠봄.
     * 
     * |---|--|
     *1|AAA|AA|2
     * |A  | A|
     * |A  | A|
     * |---|--|
     * |A  | A|
     *3|AAA|AA|4
     * |---|--|
     * 
     */
    public void showRectangle(int count, String unit) {
        int i = 0;
        int j = 0;
        for ( i = count; i > 0; i--) {
            for ( j = count; j > 0; j--) { // 1번 사각형
                if ( j == count || i == count) {
    //i == count 첫번째줄의 unit출력하기 위한 조건
    //j == count 나머지 unit 출력하기 위한 조건
    //두가지 경우 모두 출력해야하기 때문에 OR연산자로 묶음.
                    System.out.print(unit);
                }
                else {
                    System.out.print(" ");
                }
            }
            for ( j = 1; j < count; j++) {  // 2번 사각형
                if ( j == count-1 ||  i == count){
    //i == count 첫번째줄의 unit출력하기 위한 조건
    //j == count-1 나머지 unit 출력하기 위한 조건
    //두가지 경우 모두 출력해야하기 때문에 OR연산자로 묶음.
                    System.out.print(unit);
                }
                else {
                    System.out.print(" ");
                }
            }
            System.out.println("");
        }
        for ( i = 0; i < count-1; i++) { 
            for ( j = 0; j < count-1; j++) { // 3번 사각형
                if ( j== 0 || i == count-2) {
    //i == count-2 마지막줄의 unit출력하기 위한 조건
    //j== 0 마지막전줄까지 unit 출력하기 위한 조건
    //두가지 경우 모두 출력해야하기 때문에 OR연산자로 묶음.
                    System.out.print(unit);
                }
                else {
                    System.out.print(" ");
                }
            }
            for ( j = 0; j < count; j++) { // 4번 사각형
                if ( count-1 == j || count-2 == i) {
    //count-2 == i 마지막줄의 unit출력하기 위한 조건
    //count-1 == j 마지막 전줄까지 unit 출력하기 위한 조건
    //두가지 경우 모두 출력해야하기 때문에 OR연산자로 묶음.
                    System.out.print(unit);
                } 
                else {
                    System.out.print(" ");
                }
            }
            System.out.println("");
        }
    }
```
```java
    /** Quiz9. count와 unit을 입력받아서
     * 
     * ex) count = 7, unit = A
     * 
6 0  7   * A      A      A      A      A      A      A
5 6  6   *       A     A     A     A     A     A
4 11 5   *            A    A    A    A    A
3 15 4   *                A   A   A   A
2 18 3   *                   A  A  A
1 20 2   *                     A A
0 21 1   *                      A 
     *  이 문제의 경우 2 구역으로 나누어야 함.
     * 왼쪽에 숫자는 첫번째 열은 unit 사이의 공백갯수, 뒤의 숫자는 문자 찍히기 전까지의 공백갯수이다.
     * 세법째 열은 unit이 출력된 횟수.
     * 해결방법은 먼저 공백갯수를 출력한뒤 문자를 한개씩 찍어보는 것을 먼저해보고
     * A
     *       A
     *            A
     *                A
     *                   A
     *                     A
     *                      A 

     * 완료되면 그 뒤에 표시부분을 구현하는 것이 좋다.
     * 
     * @param int count
     * @param String unit
     */
    public void showWaterworks(int count, String unit) {
        int i = 0; 
        int j = 0;
        int k = 0;

        int space = 0;

        for ( i = 0; i < count ; i++) {
            for ( j = 0; j < space; j++ ) { // 공백 갯수 출력
                System.out.print(" ");
            }

            for ( j = 0; j < count-i; j++) { // unit출력
                System.out.print(unit); // 공백후 최초 unit 출력
                for ( k = 0; k < (count - 1 - i); k++) { // 다음 unit까지 공백 출력
                    System.out.print(" ");
                }
            }
            space = space + count - (i + 1); 
            //space는 각 행의 공백을 찍기 위한 변수
            // 공백의 수가 count가 7인 경우, 0, 6, 11, 15. 18, 20, 21이고, 숫자사이의 차이가 순서대로 6, 5, 4, 3, 2, 1 이므로 전체 count에서 1씩 증가하면서 값을 빼준것을 누적하는 수식.
            System.out.println(" ");
        }
    }
```
```java
    /** Quiz10. count와 unit을 입력받아서
     * 
     * ex) count = 3, unit = A
     * 
21 6     *                      A            A
15 5     *                A                       A   
10 4     *           A                                A 
6  3     *       A                                       A
3  2     *    A                                            A
1  1     *  A                                                A
0  0     * A                                                   A
     * 
     * @param count
     * @param unit
     * 
     * 이문제의 경우도 사각형으로 구역을 나누어서 생각하면 의외의 해결책이 있다.
             * |-----------------------------|-----------------------------|
21 6  7      * |                     A       |       A                 
15 5 13      * |               A             |            A            
10 4 18      * |          A                  |                A        
6  3 22      * |      A                      |                   A     
3  2 25      * |   A                         |                     A   
1  1 27      * | A                           |                       A 
0  0 28      * |A                            |                        A 
         * |----------------------------|----------------------------|
         * 앞열의 숫자는 앞쪽 공백 갯수이고
         * 뒷열의 숫자는 바로 다음열의 문자와의 공백 갯수. 가장 아래열의 경우
         * 밑에 문자가 없으므로 0
*/
    public void showParabola(int count, String unit) {
        int i = 0;
        int j = 0;

        int space1 = (count + 1) * count / 2 - count; //앞공백 출력을 위한 변수
        // 수식은 1~count 까지의 합을 구하는 공식에 count를 뺀 값을 넣음. 이유는 
        // 0부터 count - 1까지  합을 구해야하기 때문.
        int space2 = 0;
        // unit을 출력한뒤 다음 unit 줄력까지의 공백을 계산하기 위한 변수

        for ( i = 0; i < count ; i++) {
            for ( j = 0; j < space1; j++ ) { //공백 출력
                System.out.print(" ");
            }
            System.out.print(unit); //unit 출력
            space2 = space2 + count - i;
            for ( j = 0; j < space2 - 1 ; j++) { //뒷공백 출력
                System.out.print(" ");
            }
            space1 = space1 - (count - i - 1);
            for (j = 0; j < space2 - 1; j++) { //두번째 사각형 앞공백 출력
                System.out.print(" ");
            }

            System.out.println(unit);
        }
```
### 배열
 - 1차원 배열
   - 선언 : {자료형}[] {변수명} = new {자료형}[{배열크기}];
   - 선언 : {자료형} {변수명}[] = new {자료형}[{배열크기}];
   - 두개 다 유효. 취향에 맞게 사용. 
 - 2차원 배열
   - 선언 : {자료형}[][] {변수명} = new {자료형}[{배열크기}][{배열크기}];
   - 선언 : {자료형} {변수명}[][] = new {자료형}[{배열크기}][{배열크기}];
   - 두개 다 유효. 취향에 맞게 사용. 
 - 3차원 배열
   - 선언 : {자료형}[][][] {변수명} = new {자료형}[{배열크기}][{배열크기}][{배열크기}];
   - 선언 : {자료형} {변수명}[][][] = new {자료형}[{배열크기}][{배열크기}][{배열크기}];
   - 두개 다 유효. 취향에 맞게 사용. 

- class, 객체, 인스턴스
	- 개념화된 객체가 코딩된것
	- 설계단계에 대상화될 상태
	- 메모리에 올라간것
	- 공부.
	- 객체 -> 클래스를 만들 대상
	- 클래스 -> 객체를 코딩한것
	- 인스턴스(개체) -> 클래스를 메모리에 올린것.

```java
	/** Quiz1. 숫자 입력2개 받아서 1~앞의 수까지 뒤의 수와 같은 숫자가 몇번 출현하는지 구함.
	 * 배열 사용 안하고 풀것. 기준수는 0~9
	 *   
	 * ex) 입력 : 10000, 기준 수 : 8
	 *   8800 -> 2, 8888 -> 4
	 *   
	 *   방법 -> 임의의 수가 있을때 숫자 구성이 기준수와 같은 것의 갯수를 찾는것이므로
	 *   임의의수를 10으로 나누고 그값과 기준수를 비교
	 *   임의의수가 1자리 숫자가 아니라면 임의의수를 10으로 나눈 몫으로 위의 과정을 반복.
	 *   
	 * @param input
	 * @param cnt
	 */
	public void getCnt(int input, int cnt) {
		int tot = 0;
		
		int idx1 = 0;
		int temp = 0;
		
		for ( idx1 = 1; idx1 <= input; idx1++) { // 1 ~ 입력 수 까지 동작
            int idx2 = 0; 	//자리수 저장 변수
			temp = idx1;	// 과정을 수행할 값을 temp에 넣음.
			if ( temp / 10000 > 0) {	// 숫자가 10000 이상일때
				idx2 = 4;	//자리수 대입
				for ( int i = 0; i <= idx2; i++ ) {	//자리수 만큼 반복 수행
					if ( temp % 10 == cnt) {	//숫자의 1의 자리숫자에서 기준값과 동일한 값인지 판단
						tot = tot + 1;	//같으면 +1
					}
					temp = temp/10;	//숫자 변경
				}
			}
			else if ( temp / 1000 > 0) {	// 숫자가 1000 이상일때
				idx2 = 3;
				for ( int i = 0; i <= idx2; i++ ) {
					if ( temp % 10 == cnt) {
						tot = tot + 1;
					}
					temp = temp/10;
				}
			}
			else if ( temp / 100 > 0) {	// 숫자가 100 이상일때
				idx2 = 2;
				for ( int i = 0; i <= idx2; i++ ) {
					if ( temp % 10 == cnt) {
						tot = tot + 1;
					}
					temp = temp/10;
				}
			}
			else if ( temp / 10 > 0) {	// 숫자가 10 이상일때
				idx2 = 1;
				for ( int i = 0; i <= idx2; i++ ) {
					if ( temp % 10 == cnt) {
						tot = tot + 1;
					}
					temp = temp/10;
				}
			}
			else {	// 숫자가 10 미만일때
				if ( temp % 10 == cnt) {
					tot = tot + 1;
				}
				temp = temp/10;
			}
		}
		System.out.println("갯수는 " + tot);
	}	
```

- ArrayList
 - 리스트 환경의 사이즈 변경이 가능한 배열을 구현한 것.
 - ArrayList의 기본은 Object type
 - 사용을 할 때 import로 불러줘야함.
```java
import java.util.ArrayList;```

 - 선언할 때 제너릭을 해주는 것이 좋음 (제너릭은 type을 지정해주는 것)
```java
ArrayList<String> nameList1 = new ArrayList<String>();
```
 - 상세 정보는 http://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html

- String
 - 문자열 저장.
 - 선언은 아래와 같이.
```java
String str1 = "123123";
```
 - 사용 예
```java
		//1. 문자열 비교.
        System.out.println(str1.compareTo(str1));
		System.out.println(str1.equals(str1));
		
		//2. 문자열 인덱스값
		System.out.println(str1.charAt(2));
		System.out.println(str1.indexOf(str1.charAt(2)));
		
		//3. 문자열 합치기
		System.out.println(str1 + str1);
		
		//4. 시작하는 문자열파악.
		System.out.println(str1.startsWith("12"));
		System.out.println(str1.startsWith("23"));
		
		//5. 끝나는 문자열 파악.
		System.out.println(str1.endsWith("23"));
		System.out.println(str1.endsWith("12"));
		
		//6. 찾고자 하는 문자열 위치. 중복된 경우 앞쪽것만
		System.out.println(str1.indexOf("1"));
		System.out.println(str1.indexOf("4"));
		
		//7. 문자열 길이
		System.out.println(str2.length());
		
		//8. 문자열 변경
		System.out.println(str3.replace("3", "4"));
		
		//9. 문자열 자르기
		System.out.println(str2.substring(3));
		System.out.println(str2.substring(2,4));
		
		//10. 문자열 분리
		String val = "a/b/cdg/a2223/afefes";
		String[] result = val.split("/");
		
		for ( String res : result) {
			System.out.println(res);
		}
		
		//11. 문자열 -> 숫자 변환
		int change1 = Integer.parseInt("111");
		long change2 = Long.parseLong("222");

		System.out.println(change1);
		System.out.println(change2);
        
		//12. 숫자 -> char
		char change3 = Character.forDigit(8,10);
		System.out.println(change3);
        
		//13. 문자열을 한글자씩 char로 분해
		String change4 = "8888";
		char[] array = change4.toCharArray();

		System.out.println(array);
		for (char dp : array) {
			System.out.println(dp);
		}
```

- 퀴즈
```java
	/**	Quiz2. 숫자 입력2개 받아서 1~앞의 수까지 뒤의 수와 같은 숫자가 몇번 출현하는지 구함.
	 * 값은 String으로 입력
	 * 
	 * ex) 입력 : 10000, 기준 수 : 8
	 *   8800 -> 2, 8888 -> 4
	 * 
	 * @param input
	 * @param cnt
	 */
	public void getCnt1(String input, String cnt) {
		int tot = 0;
		int limit = Integer.parseInt(input);	//범위 저장
		
		for ( int idx = 1; idx <= limit; idx++)	{	// 1~input값까지 반복
			String tmp = idx + "";		// 숫자 -> String
			String[] res = tmp.split(""); // 1글자씩 나누기
			for (String str0 : res) {	// 모든 자리수 반복
				if (str0.indexOf(cnt) != -1)	{ // 기준값과 비교
					tot = tot + 1;	// 같으면 +1 추가
				}
			}
		}
		System.out.println("갯수는 " + tot);
		
		tot = 0;
		for ( int idx = 1; idx <= limit; idx++)	{
			String tmp = idx + "";
			String[] res = tmp.split(""); //1글자씩 나누기
			for (String str0 : res) {
				if (str0.equals(cnt))	{	//같은값을 찾는 방법을 equal method 를 사용
					tot = tot + 1;
				}
			}
		}
		System.out.println("갯수는 " + tot);
	}
```

```java
	/**Quiz3 입력값을 뒤집기
	 * 
	 * 입력 = was it a cat i saw? => ?was i tac a ti saw
	 * 
	 * @param input
	 */
	public void getRev(String input) {
		int limit = input.length();		// 입력받은 String 길이
        String[] arr1 = input.split("");	// 입력받은 String 1글자의 문자열로 분리
		char[] arr2 = new char[limit];	// 입력받은 String길이와 같은 char형 배열
		int idx = limit;		// 역순으로 출력받기 위한 기준설정
		for ( String tp : arr1)	{
			idx = idx - 1;		//index값이 limit부터 0까지 변하도록 함.
			arr2[idx] = tp.charAt(0);	// 각 문자열 1번째 글자를 char배열의 뒷쪽부터 넣음.
		}
		System.out.println(arr2);

		char[] arr3 = input.toCharArray();	// 입력받은 String 1글자의 문자로 분리
		for ( idx = limit - 1; idx >= 0; idx--) {
			arr2[limit - idx - 1] = arr3[idx];	// 입력1번째 글자를 char배열의 뒷쪽부터 넣음.
		}
		System.out.println(arr2);
	}
```

```java
	/** Quiz3 = 아나그램
	 * 
	 * abcd = dabc = adbc = acbd = bcad
	 * 
	 * @param input1
	 * @param input2
	 */
	public void getAnagram(String input1, String input2) {
		char[] arr1 = input1.toCharArray();		//for에서 비교하기 위해 char[]로 저장
		char[] arr2 = input2.toCharArray();		//for에서 비교하기 위해 char[]로 저장
		
		int idx = 0;
		int limit = input1.length();	//문자열 길이
		int cnt = 0;
		if (input1.length() != input2.length()) {	//문자열 길이가 다르면 무조건 fail
			System.out.println("다름");
		}
		else {
			for ( idx = 0; idx < limit; idx++) { 
				for ( int idx1 = 0; idx1 < limit; idx1++) {
					if (arr1[idx] == arr2[idx1]) {	//같은 문자가 있는지 확인
						arr2[idx1] = '\n';	//비교된것은 값을 삭제.
						idx1 = limit;	//중복 비교를 줄이기 위해 다음 글자 탐색으로 바로 보냄.
						cnt++;	//글자 비교된 횟수 확인
					}
				}
			}
			if (cnt == limit) {	//글자 탐색한 횟수가 같으면
				System.out.println("같음");
			}
			else {	//다르면.
				System.out.println("다름");
			}
		}
        
		//두 배열을 정렬 한다음.
		//그것을 비교.
        
		arr1 = input1.toCharArray();
		arr2 = input2.toCharArray();
		
		Arrays.sort(arr1);	//정렬
		Arrays.sort(arr2);	//정렬
		System.out.println(arr1.equals(arr2));	//이건 false
		System.out.println(arr1.toString().equals(arr2.toString())); //이것도 false
		System.out.println(input1.equals(input2));	//이것도 false
		
		if ( Arrays.equals(arr1, arr2)) {	//true
			System.out.println("같음");
		}
		else {
			System.out.println("다름");
		}
		String a = "1234321";
		String b = "1234321";
		
		System.out.println(a.equals(b));	//true출력
	}
```

- Class
 - 내부에 Attribute와 Method가 반드시 있어야 하는 것은 아님
 - OOP 개발과정
    - 1 계획 2 분석 3 설계 4 구현 5 Test
    - 설계가 가장 중요
    - 설계원칙 - SOLID
       |약어|상세|정의|
       |---|---|---|
       |SRP| Single Responsibility Principle| 단일책임 <br/>하나의 클래스는 하나의 역할만 맡는다. <br/>높은 응집도와 낮은 결합도를 추구, <br/>1.코드간 영향을 미치지 않도록, <br/>2 각 class 별 test가능|
       |OCP| Open Closed Principle| 개방폐쇄 <br/> 확장에는 열려 있으나 변경에는 닫혀 있어야 한다.|
       |LSP| Liskov substitution Principle| 리스코프교체 상<br/> 프로그램의 정확성을 깨뜨리지 않으면서 하위 타입의 인스턴스로 바꿀 수 있어야 한다|
       |ISP| Interface Segregation Principle| 인터페이스 분리원칙<br/>인터페이스 여러 개가 범용 인터페이스 하나보다 낫다|
       |DIP| Dependency Inversion principle| 의존관계 역전 원칙<br/>부모 클래스가 자식클래스를 의존하면 안된다|

 - method overload
    - 하나의 class에 동일한 이름을 가진 멤버 함수를 만들어 사용
    - 리턴타입이나 접근제한자는 같아도 되지만, 파라미터 개수나 타입은 달라야한다.
 - 접근제한자
  |접근제한자|내용|
  |-|-|
  |defualt|안쓰면 자동으로 인식 <br> 선언한다고 되는 것은 아님. <br> 패키지가 다르면 접근 불가. 같은 패키지 내에서는 접근 가능|
  |private|외부에서 접근 제한 <br> 선언한 class 내에서만 사용가능|
  |public|모든 클래스에서 접근 가능, 같은 패키지 다른 패키지관계없이 접근 가능, 프로젝트가 달라도 접근 가능|
  |protected|은 패키지에 속한 모든 클래스에서  접근이 가능하도록 허용하며 패키지 밖에서도 이 패키지의 클래스를 상속한 하위클래스의 멤버로의 접근이 가능하다. |

 - 상속
    - 아빠 class 로부터 상속받은 아들 class는 아빠 class의 모든 것을 가질수 있다.
    - 상속 방법은 class 아들 extends 아빠 {} 이런식으로 한다.
    - 자바는 단일 상속만 허용.
    - 단 Object는 예외이고 표시 하지 않아도 이미 상속 되어 있음.
    - 자바의 상속은 확장의 의미.그래서 extends라고 사용.\
    - 상속 순서는 아빠 class로드 후 아들 class로드.
    - 아빠 class를 상속받은 아들class는 아빠class의 다양한 형태중 하나.
       - 아빠 aa = new 아들()  이런식으로 선언하는 것이 다형성.
 - interface
    - method 이름만 선언
    - class에서 사용할 때는 implement interface_name  이런식으로 

 - Override
    - ~ 보다 더 중요하다.
    - 상속 받은 클래스에서 같은 method를 재정의 하는 것.
    - 사용할때 @Override라고 표시 해주는 것이 규칙.

 - Overloading 과 Overriding
  ||Overloading|Overriding|
  |--|--|--|
  |매개변수|다름|동일|
  |method type|다름|동일|
  |return|관계없음|동일|
  |접근제한자|관계없음|같거나 커야함|
  
 - static
    - 정적 변수, 정적 method
    - 자세한 내용은 https://wikidocs.net/228

### 게시판 작성
- 파일 저장은 아직 안배웠으니 일시적으로 저장한것처럼 보이기만 하도록 만듦.
- 기본적인 정보는 글번호, 작성자, 제목, 내용, 시간
- 기본적인 기능은 추가, 수정, 삭제, 읽기-특정글만, 읽기- 모두 읽기

- 키보드 입력

```java
public void input1() {
	////scanner 예제	
	Scanner scanner = new Scanner(System.in);
    // 사용을 위해서는 import java.util.Scanner;
	System.out.println("What is your name?"); //이름 입력
	
	String inputvalue = scanner.nextLine();
	
	System.out.println("Your name is : " + inputvalue); //이름 출력
}
```

- 게시판은 글을 여러개 저장해야하고, 글의 정보는 글번호, 작성자, 제목, 내용, 시간
- 따라서 글정보를 저장할 bbs 클래스를 만들고 이것을 제어해줄 bbscontroller 클래스를 생성.

```java
public class Bbs {
	private int bbsNo; //글번호
	private String title;//제목
	private String author;//작성자
	private String datetime;//날짜및 시간
	private String content;//내용
    
    //각 변수에 대한 get함수와 set합수를 만들기
    //eclipse를 사용하고 있다면 함수만들 위치에 커서를 놓고 
    //오른클릭 -> source -> Generate Getter and Setter선택
    // pop되는 것에서 각 변수에 체크하고 확인하면 자동생성됨.
    
    public int getBbsNo() {
		return bbsNo;
	}
	public void setBbsNo(int bbsNo) { //값을 세팅
		this.bbsNo = bbsNo;
	}
}
```

```java
public class BbsController {
	ArrayList<Bbs> database; //게시판의 글을 저장할 변수 선언
	
	public BbsController() {
		database = new ArrayList<Bbs>(); //생성시 instance 생성
	}
	/** 생성 혹은 추가
	 * @param bbs
	 */
	public void create(Bbs bbs) {
		//TODO : 생성
		database.add(bbs);	//ArrayList에 추가.
	}
	
	/** 특정읽기
	 * @param bbsNo
	 * @return
	 */
	public Bbs read(int bbsNo){	// 게시글 번호를 받음
		//TODO : 특정 읽기
		for ( Bbs item : database) { //database의 처음부터 끝까지 읽으면서 item에 값 넣기
			if ( item.getBbsNo() == bbsNo) {	//글번호비교
				return item;	//해당 게시글 전달
			}
		}
		System.out.println("No data...try again");	//게시글번호가 없을때
		return null;
	}
	
	/** 전체읽기
	 * @return
	 */
	public ArrayList<Bbs> readAll(){	//모든 글읽음
		//TODO : 전체읽기
		ArrayList<Bbs> list = new ArrayList<Bbs>();
		list = database;
		return list;
	}

	/** 수정
	 * @param bbs
	 */
	public void update(Bbs bbs) {	//게시글 받음
		//TODO : 수정
		for ( Bbs item : database) {	//모든 글 탐색
			if ( item.getBbsNo() == bbs.getBbsNo()){	//게시글번호로 판별
				item.setBbsNo(bbs.getBbsNo());	//새로운 정보 입력
				item.setTitle(bbs.getTitle());	//새로운 정보 입력
				item.setContent(bbs.getContent());	//새로운 정보 입력
				item.setAuthor(bbs.getAuthor());	//새로운 정보 입력
				item.setDatetime(bbs.getDatetime());	//새로운 정보 입력
			}
		}
	}
	
	/** 삭제
	 * @param bbsNo
	 */
	public void delete(int bbsNo) { //게시글 번호로 탐색
		//TODO : 삭제
		for ( Bbs item : database) {	//모든 글 탐색
			if ( item.getBbsNo() == bbsNo) {	//게시글번호로 판별
				database.remove(item);	//삭제
				break;	//나가기 -> 혹시 모를 게시글 번호 중복으로 다른글 삭제를 방지.
			}
		}
	}
}
```
- 글을 입력 받고 출력할 클래스를 하나더 만들때 거기에 main을 추가.
```java
public static void main(String[] args) {
		MainBbs mainBbs = new MainBbs();
		BbsController control = new BbsController();
        
		//새글 입력
		Bbs bbs1 = new Bbs();
		bbs1.setBbsNo(1);
		bbs1.setTitle("제목있음");
		bbs1.setContent("내용있음");
		bbs1.setAuthor("홍길동");
		bbs1.setDatetime("2017-01-19 11:14:31");
		control.create(bbs1);

		Bbs bbs2 = new Bbs();
		bbs2.setBbsNo(2);
		bbs2.setTitle("제목있음2");
		bbs2.setContent("내용있음2");
		bbs2.setAuthor("유재석");
		bbs2.setDatetime("2017-01-19 14:30:31");
		control.create(bbs2);

		Bbs bbs3 = new Bbs();
		bbs3.setBbsNo(3);
		bbs3.setTitle("제목있음3");
		bbs3.setContent("내용있음3");
		bbs3.setAuthor("하동훈");
		bbs3.setDatetime("2017-01-19 14:35:31");
		control.create(bbs3);
		
		for ( int i = 0; i < 5; i++) {
			Bbs bbs4 = new Bbs();
			bbs4.setBbsNo(4+i);
			bbs4.setTitle("제목있음"+(i+1));
			bbs4.setContent("내용있음" +(i+1));
			bbs4.setAuthor("피톤치즈" + (i+1));
			bbs4.setDatetime("2017-01-19 14:36:" + 10*i);
			control.create(bbs4);
		}
		////총 8개의 게시글 저장.

		ArrayList<Bbs> list = control.readAll();
		for(Bbs item : list) {	//전체 출력
			Print(item);		//게시글을 출력하는것은 method로 구현.
            // 원래는 mainBbs.Print(item) 이지만 method가 static이라 허용됨.
		}

		String command = ""; //키입력 받을 변수

		boolean flag = true;  //반복문을 빠져나가기 위한 flag
		while(flag) {
			print_menu();	//메뉴 호출
			System.out.println("명령어를 입력하세요");	//메시지 출력
			command = scanner.nextLine();	//key입력 대기
			
			if ( command.equals("create")) {	//생성
				create(scanner, control);	//create함수 호출
			}
			else if ( command.equals("remove")) {	//삭제
				remove(scanner, control);	//remove함수 호출
			}
			else if ( command.equals("read")) {	//특정 글 보기
				read(scanner, control);		//read함수 호출
			}
			else if ( command.equals("list")) {	//전체글 보기
				list(control);	//list함수 호출
			}
			else if ( command.equals("exit")) {	//나가기
				flag = false;	//flag를 false로 변경하여 프로그램 종료.
			}
			else	//잘못 입력했을때.
			{
				System.out.println("");
				System.out.println("잘못입력... 재입력");
				System.out.println("");
			}
		}
	}

	// 생성 함수
	public static void create(Scanner scanner, BbsController control) {
		Bbs bbs = new Bbs();	//함수가 호출되면 이 함수 내에서만 사용할 instance 선언
		
		System.out.println("제목을 입력하세요.");		
		bbs.setTitle(scanner.nextLine());	//제목 저장
		
		System.out.println("작성자를 입력하세요.");		
		bbs.setAuthor(scanner.nextLine());	//작성자 저장
		boolean in = true;
		System.out.println("내용을 입력하세요.(입력 완료 : wq)");
		String str = "";
		while (in) {	//내용을 multiline으로 입력
			String temp = scanner.nextLine(); 
			if ( Arrays.equals(temp.toCharArray(), "wq".toCharArray())) { //완료조건과 같으면
				in = false;	//while 종료.
			}else {	//입력받은 문자 임시 저장.
				str = str + temp + "\n ";
			}
		}
		bbs.setContent(str);	//내용 저장
		System.out.println(".....저장완료......");	//저장완료 표시.
		
		bbs.setBbsNo(control.length() + 1);	//글번호저장.
		///////////날짜
		bbs.setDatetime(Util.getDate());	//날짜 저장
        //getDate는 따로 추가 설명.
        
		control.create(bbs);	//Arraylist에 최종 저장.
	}
	
    //삭제 함수
	public static void remove(Scanner scanner, BbsController control) {
		System.out.println("작성자을 입력하세요.");
		int num = control.search(scanner.nextLine());
        //search는 따로 추가설명.
        //작성자를 입력 받아 입력된 값과 동일한 작성자가 있는 글을 찾아 글번호를 return.
		
		if (num == -1) {	//찾는 작성자가 없으면..
			System.out.println("같은 작성자가 없습니다");
		}
		else {
			control.delete(num);	//삭제
		}
	}
	
    //특정글 읽기
	public static void read(Scanner scanner, BbsController control) {
		System.out.println("글번호를 입력하세요.");
		String tStr = "";
		int idx = 2;	//번호를 입력 받지 못했을때 추가 횟수.
		int num = 0;
		
		while(idx > 0) {	//숫자가 아닌 경우 입력 추가를 위함.
			tStr = scanner.nextLine();
			if ( isDigit(tStr) == true) {	//숫자인가?
				num = Integer.parseInt(tStr);	//숫자면 String -> int 변환 후 변수 저장
				idx = -1;	//while 탈출
			}
			else {	//숫자가 아니면..
				System.out.println("숫자를 입력해주세요.");
				idx--;
			}
		}
		if ( idx == -1) {	//숫자 입력을 받았으면...
			Bbs read1 = control.read(num);	//글번호의 게시글 받아오기
			if ( read1 == null)	//글이 없으면...
			{
				System.out.println("입력한 글번호는 없습니다");
			}
			else
			{
				Print(read1);	//있으면 글 출력
			}
		}
		else {	//숫자 입력을 못받았으면...
			System.out.println("사용방법을 확인해주세요.");
		}
	}
	
    //모든 글 출력
	public static void list(BbsController control) {
		ArrayList<Bbs> list1 = control.readAll();
		
		for(Bbs item : list1) {	//처음부터 끝까지 모든글
			Print(item);		//출력
		}
	}
	
    //메뉴 출력 함수
	public static void print_menu() {

		System.out.println("명령어 SET");
		System.out.println("create");
		System.out.println("remove");
		System.out.println("read");
		System.out.println("list");
		System.out.println("exit");
	}
	
    //입력값 숫자 판별.
	public static boolean isDigit(String str)
	{
		char[] arr = str.toCharArray();
		
		int idx = 0;
		int size = arr.length;
		
		for (idx = 0; idx < size; idx++) {
			if ( !(arr[idx] >= '0' && arr[idx] <= '9')) {	//숫자범위 외의  문자가 있으면
				return false;	//false return.
			}
		}
		return true;	//입력값이 모두 숫자이면 true return.
	}

	//출력함수.
	static public void Print(Bbs pr) {
		System.out.println("No. : " + pr.getBbsNo() + ", title : " + pr.getTitle() + 
		", Author : " + pr.getAuthor() + ", Contents : " + pr.getContent() + ", Date&time : " + pr.getDatetime());
	}
```

- search 추가 설명
``` java
	public int search(String str) {	//작성자 전달받음

		for ( Bbs item : database) {	//모든 Arraylist 검색
			char[] tmp1 = str.toCharArray();
			char[] tmp2 = item.getAuthor().toCharArray();
			if ( Arrays.equals(tmp1, tmp2)) {	//전달받은 작성자와 저장된 작성자가 같으면
				return item.getBbsNo();	//게시글 번호 return
			}
		}
		return -1;	//없으면 -1
	}
```

- getDate 추가 설명

```java
	public static String getDate() {	//날짜 출력 함수
		String datetime = "";

		Calendar cal = Calendar.getInstance();	//이게 꼭 필요.
		
		int[] iArr= new int[5];	//년-월-일 시:분:초 중에서 값이 1자리 2자리로 변하는 것은
        //년을 제외한 나머지 5개 .. 그래서 배열 크기가 5
		
		int yy = cal.get(Calendar.YEAR);	//년 4자리 받음
		int mm = cal.get(Calendar.MONTH) + 1;//달은 0부터 시작이라 1 더함.
		int dd = cal.get(Calendar.DATE);	//일 받음
		
//		int ho = cal.get(Calendar.HOUR);//12시간표시로 시간을 숫자로만 표기
		int ho = cal.get(Calendar.HOUR_OF_DAY);	//24시간으로 값 리턴
		int mi = cal.get(Calendar.MINUTE);	//분 받음
		int se = cal.get(Calendar.SECOND);	//초 받음
		
        //배열에 저장
		iArr[0] = mm;
		iArr[1] = dd;
		iArr[2] = ho;
		iArr[3] = mi;
		iArr[4] = se;
		
		datetime = yy +"-";//년을 string으로 저장
		
		int idx = 0;
		for ( idx = 0; idx < 5; idx++) {	//배열 iArr크기만큼 동작
			if ( iArr[idx] < 10) {	//10보다 작으면...
				datetime = datetime + 0;	//String에 0을 추가
			}

			switch(idx) {
			case 0 :	//month
				datetime = datetime + iArr[idx] + "-";
				break;
			case 1 :	//date
				datetime = datetime + iArr[idx] + " ";
				break;
			case 2 :	//hour
				datetime = datetime + iArr[idx] + ":";
				break;
			case 3 :	//minute
				datetime = datetime + iArr[idx] + ":";
				break;
			case 4 :	//second
				datetime = datetime + iArr[idx];
				break;
			}
		}
		return datetime;	//"YYYY-MM-DD hh:mm:ss" 방식으로 저장된 string return
	}
```

- try with (JDK1.7에서 예외처리)
```java
    //기존 사용법
    try {
    }
    catch() {
    }
    final {
    }
    //try with
    try ( ) {
    }
    catch() {
    }
```
    
- string 연산
 - JDK 1.5이상에서는 String a= "aaa" + "bbb";로 처리하면 됨.
 - 반복문에서는 반복적으로 연산할때는 StringBuffer나 StringBuilder로 연산하는 것이 좋다.
 - StringBuffer : https://wikidocs.net/276
 - StringBuilder : https://opentutorials.org/module/1226/8020
- io stream 구성
 - inputStream/outputStream은 모든 것을 입출력 가능
 - reader/writer는 char만 가능.
- NIO package
 - 한글 설명 : http://blog.naver.com/PostView.nhn?blogId=horajjan&logNo=220464906740&parentCategoryNo=&categoryNo=&viewDate=&isShowPopularPosts=false&from=postView
 - https://docs.oracle.com/javase/7/docs/api/java/nio/package-summary.html
 - https://en.wikipedia.org/wiki/Non-blocking_I/O_(Java)
- NIO path 처리(jdk7이상)
 - 경로를 path라는 객체에 담는다.
 - 파일 읽기 쓰기를 위한 메소드 추가


```java
//선언
Path path = Paths.get(directory, filename);

//읽기
byte[] bytes = Files.readAllBytes(path);
String content = new String(bytes, StandardCharsets.UTF_8);
List<String> lines = Files.readAllLines(path);

//쓰기
Files.write(path, content.getBytes(StandardCharsets.UTF_8));
```


* io vs nio
|구분|IO|NIO|
|--|--|--|
|입출력방식|스트림방식|채널방식|
|버퍼 방식|넌버퍼|버퍼|
|비동기 방식|지원안함|지원|
|블로킹/넌블로킹방식|블로킹방식만 지원|블로킹/넌블로킹만 지원|
한글 설명 : http://blog.naver.com/PostView.nhn?blogId=horajjan&logNo=220464906740&parentCategoryNo=&categoryNo=&viewDate=&isShowPopularPosts=false&from=postView

- 파일처리 예(1. 버퍼사용하여 입출력)

```java
	/** 파일 쓰기
	 * 	BufferedWriter 사용하여 저장
	 */
	public void writeFile()	{
		String path = "c:\\input\\test"; //디렉토리 경로
		String fileName = "c:\\input\\test\\test01.txt"; //파일 전체 경로
		
		File dir = new File(path);
		if ( dir.exists()) {	//디렉토리가 없으면...
			//dir.mkdir();	// 마지막 디렉토리만 생성
			dir.mkdirs();	// 경로상의 디렉토리가 없으면 모든 디렉토리 생성
		}
		
		File outFile = new File(fileName);
		if ( outFile.exists()) {	//같은 파일 네임이 있으면..
			System.out.println("같은 파일이 존재");
		}
		else {
        	//try with방법으로 ...
			try ( BufferedWriter bw = new BufferedWriter(new FileWriter(fileName)))	{
				String content = "작성내용";
				bw.write(content);
				bw.flush();
			} catch (IOException e) {
				e.printStackTrace();
			}
		}
	}
	
	/** 파일 읽기
	 * BufferedReader 사용하여 읽기
	 */
	public void readFile()	{
		String path = "c:\\input\\test"; //디렉토리 경로
		String fileName = "c:\\input\\test\\test01.txt"; //파일 전체 경로
		
		File inFile = new File(fileName);
		
		//유효성 체크
		if (inFile.exists()) {	//파일이 있으면
			//tryWith
			try ( BufferedReader br = new BufferedReader(new FileReader(inFile))) {
				String line;
				while( (line = br.readLine()) != null) {
					System.out.println(line);
				}
			} catch (FileNotFoundException e) {
				e.printStackTrace();
			} catch (IOException e) {
				e.printStackTrace();
			}
		} else {	//파일 없으면
			System.out.println("파일 없음");
		}
	}
```

- 파일처리 예(2. stream 사용하여 입출력)

```java
	/** 파일 쓰기
	 * FileOutputStream 사용하여 쓰기
	 */
	public void writeStream()	{
		String path = "c:\\input\\test"; //디렉토리 경로
		String fileName = "c:\\input\\test\\test01.txt"; //파일 전체 경로
		
		File dir = new File(path);
		if ( dir.exists()) {	//디렉토리가 없으면...
			//dir.mkdir();	// 마지막 디렉토리만 생성
			dir.mkdirs();	// 경로상의 디렉토리가 없으면 모든 디렉토리 생성
		}
		
		File outFile = new File(fileName);
		if ( outFile.exists()) {	//같은 파일 네임이 있으면..내용 추가
			try (FileOutputStream fos = new FileOutputStream(fileName, true)) {
				String content = "작성할 내용이 여기임...";
				fos.write(content.getBytes());
			} catch (FileNotFoundException e) {
				e.printStackTrace();
			} catch (IOException e) {
				e.printStackTrace();
			}
		}
		else {	//같은 파일 네임이 없으면..파일 생성
			try (FileOutputStream fos = new FileOutputStream(fileName)) {
				String content = "작성할 내용이 여기임...";
				fos.write(content.getBytes());
			} catch (FileNotFoundException e) {
				e.printStackTrace();
			} catch (IOException e) {
				e.printStackTrace();
			}
		}
	}
	
	/** 파일 읽기 : 1 Line씩 읽기
     *
     */
	public void readStream3() {
		String path = "c:\\input\\test"; //디렉토리 경로
		String fileName = "c:\\input\\test\\test01.txt"; //파일 전체 경로
		
		File file = new File(fileName);
		//파일이 있으면
		if ( file.exists()) {
			try (BufferedReader fis = new BufferedReader(new InputStreamReader(new FileInputStream(fileName), "UTF-8"))) {
			// 파일 인코딩을 지정할때 UTF-8을 쓸것.
				String line;	//file에서 1줄씩 읽어옴
				while((line = fis.readLine()) != null)	{
					System.out.println(line);
				}
			} catch (FileNotFoundException e) {
				e.printStackTrace();
			} catch (IOException e) {
				e.printStackTrace();
			}
		}
		else {
			System.out.println("파일 없음");
		}
	}
    
	/** 파일 읽기 : byte[]의 사이즈 만큼
     *
     */
	public void readStream2() {
		String path = "c:\\input\\test"; //디렉토리 경로
		String fileName = "c:\\input\\test\\test01.txt"; //파일 전체 경로
		File file = new File(fileName);
		
		//파일이 있으면
		if ( file.exists()) {
			try (FileInputStream fis = new FileInputStream(fileName)) {
				byte[] byArr = new byte[10];
				int count = 0;
				//byArr사이즈 만큼 읽어옴.
				while((count = fis.read(byArr)) != -1)	{
					for ( int j = 0; j < count; j++ ) {
						System.out.println((char)byArr[j]); //한글이 안나옴.
					}
				}
			} catch (FileNotFoundException e) {
				e.printStackTrace();
			} catch (IOException e) {
				e.printStackTrace();
			}
		}
		else {
			System.out.println("파일 없음");
		}
	}
    
	/** 파일 읽기 : 1byte씩
     *
     */
	public void readStream1() {
		String path = "c:\\input\\test"; //디렉토리 경로
		String fileName = "c:\\input\\test\\test01.txt"; //파일 전체 경로
		
		File file = new File(fileName);
		
		//파일이 있으면
		if ( file.exists()) {
			try (FileInputStream fis = new FileInputStream(fileName)) {
				int i = -1;
				while((i = fis.read()) != -1)	{ //1byte씩 읽어옴.
					System.out.println((char)i);
				}
			} catch (FileNotFoundException e) {
				e.printStackTrace();
			} catch (IOException e) {
				e.printStackTrace();
			}
		}
		else {
			System.out.println("파일 없음");
		}
	}
```

- 파일처리 예(3. NIO 사용하여 입출력)

```java
	/** 파일 읽기
     *
     */
	public void readNio() {
		String dir = "c:\\input\\test"; //디렉토리 경로
		String fileName = "c:\\input\\test\\test01.txt"; //파일 전체 경로
		Path path = Paths.get(dir, filename);
		
		try {
			byte[] bytes = Files.readAllBytes(path);//파일의 모든 내용
			String content = new String(bytes, StandardCharsets.UTF_8); //인코딩방식 지정
			System.out.println(content);
		} catch (IOException e) {
			e.printStackTrace();
		}
	}
	
	/** 파일 쓰기
     *
     */
	public void writeNio(Bbs data) {
		String dir = "c:\\input\\test"; //디렉토리 경로
		String fileName = "c:\\input\\test\\test01.txt"; //파일 전체 경로
		Path path = Paths.get(dir, filename);
		
		String tmp = "";
		try {
			Files.write(path, tmp.getBytes(StandardCharsets.UTF_8, StandardOpenOption.CREATE,StandardOpenOption.APPEND));//파일을 쓸때 생성하거나 내용추가.
		} catch (IOException e) {
			e.printStackTrace();
		}
	}
```