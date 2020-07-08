---
title: Konwencja wywoływania x64
description: Szczegóły domyślnej konwencji wywoływania x64.
ms.date: 07/06/2020
ms.assetid: 41ca3554-b2e3-4868-9a84-f1b46e6e21d9
ms.openlocfilehash: 9bfecd0fb154658a299d3dac7d9e45398ebe450b
ms.sourcegitcommit: 85d96eeb1ce41d9e1dea947f65ded672e146238b
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86058636"
---
# <a name="x64-calling-convention"></a>Konwencja wywoływania x64

W tej sekcji opisano standardowe procesy i konwencje używane przez jedną funkcję (wywołującą) do wykonywania wywołań do innej funkcji (wywoływanej) w kodzie x64.

## <a name="calling-convention-defaults"></a>Ustawienia domyślne konwencji wywoływania

Interfejs binarny aplikacji (ABI) dla architektury x64 domyślnie używa konwencji wywoływania funkcji szybkiego wywołania funkcji "4-Register". Miejsce jest przydzielono na stosie wywołań jako magazyn w tle dla wywoływane w celu zapisania tych rejestrów.

Istnieje ścisła zgodność jeden-do-jednego między argumentami wywołania funkcji i rejestrami używanymi dla tych argumentów. Każdy argument, który nie mieści się w 8 bajtach lub nie ma 1, 2, 4 lub 8 bajtów, musi być przesyłany przez odwołanie. Pojedynczy argument nigdy nie jest rozłożony na wiele rejestrów.

Stos rejestru x87 jest nieużywany. Może być używany przez wywoływany element, ale należy rozważyć nietrwały w wywołaniach funkcji. Wszystkie operacje zmiennoprzecinkowe są wykonywane przy użyciu 16 XMM rejestrów.

