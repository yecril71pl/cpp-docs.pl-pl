---
title: Literały numeryczne, wartości logicznych iC++wskaźników ()
ms.date: 11/04/2016
helpviewer_keywords:
- literals, C++
- constants, literals
- literals [C++]
ms.assetid: 17c09fc3-3ad7-47e2-8b48-ba8ae994edc8
ms.openlocfilehash: 467300501ffbbf8063e203d4c7395af34a954ed0
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301369"
---
# <a name="numeric-boolean-and-pointer-literals"></a>Literały numeryczne, wartości logicznych i wskaźników

Literał to element programu, który bezpośrednio reprezentuje wartość. W tym artykule opisano literały typu Integer, zmiennoprzecinkowego, wartości logicznej i wskaźnika. Aby uzyskać informacje o literałach ciągów i znakach, zobacz [literały ciągów iC++znaków ()](../cpp/string-and-character-literals-cpp.md). Można także definiować własne literały na podstawie dowolnej z tych kategorii; Aby uzyskać więcej informacji, zobacz [literały zdefiniowane przezC++użytkownika ()](../cpp/user-defined-literals-cpp.md)

. Literałów można używać w wielu kontekstach, ale najczęściej do inicjowania nazwanych zmiennych i przekazywania argumentów do funkcji:

```cpp
const int answer = 42; // integer literal
double d = sin(108.87);     //floating point literal passed to sin function
bool b = true;              // boolean literal
MyClass* mc = nullptr;      // pointer literal
```

Czasami ważne jest, aby poinformować kompilator, jak interpretuje literał lub jaki konkretny typ ma udzielić. Można to zrobić przez dołączenie prefiksów lub sufiksów do literału. Na przykład prefiks 0x instruuje kompilator, aby interpretuje liczbę, która następuje po niej jako wartość szesnastkową, na przykład 0x35. Sufiks EŁNA instruuje kompilator, aby traktował wartość jako **unsigned long long** Type, jak w 5894345ULL. Zapoznaj się z następującymi sekcjami, aby uzyskać pełną listę prefiksów i sufiksów dla każdego typu literału.

## <a name="integer-literals"></a>Literały całkowite

Literały całkowite zaczynają się cyfrą i nie mają części ułamkowych ani wykładników. Literały całkowite można określić w postaci dziesiętnej, ósemkowej lub szesnastkowej. Mogą one określać typy oznaczone lub nieoznaczone oraz typy long lub short.

Gdy nie ma żadnego prefiksu lub sufiksu, kompilator poda całkowitą wartość literału typ **int** (32 bitów), jeśli wartość będzie pasować, w przeciwnym razie będzie mieć typ **long long** (64 bitów).

Aby określić dziesiętny literał całkowity, Rozpocznij specyfikację z cyfrą różną od zera. Na przykład:

```cpp
int i = 157;   // Decimal literal
int j = 0198;       // Not a decimal number; erroneous octal literal
int k = 0365;       // Leading zero specifies octal literal, not decimal
int m = 36'000'000  // digit separators make large values more readable
int
```

Aby określić literał całkowity w postaci ósemkowej, Rozpocznij specyfikację 0, a następnie sekwencję cyfr z zakresu od 0 do 7. Cyfry 8 i 9 są błędami określającymi literał ósemkowy. Na przykład:

```cpp
int i = 0377;   // Octal literal
int j = 0397;        // Error: 9 is not an octal digit
```

Aby określić szesnastkowy literał całkowity, Rozpocznij specyfikację z `0x` lub `0X` (przypadek "x" nie ma znaczenia), po którym następuje sekwencja cyfr w zakresie `0` przez `9` i `a` (lub `A`) przez `f` (lub `F`). Cyfry szesnastkowe od `a` (lub `A`) do `f` (lub `F`) reprezentują wartości z zakresu od 10 do 15. Na przykład:

```cpp
int i = 0x3fff;   // Hexadecimal literal
int j = 0X3FFF;        // Equal to i
```

Aby określić typ bez znaku, użyj sufiksu `u` lub `U`. Aby określić typ długi, użyj sufiksu `l` lub `L`. Aby określić 64-bitowy typ całkowity, użyj sufiksu LL lub LL. Sufiks I64 jest nadal obsługiwany, ale należy go unikać, ponieważ jest on specyficzny dla firmy Microsoft i nie jest przenośny. Na przykład:

```cpp
unsigned val_1 = 328u;             // Unsigned value
long val_2 = 0x7FFFFFL;                 // Long value specified
                                        //  as hex literal
unsigned long val_3 = 0776745ul;        // Unsigned long value
auto val_4 = 108LL;                           // signed long long
auto val_4 = 0x8000000000000000ULL << 16;     // unsigned long long
```

**Separatory cyfr**: można użyć znaku pojedynczego cudzysłowu (apostrof) do oddzielenia wartości umieszczanych w większych numerach, aby ułatwić ich odczytywanie. Separatory nie mają wpływu na kompilację.

```cpp
long long i = 24'847'458'121
```

## <a name="floating-point-literals"></a>Literały zmiennoprzecinkowe

Literały zmiennoprzecinkowe określają wartości, które muszą mieć część ułamkową. Te wartości zawierają Separatory dziesiętne ( **.** ) i mogą zawierać wykładniki.

Literały zmiennoprzecinkowe mają "mantysy", który określa wartość liczby, "wykładnik", która określa wielkość liczby oraz opcjonalny sufiks, który określa typ literału. Mantysy jest określony jako sekwencja cyfr, po których następuje kropka, po której następuje opcjonalna sekwencja cyfr reprezentująca część ułamkową liczby. Na przykład:

```cpp
18.46
38.
```

Wykładnik, jeśli jest obecny, określa wielkość liczby jako potęgi 10, jak pokazano w następującym przykładzie:

```cpp
18.46e0      // 18.46
18.46e1           // 184.6
```

Wykładnik może być określony przy użyciu `e` lub `E`, który ma takie samo znaczenie, po którym następuje znak opcjonalny (+ lub-) i sekwencja cyfr.  W przypadku obecności wykładnika, końcowy punkt dziesiętny jest zbędny w liczbie całkowitej, takiej jak `18E0`.

Literały zmiennoprzecinkowe domyślnie są typu **Double**. Przy użyciu sufiksów `f` lub `l` (lub `F` lub `L` — sufiks nie jest rozróżniana wielkość liter), literał może być określony odpowiednio jako **float** lub **Long Double**.

Chociaż **Long Double** i **Double** mają tę samą reprezentację, nie są tego samego typu. Na przykład można mieć przeciążone funkcje, takie jak

```cpp
void func( double );
```

and

```cpp
void func( long double );
```

## <a name="boolean-literals"></a>Literały logiczne

Literały logiczne to **true** i **false**.

## <a name="pointer-literal-c11"></a>Literał wskaźnika (C++ 11)

C++wprowadza literał [nullptr](../cpp/nullptr.md) , aby określić wskaźnik zainicjowany przez zero. W kodzie przenośnym należy używać **nullptr** zamiast typu całkowitego zero lub makr, takich jak null.

## <a name="binary-literals-c14"></a>Literały binarne (C++ 14)

Literał binarny może być określony przy użyciu prefiksu `0B` lub `0b`, po którym następuje sekwencja 1 i 0:

```cpp
auto x = 0B001101 ; // int
auto y = 0b000001 ; // int
```

## <a name="avoid-using-literals-as-magic-constants"></a>Unikaj używania literałów jako "stałych"

Literałów można używać bezpośrednio w wyrażeniach i instrukcjach, chociaż nie zawsze jest dobrym sposobem programowania:

```cpp
if (num < 100)
    return "Success";
```

W poprzednim przykładzie lepszym rozwiązaniem jest użycie nazwanej stałej, która daje jasne znaczenie, na przykład "MAXIMUM_ERROR_THRESHOLD". A jeśli wartość zwracana "powodzenie" jest widoczna dla użytkowników końcowych, warto lepiej użyć nazwanej stałej ciągu, która może być przechowywana w jednej lokalizacji w pliku, z której można ją lokalizować w innych językach. Używanie nazwanych stałych pomaga innym, a także sobie zrozumieć intencję kodu.

## <a name="see-also"></a>Zobacz także

[Konwencje leksykalne](../cpp/lexical-conventions.md)<br/>
[C++Literały ciągu](../cpp/string-and-character-literals-cpp.md)<br/>
[C++Literały zdefiniowane przez użytkownika](../cpp/user-defined-literals-cpp.md)