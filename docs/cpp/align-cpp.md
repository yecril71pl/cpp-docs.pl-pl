---
title: Dopasuj (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: align_cpp
dev_langs: C++
helpviewer_keywords:
- align __declspec keyword
- __declspec keyword [C++], align
ms.assetid: 9cb63f58-658b-4425-ac47-af8eabfc5878
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7872e01516ea7420533cccf0398164d50603dded
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="align-c"></a>align (C++)
W programie Visual Studio 2015 lub nowszego oraz używać języka C ++ 11 standard `alignas` specyfikator do kontroli nad położeniem. Aby uzyskać więcej informacji, zobacz [wyrównanie](../cpp/alignment-cpp-declarations.md).  
  
 **Dotyczące firmy Microsoft**  
  
 Użyj `__declspec(align(#))` do precyzyjne sterowanie wyrównania danych zdefiniowane przez użytkownika (na przykład statycznych alokacji lub danych w funkcji).  
  
## <a name="syntax"></a>Składnia  
  
```  
__declspec( align( # ) ) declarator  
```  
  
## <a name="remarks"></a>Uwagi  
 Pisanie aplikacji, które korzystają z najnowszej instrukcjami procesora wprowadza pewne problemy i nowych ograniczeń. W szczególności wiele nowych instrukcji wymagają, że dane muszą być wyrównane do 16-bajtowych granicach. Ponadto dzięki wyrównaniu często używanych danych do rozmiaru wiersza pamięci podręcznej konkretny procesor, możesz zwiększyć wydajność pamięci podręcznej. Na przykład w przypadku definiowania struktury, którego rozmiar jest mniejszy niż 32 bajtów, może być dostosowanie go do 32 bajtów, aby upewnić się, że obiekty tego typu struktury wydajne są buforowane.  
  
 \#jest to wartość wyrównania. Prawidłowymi wpisami są potęgami liczby całkowitej liczby dwa z zakresu od 1 do 8192 (w bajtach), na przykład 2, 4, 8, 16, 32 lub 64. `declarator`to dane, które są deklarowanie jako wyrównane.  
  
 Informacje na temat zwracać wartość typu `size_t` to wymaganie wyrównania typu, zobacz [__alignof](../cpp/alignof-operator.md). Informacje o sposobie deklarowanie niewyrównany wskaźników, gdy 64-bitowych procesorach, zobacz [__unaligned](../cpp/unaligned.md).  
  
 Można użyć `__declspec(align(#))` podczas definiowania `struct`, `union`, lub `class`, lub gdy zadeklarować zmiennej.  
  
 Kompilator gwarancji lub nie próbuj utrwalać atrybut wyrównania danych podczas kopiowania lub danych operacji przekształcania. Na przykład [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) można skopiować struktury zadeklarowana z `__declspec(align(#))` do dowolnej lokalizacji. Należy pamiętać, że zwykłych allocators — — na przykład [— funkcja malloc](../c-runtime-library/reference/malloc.md), C++ [nowy operator](new-operator-cpp.md)i allocators — Win32 — zwraca pamięci, która zazwyczaj nie jest wystarczająco wyrównany do `__declspec(align(#))` struktury lub tablic struktury. Aby zagwarantować, że docelowy operacji kopiowania lub danych przekształcania jest ustawione poprawnie, należy użyć [_aligned_malloc —](../c-runtime-library/reference/aligned-malloc.md), lub napisać własny przydzielania.  
  
 Nie można określić wyrównanie parametrów funkcji. Gdy dane, które ma atrybut wyrównania jest przekazywany przez wartość na stosie, jego wyrównania jest kontrolowana przez Konwencję wywołania. Jeśli wyrównanie danych odgrywa ważną rolę w wywołana funkcja, skopiuj parametr do pamięci prawidłowo ustawione przed użyciem.  
  
 Bez `__declspec(align(#))`, Visual C++ powoduje wyrównanie danych na fizyczną granic na podstawie procesora docelowych i rozmiar danych, maksymalnie 4-bajtowych granicach na 32-bitowych procesorach i 8-bajtowych granicach na 64-bitowych procesorach. Dane klasy lub struktury jest wyrównywany w klasy lub struktury co najmniej naturalnego wyrównania elementu i bieżące ustawienie opakowania (z #pragma `pack` lub **/Zp** — opcja kompilatora).  
  
 W tym przykładzie przedstawiono użycie `__declspec(align(#))`:  
  
```  
__declspec(align(32)) struct Str1{  
   int a, b, c, d, e;  
};  
```  
  
 Ten typ ma teraz atrybut wyrównania 32 bajtów. Oznacza to, że wszystkie wystąpienia statyczne i automatyczne uruchomić w 32-bajtowe granice. Typy struktur dodatkowe zadeklarowana z tego typu jako element członkowski zachować atrybut wyrównania tego typu, oznacza to, że wszelkie struktury z `Str1` jako element ma atrybut wyrównania przynajmniej 32.  
  
 Należy pamiętać, że `sizeof(struct Str1)` jest równa 32. Oznacza to, że jeśli jest tworzona jest Tablica obiektów Str1 i podstawowa tablicy jest 32-bajtowych wyrównane, każdy element członkowski tablicy jest również 32-bajtowych wyrównane. Aby utworzyć tablicę, którego podstawowy jest ustawione poprawnie w pamięci dynamicznej, użyj [_aligned_malloc —](../c-runtime-library/reference/aligned-malloc.md), lub napisać własny przydzielania.  
  
 `sizeof` Wartość dla dowolnej struktury jest przesunięcie końcowe elementu członkowskiego plus rozmiar tego członka, zaokrąglona w górę do najbliższej wielokrotności największą wartość wyrównania elementu członkowskiego lub wartość wyrównania całej struktury, w zależności od jest większy.  
  
 Kompilator używa tych reguł dla wyrównania struktury:  
  
-   Jeśli zastępowany `__declspec(align(#))`, minimalnym jego rozmiar i bieżącego dokumentu jest wyrównanie członka struktury skalarne.  
  
-   Jeśli zastępowany `__declspec(align(#))`, Wyrównanie struktury jest maksymalnie wyrównanie poszczególnych jego członków.  
  
-   Element członkowski struktury jest umieszczana po przesunięcie od początku jego struktury nadrzędnej, która jest najmniejsza wielokrotnością wyrównania większa lub równa przesunięcia końca poprzedni element członkowski.  
  
-   Rozmiar struktury jest najmniejsza wielokrotnością wyrównania większa lub równa przesunięcia końca jego ostatniego członka.  
  
 `__declspec(align(#))`tylko zwiększyć liczbę ograniczeń wyrównania.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Dopasuj przykłady](#vclrfalignexamples)  
  
-   [Definiowanie nowych typów z __declspec(align(#))](#vclrf_declspecaligntypedef)  
  
-   [Wyrównywanie danych w lokalny magazyn wątków](#vclrfthreadlocalstorageallocation)  
  
-   [Jak wyrównać współpracuje z danych dokumentu](#vclrfhowalignworkswithdatapacking)  
  
-   [Przykłady wyrównania struktury](../build/examples-of-structure-alignment.md) (x64 określonych)  
  
##  <a name="vclrfalignexamples"></a>Dopasuj przykłady  
 W poniższych przykładach pokazano sposób `__declspec(align(#))` wpływa na rozmiar i wyrównanie struktur danych. Przykłady Załóżmy następujące definicje:  
  
```  
#define CACHE_LINE  32  
#define CACHE_ALIGN __declspec(align(CACHE_LINE))  
```  
  
 W tym przykładzie `S1` struktura jest definiowana za pomocą `__declspec(align(32))`. Wszystkie zastosowania `S1` dla definicji zmiennej lub innego typu deklaracje są wyrównane do 32 bajtów. `sizeof(struct S1)`Zwraca 32, i `S1` ma 16 bajtów uzupełnienia po 16 bajtów do przeprowadzenia czterech liczb całkowitych. Każdy `int` wyrównanie 4-bajtowych wymaga elementu członkowskiego, ale wyrównania struktury sam został zadeklarowany jako 32. W związku z tym ogólnego wyrównania to 32.  
  
```  
struct CACHE_ALIGN S1 { // cache align all instances of S1  
   int a, b, c, d;  
};  
struct S1 s1;   // s1 is 32-byte cache aligned  
```  
  
 W tym przykładzie `sizeof(struct S2)` Zwraca 16, które to dokładnie suma rozmiarów elementu członkowskiego, ponieważ jest to wiele największego zapotrzebowania wyrównanie (wielokrotnością liczby 8).  
  
```  
__declspec(align(8)) struct S2 {  
   int a, b, c, d;  
};  
```  
  
 W poniższym przykładzie `sizeof(struct S3)` zwraca 64.  
  
```  
struct S3 {  
   struct S1 s1;   // S3 inherits cache alignment requirement  
                  // from S1 declaration  
   int a;         // a is now cache aligned because of s1  
                  // 28 bytes of trailing padding  
};  
```  
  
 W tym przykładzie należy zauważyć, że `a` ma wyrównanie jego fizyczną typu, w tym przypadku 4 bajty. Jednak `S1` muszą być 32-bajtowych wyrównane. Dwudziestu ośmiu bajtów wypełniania wykonaj `a`, dzięki czemu `s1` rozpoczyna się od przesunięcia 32. `S4`następnie dziedziczy wymóg wyrównanie `S1`, ponieważ jest on największego zapotrzebowania wyrównania w strukturze. `sizeof(struct S4)`Zwraca 64.  
  
```  
struct S4 {  
   int a;  
   // 28 bytes padding  
    struct S1 s1;      // S4 inherits cache alignment requirement of S1  
};  
```  
  
 Następujące trzy deklaracje zmiennej również użyć `__declspec(align(#))`. W każdym przypadku zmiennej musi być wyrównany 32-bajtowych. W przypadku tablicy adres podstawowy tablicy nie każdego elementu członkowskiego tablicy jest 32-bajtowych wyrównane. `sizeof` Wartość dla każdego elementu członkowskiego tablicy nie ma wpływu, korzystając z `__declspec(align(#))`.  
  
```  
CACHE_ALIGN int i;  
CACHE_ALIGN int array[128];  
CACHE_ALIGN struct s2 s;  
```  
  
 Aby wyrównać każdy element członkowski tablicy, można użyć kodu, takich jak ta:  
  
```  
typedef CACHE_ALIGN struct { int a; } S5;  
S5 array[10];  
```  
  
 W tym przykładzie należy zauważyć, że wyrównywanie struktury sam i wyrównywanie pierwszym elementem mają ten sam efekt:  
  
```  
CACHE_ALIGN struct S6 {  
   int a;  
   int b;  
};  
  
struct S7 {  
   CACHE_ALIGN int a;  
               int b;  
};  
```  
  
 `S6`i `S7` mają identyczne wyrównania, alokacji i rozmiar właściwości.  
  
 W tym przykładzie adresy wyrównanie początkową, b, c, a d są odpowiednio 4, 1, 4 i 1.  
  
```  
void fn() {   
   int a;  
   char b;  
   long c;  
   char d[10]  
}   
```  
  
 Wyrównanie, gdy jest przydzielana pamięć na stercie zależy od tego, których alokacji funkcja jest wywoływana.  Na przykład, jeśli używasz `malloc`, wynik zależy od rozmiaru argument. Jeśli *arg* > = 8, pamięć zwracane jest wyrównany 8 bajtów. Jeśli *arg* < 8, wyrównanie pamięci, zwracany jest pierwszy potęgą liczby 2 mniej niż *arg*. Na przykład jeśli używasz malloc(7) wyrównanie jest 4 bajty.  
  
##  <a name="vclrf_declspecaligntypedef"></a>Definiowanie nowych typów z __declspec(align(#))  
 Można określić typ z charakterystyki wyrównania.  
  
 Na przykład można zdefiniować `struct` z wyrównaniem wartość w ten sposób:  
  
```  
struct aType {int a; int b;};  
typedef __declspec(align(32)) struct aType bType;  
```  
  
 Teraz `aType` i `bType` są tego samego rozmiaru (8 bajtów), ale zmiennych typu `bType` zostaną porównane 32 bajtów.  
  
##  <a name="vclrfthreadlocalstorageallocation"></a>Wyrównywanie danych w lokalny magazyn wątków  
 Statyczne lokalny magazyn wątków (TLS) utworzone za pomocą `__declspec(thread)` atrybutu i umieszcza w sekcji TLS works obrazu dla wyrównania, tak samo jak normalne danych statycznych. Aby utworzyć dane TLS, system operacyjny przydziela pamięć rozmiar sekcji TLS i szanuje atrybut wyrównania sekcji TLS.  
  
 Ten przykład przedstawia różne sposoby umieszczenia danych wyrównany w lokalny magazyn wątków.  
  
```  
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
  
##  <a name="vclrfhowalignworkswithdatapacking"></a>Jak wyrównać współpracuje z danych dokumentu  
 **/Zp** — opcja kompilatora i `pack` pragma obowiązują pakowania danych elementy członkowskie struktury i Unii. W tym przykładzie pokazano sposób **/Zp** i `__declspec(align(#))` współpracują ze sobą:  
  
```  
struct S {  
   char a;  
   short b;  
   double c;  
   CACHE_ALIGN double d;  
   char e;  
   double f;  
};  
```  
  
 W poniższej tabeli wymieniono przesunięcie każdy element członkowski w różnych **/Zp** (lub #pragma `pack`) wartości przedstawiający interakcje między nimi.  
  
|Zmienna|/ Zp1|/ Zp2|/ Zp4|/ Zp8|  
|--------------|-----------|-----------|-----------|-----------|  
|A|0|0|0|0|  
|B|1|2|2|2|  
|c|3|4|4|8|  
|d|32|32|32|32|  
|e|40|40|40|40|  
|F|41|42|44|48|  
|sizeof (S)|64|64|64|64|  
  
 Aby uzyskać więcej informacji, zobacz [/Zp (wyrównanie członka struktury)](../build/reference/zp-struct-member-alignment.md).  
  
 Przesunięcie obiektu jest oparta na przesunięcie poprzedni obiekt i bieżące ustawienie pakowania, chyba że obiekt ma `__declspec(align(#))` atrybutów, w którym to przypadku wyrównanie opiera się na przesunięcie poprzedni obiekt i `__declspec(align(#))` wartość dla obiekt.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__declspec](../cpp/declspec.md)   
 [Przegląd Konwencji ABI ARM](../build/overview-of-arm-abi-conventions.md)   
 [Omówienie x64 Konwencje wywoływania](../build/overview-of-x64-calling-conventions.md)
