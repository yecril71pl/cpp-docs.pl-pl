---
title: __vectorcall
ms.date: 12/17/2018
f1_keywords:
- __vectorcall_cpp
- __vectorcall
- _vectorcall
helpviewer_keywords:
- __vectorcall keyword
- __vectorcall
ms.assetid: 1c95ed59-86c6-4857-b4ed-10519193f851
ms.openlocfilehash: c933f995c57094b28e477e439c7b9ff5a13c2063
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187521"
---
# <a name="__vectorcall"></a>__vectorcall

**Specyficzne dla firmy Microsoft**

Konwencja wywoływania **__vectorcall** określa, że argumenty funkcji mają być przekazane w rejestrach, jeśli jest to możliwe. **__vectorcall** używa więcej rejestrów dla argumentów niż [__fastcall](../cpp/fastcall.md) lub domyślnej [konwencji wywoływania x64](../build/x64-calling-convention.md) . Konwencja wywoływania **__vectorcall** jest obsługiwana tylko w kodzie natywnym na procesorach x86 i x64, które zawierają Streaming SIMD Extensions 2 (SSE2) i nowsze. Użyj **__vectorcall** , aby przyspieszyć funkcje, które przechodzą kilka argumentów wektora zmiennoprzecinkowego lub SIMD i wykonują operacje, które wykorzystują argumenty załadowane w rejestrach. Na poniższej liście przedstawiono funkcje, które są wspólne dla implementacji architektury x86 i x64 **__vectorcall**. Różnice są wyjaśnione w dalszej części tego artykułu.

|Element|Wdrażanie|
|-------------|--------------------|
|Konwencja dekoracji nazw języka C|Nazwy funkcji są sufiksami z dwoma znakami "at" (\@\@), po których następuje liczba bajtów (w zapisie dziesiętnym) na liście parametrów.|
|Konwencja translacji wielkości liter|Nie jest wykonywane żadne tłumaczenie wielkości liter.|

Użycie opcji kompilatora [/GV](../build/reference/gd-gr-gv-gz-calling-convention.md) powoduje, że każda funkcja w module jest skompilowana jako **__vectorcall** , chyba że funkcja jest funkcją składową, jest zadeklarowana przy użyciu atrybutu konwencji wywoływania powodującego konflikt, używa listy argumentów zmiennych `vararg` lub ma nazwę `main`.

Można przekazać trzy rodzaje argumentów przez zarejestrowanie w funkcjach **__vectorcall** : wartości *typu Integer* , wartości *typu wektora* i *jednorodnej wartości zagregowanej wektora* (HVA).

Typ liczby całkowitej spełnia dwa wymagania: pasuje do natywnego rozmiaru rejestru procesora — na przykład 4 bajty na komputerze z procesorem x86 lub 8 bajtów na komputerze x64 — i jest konwertowany na liczbę całkowitą długości rejestru i ponownie bez zmiany jego bitu reprezentowana. Na przykład dowolny typ, który może zostać podwyższony **do int** w x86 (**Long Long** on x64) — na przykład **char** lub **Short**— lub który może być rzutowany na **int** (**Long Long** on x64) i z powrotem do oryginalnego typu bez zmiany, jest typem liczb całkowitych. Typy całkowite obejmują wskaźniki, odwołania i **struktury** lub typy **Unii** 4 bajty (8 bajtów na x64) lub mniej. Na platformach x64, większe **struktury** i typy **Unii** są przesyłane przez odwołanie do pamięci przydzielonej przez obiekt wywołujący; na platformach x86 są one przesyłane przez wartość na stosie.

Typ wektora jest typem zmiennoprzecinkowym — na przykład **zmiennoprzecinkowym** lub **podwójnym**— lub typu wektora SIMD — na przykład **__m128** lub **__m256**.

Typ HVA to złożony typ składający się z maksymalnie czterech składowych danych, które mają identyczne typy wektorów. Typ HVA ma takie samo wymaganie wyrównania jak typ wektora jego składowych. Jest to przykład definicji **struktury** HVA, która zawiera trzy identyczne typy wektorów i ma 32-bajtowe wyrównanie:

