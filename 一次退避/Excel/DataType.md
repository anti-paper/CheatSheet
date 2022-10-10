# アセンブリ（MASM32）

EAXの下半分を使うとAX、AXの上半分を使うとAH、AXの下半分を使うとALとなる

レジスタ略称	名前	主な用途	ビット
EAX	Extended Accumulator register	データの一時記憶、各種演算。	32
EBX	Extended Base address register	特定のメモリを指定するポインタ。一時的に値を保存する場所がEAX以外に必要な時にも使う。	32
ECX	Extended Count register	繰り返し処理命令の回数を数えるカウンタ。	32
EDX	Extended Data register	データの一時記憶。EAXと組み合わせて乗除算。	32
ESI	Extended Source register	転送元のデータのメモリアドレスを保存。	32
EDI	Extended Destination register	転送先のデータのメモリアドレスを保存。	32
ESP		スタックポインタのアドレスを保存。	32
EBP		スタックフレームのアドレスを保存。	32
EFLAGS		CPUの状態を表す一連のフラグを保存。	32
AX	Accumulator register	データの一時記憶、各種演算。	16
BX	Base address register	特定のメモリを指定するポインタ。	16
CX	Count register	繰り返し処理命令の回数を数えるカウンタ。	16
DX	Data register	データの一時記憶。AXと組み合わせて乗除算。	16
SI	Source register	転送元のデータのメモリアドレスを保存。	16
DI	Destination register	転送先のデータのメモリアドレスを保存。	16


# MySQL

エスケープシーケンス\

データ型	意味	対応している範囲
INT	右の範囲の整数	-2147483648～2147483647
TINYINT	とても小さな整数	-128～127
SMALLINT	小さな整数	-32768～32767
MEDIUMINT	中くらいの整数	-8388608～8388607
BIGINT	大きい整数	-9223372036854775808～9223372036854775807
FLOAT	単精度浮動小数点数	-3.402823466E+38～-1.175494351E-38
DOUBLE	倍精度浮動小数点数	-2.2250738585072014E-308～-1.7976931348623157E+308
DECIMAL	固定小数点数	DECIMAL（最大桁数,小数点以下桁数）の形式で「最大桁数」は65まで、「小数点以下桁数」は30まで指定可。誤差が生じない。
CHAR	固定長の文字列	255文字まで
VARCHAR	可変長の文字列	1～65532バイト。文字数の上限は利用する文字コードによるが、シフトJISでは255文字
TEXT	長い文字列	65535文字まで
LONGTEXT	とても長い文字列	4294967295文字まで
DATETIME	日付と時刻	1000-01-01 00:00:00～9999-12-31 23:59:59
DATE	日付	1000-01-01～9999-12-31
YEAR	年	1901～2155（4桁のとき） 1970～2069（70～69）（2桁のとき）
TIME	時刻	-838:59:59～838:59:59


# PHP

エスケープシーケンス	\

データ型	意味
integer	整数
float	浮動小数点
double	浮動小数点
string	文字列
boolean	論理値
object	オブジェクト
array	配列
NULL	ヌル（空の値）


# Python

エスケープシーケンス	\

データ型	意味
int	整数リテラル
float	浮動小数点数リテラル
str	文字列リテラル
bool	YesとNoを表す「True」「False」の2つの値を扱う。
