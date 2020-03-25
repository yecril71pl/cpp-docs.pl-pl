---
title: align (C++)
ms.date: 12/17/2018
f1_keywords:
- align_cpp
helpviewer_keywords:
- align __declspec keyword
- __declspec keyword [C++], align
ms.assetid: 9cb63f58-658b-4425-ac47-af8eabfc5878
ms.openlocfilehash: 227053fbfa4190dc6227ba7096a7c76aef30bb54
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181554"
---
# <a name="align-c"></a>align (C++)

W programie Visual Studio 2015 i nowszych należy użyć specyfikatora `alignas` standardowego języka C++ 11 do sterowania wyrównaniem. Aby uzyskać więcej informacji, zobacz [wyrównanie](../cpp/alignment-cpp-declarations.md).

**Specyficzne dla firmy Microsoft**

Użyj `__declspec(align(#))`, aby precyzyjnie kontrolować wyrównanie danych zdefiniowanych przez użytkownika (na przykład statyczne alokacje lub automatyczne dane w funkcji).

## <a name="syntax"></a>Składnia

> **__declspec (align (** *#* **))** *deklarator*

## <a name="remarks"></a>Uwagi

Pisanie aplikacji, które korzystają z najnowszych instrukcji procesora, wprowadza pewne nowe ograniczenia i problemy. W szczególności wiele nowych instrukcji wymaga, aby dane były wyrównane do 16-bajtowych granic. Ponadto poprzez wyrównywanie często używanych danych do rozmiaru linii pamięci podręcznej określonego procesora, można zwiększyć wydajność pamięci podręcznej. Na przykład, jeśli zdefiniujesz strukturę o rozmiarze mniejszym niż 32 bajtów, możesz chcieć dostosować ją do 32 bajtów, aby upewnić się, że obiekty tego typu struktury są efektywnie buforowane.

\# jest wartością wyrównania. Prawidłowe wpisy to liczby całkowite z przedziału od 1 do 8192 (bajty), takie jak 2, 4, 8, 16, 32 lub 64. `declarator` to dane, które są deklarowane jako wyrównane.

Aby uzyskać informacje o sposobach zwracania wartości typu `size_t`, która jest wymaganiem wyrównania typu, zobacz [__alignof](../cpp/alignof-operator.md). Aby uzyskać informacje na temat deklarowania niewyrównanych wskaźników w przypadku procesorów 64-bitowych, zobacz [__unaligned](../cpp/unaligned.md).

`__declspec(align(#))` można użyć podczas definiowania **struktury**, **Unii**lub **klasy**lub podczas deklarowania zmiennej.

Kompilator nie gwarantuje ani nie próbuje zachować atrybutu wyrównania danych podczas operacji kopiowania lub przekształcania danych. Na przykład [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) może skopiować strukturę zadeklarowaną z `__declspec(align(#))` do dowolnej lokalizacji. Należy zauważyć, że zwykłe przydzielenie — na przykład [malloc](../c-runtime-library/reference/malloc.md), C++ [operator new](new-operator-cpp.md)i przydziela Win32 — zwraca pamięć, która zwykle nie jest wyrównana do struktur `__declspec(align(#))` lub tablic struktury. Aby zagwarantować, że miejsce docelowe operacji kopiowania lub przekształcania danych jest prawidłowo wyrównane, użyj [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md)lub napisz własny Alokator.

Nie można określić wyrównania parametrów funkcji. Gdy dane, które mają atrybut wyrównania, są przesyłane przez wartość na stosie, jego wyrównanie jest kontrolowane przez konwencję wywoływania. Jeśli wyrównanie danych jest ważne w wywołanej funkcji, skopiuj parametr do prawidłowo wyrównanej pamięci przed użyciem.

Bez `__declspec(align(#))`, kompilator ogólnie wyrównuje dane z naturalnych granic na podstawie docelowego procesora i rozmiaru danych, maksymalnie 4-bajtowych granic na procesorach 32-bitowych i 8-bajtowych granic w procesorach 64-bitowych. Dane w klasach lub strukturach są wyrównane do klasy lub struktury w minimalnym wyrównaniu naturalnym i bieżące ustawienie pakowania (z #pragma `pack` lub opcji kompilatora `/Zp`).

W tym przykładzie pokazano sposób użycia `__declspec(align(#))`:

```cpp
__declspec(align(32)) struct Str1{
   int a, b, c, d, e;
};
```

Ten typ ma teraz atrybut wyrównania 32-bajtowego. Oznacza to, że wszystkie wystąpienia statyczne i automatyczne zaczynają się na granicy 32-bajtowej. Dodatkowe typy struktury zadeklarowane z tym typem jako element członkowski zachowują atrybut wyrównania tego typu, czyli każda struktura o `Str1` jako element ma atrybut wyrównania co najmniej 32.

Należy pamiętać, że `sizeof(struct Str1)` jest równa 32. Oznacza to, że jeśli zostanie utworzona tablica obiektów str1, a podstawą tablicy jest 32-bajtowe wyrównanie, każdy element członkowski tablicy jest także wyrównany do 32 bajtów. Aby utworzyć tablicę, której baza jest prawidłowo wyrównana w pamięci dynamicznej, użyj [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md)lub napisz własny Alokator.

`sizeof` wartością dla każdej struktury jest przesunięcie końcowego elementu członkowskiego oraz rozmiar tego elementu członkowskiego, zaokrąglony do najbliższej wielokrotności największej wartości wyrównania składowej lub całej wartości wyrównania struktury, w zależności od tego, która jest większa.

Kompilator używa tych reguł do wyrównania struktury:

- O ile nie zostanie zastąpiony `__declspec(align(#))`, wyrównanie elementu członkowskiego struktury skalarnej jest minimum rozmiaru i bieżącego pakowania.

- O ile nie zostanie zastąpiony `__declspec(align(#))`, wyrównanie struktury jest maksymalną wartością wyrównania poszczególnych elementów członkowskich.

- Składowa struktury jest umieszczana na przesunięciu od początku swojej struktury nadrzędnej, która jest najmniejszą wielokrotnością jego wyrównania większą lub równą przesunięciu końca poprzedniego elementu członkowskiego.

- Rozmiar struktury jest najmniejszą wielokrotnością jego wyrównania większą lub równą przesunięciu końca ostatniego elementu członkowskiego.

`__declspec(align(#))` można zwiększyć tylko ograniczenia wyrównania.

Aby uzyskać więcej informacji, zobacz:

- [Wyrównaj przykłady](#vclrfalignexamples)

- [Definiowanie nowych typów z __declspec (align (#))](#vclrf_declspecaligntypedef)

- [Wyrównywanie danych w lokalnym magazynie wątków](#vclrfthreadlocalstorageallocation)

- [Jak wyrównać działanie w przypadku pakowania danych](#vclrfhowalignworkswithdatapacking)

- [Przykłady wyrównania struktury](../build/x64-software-conventions.md#examples-of-structure-alignment) (specyficzne dla architektury x64)

## <a name="align-examples"></a><a name="vclrfalignexamples"></a>Wyrównaj przykłady

W poniższych przykładach pokazano, jak `__declspec(align(#))` wpływa na rozmiar i wyrównanie struktur danych. Przykłady zakładają następujące definicje:

```cpp
#define CACHE_LINE  32
#define CACHE_ALIGN __declspec(align(CACHE_LINE))
```

W tym przykładzie struktura `S1` jest definiowana przy użyciu `__declspec(align(32))`. Wszystkie zastosowania `S1` dla definicji zmiennej lub w innych deklaracjach typów są 32-bajtowo wyrównane. `sizeof(struct S1)` zwraca 32, a `S1` ma 16 bajtów wypełnienia po 16 bajtach wymaganych do przechowywania czterech liczb całkowitych. Każdy element członkowski **int** wymaga wyrównania 4-bajtowego, ale wyrównanie samej struktury jest deklarowane jako 32. W związku z tym ogólne wyrównanie jest 32.

```cpp
struct CACHE_ALIGN S1 { // cache align all instances of S1
   int a, b, c, d;
};
struct S1 s1;   // s1 is 32-byte cache aligned
```

W tym przykładzie `sizeof(struct S2)` zwraca wartość 16, która jest dokładnie sumą rozmiarów elementów członkowskich, ponieważ jest to wielokrotność największego wymagania wyrównania (wielokrotność liczby 8).

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

W tym przykładzie należy zauważyć, że `a` ma wyrównanie jego typu naturalnego, w tym przypadku 4 bajty. Jednak `S1` muszą być wyrównane do 32-bajtowe. Dwadzieścia osiem bajtów wypełnienia następuje `a`, dzięki czemu `s1` zaczyna się od przesunięcia 32. `S4` następnie dziedziczy wymaganie wyrównania `S1`, ponieważ jest to największe wymaganie wyrównania w strukturze. `sizeof(struct S4)` zwraca 64.

```cpp
struct S4 {
   int a;
   // 28 bytes padding
    struct S1 s1;      // S4 inherits cache alignment requirement of S1
};
```

Poniższe trzy deklaracje zmiennych używają również `__declspec(align(#))`. W każdym przypadku zmienna musi być 32-bajtowo wyrównane. W przypadku tablicy, adres podstawowy tablicy, a nie każdy element członkowski tablicy, to 32-bajty wyrównane. W przypadku użycia `__declspec(align(#))`nie ma to żadnego oddziaływania na `sizeof` wartość dla każdego elementu członkowskiego tablicy.

```cpp
CACHE_ALIGN int i;
CACHE_ALIGN int array[128];
CACHE_ALIGN struct s2 s;
```

Aby wyrównać każdy element członkowski tablicy, należy użyć kodu takiego jak:

```cpp
typedef CACHE_ALIGN struct { int a; } S5;
S5 array[10];
```

W tym przykładzie należy zauważyć, że wyrównanie samej struktury i wyrównywanie pierwszego elementu ma ten sam skutek:

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

W tym przykładzie wyrównanie adresów początkowych a, b, c i d jest odpowiednio 4, 1, 4 i 1.

```cpp
void fn() {
   int a;
   char b;
   long c;
   char d[10]
}
```

Wyrównanie w przypadku przydzielenia pamięci na stercie zależy od tego, która funkcja alokacji jest wywoływana.  Na przykład, jeśli używasz `malloc`, wynik zależy od rozmiaru operandu. Jeśli *arg* > = 8, zwracana pamięć to 8-bajtowe wyrównanie. Jeśli *arg* < 8, wyrównanie zwróconej pamięci jest pierwszą potęgą wynoszącą 2 mniej niż *ARG*. Jeśli na przykład używasz opcji malloc (7), wyrównanie wynosi 4 bajty.

## <a name="defining-new-types-with-__declspecalign"></a><a name="vclrf_declspecaligntypedef"></a>Definiowanie nowych typów z __declspec (align (#))

Można zdefiniować typ z cechą wyrównania.

Na przykład można zdefiniować `struct` z wartością wyrównania w następujący sposób:

```cpp
struct aType {int a; int b;};
typedef __declspec(align(32)) struct aType bType;
```

Teraz `aType` i `bType` mają ten sam rozmiar (8 bajtów), ale zmienne typu `bType` są wyrównane do 32 bajtów.

## <a name="aligning-data-in-thread-local-storage"></a><a name="vclrfthreadlocalstorageallocation"></a>Wyrównywanie danych w lokalnym magazynie wątków

Statyczny Magazyn wątków (TLS) utworzony przy użyciu atrybutu `__declspec(thread)` i umieszczony w sekcji TLS w obrazie działa do wyrównania dokładnie taki sam jak normalne dane statyczne. Aby można było utworzyć dane protokołu TLS, system operacyjny przydziela pamięć rozmiar sekcji TLS i uwzględnia atrybut wyrównania sekcji TLS.

W tym przykładzie przedstawiono różne sposoby umieszczania wyrównanych danych do lokalnego magazynu wątków.

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

## <a name="how-align-works-with-data-packing"></a><a name="vclrfhowalignworkswithdatapacking"></a>Jak wyrównać działanie w przypadku pakowania danych

Opcja kompilatora `/Zp` i `pack` pragma mają wpływ na dane pakowania dla elementów członkowskich struktury i Unii. Ten przykład pokazuje, jak `/Zp` i `__declspec(align(#))` współdziałać:

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

Poniższa tabela zawiera informacje o przesunięciu każdego elementu członkowskiego w ramach różnych wartości `/Zp` (lub #pragma `pack`), które pokazują, jak te dwa współpracują.

|Zmienna|/Zp1|/Zp2|/Zp4|/Zp8|
|--------------|-----------|-----------|-----------|-----------|
|a|0|0|0|0|
|b|1|2|2|2|
|c|3|4|4|8|
|d.|32|32|32|32|
|e|40|40|40|40|
|f|41|42|44|48|
|sizeof (S)|64|64|64|64|

Aby uzyskać więcej informacji, zobacz [/ZP (wyrównanie składowej struktury)](../build/reference/zp-struct-member-alignment.md).

Przesunięcie obiektu jest oparte na przesunięciu poprzedniego obiektu i bieżące ustawienie pakowania, chyba że obiekt ma atrybut `__declspec(align(#))`, w takim przypadku wyrównanie jest oparte na przesunięciu poprzedniego obiektu i wartości `__declspec(align(#))` dla obiektu.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[__declspec](../cpp/declspec.md)<br/>
[Przegląd konwencji ABI ARM](../build/overview-of-arm-abi-conventions.md)<br/>
[Konwencje kodowania x64](../build/x64-software-conventions.md)
