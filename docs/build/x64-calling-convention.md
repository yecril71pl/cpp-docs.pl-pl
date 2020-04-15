---
title: Konwencja wywoływania x64
description: Szczegóły domyślnej konwencji wywoływania ABI x64.
ms.date: 12/17/2018
ms.assetid: 41ca3554-b2e3-4868-9a84-f1b46e6e21d9
ms.openlocfilehash: caf22172ea5e9c20280bce8e508d72fd30c00c5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335130"
---
# <a name="x64-calling-convention"></a>Konwencja wywoływania x64

W tej sekcji opisano standardowe procesy i konwencje, które jedna funkcja (wywołujący) używa do wywołania innej funkcji (wywoływany) w kodzie x64.

## <a name="calling-convention-defaults"></a>Domyślne ustawienia konwencji wywoływania

Interfejs binarny aplikacji x64 (ABI) domyślnie używa czteroestrowej konwencji szybkiego wywoływania. Miejsce jest przydzielane na stosie wywołań jako magazyn cieni dla wywoływanych, aby zapisać te rejestry. Istnieje ścisła korespondencja jeden do jednego między argumentami do wywołania funkcji i rejestrów używanych dla tych argumentów. Każdy argument, który nie mieści się w 8 bajtów lub nie jest 1, 2, 4 lub 8 bajtów, musi być przekazywany przez odwołanie. Pojedynczy argument nigdy nie jest rozłożony na wiele rejestrów. Stos rejestru x87 jest nieużywane i mogą być używane przez wywoływanego, ale muszą być uważane za lotne w wywołaniach funkcji. Wszystkie operacje zmiennoprzecinowe są wykonywane przy użyciu 16 rejestrów XMM. Argumenty liczby całkowitej są przekazywane w rejestrach RCX, RDX, R8 i R9. Argumenty zmiennoprzecinowe są przekazywane w xmm0l, XMM1L, XMM2L i XMM3L. Argumenty 16-bajtowe są przekazywane przez odwołanie. Przekazywanie parametrów jest szczegółowo opisane w [parametr przekazywaniu](#parameter-passing). Oprócz tych rejestrów, RAX, R10, R11, XMM4 i XMM5 są uważane za lotne. Wszystkie inne rejestry nie są zmienne. Użycie rejestru jest szczegółowo udokumentowane w [rejestrze użycia](../build/x64-software-conventions.md#register-usage) i [caller / callee zapisane rejestry](#callercallee-saved-registers).

W przypadku funkcji prototypowych wszystkie argumenty są konwertowane na typy wywoływane oczekiwane przed przekazaniem. Wywołujący jest odpowiedzialny za przydzielanie miejsca dla parametrów do wywoływane i zawsze musi przydzielić wystarczającą ilość miejsca do przechowywania czterech parametrów rejestru, nawet jeśli wywoływany nie przyjmuje tak wielu parametrów. Ta konwencja upraszcza obsługę nieprototyped funkcji języka C i vararg C/C++ funkcje. W przypadku funkcji vararg lub nieprototyped wszelkie wartości zmiennoprzecinkowe muszą być duplikowane w odpowiednim rejestrze ogólnego przeznaczenia. Wszystkie parametry poza pierwsze cztery muszą być przechowywane na stosie po magazynie cienia przed wywołaniem. Szczegóły funkcji Vararg można znaleźć w [Varargs](#varargs). Informacje o funkcji nieprototyped jest szczegółowo w [funkcji nieprototyped](#unprototyped-functions).

## <a name="alignment"></a>Wyrównanie

Większość struktur jest wyrównana do ich naturalnego wyrównania. Wyjątkiem podstawowym są wskaźnik stosu i `malloc` lub `alloca` pamięci, które są wyrównane do 16 bajtów w celu uzyskania wydajności. Wyrównanie powyżej 16 bajtów musi być wykonane ręcznie, ale ponieważ 16 bajtów jest typowym rozmiarem wyrównania dla operacji XMM, ta wartość powinna działać dla większości kodu. Aby uzyskać więcej informacji na temat układu struktury i wyrównania, zobacz [Typy i Magazyn](../build/x64-software-conventions.md#types-and-storage). Aby uzyskać informacje na temat układu stosu, zobacz [użycie stosu x64](../build/stack-usage.md).

## <a name="unwindability"></a>Odwijanie

Funkcje liścia są funkcje, które nie zmieniają żadnych rejestrów nieulotnych. Funkcja nieskrzydłowa może zmienić nieulotny RSP, na przykład wywołując funkcję lub przydzielając dodatkowe miejsce na stos dla zmiennych lokalnych. Aby odzyskać rejestry nieulotne, gdy wyjątek jest obsługiwany, funkcje nie-liść musi być adnotated z danymi statycznymi, który opisuje, jak prawidłowo odwinąć funkcję w dowolnej instrukcji. Dane te są przechowywane jako *pdata*lub dane procedury, co z kolei odnosi się do *xdata*, dane obsługi wyjątków. Xdata zawiera informacje o odwijaniu i może wskazywać na dodatkowe pdata lub funkcję obsługi wyjątków. Prologi i epilogi są bardzo ograniczone, dzięki czemu można je prawidłowo opisać w xdata. Wskaźnik stosu musi być wyrównany do 16 bajtów w dowolnym regionie kodu, który nie jest częścią epilogu lub prologu, z wyjątkiem funkcji liścia. Funkcje liści można rozwiać po prostu symulując powrót, więc pdata i xdata nie są wymagane. Aby uzyskać szczegółowe informacje na temat prawidłowej struktury prologów funkcji i epilogów, zobacz [x64 prolog i epilog](../build/prolog-and-epilog.md). Aby uzyskać więcej informacji na temat obsługi wyjątków oraz obsługi wyjątków i odwijania pdata i xdata, zobacz [obsługę wyjątków x64](../build/exception-handling-x64.md).

## <a name="parameter-passing"></a>Przekazywanie parametrów

Pierwsze cztery argumenty całkowite są przekazywane w rejestrach. Wartości całkowite są przekazywane w kolejności od lewej do prawej odpowiednio w RCX, RDX, R8 i R9. Argumenty pięć i wyższe są przekazywane na stosie. Wszystkie argumenty są prawouprawnie uzasadnione w rejestrach, więc wywoływany może ignorować górne bity rejestru i uzyskać dostęp tylko do części rejestru niezbędne.

Wszelkie argumenty zmiennoprzecinowe i podwójnej precyzji w pierwszych czterech parametrach są przekazywane w XMM0 - XMM3, w zależności od położenia. Liczba całkowita rejestruje RCX, RDX, R8 i R9, które normalnie byłyby używane dla tych pozycji są ignorowane, z wyjątkiem argumentów varargs. Aby uzyskać szczegółowe informacje, zobacz [Varargs](#varargs). Podobnie rejestry XMM0 - XMM3 są ignorowane, gdy odpowiedni argument jest typem liczby całkowitej lub wskaźnika.

[__m128](../cpp/m128.md) typy, tablice i ciągi nigdy nie są przekazywane przez natychmiastową wartość. Zamiast tego wskaźnik jest przekazywany do pamięci przydzielonej przez wywołującego. Struktury i złącza o rozmiarze 8, 16, 32 lub 64 bitów i typach __m64 są przekazywane tak, jakby były liczbami całkowitymi o tym samym rozmiarze. Struktury lub złącza innych rozmiarów są przekazywane jako wskaźnik do pamięci przydzielonej przez wywołującego. Dla tych typów agregacji \_przekazywane jako wskaźnik, w tym _m128, pamięci tymczasowej przydzielonej przez wywołującego musi być wyrównane 16 bajtów.

Wewnętrzne funkcje, które nie przydzielają miejsca na stosie i nie wywołują innych funkcji, czasami używają innych rejestrów lotnych do przekazywania dodatkowych argumentów rejestru. Ta optymalizacja jest możliwa dzięki ścisłemu wiązaniu między kompilatorem a implementacją funkcji wewnętrznych.

Wywoływany jest odpowiedzialny za wyrzucenie parametrów rejestru do ich przestrzeni cienia, jeśli to konieczne.

W poniższej tabeli podsumowano sposób przekazywania parametrów:

|Typ parametru|Jak minęło|
|--------------------|----------------|
|Liczba zmiennoprzecinkowa|Pierwsze 4 parametry - XMM0 do XMM3. Inne przekazywane na stosie.|
|Liczba całkowita|Pierwsze 4 parametry - RCX, RDX, R8, R9. Inne przekazywane na stosie.|
|Agregaty (8, 16, 32 lub 64 bity) i __m64|Pierwsze 4 parametry - RCX, RDX, R8, R9. Inne przekazywane na stosie.|
|Agregaty (inne)|Według wskaźnika. Pierwsze 4 parametry przekazywane jako wskaźniki w RCX, RDX, R8 i R9|
|__m128|Według wskaźnika. Pierwsze 4 parametry przekazywane jako wskaźniki w RCX, RDX, R8 i R9|

### <a name="example-of-argument-passing-1---all-integers"></a>Przykład przekazywania argumentu 1 — wszystkie liczby całkowite

```cpp
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

### <a name="example-of-argument-passing-2---all-floats"></a>Przykład przekazywania argumentu 2 - wszystkie pływaki

```cpp
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

### <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>Przykład przekazywania argumentu 3 - mieszane ints i pływaków

```cpp
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

### <a name="example-of-argument-passing-4--__m64-__m128-and-aggregates"></a>Przykład przekazywania argumentu 4-__m64, \__m128 i agregatów

```cpp
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="varargs"></a>Elementy vararg

Jeśli parametry są przekazywane przez varargs (na przykład argumenty wielokropka), a następnie normalny parametr rejestru przekazywania konwencji stosuje, w tym rozlanie piątego i kolejnych argumentów do stosu. Jest to callee jest odpowiedzialny za zrzut argumentów, które mają ich adres podjęte. Tylko dla wartości zmiennoprzecinkowych zarówno rejestr liczby całkowitej, jak i rejestr zmiennoprzecinowy muszą zawierać wartość, w przypadku gdy wywoływany oczekuje wartości w rejestrach całkowitych.

## <a name="unprototyped-functions"></a>Funkcje nieprototyped

W przypadku funkcji, które nie są w pełni prototypowe, obiekt wywołujący przekazuje wartości całkowite jako liczby całkowite i wartości zmiennoprzecinkowe jako podwójną precyzję. Tylko dla wartości zmiennoprzecinkowych zarówno rejestr liczby całkowitej, jak i rejestr zmiennoprzecinkowy zawierają wartość zmiennoprzecinkową w przypadku, gdy wywoływany oczekuje wartości w rejestrach liczby całkowitej.

```cpp
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="return-values"></a>Zwracane wartości

Skalarna wartość zwracana, która może zmieścić się w 64 bitach jest zwracana za pośrednictwem RAX; obejmuje to typy __m64. Typy nieskalowalne, w tym floats, doubles i typy wektorowe, takie jak [__m128](../cpp/m128.md), [__m128i](../cpp/m128i.md), [__m128d](../cpp/m128d.md) są zwracane w xmm0. Stan nieużywanych bitów w wartości zwróconej w RAX lub XMM0 jest niezdefiniowany.

Typy zdefiniowane przez użytkownika mogą być zwracane przez wartość z funkcji globalnych i statycznych funkcji członkowskich. Aby zwrócić typ zdefiniowany przez użytkownika według wartości w RAX, musi mieć długość 1, 2, 4, 8, 16, 32 lub 64 bitów. Musi również nie mieć zdefiniowanego przez użytkownika konstruktora, destruktora ani operatora przypisania kopii; brak prywatnych lub chronionych niestatycznych elementów członkowskich danych; brak niestatycznych elementów członkowskich danych typu referencyjnego; brak klas podstawowych; brak funkcji wirtualnych; i nie ma elementów członkowskich danych, które również nie spełniają tych wymagań. (Jest to zasadniczo definicja typu C++ 03 POD. Ponieważ definicja została zmieniona w standardzie C++11, nie zaleca się używania `std::is_pod` tego testu.) W przeciwnym razie wywołujący przyjmuje na siebie odpowiedzialność przydzielania pamięci i przekazywania wskaźnika dla zwracanej wartości jako pierwszego argumentu. Kolejne argumenty są następnie przesuwane o jeden argument w prawo. Ten sam wskaźnik musi być zwracany przez wywoływane w RAX.

Te przykłady pokazują, jak parametry i zwracane wartości są przekazywane dla funkcji z określonymi deklaracjami:

### <a name="example-of-return-value-1---64-bit-result"></a>Przykład zwracanej wartości 1 - wynik 64-bitowy

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

### <a name="example-of-return-value-2---128-bit-result"></a>Przykład zwracanej wartości 2 - wynik 128-bitowy

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

### <a name="example-of-return-value-3---user-type-result-by-pointer"></a>Przykład zwracanej wartości 3 - wynik typu użytkownika według wskaźnika

```Output
struct Struct1 {
   int j, k, l;    // Struct1 exceeds 64 bits.
};
Struct1 func3(int a, double b, int c, float d);
// Caller allocates memory for Struct1 returned and passes pointer in RCX,
// a in RDX, b in XMM2, c in R9, d pushed on the stack;
// callee returns pointer to Struct1 result in RAX.
```

### <a name="example-of-return-value-4---user-type-result-by-value"></a>Przykład zwracanej wartości 4 - wynik typu użytkownika według wartości

```Output
struct Struct2 {
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.
};
Struct2 func4(int a, double b, int c, float d);
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;
// callee returns Struct2 result by value in RAX.
```

## <a name="callercallee-saved-registers"></a>Rejestry zapisane przez rozmówcę/rozmówcę

Rejestry RAX, RCX, RDX, R8, R9, R10, R11, XMM0-5 oraz górne części YMM0-15 i ZMM0-15 są uważane za niestabilne i należy je uznać za zniszczone podczas wywołań funkcji (chyba że analiza, taka jak optymalizacja całego programu, może być uznana za zniszczoną (chyba że można je dzić inaczej bezpieczeństwa. Na avx512VL, ZMM, YMM i XMM rejestry 16-31 są lotne.

Rejestry RBX, RBP, RDI, RSI, RSP, R12, R13, R14, R15 i XMM6-15 są uważane za nieulotne i muszą zostać zapisane i przywrócone przez funkcję, która ich używa.

## <a name="function-pointers"></a>Wskaźniki funkcji

Wskaźniki funkcji są po prostu wskaźniki do etykiety odpowiedniej funkcji. Nie ma żadnych wymagań spisu treści (SPISU TREŚCI) dla wskaźników funkcji.

## <a name="floating-point-support-for-older-code"></a>Obsługa zmiennoprzecinkowy starszego kodu

Rejestry MMX i stosów zmiennoprzecinkowych (MM0-MM7/ST0-ST7) są zachowywane w przełącznikach kontekstowych. Nie ma wyraźnej konwencji wzywania dla tych rejestrów. Korzystanie z tych rejestrów jest surowo zabronione w kodzie trybu jądra.

## <a name="fpcsr"></a>FpCsr

Stan rejestru zawiera również słowo sterujące fpu x87. Konwencja wywołująca nakazuje, aby ten rejestr był nieulotny.

Rejestr słów sterujących fpu x87 jest ustawiony na następujące wartości standardowe na początku wykonywania programu:

| Zarejestruj\[bity] | Ustawienie |
|-|-|
| FPCSR\[0:6] | Maski wyjątków wszystkie 1 (wszystkie wyjątki zamaskowane) |
| FPCSR\[7] | Zarezerwowane - 0 |
| FPCSR\[8:9] | Precyzyjna kontrola - 10B (podwójna precyzja) |
| FPCSR\[10:11] | Kontrola zaokrąglania - 0 (zaokrąglanie do najbliższej) |
| FPCSR\[12] | Sterowanie nieskończoności - 0 (nie używane) |

Wywoływany, który modyfikuje dowolne pola w FPCSR należy przywrócić je przed zwróceniem do jego obiektu wywołującego. Ponadto wywołujący, który zmodyfikował dowolne z tych pól, musi przywrócić je do ich standardowych wartości przed wywołaniem wywoływanego, chyba że zgodnie z umową wywoływany oczekuje zmodyfikowanych wartości.

Istnieją dwa wyjątki od zasad dotyczących braku zmienności flag kontrolnych:

1. W funkcjach, w których udokumentowanym celem danej funkcji jest modyfikowanie nieulotnych flag FPCsr.

1. Gdy jest provably poprawne, że naruszenie tych reguł powoduje program, który zachowuje się tak samo jak program, w którym te reguły nie są naruszane, na przykład poprzez analizę całego programu.

## <a name="mxcsr"></a>MxCsr

Stan rejestru obejmuje również MxCsr. Konwencja wywołująca dzieli ten rejestr na część lotną i część nieulotną. Część lotna składa się z sześciu flag\[stanu, w MXCSR 0:5],\[podczas gdy reszta rejestru, MXCSR 6:15], jest uważana za nieulotną.

Część nieulotna jest ustawiona na następujące wartości standardowe na początku wykonywania programu:

| Zarejestruj\[bity] | Ustawienie |
|-|-|
| MXCSR\[6] | Denormals są zera - 0 |
| MXCSR\[7:12] | Maski wyjątków wszystkie 1 (wszystkie wyjątki zamaskowane) |
| MXCSR\[13:14] | Kontrola zaokrąglania - 0 (zaokrąglanie do najbliższej) |
| MXCSR\[15] | Kolor do zera dla zamaskowanego niedopełnienia - 0 (wyłączony) |

Wywoływany, który modyfikuje dowolne pola nieulotne w MXCSR należy przywrócić je przed zwróceniem do jego obiektu wywołującego. Ponadto wywołujący, który zmodyfikował dowolne z tych pól, musi przywrócić je do ich standardowych wartości przed wywołaniem wywoływanego, chyba że zgodnie z umową wywoływany oczekuje zmodyfikowanych wartości.

Istnieją dwa wyjątki od zasad dotyczących braku zmienności flag kontrolnych:

- W funkcjach, w których udokumentowanym celem danej funkcji jest modyfikowanie nieulotnych flag MxCsr.

- Gdy jest provably poprawne, że naruszenie tych reguł powoduje program, który zachowuje się tak samo jak program, w którym te reguły nie są naruszane, na przykład poprzez analizę całego programu.

Nie można zakładać o stanie lotnej części MXCSR w granicach funkcji, chyba że szczegółowo opisane w dokumentacji funkcji.

## <a name="setjmplongjmp"></a>setjmp/longjmp

Po dołączeniu setjmpex.h lub setjmp.h, wszystkie wywołania [setjmp](../c-runtime-library/reference/setjmp.md) lub [longjmp](../c-runtime-library/reference/longjmp.md) spowodować `__finally` unwind, który wywołuje destruktorów i wywołań.  Różni się to od x86, gdzie łącznie `__finally` setjmp.h powoduje klauzule i destruktory nie są wywoływane.

Wywołanie `setjmp` zachowuje bieżący wskaźnik stosu, rejestry nieulotne i rejestry MxCsr.  Wywołania, aby powrócić do `longjmp` ostatniej `setjmp` witryny wywołania i resetuje wskaźnik stosu, rejestry nieulotne i rejestry MxCsr, z powrotem do stanu zachowanego przez ostatnie `setjmp` wywołanie.

## <a name="see-also"></a>Zobacz też

[Konwencje kodowania x64](../build/x64-software-conventions.md)