```cpp
typedef struct {
   __m256 x;
   __m256 y;
   __m256 z;
} hva3;    // 3 element HVA type on __m256
```

Zadeklaruj funkcje jawnie za pomocą słowa kluczowego **__vectorcall** w plikach nagłówkowych, aby umożliwić użycie osobno skompilowanego kodu do łączenia się bez błędów. Funkcje muszą być prototypami, aby można było używać **__vectorcall**i nie mogą używać listy argumentów `vararg` o zmiennej długości.

Funkcja członkowska może być zadeklarowana przy użyciu specyfikatora **__vectorcall** . Ukryty **ten** wskaźnik jest przesyłany przez zarejestrowanie jako pierwszy argument typu Liczba całkowita.

Na komputerach ARM **__vectorcall** jest akceptowana i ignorowana przez kompilator.

W przypadku niestatycznych funkcji składowych klasy, jeśli funkcja jest zdefiniowana poza wierszem, modyfikator konwencji wywołania nie musi być określony w definicji poza wierszem. Oznacza to, że dla niestatycznych elementów członkowskich klasy, Konwencja wywoływania określona podczas deklaracji jest założono w punkcie definicji. Biorąc pod uwagę tę definicję klasy:

```cpp
struct MyClass {
   void __vectorcall mymethod();
};
```

to:

```cpp
void MyClass::mymethod() { return; }
```

jest równoważne temu:

```cpp
void __vectorcall MyClass::mymethod() { return; }
```

Modyfikator **__vectorcall** konwencji wywoływania należy określić, gdy zostanie utworzony wskaźnik do funkcji **__vectorcall** . W następnym przykładzie jest tworzony **element typedef** dla wskaźnika do funkcji **__vectorcall** , która przyjmuje cztery **podwójne** argumenty i zwraca wartość **__m256** :

```cpp
typedef __m256 (__vectorcall * vcfnptr)(double, double, double, double);
```

W celu zapewnienia zgodności z poprzednimi wersjami **_vectorcall** jest synonimem dla **__vectorcall** , chyba że opcja kompilatora [/za \(Wyłącz rozszerzenia językowe)](../build/reference/za-ze-disable-language-extensions.md) .

## <a name="__vectorcall-convention-on-x64"></a>Konwencja __vectorcall x64

Konwencja wywoływania **__vectorcall** w systemie x64 rozszerza standardową Konwencję wywołań x64, aby skorzystać z dodatkowych rejestrów. Argumenty typu integer i argumenty typu Vector są mapowane na rejestry na podstawie pozycji na liście argumentów. Argumenty HVA są przydzieleni do nieużywanych rejestrów wektorów.

Gdy którykolwiek z pierwszych czterech argumentów w kolejności od lewej do prawej to argumenty typu Liczba całkowita, są one przesyłane do rejestru odpowiadającego tej pozycji — RCX, RDX, R8 lub R9. Ukryty **ten** wskaźnik jest traktowany jako pierwszy argument typu Liczba całkowita. Gdy w dostępnych rejestrach nie można przesłać argumentu HVA w jednym z pierwszych czterech argumentów, odwołanie do pamięci przydzieloną przez wywołującego jest przesyłane w odpowiednim rejestrze typu Liczba całkowita. Argumenty typu Integer po czwartej pozycji parametru są przesyłane na stosie.

Gdy którekolwiek z pierwszych sześciu argumentów w kolejności od lewej do prawej są argumentami typu Vector, są one przenoszone przez wartość w rejestrach wektorów SSE od 0 do 5 według pozycji argumentu. Typy zmiennoprzecinkowe i **__m128** są przesyłane w rejestrach XMM, a typy **__m256** są przesyłane w rejestrach YMM. Różni się to od standardowej konwencji wywoływania x64, ponieważ typy wektorów są przenoszone przez wartość, a nie przez odwołanie, i używane są dodatkowe rejestry. Przestrzeń stosu w tle przypisana dla argumentów typu Vector ma ustaloną wartość 8 bajtów, a opcja [/homeparams](../build/reference/homeparams-copy-register-parameters-to-stack.md) nie ma zastosowania. Argumenty typu Vector w pozycjach siódmych i późniejszych parametrów są przesyłane na stosie przez odwołanie do pamięci przydzielonej przez obiekt wywołujący.

