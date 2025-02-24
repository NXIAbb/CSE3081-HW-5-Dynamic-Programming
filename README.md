Download Link :https://programming.engineering/product/cse3081-hw-5-dynamic-programming/


# CSE3081-HW-5-Dynamic-Programming
CSE3081 HW 5: Dynamic Programming
마감: 11월 23일 수요일 오후 8시 정각 (이후 제출자에 대해서 LATE 감점적용)

제출물 및 제출방법: 조교가 사이버 캠퍼스의 과목게시판에 공지할 예정임.

목표: (1) 알고리즘 설계기법 중의하나인 Dynamic Programming 방법에 대한이해도를 높이도록 한다.

주어진문제로부터 재귀적인 구조를유추하고, 이를 테이블을사용하여 계산하는 과정에 대하여연 습하여 본다.

1. 다음 글을읽은 후 아래에 기술하는 gapped alignment 문제를 풀어보자 (출처: Wikipedia).

In bioinformatics, a sequence alignment is a way of arranging the sequences of DNA, RNA, or protein to identify regions of similarity that may be a consequence of functional, structural, or evolutionary relationships between the sequences. Aligned sequences of nu-cleotide or amino acid residues are typically represented as rows within a matrix. Gaps are inserted between the residues so that identical or similar characters are aligned in successive columns.

두개의 문자열 (string)에 대해임의로 indel이라고 하는 gap –을 적절히 삽입할 수 있으나, 그러한 삽입을가급적 방지하기 위하여 매번 -p점 만큼의감점을부과한다. 만약 indel이아닌두 대응되는 문자가 일치하면 s점 만큼의 점수를, 아닐 경우 -f점 만큼의 감점을 부과한다. 만약 s = 2, f = 1, p = 2라고가정할 경우, X = ATCGGATCT와 Y = ACGGACT에 대해 X = ATCGGAT-CT와 Y = A-C-GG-ACT와같이 gap이삽입되었다면 전체 유사성 점수는 1점, 그리고 X = ATCGGATCT와 Y = A-CGG-ACT와같이 gap이삽입되었다면 전체 유사성 점수는 7점이 된다.

이제 임의로 주어진문자열 X = x1x2 · · · xm과 Y = y1y2 · · · yn에 대하여, O(mn) 시간복잡도를 가지는 dynamic programming 알고리즘을사용하여, 전체 유사성 점수를 최대로해주는 gap 삽입

방법을 출력해주는프로그램을작성하여 보자. 여러분의프로그램은다음과같은입출력요구사 항을만족해야 한다.

입력 형식

프로그램이수행되면 이름이 input.txt인텍스트 파일에서 다음과같은형식으로 저장되어 있 는정보를읽어 들여야 한다.

twostrings.bin

s f p

서강대학교 공과대학 컴퓨터공학과

(2/4)

이파일의첫번째줄에는두문자열데이터를저장하고있는텍스트파일의이름이저장되어있다. 이파일에는이진 형식 (binary format)으로데이터가 저장되어 있는데, 첫 4 바이트에는 X의길이 m, 그리고 다음 4 바이트에는 Y 의 길이 n이 각각 int 타입으로 저장이 되어 있고, 다음 m 바이트 에는 X가, 그리고 그 다음 n 바이트에는 Y 가 char 타입으로 저장이 되어있다. 다음 세 개의 양의 정수 s, f, p가 (의미는 분명) int 타입으로 저장되어 있다.

출력 형식

프로그램 수행후 이름이 output.txt인텍스트 파일에 다음과같은방식으로계산결과를출력 하라.

1

10

1

8

3

2

4

7

여기서 첫줄에는자신이 구한 최대 전체유사성 점수, 두 번째줄에는 gap을 포함한 전체문자열의 길이가저장이 되어야 한다. 다음 X에 삽입된 gap의 개수와그 개수 만큼 gap이삽입된 위치를 저장되어야 하며, 그 다음마찬가지로 Y 에 대한 gap 정보가 저장되어야 한다.

회문(回文)이란 ‘madam’이나 ‘소주만병만주소’ 처럼앞에서부터읽으나 뒤에서부터읽으나 동 일한단어나구를뜻한다. 이문제에서는‘0’, ‘1’, ‘2’, ···, ‘9’ 등10개의문자로구성된 문자열을생각하자. 임의의 문자열은 몇개의 회문으로 구성되어 있다고 할 수있는데 (한 개의 문 자로 구성된 문자열은그 자체가회문임),

예를 들어, ‘37352259889’의 경우,

‘373’ + ‘5225’ + ‘9889’,

‘373’ + ‘5’ + ‘22’ + ‘5’ + ‘9889’,

‘3’ + ‘7’ + ‘3’ + ‘5225’ + ‘9’ + ‘8’ + ‘8’ + ‘9’

등과같이 회문으로 구성되어 있다고 할 수 있다.

지금 임의로 주어진문자열 X = x1x2 · · · xn을 dynamic programming 기법을사용하여 최소 개 수의 회문으로 나누어 주는프로그램을작성하여 보자. 여러분의프로그램은다음과같은입출력

요구사항을만족해야 한다.

입력 형식

입력데이터는이름이 input.txt인텍스트 파일에 저장되어 있다. 첫 째줄에는입력 문자열의 개수가주어져 있고, 다음 그 개수만큼 각문자열의 길이와문자열 쌍이 순서대로저장되어 있다.

2

11

37352259889

14

57134317562326

– [CS3081(2반): 알고리즘 설계와분석] HW2: Dynamic Programming 연습 (2022년 11월 9일) –
