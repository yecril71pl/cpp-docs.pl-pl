---
title: align (C++)
ms.date: 12/17/2018
f1_keywords:
- align_cpp
helpviewer_keywords:
- align __declspec keyword
- __declspec keyword [C++], align
ms.assetid: 9cb63f58-658b-4425-ac47-af8eabfc5878
ms.openlocfilehash: 1bfe6e7a4646be8cea622078b4d85f20f458e1c5
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627335"
---
# <a name="align-c"></a>align (C++)

W programie Visual Studio 2015 i nowszych, należy użyć standard C ++ 11 `alignas` specyfikator do kontroli nad położeniem kontrolki. Aby uzyskać więcej informacji, zobacz [wyrównanie](../cpp/alignment-cpp-declarations.md).

**Microsoft Specific**

Użyj `__declspec(align(#))` Aby precyzyjnie kontrolować wyrównanie danych zdefiniowane przez użytkownika (np. statycznych alokacji lub danych automatycznych w funkcji).

## <a name="syntax"></a>Składnia

> **__declspec (Wyrównaj (** *#* **))** *deklaratora*

## <a name="remarks"></a>Uwagi

Pisania aplikacji wykorzystujących najnowsze instrukcje procesora wprowadza pewne nowe ograniczenia i problemy. W szczególności wiele nowych instrukcji wymaga, że dane muszą być dostosowane do 16-bajtowych granicach. Dodatkowo wyrównując często używane dane do rozmiaru wiersza pamięci podręcznej określonemu procesorowi, zwiększasz wydajność pamięci podręcznej. Na przykład jeśli zdefiniujesz strukturę, której rozmiar jest mniejszy niż 32 bajty, możesz dostosować ją do 32 bajtów, aby upewnić się, że efektywne buforowania obiektów tego typu struktury.

\# jest wartością wyrównania. Prawidłowe wartości to potęgi liczb z zakresu od 1 do 8192 (bitów), takie jak 2, 4, 8, 16, 32 lub 64 całkowitych. `declarator` są to dane, które użytkownik deklaruje jako wyrównane.

Aby uzyskać informacje dotyczące sposobu zwracania wartości typu `size_t` to wymóg wyrównania tego typu, zobacz [__alignof](../cpp/alignof-operator.md). Aby uzyskać informacji na temat sposobu deklarowania wskaźników nierównoległych przeznaczonych dla 64-bitowe procesory, zobacz [__unaligned](../cpp/unaligned.md).

Możesz użyć `__declspec(align(#))` podczas definiowania **struktury**, **Unii**, lub **klasy**, lub kiedy Deklarujesz zmienną.

Kompilator nie gwarantuje lub próba zachowują atrybut wyrównania danych podczas kopiowania lub danych operacji przekształcania. Na przykład [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) można skopiować struktury zadeklarowane za pomocą `__declspec(align(#))` do dowolnej lokalizacji. Należy pamiętać, że zwykłych buforów — na przykład [— funkcja malloc](../c-runtime-library/reference/malloc.md), C++ [nowy operator](new-operator-cpp.md)i alokatory Win32 — zwracają pamięć, która jest zwykle nie wystarczająco wyrównywana do `__declspec(align(#))` lub tablic struktury. Aby zagwarantować, że miejsce docelowe kopiowania lub danych operacji przekształcania są ustawione poprawnie, należy użyć [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md), lub Zapisz swój własny alokator.

Nie można określić wyrównania dla parametrów funkcji. W przypadku danych, który ma atrybut wyrównania jest przekazywany przez wartość na stosie, jego wyrównania jest kontrolowana przez Konwencję wywoływania. Jeśli wyrównanie danych jest ważne dla wywołanej funkcji, skopiuj parametr do pamięci prawidłowo wyrównane przed użyciem.

Bez `__declspec(align(#))`, kompilator ogólnie Wyrównuje dane na naturalnych uwzględniając procesor docelowy i rozmiar danych, maksymalnie 4-bajtowych granicach na 32-bitowe procesory i 8-bajtowych granicach na 64-bitowych procesorach. Dane klasach lub strukturach są wyrównane w klasie lub strukturze co najmniej do ich naturalnego wyrównania i bieżące ustawienia pakietów (z #pragma `pack` lub `/Zp` — opcja kompilatora).

W tym przykładzie pokazano użycie `__declspec(align(#))`:

```cpp
__declspec(align(32)) struct Str1{
   int a, b, c, d, e;
};
```

Ten typ posiada obecnie 32-bitowy atrybut dopasowania. Oznacza to, że wszystkie wystąpienia statycznego i automatyczne Uruchom na 32-bitowej granicy. Dodatkowe typy struktury zadeklarowane z tym typem jako członkiem zachowują atrybut wyrównania tego typu, to znaczy jakakolwiek struktura `Str1` jako element ma atrybut wyrównania co najmniej 32.

Należy pamiętać, że `sizeof(struct Str1)` jest równa 32. Oznacza to, że jeżeli Tablica obiektów Str1 jest tworzona i podstawa tablicy jest 32 bajtowa wyrównane, każdy element członkowski tablicy jest również 32-bajty. Aby utworzyć tablicę, której baza jest prawidłowo wyrównany w pamięci dynamicznej, należy użyć [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md), lub Zapisz swój własny alokator.

`sizeof` Wartość dla każdej struktury to przesunięcie ostatniego elementu członkowskiego, plus rozmiar tego elementu, zaokrąglony do najbliższej wielokrotności największą wartość wyrównanie elementu członkowskiego lub wartości wyrównania całej struktury, która kwota jest większa.

Kompilator używa tych reguł Wyrównanie struktury:

- O ile nie zostanie zastąpiona zestawem `__declspec(align(#))`, wyrównanie elementu członkowskiego struktury skalarnej to minimum jego rozmiaru i bieżące opakowanie.

- O ile nie zostanie zastąpiona zestawem `__declspec(align(#))`, Wyrównanie struktury to maksimum indywidualnych wyrównań jego członków.

- Element członkowski struktury jest umieszczany na przesunięcie od początku jego nadrzędnej struktury, który jest najmniejszą wielokrotnością jego wyrównania, większa niż lub równe przesunięcia do końca poprzedniego elemenut Członkowskiego.

- Rozmiar struktury jest najmniejszą wielokrotnością jego wyrównania, większa lub równa przesunięciu końca jej ostatniego elementu członkowskiego.

`__declspec(align(#))` mogą jedynie podnieść ograniczenia wyrównania.

Aby uzyskać więcej informacji, zobacz:

- [Wyrównaj przykłady](#vclrfalignexamples)

- [Definiowanie nowych typów z __declspec(align(#))](#vclrf_declspecaligntypedef)

- [Wyrównywanie danych w pamięci lokalnej wątku](#vclrfthreadlocalstorageallocation)

- [Jak dopasować pakowania danych](#vclrfhowalignworkswithdatapacking)

- [Przykłady wyrównania struktury](../build/x64-software-conventions.md#examples-of-structure-alignment) — x64 określonych 64

## <a name="vclrfalignexamples"></a> Wyrównaj przykłady

W poniższych przykładach pokazano sposób `__declspec(align(#))` wpływa na rozmiar i wyrównanie struktur danych. W przykładach założono następujące definicje:

```cpp
#define CACHE_LINE  32
#define CACHE_ALIGN __declspec(align(CACHE_LINE))
```

W tym przykładzie `S1` struktura jest zdefiniowana za pomocą `__declspec(align(32))`. Wszystkie przypadki użycia `S1` dla definicji zmiennej lub innego typu deklaracje są wyrównane do 32 bajtów. `sizeof(struct S1)` Zwraca 32, i `S1` posiada 16 bajtów uzupełniających po 16 bajtach wymaganych do przechowywania czterech liczb całkowitych. Każdy **int** członek wymaga wyrównania 4-bajtowego, ale wyrównanie samej struktury zostało zadeklarowane jako 32. W związku z tym Wyrównanie ogólne wynosi 32.

```cpp
struct CACHE_ALIGN S1 { // cache align all instances of S1
   int a, b, c, d;
};
struct S1 s1;   // s1 is 32-byte cache aligned
```

W tym przykładzie `sizeof(struct S2)` Zwraca 16, co jest dokładnie sumę rozmiarów elementu członkowskiego, ponieważ jest to wielokrotność największego wymogu wyrównania (wielokrotność liczby 8).

```cpp
__declspec(align(8)) struct S2 {
   int a, b, c, d;
};
```

W poniższym przykładzie `sizeof(struct S3)` zwraca 64.

```cpp
struct S3 {
   struct S1 s1;   // S3 inherits cache alignment requirement
                  // from S1 declaration
   int a;         // a is now cache aligned because of s1
                  // 28 bytes of trailing padding
};
```

W tym przykładzie należy zauważyć, że `a` ma wyrównanie jego typu naturalnego, w tym przypadku 4 bajty. Jednak `S1` musi być z 32 bajtami. Dwadzieścia osiem bitów zabezpieczenia `a`, dzięki czemu `s1` zaczyna się z przesunięciem 32. `S4` następnie dziedziczy wymóg wyrównania `S1`, ponieważ jest to największy wymóg wyrównania w strukturze. `sizeof(struct S4)` Zwraca 64.

```cpp
struct S4 {
   int a;
   // 28 bytes padding
    struct S1 s1;      // S4 inherits cache alignment requirement of S1
};
```

Poniższe trzy deklaracje zmiennych korzystają także `__declspec(align(#))`. W każdym przypadku zmienna musi być 32-bajty. W przypadku tablicy adres bazowy tablicy, a nie każdego elementu członkowskiego tablicy jest 32-bajty. `sizeof` Wartość dla każdego elementu członkowskiego tablicy nie ma wpływu, gdy używasz `__declspec(align(#))`.

```cpp
CACHE_ALIGN int i;
CACHE_ALIGN int array[128];
CACHE_ALIGN struct s2 s;
```

Aby wyrównać każdy element członkowski na tablicy, należy użyć kodu takiego jak to:

```cpp
typedef CACHE_ALIGN struct { int a; } S5;
S5 array[10];
```

W tym przykładzie należy zauważyć, że wyrównywanie samej struktury i wyrównywanie pierwszego elementu mają ten sam efekt:

```cpp
CACHE_ALIGN struct S6 {
   int a;
   int b;
};

struct S7 {
   CACHE_ALIGN int a;
               int b;
};
```

`S6` i `S7` mają identyczne wyrównanie, alokację i charakterystykę rozmiaru.

W tym przykładzie adresy wyrównanie początkowych z, b, c i d wynosi odpowiednio 4, 1, 4 i 1.

```cpp
void fn() {
   int a;
   char b;
   long c;
   char d[10]
}
```

Wyrównanie, jeśli pamięć została przydzielona na stosie, zależy od tego, która funkcja alokacji jest wywoływana.  Na przykład, jeśli używasz `malloc`, wynik zależy od wielkości operandu. Jeśli *arg* > = 8, pamięć, zwracany jest wyrównany 8 bajtów. Jeśli *arg* < 8, wyrównanie pamięci, zwracany jest pierwszy potęgą liczby 2 mniej niż *arg*. Na przykład jeśli korzystasz z malloc(7), wyrównanie wynosi 4 bajty.

## <a name="vclrf_declspecaligntypedef"></a> Definiowanie nowych typów z __declspec(align(#))

Można zdefiniować typ za pomocą właściwości wyrównania.

Na przykład można zdefiniować `struct` z wyrównaniem wartości w ten sposób:

```cpp
struct aType {int a; int b;};
typedef __declspec(align(32)) struct aType bType;
```

Teraz `aType` i `bType` są samej wielkości (8 bajtów), ale zmienne typu `bType` są wyrównane do 32 bajtów.

## <a name="vclrfthreadlocalstorageallocation"></a> Wyrównywanie danych w pamięci lokalnej wątku

Statyczne lokalny magazyn wątków (TLS) utworzone za pomocą `__declspec(thread)` atrybutu i umieścić w sekcji TLS w obrazie działa w przypadku wyrównania dokładnie tak samo jak normalne dane statyczne. Aby utworzyć dane TLS, system operacyjny przydziela pamięć rozmiarze sekcji TLS i uwzględnia atrybut wyrównania sekcji TLS.

Ten przykład pokazuje różne sposoby umieszczania wyrównanych danych w pamięci lokalnej wątku.

```cpp
// put an aligned integer in TLS
__declspec(thread) __declspec(align(32)) int a;

// define an aligned structure and put a variable of the struct type
// into TLS
__declspec(thread) __declspec(align(32)) struct F1 { int a; int b; } a;

// create an aligned structure
struct CACHE_ALIGN S9 {
   int a;
   int b;
};
// put a variable of the structure type into TLS
__declspec(thread) struct S9 a;
```

## <a name="vclrfhowalignworkswithdatapacking"></a> Jak dopasować pakowania danych

`/Zp` — Opcja kompilatora i `pack` pragma zapewniają efekt pakowania danych dla członków struktur i związków. Ten przykład pokazuje, jak `/Zp` i `__declspec(align(#))` współpracują ze sobą:

```cpp
struct S {
   char a;
   short b;
   double c;
   CACHE_ALIGN double d;
   char e;
   double f;
};
```

W poniższej tabeli wymieniono przesunięcie każdego członka w różnych `/Zp` (lub #pragma `pack`) wartości, pokazujący, jak dwa oddziałują ze sobą.

|Zmienna|/Zp1|/Zp2|/Zp4|/Zp8|
|--------------|-----------|-----------|-----------|-----------|
|a|0|0|0|0|
|b|1|2|2|2|
|c|3|4|4|8|
|d|32|32|32|32|
|e|40|40|40|40|
|f|41|42|44|48|
|sizeof (S)|64|64|64|64|

Aby uzyskać więcej informacji, zobacz [/ZP (wyrównanie członka struktury)](../build/reference/zp-struct-member-alignment.md).

Przesunięcie obiektu bazuje na przesunięciu poprzedniego obiektu i bieżącemu ustawieniu pakowania, chyba że obiekt ma `__declspec(align(#))` atrybut, w którym to przypadku dopasowanie bazuje na przesunięciu poprzedniego obiektu i `__declspec(align(#))` dla tego obiektu.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[__declspec](../cpp/declspec.md)<br/>
[Przegląd konwencji ABI ARM](../build/overview-of-arm-abi-conventions.md)<br/>
[x64 konwencje kodowania](../build/x64-software-conventions.md)