Argumenty całkowite są przesyłane w rejestrach RCX, RDX, R8 i R9. Argumenty zmiennoprzecinkowe są przekazane w XMM0L, XMM1L, XMM2L i XMM3L. argumenty 16-bajtowe są przesyłane przez odwołanie. Przekazywanie parametrów zostało szczegółowo opisane w [parametrach przekazujących](#parameter-passing). Te rejestry, RAX, R10, R11, XMM4 i XMM5, są uznawane za nietrwałe. Użycie rejestru zostało udokumentowane szczegółowo w temacie [Rejestrowanie użycia](../build/x64-software-conventions.md#register-usage) i [wywołujące/wywoływane zapisane rejestry](#callercallee-saved-registers).

W przypadku funkcji prototypowych wszystkie argumenty są konwertowane na oczekiwane typy wywoływane przed przekazaniem. Obiekt wywołujący jest odpowiedzialny za przydzielanie miejsca dla parametrów wywoływanego elementu. Obiekt wywołujący musi zawsze przydzielać wystarczającą ilość miejsca do przechowywania czterech parametrów rejestru, nawet jeśli wywoływany nie przyjmuje wielu parametrów. Ta konwencja upraszcza obsługę nieprototypowych funkcji języka C i funkcji vararg C/C++. W przypadku funkcji vararg lub nieprototypowych wszystkie wartości zmiennoprzecinkowe muszą być zduplikowane w odpowiednim rejestrze ogólnego przeznaczenia. Wszystkie parametry, które wykraczają poza pierwsze cztery, muszą być przechowywane na stosie po magazynie w tle przed wywołaniem. Szczegóły funkcji vararg można znaleźć w elemencie [VarArgs](#varargs). Informacje o nieprototypowej funkcji są szczegółowo opisane w [funkcjach nieprototypowych](#unprototyped-functions).

## <a name="alignment"></a>Wyrównanie

Większość struktur jest wyrównana do ich naturalnego wyrównania. Podstawowe wyjątki to wskaźnik stosu i `malloc` `alloca` pamięć, które są 16-bajtowe wyrównane do wydajności. Wyrównanie powyżej 16 bajtów musi być wykonywane ręcznie. Ponieważ 16 bajtów jest typowym rozmiarem wyrównania dla operacji XMM, ta wartość powinna funkcjonować w przypadku większości kodu. Aby uzyskać więcej informacji na temat układu i wyrównania struktury, zobacz [typy i magazynowanie](../build/x64-software-conventions.md#types-and-storage). Aby uzyskać informacje na temat układu stosu, zobacz temat [użycie stosu x64](../build/stack-usage.md).

## <a name="unwindability"></a>Niekontrolowana

Funkcje liścia to funkcje, które nie zmieniają żadnych rejestrów nietrwałych. Funkcja, która nie jest elementem liścia, może zmienić nietrwałe żądanie RSP, na przykład przez wywołanie funkcji. Lub można zmienić żądanie RSP przez przydzielenie dodatkowej przestrzeni stosu dla zmiennych lokalnych. W celu odzyskania rejestrów nietrwałych, gdy wyjątek jest obsługiwany, funkcje spoza liścia są adnotacjami z danymi statycznymi. Dane opisują, jak prawidłowo przewinięcie funkcji w dowolnej instrukcji. Te dane są przechowywane jako *pData*lub dane procedury, które z kolei odwołują się do *xdata*, danych obsługi wyjątków. Xdata zawiera informacje dotyczące odwinięcia i może wskazywać na dodatkowe pData lub funkcję obsługi wyjątków.

Dzienniki i epilogs są wysoce ograniczone, aby można je było prawidłowo opisać w XData. Wskaźnik stosu musi pozostać 16-bajtowy w dowolnym regionie kodu, który nie jest częścią epilogu lub prologu, z wyjątkiem funkcji liścia. Funkcje liścia mogą być rozwiązane po prostu poprzez symulowanie powrotu, więc pData i xdata nie są wymagane. Aby uzyskać szczegółowe informacje na temat właściwej struktury funkcji rejestrowania i epilogs, zobacz [x64 Prolog i epilogu](../build/prolog-and-epilog.md). Aby uzyskać więcej informacji na temat obsługi wyjątków oraz obsługi wyjątków i odwinięcia pData i xdata, zobacz [Obsługa wyjątków x64](../build/exception-handling-x64.md).

## <a name="parameter-passing"></a>Przekazywanie parametrów

Domyślnie Konwencja wywoływania x64 przekazuje pierwsze cztery argumenty do funkcji w rejestrach. Rejestry używane dla tych argumentów zależą od pozycji i typu argumentu. Pozostałe argumenty są wypychane na stosie w kolejności od prawej do lewej.

Argumenty o wartościach całkowitych w czterech miejscach z lewej strony są przesyłane odpowiednio do kolejności w RCX, RDX, R8 i R9. Argumenty piąty i wyższy są przesyłane na stosie, jak opisano wcześniej. Wszystkie argumenty całkowite w rejestrach są wyrównane do prawej, więc wywoływany może ignorować górne bity rejestru i uzyskać dostęp tylko do wymaganej części rejestru.

Wszystkie argumenty zmiennoprzecinkowe i podwójnej precyzji w pierwszych czterech parametrach są przesyłane w XMM0-XMM3, w zależności od pozycji. Wartości zmiennoprzecinkowe są umieszczane tylko w rejestrach całkowitych RCX, RDX, R8 i R9, gdy istnieją argumenty typu VarArgs. Aby uzyskać szczegółowe informacje, zobacz [VarArgs](#varargs). Podobnie rejestry XMM0-XMM3 są ignorowane, gdy odpowiadający argument jest liczbą całkowitą lub wskaźnikiem.

[`__m128`](../cpp/m128.md)typy, tablice i ciągi nigdy nie są przesyłane przez bezpośrednią wartość. Zamiast tego wskaźnik jest przesyłany do pamięci przydzielonej przez obiekt wywołujący. Struktury i Unii o rozmiarze 8, 16, 32 lub 64 bitów i `__m64` typach są przesyłane tak, jakby były liczbami całkowitymi o tym samym rozmiarze. Struktury lub złożenia innych rozmiarów są przesyłane jako wskaźnik do pamięci przydzielonej przez obiekt wywołujący. Dla tych typów agregacji przechodzą jako wskaźnik, w tym `__m128` , Pamięć tymczasowa przydzielonej przez obiekt wywołujący musi być równa 16-bajtowa.

Funkcje wewnętrzne, które nie przydzielą przestrzeni stosu i nie wywołują innych funkcji, czasami używają innych nietrwałych rejestrów do przekazania dodatkowych argumentów rejestru. Optymalizacja jest możliwa przez ścisłe powiązanie między kompilatorem a implementacją funkcji wewnętrznej.

Wywoływany jest odpowiedzialny za zatopienie parametrów rejestru w ich miejscu w tle, w razie potrzeby.

Poniższa tabela zawiera podsumowanie sposobu przekazywania parametrów według typu i pozycji od lewej:

| Typ parametru | piąty i wyższy | IV | innych | sekunda | położony |
|-|-|-|-|-|-|
| liczba zmiennoprzecinkowa | stack | XMM3 | XMM2 | XMM1 | XMM0 |
| liczba całkowita | stack | R9 | R8 | RDX | RCX |
| Agregaty (8, 16, 32 lub 64 bitów) i`__m64` | stack | R9 | R8 | RDX | RCX |
| Inne agregaty, jako wskaźniki | stack | R9 | R8 | RDX | RCX |
| `__m128`, jako wskaźnik | stack | R9 | R8 | RDX | RCX |

### <a name="example-of-argument-passing-1---all-integers"></a>Przykład przejścia argumentu 1 — wszystkie liczby całkowite

```cpp
func1(int a, int b, int c, int d, int e, int f);
// a in RCX, b in RDX, c in R8, d in R9, f then e pushed on stack
```

### <a name="example-of-argument-passing-2---all-floats"></a>Przykład przejścia argumentu 2 — wszystkie wartości zmiennoprzecinkowe

```cpp
func2(float a, double b, float c, double d, float e, float f);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, f then e pushed on stack
```

### <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>Przykład przejścia argumentu 3 — mieszane liczby całkowite i zmiennoprzecinkowe

```cpp
func3(int a, double b, int c, float d, int e, float f);
// a in RCX, b in XMM1, c in R8, d in XMM3, f then e pushed on stack
```

### <a name="example-of-argument-passing-4---__m64-__m128-and-aggregates"></a>Przykład przejścia argumentu 4- `__m64` , `__m128` i agregacji

```cpp
func4(__m64 a, __m128 b, struct c, float d, __m128 e, __m128 f);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3,
// ptr to f pushed on stack, then ptr to e pushed on stack
```

## <a name="varargs"></a>Elementy vararg

Jeśli parametry są przekazywane za pośrednictwem typu VarArgs (na przykład argumenty wielokropka), stosowana jest normalna Konwencja przekazywania parametrów rejestru. Ta Konwencja obejmuje rozłożenie piątego i późniejszego argumentu na stos. Jest on odpowiedzialny za wywoływanie argumentów, które mają swój adres. Tylko w przypadku wartości zmiennoprzecinkowych zarówno rejestry całkowite, jak i rejestr zmiennoprzecinkowy muszą zawierać wartość, w przypadku gdy wywoływany oczekuje wartość w rejestrach liczb całkowitych.

## <a name="unprototyped-functions"></a>Funkcje nieprototypowe

W przypadku funkcji, które nie są w pełni prototypem, obiekt wywołujący przekazuje wartości całkowite jako liczby całkowite i wartości zmiennoprzecinkowe jako podwójną precyzję. Tylko w przypadku wartości zmiennoprzecinkowych zarówno rejestry całkowite, jak i rejestr zmiennoprzecinkowy zawierają wartość zmiennoprzecinkową w przypadku, gdy obiekt wywołujący oczekuje wartości w rejestrach liczb całkowitych.

```cpp
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="return-values"></a>Zwracane wartości

Skalarna wartość zwracana, która może pasować do 64 bitów, łącznie z `__m64` typem, jest zwracana przez RAX. Typy nieskalarne, w tym wartości zmiennoprzecinkowe, podwaja i typy wektorów, takie jak [`__m128`](../cpp/m128.md) , [`__m128i`](../cpp/m128i.md) [`__m128d`](../cpp/m128d.md) są zwracane w XMM0. Stan nieużywanych bitów w wartości zwracanej przez RAX lub XMM0 jest niezdefiniowany.

Typy zdefiniowane przez użytkownika mogą być zwracane przez wartość z funkcji globalnych i statycznych funkcji składowych. Aby zwrócić typ zdefiniowany przez użytkownika przez wartość w RAX, musi mieć długość 1, 2, 4, 8, 16, 32 lub 64 bitów. Musi on również mieć zdefiniowany przez użytkownika Konstruktor, destruktor lub operator przypisania kopiowania. Nie może mieć żadnych prywatnych lub chronionych niestatycznych elementów członkowskich danych i nie ma żadnych statycznych składowych danych typu referencyjnego. Nie może mieć klas bazowych ani funkcji wirtualnych. Ponadto może mieć tylko składowe danych, które spełniają te wymagania. (Ta definicja jest zasadniczo taka sama jak w przypadku typu C++ 03 POD. Ze względu na to, że definicja została zmieniona w standardzie C++ 11, nie zalecamy używania `std::is_pod` dla tego testu.) W przeciwnym razie obiekt wywołujący musi przydzielić pamięć dla wartości zwracanej i przekazać do niego wskaźnik jako pierwszy argument. Pozostałe argumenty są następnie przesunięte o jeden argument w prawo. Ten sam wskaźnik musi być zwracany przez obiekt wywoływany w RAX.

W poniższych przykładach pokazano, jak parametry i zwracane wartości są przesyłane do funkcji z określonymi deklaracjami:

### <a name="example-of-return-value-1---64-bit-result"></a>Przykład zwracanej wartości 1-64-bitowego wyniku

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

### <a name="example-of-return-value-2---128-bit-result"></a>Przykład zwracanej wartości 2-128-bitowego wyniku

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

### <a name="example-of-return-value-3---user-type-result-by-pointer"></a>Przykład wartości zwracanej 3 — wynik typu użytkownika według wskaźnika

```Output
struct Struct1 {
   int j, k, l;    // Struct1 exceeds 64 bits.
};
Struct1 func3(int a, double b, int c, float d);
// Caller allocates memory for Struct1 returned and passes pointer in RCX,
// a in RDX, b in XMM2, c in R9, d pushed on the stack;
// callee returns pointer to Struct1 result in RAX.
```

### <a name="example-of-return-value-4---user-type-result-by-value"></a>Przykład wartości zwracanej 4 — wynik typu użytkownika według wartości

```Output
struct Struct2 {
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.
};
Struct2 func4(int a, double b, int c, float d);
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;
// callee returns Struct2 result by value in RAX.
```

## <a name="callercallee-saved-registers"></a>Zapisane rejestry wywołującego/wywoływanego

Architektura x64 ABI uwzględnia rejestry RAX, RCX, RDX, R8, R9, R10, R11 i XMM0-XMM5 volatile. Gdy jest obecny, górne fragmenty YMM0-YMM15 i ZMM0-ZMM15 są również nietrwałe. W AVX512VL, ZMM, YMM i XMM rejestry 16-31 są również nietrwałe. Rozważ użycie rejestrów nietrwałych zniszczonych w wywołaniach funkcji, o ile nie ma w tym celu zabezpieczeń-sprawdzalnych, takich jak optymalizacja całego programu

Architektura x64 ABI uwzględnia rejestry RBX, RBP, RDI, RSI, RSP, R12, R13, R14, R15 i XMM6-XMM15 unvolatile. Muszą zostać zapisane i przywrócone przez funkcję, która go używa.

## <a name="function-pointers"></a>Wskaźniki funkcji

Wskaźniki funkcji są po prostu wskaźnikami do etykiety odpowiedniej funkcji. Nie istnieje wymóg spisu treści (TOC) dla wskaźników funkcji.

## <a name="floating-point-support-for-older-code"></a>Obsługa zmiennoprzecinkowa dla starszego kodu

Rejestry stosu MMX i zmiennoprzecinkowe (MM0-MM7/ST0-ST7) są zachowywane między przełącznikami kontekstowymi. Brak jawnej konwencji wywoływania dla tych rejestrów. Korzystanie z tych rejestrów jest absolutnie zabronione w kodzie trybu jądra.

## <a name="fpcsr"></a>FPCSR

Stan rejestru zawiera również słowo x87 FPU Control. Konwencja wywoływania wymusza, aby ta rejestracja była nietrwała.

Rejestracja słowa x87 FPU Control zostanie ustawiona przy użyciu następujących wartości standardowych na początku wykonywania programu:

| \[Bity rejestru] | Ustawienie |
|-|-|
| FPCSR \[ 0:6] | Maski wyjątków wszystkie 1 (wszystkie wyjątki są maskowane) |
| FPCSR \[ 7] | Zarezerwowane — 0 |
| FPCSR \[ 8:9] | Precision Control-10B (Podwójna precyzja) |
| FPCSR \[ 10:11] | Kontrolka zaokrąglania-0 (Zaokrąglij do najbliższej) |
| FPCSR \[ 12] | Nieskończoność — 0 (nieużywane) |

Wywoływany, który modyfikuje wszystkie pola w FPCSR, musi przywrócić je przed powrotem do obiektu wywołującego. Ponadto obiekt wywołujący, który zmodyfikował dowolne z tych pól, musi przywrócić je do wartości standardowych przed wywołaniem elementu wywoływanego, chyba że w ramach umowy element wywoływany oczekuje zmodyfikowanych wartości.

Istnieją dwa wyjątki od zasad dotyczących niezmienności flag formantów:

- W funkcjach, w których cel danej funkcji jest modyfikowany przez nietrwałe flagi FPCSR.

- Provably poprawiają, że naruszenie tych reguł powoduje, że program zachowuje się tak samo jak program, który nie narusza reguł, na przykład za pomocą analizy całego programu.

## <a name="mxcsr"></a>MXCSR

Stan rejestru zawiera również MXCSR. Konwencja wywoływania dzieli ten rejestr na część nietrwałą i nielotną część. Część nietrwała składa się z sześciu flag stanu, w MXCSR \[ 0:5], podczas gdy pozostała część rejestru MXCSR \[ 6:15] jest uznawana za nietrwałą.

Część nietrwała jest ustawiona na następujące wartości standardowe na początku wykonywania programu:

| \[Bity rejestru] | Ustawienie |
|-|-|
| MXCSR \[ 6] | Nienormalne wartości są zerami-0 |
| MXCSR \[ 7:12] | Maski wyjątków wszystkie 1 (wszystkie wyjątki są maskowane) |
| MXCSR \[ 13:14] | Kontrolka zaokrąglania-0 (Zaokrąglij do najbliższej) |
| MXCSR \[ 15] | Opróżnianie do zera dla zamaskowanego niedopełnienia-0 (wyłączone) |

Wywoływany, który modyfikuje dowolne z nietrwałych pól w MXCSR, musi przywrócić je przed powrotem do obiektu wywołującego. Ponadto obiekt wywołujący, który zmodyfikował dowolne z tych pól, musi przywrócić je do wartości standardowych przed wywołaniem elementu wywoływanego, chyba że w ramach umowy element wywoływany oczekuje zmodyfikowanych wartości.

Istnieją dwa wyjątki od zasad dotyczących niezmienności flag formantów:

- W funkcjach, w których cel danej funkcji jest modyfikowany przez nietrwałe flagi MXCSR.

- Provably poprawiają, że naruszenie tych reguł powoduje, że program zachowuje się tak samo jak program, który nie narusza reguł, na przykład za pomocą analizy całego programu.

Nie należy wprowadzać żadnych założeń dotyczących nietrwałego stanu części rejestru MXCSR na granicy funkcji, chyba że dokumentacja funkcji jawnie ją opisuje.

## <a name="setjmplongjmp"></a>setjmp/longjmp

Po dołączeniu SETJMPEX. h lub setjmp. h wszystkie wywołania [`setjmp`](../c-runtime-library/reference/setjmp.md) lub [`longjmp`](../c-runtime-library/reference/longjmp.md) powodują odwinięcie, które wywołuje destruktory i `__finally` wywołania.  To zachowanie różni się od x86, gdzie w tym setjmp. h powoduje, `__finally` że nie są wywoływane klauzule i destruktory.

Wywołanie w celu `setjmp` zachowywania bieżącego wskaźnika stosu, rejestrów nietrwałych i rejestrów MXCSR.  Wywołania do `longjmp` powrotu do najnowszej `setjmp` lokacji wywołania i resetowania wskaźnika stosu, rejestrów nietrwałych i rejestrów MXCSR, z powrotem do stanu zakonserwowanego przez ostatnie `setjmp` wywołanie.

## <a name="see-also"></a>Zobacz także

[Konwencje kodowania x64](../build/x64-software-conventions.md)