Po przypisaniu rejestrów dla argumentów wektorowych elementy członkowskie danych argumentów HVA są przypisywane w kolejności rosnącej, do nieużywanych wektorów rejestruje XMM0 do XMM5 (lub YMM0 do YMM5, dla typów **__m256** ), o ile dostępne są wystarczające rejestry dla całego HVA. Jeśli jest za mało dostępnych rejestrów, argument HVA jest przesyłany przez odwołanie do pamięci przydzielonej przez obiekt wywołujący. Przestrzeń cienia stosu dla argumentu HVA ma ustaloną wartość 8 bajtów z niezdefiniowaną zawartością. Argumenty HVA są przypisywane do rejestrów w kolejności od lewej do prawej na liście parametrów i mogą znajdować się w dowolnym położeniu. Argumenty HVA w jednym z pierwszych czterech pozycji argumentów, które nie są przypisane do rejestrów wektorów, są przenoszone przez odwołanie w rejestrze liczb całkowitych odpowiadającym tej pozycji. Argumenty HVA przekazane przez odwołanie po przejściu czwartej pozycji parametru są wypychane na stosie.

Wyniki funkcji **__vectorcall** są zwracane przez wartość w rejestrach, gdy jest to możliwe. Wyniki typu Liczba całkowita, w tym struktury lub Unii o długości 8 bajtów lub mniej, są zwracane przez wartość w RAX. Wyniki typu Vector są zwracane przez wartość w XMM0 lub YMM0, w zależności od rozmiaru. Wyniki HVA mają każdy element danych zwrócony przez wartość w rejestrach XMM0: XMM3 lub YMM0: YMM3, w zależności od rozmiaru elementu. Typy wyników, które nie mieszczą się w odpowiednich rejestrach są zwracane przez odwołanie do pamięci przydzielonej przez obiekt wywołujący.

Stos jest obsługiwany przez obiekt wywołujący w implementacji x64 **__vectorcall**. Kod prologu i epiloguego wywołującego przypisuje i czyści stos dla wywołanej funkcji. Argumenty są wypychane na stosie od prawej do lewej, a przestrzeń sterty w tle jest przypisana do argumentów przekazana do rejestrów.

Przykłady:

```cpp
// crt_vc64.c
// Build for amd64 with: cl /arch:AVX /W3 /FAs crt_vc64.c
// This example creates an annotated assembly listing in
// crt_vc64.asm.

#include <intrin.h>
#include <xmmintrin.h>

typedef struct {
   __m128 array[2];
} hva2;    // 2 element HVA type on __m128

typedef struct {
   __m256 array[4];
} hva4;    // 4 element HVA type on __m256

// Example 1: All vectors
// Passes a in XMM0, b in XMM1, c in YMM2, d in XMM3, e in YMM4.
// Return value in XMM0.
__m128 __vectorcall
example1(__m128 a, __m128 b, __m256 c, __m128 d, __m256 e) {
   return d;
}

// Example 2: Mixed int, float and vector parameters
// Passes a in RCX, b in XMM1, c in R8, d in XMM3, e in YMM4,
// f in XMM5, g pushed on stack.
// Return value in YMM0.
__m256 __vectorcall
example2(int a, __m128 b, int c, __m128 d, __m256 e, float f, int g) {
   return e;
}

// Example 3: Mixed int and HVA parameters
// Passes a in RCX, c in R8, d in R9, and e pushed on stack.
// Passes b by element in [XMM0:XMM1];
// b's stack shadow area is 8-bytes of undefined value.
// Return value in XMM0.
__m128 __vectorcall example3(int a, hva2 b, int c, int d, int e) {
   return b.array[0];
}

// Example 4: Discontiguous HVA
// Passes a in RCX, b in XMM1, d in XMM3, and e is pushed on stack.
// Passes c by element in [YMM0,YMM2,YMM4,YMM5], discontiguous because
// vector arguments b and d were allocated first.
// Shadow area for c is an 8-byte undefined value.
// Return value in XMM0.
float __vectorcall example4(int a, float b, hva4 c, __m128 d, int e) {
   return b;
}

// Example 5: Multiple HVA arguments
// Passes a in RCX, c in R8, e pushed on stack.
// Passes b in [XMM0:XMM1], d in [YMM2:YMM5], each with
// stack shadow areas of an 8-byte undefined value.
// Return value in RAX.
int __vectorcall example5(int a, hva2 b, int c, hva4 d, int e) {
   return c + e;
}

// Example 6: HVA argument passed by reference, returned by register
// Passes a in [XMM0:XMM1], b passed by reference in RDX, c in YMM2,
// d in [XMM3:XMM4].
// Register space was insufficient for b, but not for d.
// Return value in [YMM0:YMM3].
hva4 __vectorcall example6(hva2 a, hva4 b, __m256 c, hva2 d) {
   return b;
}

int __cdecl main( void )
{
   hva4 h4;
   hva2 h2;
   int i;
   float f;
   __m128 a, b, d;
   __m256 c, e;

   a = b = d = _mm_set1_ps(3.0f);
   c = e = _mm256_set1_ps(5.0f);
   h2.array[0] = _mm_set1_ps(6.0f);
   h4.array[0] = _mm256_set1_ps(7.0f);

   b = example1(a, b, c, d, e);
   e = example2(1, b, 3, d, e, 6.0f, 7);
   d = example3(1, h2, 3, 4, 5);
   f = example4(1, 2.0f, h4, d, 5);
   i = example5(1, h2, 3, h4, 5);
   h4 = example6(h2, h4, c, h2);
}
```

