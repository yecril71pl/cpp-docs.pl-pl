---
title: Literały numeryczne, atrybut typu wartość logiczna i wskaźnika (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- literals, C++
- constants, literals
- literals [C++]
ms.assetid: 17c09fc3-3ad7-47e2-8b48-ba8ae994edc8
ms.openlocfilehash: f263e9a2ed357cdc80ec29fc5d1b6d58c9e093e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545798"
---
# <a name="numeric-boolean-and-pointer-literals--c"></a>Literały numeryczne, atrybut typu wartość logiczna i wskaźnika (C++)

Literał jest element program, który bezpośrednio reprezentuje wartość. W tym artykule opisano literałów typu całkowitego, zmiennoprzecinkowego, wartości logicznych i wskaźników. Dla informacji na temat literały ciągów i znakowe [ciąg znaków i literały znaków (C++)](../cpp/string-and-character-literals-cpp.md). Można również definiować własne literały według dowolnej z tych kategorii; Aby uzyskać więcej informacji, zobacz [literały zdefiniowane przez użytkownika (C++)](../cpp/user-defined-literals-cpp.md)

. Umożliwia literały w wielu kontekstach, ale większość często do inicjowania zmiennych nazwanych i aby przekazać argumenty do funkcji:

```cpp
const int answer = 42; // integer literal
double d = sin(108.87);     //floating point literal passed to sin function
bool b = true;              // boolean literal
MyClass* mc = nullptr;      // pointer literal
```

Czasami jest ważne poinformować kompilator, jak interpretować literału lub jakie określonego typu, aby zapewnić do niego. Można to zrobić, dodając prefiksów lub sufiksów do literału. Na przykład prefiksu 0 x informuje kompilator, aby zinterpretować numer, który po nim następuje jako wartość szesnastkową, na przykład 0x35. Sufiks EŁNY informuje kompilator, aby traktować wartości jako **unsigned long long** typu, tak jak 5894345ULL. Zobacz poniższe sekcje, aby uzyskać pełną listę prefiksów i sufiksów dla każdego typu literału.

## <a name="syntax"></a>Składnia

## <a name="integer-literals"></a>Literały całkowite

Literały całkowite zaczynać się cyfrą i mieć nie części ułamkowych lub wykładników. Możesz określić literały całkowite w formie dziesiętnej, ósemkowej lub szesnastkowej. Mogą one określać typy oznaczone lub nieoznaczone oraz typy long lub short.

Gdy nie prefiksu lub sufiksu jest obecny, kompilator umożliwi typu całkowitego wartości literału **int** (32-bitowy), jeśli wartość mieści się, w przeciwnym razie daje on typ **long long** (64-bitowy).

Aby określić dziesiętny literał typu całkowitego, należy rozpocząć Określanie od cyfry niezerowych. Na przykład:

```cpp
int i = 157;   // Decimal literal
int j = 0198;       // Not a decimal number; erroneous octal literal
int k = 0365;       // Leading zero specifies octal literal, not decimal
int m = 36'000'000  // digit separators make large values more readable
int
```

Aby określić ósemkową literał typu całkowitego, należy rozpocząć Określanie od 0, następuje sekwencja cyfr z zakresu od 0 do 7. Cyfry 8 i 9 są błędy podczas określania ósemkową literału. Na przykład:

```cpp
int i = 0377;   // Octal literal
int j = 0397;        // Error: 9 is not an octal digit
```

Aby określić szesnastkowy literał typu całkowitego, należy rozpocząć Określanie od `0x` lub `0X` (wielkość liter "x" nie ma znaczenia), następuje sekwencja cyfr w zakresie `0` za pośrednictwem `9` i `a` (lub `A`) za pomocą `f` (lub `F`). Cyfry szesnastkowe od `a` (lub `A`) do `f` (lub `F`) reprezentują wartości z zakresu od 10 do 15. Na przykład:

```cpp
int i = 0x3fff;   // Hexadecimal literal
int j = 0X3FFF;        // Equal to i
```

Aby określić typ nieoznaczony, należy użyć `u` lub `U` sufiks. Aby określić typ long, należy użyć `l` lub `L` sufiks. Aby określić 64-bitowy typ całkowity, użyj LL lub ll sufiks. Sufiks i64 nadal są obsługiwane, ale należy unikać, ponieważ zależy od firmy Microsoft i nie jest przenośny. Na przykład:

```cpp
unsigned val_1 = 328u;             // Unsigned value
long val_2 = 0x7FFFFFL;                 // Long value specified
                                        //  as hex literal
unsigned long val_3 = 0776745ul;        // Unsigned long value
auto val_4 = 108LL;                           // signed long long
auto val_4 = 0x8000000000000000ULL << 16;     // unsigned long long
```

**Separatory cyfr**: znak pojedynczego cudzysłowu (apostrof) służy do oddzielania wartości miejsce w większą liczbą, aby były one bardziej czytelne dla człowieka do odczytu. Separatory nie mają wpływu na kompilację.

```cpp
long long i = 24'847'458'121
```

## <a name="floating-point-literals"></a>Literały punktu zmiennoprzecinkowego

Literały zmiennoprzecinkowych określić wartości, które muszą mieć część ułamkową. Wartości te zawierają dziesiętnymi (**.**) i może zawierać wykładników.

Literały zmiennoprzecinkowych mieć "mantysy," który określa wartość numer, "wykładnik,", który określa wielkość liczbą, i opcjonalnie sufiks, który określa typ literału. Mantysy jest określony jako sekwencję cyfr, następuje kropka, a następnie opcjonalnie sekwencję cyfr, reprezentujących część ułamkową liczby. Na przykład:

```cpp
18.46
38.
```

Wykładnik, jeśli jest obecny, określa wielkość numer jako potęga 10, jak pokazano w poniższym przykładzie:

```cpp
18.46e0      // 18.46
18.46e1           // 184.6
```

Wykładnik może być określony przy użyciu `e` lub `E`, które mają takie samo znaczenie, następuje opcjonalny znak (+ lub -) i sekwencję cyfr.  Jeśli wykładnik jest obecny, końcowe punktu dziesiętnego nie jest konieczne w liczbach takich jak `18E0`.

Literały zmiennoprzecinkowych domyślnie wpisz **double**. Za pomocą sufiksy `f` lub `l` (lub `F` lub `L` — sufiks nie uwzględnia wielkości liter), literał może być określony jako **float** lub **typu long double**, odpowiednio.

Mimo że **typu long double** i **double** mają tę samą reprezentację, nie są tego samego typu. Na przykład możesz mogą mieć przeciążone funkcje, takie jak

```cpp
void func( double );
```

and

```cpp
void func( long double );
```

## <a name="boolean-literals"></a>Wartość logiczna literałów

Wartość logiczna literały są **true** i **false**.

## <a name="pointer-literal-c11"></a>Wskaźnik literał (C ++ 11)

Wprowadza C++ [nullptr](../cpp/nullptr.md) literału do określenia wskaźnika inicjowany z wartością zerową. W kodzie przenośnym **nullptr** powinny być używane zamiast typu całkowitego zero lub makra takie jak wartości NULL.

## <a name="binary-literals-c14"></a>Literały binarne (C ++ 14)

Można określić przy użyciu literału binarnego `0B` lub `0b` prefiksu, następuje Sekwencja 1 i 0:

```cpp
auto x = 0B001101 ; // int
auto y = 0b000001 ; // int
```

## <a name="avoid-using-literals-as-magic-constants"></a>Unikaj używania literałów jako "stałe magic"

Można użyć literały bezpośrednio w wyrażeniach i instrukcji, chociaż nie zawsze jest dobrą praktyką programowania:

```cpp
if (num < 100)
    return "Success";
```

W poprzednim przykładzie może być lepiej używać nazwanych stałą, która wywołuje wyczyść znaczenia, na przykład "MAXIMUM_ERROR_THRESHOLD". A jeśli wartość zwracaną, którą "Success" jest widoczny dla użytkowników końcowych, a następnie ją może być lepiej używać stałą ciągu o nazwie, które mogą być przechowywane w jednej lokalizacji w pliku, z którym może być lokalizowana w innych językach. Za pomocą nazwanych stałych pomaga innych użytkowników, a także aby zrozumieć intencje kodu.

## <a name="see-also"></a>Zobacz także

[Konwencje leksykalne](../cpp/lexical-conventions.md)<br/>
[Literały ciągu języka C++](../cpp/string-and-character-literals-cpp.md)<br/>
[Literały zdefiniowane przez użytkownika języka C++](../cpp/user-defined-literals-cpp.md)