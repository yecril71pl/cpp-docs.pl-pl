---
title: x64 konwencji wywoływania
description: Szczegóły konwencji wywoływania interfejsu ABI domyślne x64.
ms.date: 12/17/2018
ms.assetid: 41ca3554-b2e3-4868-9a84-f1b46e6e21d9
ms.openlocfilehash: 02bf4719766366049b600b148ad88fc238f4e54e
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415789"
---
# <a name="x64-calling-convention"></a>x64 konwencji wywoływania

W tej sekcji opisano standardowe procesy i Konwencji jednej funkcji (wywołujący) używa do nawiązywania połączeń do innej funkcji (wywoływany) w x64 kodu.

## <a name="calling-convention-defaults"></a>Wartości domyślnych konwencji wywoływania

X64 który binarnym interfejsem aplikacji (ABI) używa konwencji wywoływania wywołania fast rejestru czterech przez domyślne. Miejsce jest przydzielane w stosie wywołań jako magazynu w tle dla wywoływane zapisać te rejestrów. Ma rygorystyczne relację między argumenty do wywołania funkcji i rejestry, używany dla tych argumentów. Dowolny z argumentów, który nie mieści się w 8 bajtów lub nie jest 1, 2, 4 lub 8 bajtów, muszą być przekazywane przez odwołanie. Pojedynczy argument nigdy nie rozkłada się na wiele rejestrów. X87 zarejestrować stosu jest nieużywana, mogą być używane przez obiekt wywoływany, ale należy rozważyć volatile dla wywołania funkcji. Wszystkie zmiennoprzecinkowej operacje są wykonywane przy użyciu 16 rejestrów XMM. Liczba całkowita argumenty są przekazywane w rejestrach RCX, RDX, R8 i R9. Zmiennoprzecinkowe argumenty są przekazywane do XMM0L, XMM1L, XMM2L i XMM3L. 16-bajtowy argumenty są przekazywane przez odwołanie. Przekazywanie parametru jest szczegółowo opisane w [przekazywania parametru](#parameter-passing). Oprócz tych rejestrów RAX R10, R11, XMM4 i XMM5 są traktowane jako nietrwałe. Wszystkie inne rejestrów jest trwała. Rejestrowanie użycia jest szczegółowo udokumentowano w [rejestrowanie użycia](../build/x64-software-conventions.md#register-usage) i [rejestruje zapisać element wywołujący/wywoływany](#callercallee-saved-registers).

Dla funkcji prototypowej wszystkie argumenty są konwertowane na typy oczekiwanego / / wywoływany przed przekazaniem. Obiekt wywołujący jest odpowiedzialny za przydzielanie miejsca dla parametrów, aby obiekt wywoływany i zawsze należy przydzielić wystarczającej ilości miejsca do przechowywania czterech Parametry rejestru, nawet wtedy, gdy obiekt wywoływany nie przyjmuje parametrów tę liczbę. Ta konwencja upraszcza obsługę bez pierwowzoru języka C i funkcje vararg C/C++. Dla funkcji vararg lub funkcji nieprototypowanych, wszelkie zmiennoprzecinkowej wartości muszą być zduplikowane w odpowiednim rejestrze ogólnego przeznaczenia. Wszelkie parametry poza pierwsze cztery muszą być przechowywane na stosie po cień przechowywania przed wywołaniem. Szczegóły funkcji Vararg znajdują się w [Varargs](#varargs). Informacje o funkcji bez Pierwowzoru została szczegółowo opisana w [funkcje bez Pierwowzoru](#unprototyped-functions).

## <a name="alignment"></a>Wyrównanie

Większość struktury są wyrównane do ich naturalnego wyrównania składowej. Podstawowe wyjątki są wskaźnik stosu i `malloc` lub `alloca` pamięci, które są wyrównane do 16-bajtowy, aby pomóc wydajności. Wyrównanie powyżej 16 bajtów musi być wykonywane ręcznie, ale ponieważ 16 bajtów to typowy rozmiar wyrównania dla operacji XMM, ta wartość powinna działać dla większości kodu. Aby uzyskać więcej informacji na temat układ struktury i wyrównania, zobacz [typy i magazyn](../build/x64-software-conventions.md#types-and-storage). Aby uzyskać informacji na temat układ stosu, zobacz [x64 stosu użycia](../build/stack-usage.md).

## <a name="unwindability"></a>Unwindability

Funkcje typu liść są funkcje, które nie zmieniaj żadnych rejestrów trwałej. Funkcja elementu członkowskiego typu liść mogą ulec zmianie RSP trwałej, na przykład przez wywołanie funkcji lub przydzielenie miejsca na stosie dodatkowe dla zmiennych lokalnych. Aby można było odzyskać trwałej rejestrów, gdy wyjątek jest obsługiwany, funkcji elementu członkowskiego typu liść musi być oznaczona przy użyciu danych statycznych, który opisuje sposób prawidłowo unwind funkcji w dowolnych instrukcji. Te dane są przechowywane jako *pdata*, lub procedury danych, który z kolei odnosi się do *xdata*, wyjątków, Obsługa danych. Xdata odwijania informacjami i może wskazywać dodatkowe pdata lub funkcję obsługi wyjątków. Prologs i epilogs są zastrzeżonych, tak aby mogły być prawidłowo opisanych w xdata. Wskaźnik stosu muszą być dostosowane do 16 bajtów w dowolnym regionie kod, który nie jest częścią epilogu lub prologu, z wyjątkiem w funkcjach typu liść. Funkcje typu liść można odwinięty po prostu symulując zwrotu, dzięki czemu pdata i xdata nie są wymagane. Aby uzyskać szczegółowe informacje o strukturze odpowiednie prologs funkcji i epilogs, zobacz [x64 prologu i epilogu](../build/prolog-and-epilog.md). Aby uzyskać więcej informacji na temat obsługi wyjątków i wyjątków, obsługa i odwinięcie pdata i xdata, zobacz [x64 wyjątków](../build/exception-handling-x64.md).

## <a name="parameter-passing"></a>Przekazywanie parametru

Pierwsze cztery liczby całkowitej argumenty są przekazywane w rejestrach. Wartości całkowite są przekazywane w kolejności od lewej do prawej w RCX, RDX, R8 i R9, odpowiednio. Od pięciu argumentów i nowszej są przekazywane na stosie. Wszystkie argumenty są wyrównane do prawej w rejestrach, więc wywoływany można zignorować górny bitów rejestru i uzyskać dostęp do części rejestru, które są niezbędne.

Argumenty zmiennoprzecinkowe i podwójną precyzją pierwsze cztery parametry są przekazywane w XMM0 - XMM3, w zależności od pozycji. Rejestruje liczbę całkowitą RCX, RDX, R8 i R9, która jest zwykle używane dla tych pozycji są ignorowane, z wyjątkiem w przypadku argumentów typu varargs. Aby uzyskać więcej informacji, zobacz [Varargs](#varargs). Podobnie XMM0 - XMM3 rejestrów są ignorowane, gdy odpowiedni argument jest typem liczby całkowitej lub wskaźnika.

[__m128](../cpp/m128.md) typów, tablic i ciągi nigdy nie są przekazywane przez natychmiastowe korzyści. Zamiast tego wskaźnika jest przekazywany do pamięci przydzielonej przez obiekt wywołujący. Tak, jakby były one liczb całkowitych o tym samym rozmiarze, struktur i Unii, rozmiar, 8, 16, 32 lub 64 bitów i typy __m64, są przekazywane. Strukturami lub związkami o innych rozmiarach są przekazywane jako wskaźnik do pamięci przydzielonej przez obiekt wywołujący. Dla tych typów agregacji, które zostały przekazane jako wskaźnik tym \__m128, tymczasowy pamięci przydzielonej przez obiekt wywołujący musi być wyrównany 16-bajtowy.

Funkcje wewnętrzne, które nie przydzielaj obszar stosu, a nie wywołuj innych funkcji, czasami wykorzystują innych rejestrów volatile Aby przekazać argumenty dodatkowe rejestrowanie. Tego rodzaju optymalizacji jest możliwe dzięki ścisłej powiązania między kompilator i implementację funkcji wewnętrznej.

Obiekt wywoływany jest odpowiedzialny za zrzucanie Parametry rejestru do ich miejsca w tle, jeśli to konieczne.

W poniższej tabeli przedstawiono, jak parametry są przekazywane:

|Typ parametru|Jak przekazany|
|--------------------|----------------|
|Liczba zmiennoprzecinkowa|Pierwsze 4 parametry - XMM0 za pośrednictwem XMM3. Inne są przekazywane na stosie.|
|Liczba całkowita|Pierwsze 4 parametry — RCX, RDX, R8, R9. Inne są przekazywane na stosie.|
|Agregacje (8, 16, 32 lub 64-bitowy) i __m64|Pierwsze 4 parametry — RCX, RDX, R8, R9. Inne są przekazywane na stosie.|
|Agregacje (inne)|Przez wskaźnik. Pierwsze 4 parametry są przekazywane jako wskaźniki w RCX, RDX, R8 i R9|
|__m128|Przez wskaźnik. Pierwsze 4 parametry są przekazywane jako wskaźniki w RCX, RDX, R8 i R9|

### <a name="example-of-argument-passing-1---all-integers"></a>Przykład 1 - wszystkich liczb całkowitych przekazywanie argumentów

```cpp
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

### <a name="example-of-argument-passing-2---all-floats"></a>Przykład 2 — wszystkie wartości zmiennoprzecinkowe przekazywanie argumentów

```cpp
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

### <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>Przykład 3 - mieszane liczby całkowite i wartości zmiennoprzecinkowe przekazywanie argumentów

```cpp
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

### <a name="example-of-argument-passing-4--m64-m128-and-aggregates"></a>Przykład 4 przekazywania argumentu-__m64, \__m128, a agregacje

```cpp
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="varargs"></a>Elementy vararg

Jeśli parametry są przekazywane za pośrednictwem varargs (na przykład wielokropka argumentów), następnie przekazywanie Konwencji parametru normalne rejestru ma zastosowanie, tym rozlanie piątym i kolejne argumenty stosu. Odpowiada za / / wywoływany argumenty zrzutu, które ma zajęty adres w ich. Tylko wartości zmiennoprzecinkowych Zarejestruj liczba całkowita i zmiennoprzecinkowa rejestr musi zawierać wartość, w przypadku, gdy wywoływany oczekuje, że wartość w rejestrach liczby całkowitej.

## <a name="unprototyped-functions"></a>Funkcje bez Pierwowzoru

W przypadku funkcji nie jest w pełni prototypowane obiekt wywołujący przekazuje liczb całkowitych jako liczby całkowite i zmiennoprzecinkowe wartości jako podwójnej precyzji. Tylko wartości zmiennoprzecinkowych Zarejestruj liczba całkowita i zmiennoprzecinkowa Rejestr zawiera wartości zmiennoprzecinkowej w przypadku, gdy wywoływany oczekuje, że wartość w rejestrach liczby całkowitej.

```cpp
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="return-values"></a>Zwracane wartości

Skalarne, zwracana wartość, którą można dopasować do 64 bitów jest zwracana za pośrednictwem RAX; w tym typy __m64. Typy non-scalar, w tym wartości zmiennoprzecinkowe wartości podwójnej precyzji i typy wektorowe, takie jak [__m128](../cpp/m128.md), [__m128i](../cpp/m128i.md), [__m128d](../cpp/m128d.md) są zwracane w XMM0. Stan nieużywane bity w wartości zwracanej w RAX lub XMM0 jest niezdefiniowane.

Typy zdefiniowane przez użytkownika mogą być zwracane przez wartość z funkcji globalnych i statycznych elementów członkowskich. Aby przywrócić typ zdefiniowany przez użytkownika według wartości w RAX, musi mieć długość 1, 2, 4, 8, 16, 32 lub 64-bitowy. Musi mieć również nie zdefiniowane przez użytkownika Konstruktor, destruktor lub operator przypisania kopiowania; nie prywatnych lub chronionych niestatycznych składowych danych; nie elementów członkowskich danych niestatycznych typu odwołania; nie mają klas bazowych; żadnych funkcji wirtualnych; i żadnych składowych danych, które również nie spełniają tych wymagań. (To jest zasadniczo definicja C ++ 03 typu POD. Ponieważ definicja została zmieniona w standardem C ++ 11, nie zalecamy używania `std::is_pod` dla tego testu.) W przeciwnym razie obiekt wywołujący przejmie odpowiedzialność przydzielania pamięci i przekazywania wskaźnika dla wartości zwracanej jako pierwszy argument. Pozostałe argumenty są następnie przesunięte jeden argument w prawo. Ten sam wskaźnik muszą zostać zwrócony przez element wywołujący w RAX.

Poniższe przykłady pokazują sposób przekazywania parametrów i zwracanych wartości dla funkcji za pomocą określonego deklaracji:

### <a name="example-of-return-value-1---64-bit-result"></a>Przykład wartości zwracanej 1 – wynik 64 bitowy

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

### <a name="example-of-return-value-2---128-bit-result"></a>Przykład wartości zwracanej 2 - 128-bitowego wyniku

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

### <a name="example-of-return-value-3---user-type-result-by-pointer"></a>Przykład wartości zwracanej 3 – wynik typu użytkownika przez wskaźnik

```Output
struct Struct1 {
   int j, k, l;    // Struct1 exceeds 64 bits.
};
Struct1 func3(int a, double b, int c, float d);
// Caller allocates memory for Struct1 returned and passes pointer in RCX,
// a in RDX, b in XMM2, c in R9, d pushed on the stack;
// callee returns pointer to Struct1 result in RAX.
```

### <a name="example-of-return-value-4---user-type-result-by-value"></a>Przykład wartości zwracanej 4 – wynik typu użytkownika według wartości

```Output
struct Struct2 {
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.
};
Struct2 func4(int a, double b, int c, float d);
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;
// callee returns Struct2 result by value in RAX.
```

## <a name="callercallee-saved-registers"></a>Zapisane rejestrowania wywołującego/wywoływanego

Rejestry RAX RCX, RDX, R8, R9, R10, R11 są traktowane jako nietrwałe oraz muszą być rozważone zniszczona na wywołania funkcji (chyba że inaczej bezpieczeństwa sprawdzalnych podczas analizy, takie jak optymalizacja całego programu).

Rejestrów RBX RBP, RDI, RSI, RSP, R12, R13, R14 i R15 są traktowane jako trwałej i muszą zostać zapisane i przywrócone przez funkcję używającą je.

## <a name="function-pointers"></a>Wskaźniki funkcji

Wskaźniki funkcji są po prostu wskaźnikami do etykiety odpowiednich funkcji. Nie ma żadnych spis treści (TOC) wymagania dotyczące wskaźników do funkcji.

## <a name="floating-point-support-for-older-code"></a>Obsługa modelu zmiennoprzecinkowego w przypadku starszego kodu

MMX i rejestruje stosu zmiennoprzecinkowego (MM0-MM7/ST0-ST7) są zachowywane między przełączeń kontekstu. Nie ma żadnych jawnej konwencji wywoływania dla tych rejestrów. Korzystanie z tych rejestrów jest bezwzględnie zabronione w kod trybu jądra.

## <a name="fpcsr"></a>FpCsr

Stan Rejestr zawiera również x87 FPU słowa sterującego. Konwencja wywoływania nakazują tego Zarejestruj się w nieulotnej.

Wykonywanie programu x87 rejestr słowo sterowania FPU jest ustawiony na następujące standardowe wartości na początku:

| Zarejestruj\[bitów] | Ustawienie |
|-|-|
| FPCSR\[0:6] | Wyjątek maskuje wszystkich 1 (wszystkie wyjątki maskowane) |
| FPCSR\[7] | Zastrzeżone — 0 |
| FPCSR\[8:9] | Sterowanie dokładnością - 10B (Podwójna precyzja) |
| FPCSR\[10:11] | Formant zaokrąglenia - 0 (zaokrąglony do najbliższej) |
| FPCSR\[12] | Formant nieskończoność - 0 (nieużywane) |

/ / Wywoływany modyfikującego pól w FPCSR należy przywrócić je przed zwróceniem do obiektu wywołującego. Ponadto obiekt wywołujący, który zmodyfikował tych pól należy przywrócić ich standardowe wartości przed wywołaniem / / wywoływany, chyba że umowie wywoływany oczekuje zmodyfikowane wartości.

Istnieją dwa wyjątki reguł dotyczących innych zmienności flagi kontrolne:

1. W funkcjach, gdzie jest udokumentowane celem daną funkcję do modyfikowania nieulotnej FpCsr flag.

1. Gdy jest zgodność poprawne, że program, który działa tak samo, jak program, gdy te zasady nie są naruszone, na przykład dzięki analizie całego programu powoduje naruszenie niniejszych zasad.

## <a name="mxcsr"></a>MxCsr

Stan Rejestr zawiera również MxCsr. Konwencja wywoływania dzieli tego rejestru na volatile części i nieulotnej części. Volatile część składa się z sześciu stan flagi, w MXCSR\[0:5], podczas gdy pozostałe rejestru MXCSR\[6:15], jest uznawana za nieulotnej.

Na początku wykonywania programu nieulotnej część ma wartość standardowe następujące wartości:

| Zarejestruj\[bitów] | Ustawienie |
|-|-|
| MXCSR\[6] | Denormals jest zer - 0 |
| MXCSR\[7:12] | Wyjątek maskuje wszystkich 1 (wszystkie wyjątki maskowane) |
| MXCSR\[13:14] | Formant zaokrąglenia - 0 (zaokrąglony do najbliższej) |
| MXCSR\[15] | Zapisywanie do wartości zero dla maskowanego niedopełnienie - 0 (wyłączone) |

/ / Wywoływany, który modyfikuje znajdujących się w nieulotnej pól w mxcsr rejestru należy przywrócić je przed zwróceniem do obiektu wywołującego. Ponadto obiekt wywołujący, który zmodyfikował tych pól należy przywrócić ich standardowe wartości przed wywołaniem / / wywoływany, chyba że umowie wywoływany oczekuje zmodyfikowane wartości.

Istnieją dwa wyjątki reguł dotyczących innych zmienności flagi kontrolne:

- W funkcjach, gdzie jest udokumentowane celem daną funkcję do modyfikowania nieulotnej MxCsr flag.

- Gdy jest zgodność poprawne, że program, który działa tak samo, jak program, gdy te zasady nie są naruszone, na przykład dzięki analizie całego programu powoduje naruszenie niniejszych zasad.

Nie można wykonać o stanie volatile część MXCSR granicę funkcji, chyba że wyraźnie określonych w dokumentacji funkcji.

## <a name="setjmplongjmp"></a>setjmp/longjmp

Po włączeniu setjmpex.h lub setjmp.h wszystkie wywołania [setjmp](../c-runtime-library/reference/setjmp.md) lub [longjmp](../c-runtime-library/reference/longjmp.md) powoduje rozwinięcie, który wywołuje destruktory i `__finally` wywołania.  To różni się od x86, której wynikiem tym setjmp.h `__finally` klauzul i destruktory nie są wywoływane.

Wywołanie `setjmp` zachowuje bieżący wskaźnik stosu, rejestrów trwała i MxCsr rejestrów.  Wywołania `longjmp` wróć do najnowszych, ostatnio `setjmp` wywołań lokacji i resetuje wskaźnik stosu, rejestrów trwała i MxCsr rejestruje, do stanu zachowanego przez najnowszych, ostatnio `setjmp` wywołania.

## <a name="see-also"></a>Zobacz także

[Konwencje kodowania x64](../build/x64-software-conventions.md)