## <a name="__vectorcall-convention-on-x86"></a>Konwencja __vectorcall na architekturze x86

Konwencja wywoływania **__vectorcall** jest zgodna z konwencją **__fastcall** dla argumentów typu Liczba całkowita 32-bitowa i wykorzystuje rejestry wektorów SSE dla typu wektorów i argumentów HVA.

Pierwsze dwa argumenty typu Integer, które znajdują się na liście parametrów od lewej do prawej są odpowiednio umieszczone w ECX i EDX. **Ukryty wskaźnik** jest traktowany jako pierwszy argument typu integer i jest przenoszona w ECX. Pierwsze sześć argumentów typu wektora są przekazane przez wartość za pomocą rejestrów wektorów SSE 0 – 5 w rejestrach XMM lub YMM, w zależności od rozmiaru argumentu.

Pierwsze sześć argumentów typu Vector w kolejności od lewej do prawej są przekazane przez wartość w rejestrach wektorów SSE 0 – 5. Typy zmiennoprzecinkowe i **__m128** są przesyłane w rejestrach XMM, a typy **__m256** są przesyłane w rejestrach YMM. Nie przydzielono żadnego miejsca stosu cienia dla argumentów typu wektorowego przekazanego przez register. Siódme i kolejne argumenty typu wektora są przesyłane na stosie przez odwołanie do pamięci przydzielonej przez obiekt wywołujący. Ograniczenie błędu kompilatora [C2719](../error-messages/compiler-errors-2/compiler-error-c2719.md) nie ma zastosowania do tych argumentów.

Po przypisaniu rejestrów dla argumentów wektorowych elementy członkowskie danych argumentów HVA są przypisywane w kolejności rosnącej do nieużywanych rejestrów wektorów XMM0 do XMM5 (lub YMM0 do YMM5, dla typów **__m256** ), o ile dostępne są wystarczające rejestry dla całego HVA. Jeśli jest za mało dostępnych rejestrów, argument HVA jest przesyłany na stosie przez odwołanie do pamięci przydzielonej przez obiekt wywołujący. Brak miejsca na stosie stosu dla argumentu HVA. Argumenty HVA są przypisywane do rejestrów w kolejności od lewej do prawej na liście parametrów i mogą znajdować się w dowolnym położeniu.

Wyniki funkcji **__vectorcall** są zwracane przez wartość w rejestrach, gdy jest to możliwe. Wyniki typu Liczba całkowita, w tym struktury lub Unii z 4 bajtami lub mniej, są zwracane przez wartość w EAX. Struktury typu Integer lub sumy składające się z 8 bajtów lub mniej są zwracane przez wartość w EDX: EAX. Wyniki typu Vector są zwracane przez wartość w XMM0 lub YMM0, w zależności od rozmiaru. Wyniki HVA mają każdy element danych zwrócony przez wartość w rejestrach XMM0: XMM3 lub YMM0: YMM3, w zależności od rozmiaru elementu. Inne typy wyników są zwracane przez odwołanie do pamięci przydzielonej przez obiekt wywołujący.

Implementacja standardu x86 **__vectorcall** jest zgodna z Konwencją argumentów wypychanych na stosie od prawej do lewej przez obiekt wywołujący, a wywoływana funkcja czyści stos tuż przed zwróceniem. Tylko argumenty, które nie są umieszczone w rejestrach, są wypychane na stosie.

Przykłady:

```cpp
// crt_vc86.c
// Build for x86 with: cl /arch:AVX /W3 /FAs crt_vc86.c
// This example creates an annotated assembly listing in
// crt_vc86.asm.

#include <intrin.h>
#include <xmmintrin.h>

typedef struct {
   __m128 array[2];
} hva2;    // 2 element HVA type on __m128

typedef struct {
   __m256 array[4];
} hva4;    // 4 element HVA type on __m256

// Example 1: All vectors
// Passes a in XMM0, b in XMM1, c in YMM2, d in XMM3, e in YMM4.
// Return value in XMM0.
__m128 __vectorcall
example1(__m128 a, __m128 b, __m256 c, __m128 d, __m256 e) {
   return d;
}

// Example 2: Mixed int, float and vector parameters
// Passes a in ECX, b in XMM0, c in EDX, d in XMM1, e in YMM2,
// f in XMM3, g pushed on stack.
// Return value in YMM0.
__m256 __vectorcall
example2(int a, __m128 b, int c, __m128 d, __m256 e, float f, int g) {
   return e;
}

// Example 3: Mixed int and HVA parameters
// Passes a in ECX, c in EDX, d and e pushed on stack.
// Passes b by element in [XMM0:XMM1].
// Return value in XMM0.
__m128 __vectorcall example3(int a, hva2 b, int c, int d, int e) {
   return b.array[0];
}

// Example 4: HVA assigned after vector types
// Passes a in ECX, b in XMM0, d in XMM1, and e in EDX.
// Passes c by element in [YMM2:YMM5].
// Return value in XMM0.
float __vectorcall example4(int a, float b, hva4 c, __m128 d, int e) {
   return b;
}

// Example 5: Multiple HVA arguments
// Passes a in ECX, c in EDX, e pushed on stack.
// Passes b in [XMM0:XMM1], d in [YMM2:YMM5].
// Return value in EAX.
int __vectorcall example5(int a, hva2 b, int c, hva4 d, int e) {
   return c + e;
}

// Example 6: HVA argument passed by reference, returned by register
// Passes a in [XMM1:XMM2], b passed by reference in ECX, c in YMM0,
// d in [XMM3:XMM4].
// Register space was insufficient for b, but not for d.
// Return value in [YMM0:YMM3].
hva4 __vectorcall example6(hva2 a, hva4 b, __m256 c, hva2 d) {
   return b;
}

int __cdecl main( void )
{
   hva4 h4;
   hva2 h2;
   int i;
   float f;
   __m128 a, b, d;
   __m256 c, e;

   a = b = d = _mm_set1_ps(3.0f);
   c = e = _mm256_set1_ps(5.0f);
   h2.array[0] = _mm_set1_ps(6.0f);
   h4.array[0] = _mm256_set1_ps(7.0f);

   b = example1(a, b, c, d, e);
   e = example2(1, b, 3, d, e, 6.0f, 7);
   d = example3(1, h2, 3, 4, 5);
   f = example4(1, 2.0f, h4, d, 5);
   i = example5(1, h2, 3, h4, 5);
   h4 = example6(h2, h4, c, h2);
}
```

**Zakończenie określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
