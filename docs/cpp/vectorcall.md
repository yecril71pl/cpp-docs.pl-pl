---
title: __vectorcall | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 1c95ed59-86c6-4857-b4ed-10519193f851
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 335f81a204ec91361c51f7573e58b61fad91f97b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061711"
---
# <a name="vectorcall"></a>__vectorcall

**Microsoft Specific**

**__Vectorcall** konwencji wywoływania Określa, że argumenty funkcji są przekazywane do rejestrów, gdy jest to możliwe. **__vectorcall** używa więcej rejestrów dla argumentów niż [__fastcall](../cpp/fastcall.md) lub wartość domyślną [x64 konwencji wywoływania](../build/overview-of-x64-calling-conventions.md) użycia. **__Vectorcall** konwencja wywołania jest obsługiwana tylko w kodzie macierzystym na procesorach x86 i x64, obejmujących Streaming SIMD Extensions 2 (SSE2) i nowszych. Użyj **__vectorcall** przyspieszyć funkcje, które wychodzą za kilka zmiennoprzecinkowego lub argumentów wektora SIMD i wykonywać operacje, które wykorzystują argumenty załadowane w rejestrach. Poniższa lista zawiera funkcje, które są wspólne dla implementacji x86 i x64 **__vectorcall**. Różnice zostały wyjaśnione w dalszej części tego artykułu.

|Element|Implementacja|
|-------------|--------------------|
|Konwencja dekorowania nazw języka C|Nazwy funkcji są umieszczone dwa "znaki at" (\@\@) następuje liczba bajtów (w zapisie dziesiętnym na liście parametrów).|
|Konwencja translacji wielkości liter|Translacja wielkości liter nie jest wykonywane.|

Za pomocą [GV](../build/reference/gd-gr-gv-gz-calling-convention.md) — opcja kompilatora powoduje, że każda funkcja w module jest skompilowana jako **__vectorcall** chyba, że funkcja jest funkcją składową, jest zadeklarowane ze sprzecznym atrybutem konwencji wywoływania, używa `vararg` listy zmiennych argumentów lub ma nazwę `main`.

Możesz przekazać trzy rodzaje argumenty przez rejestr w **__vectorcall** funkcji: *typu Liczba całkowita* wartości *typu wektor* wartości i *agregat wektora Łączny* wartości (HVA).

Typ liczby całkowitej spełnia dwa wymogi: pasuje do rozmiaru rejestru macierzystego procesora — na przykład 4 bajty na x86 maszyny lub 8 bajtów na x64 maszyny — i jest konwertowany na liczbę całkowitą długości rejestru i ponownie ponownie bez zmiany jego bitowej Reprezentacja. Na przykład dowolny typ, który może być podwyższony do **int** na x86 (**long long** na x64) — na przykład **char** lub **krótki**— lub mogą być rzutowane na **int** (**long long** na x64) i z powrotem do oryginalnego typu bez zmiany typu integer. Całkowitoliczbowe obejmują wskaźnik, odniesieni i **struktury** lub **Unii** typy 4 bajty (8 bajtów x64) lub mniej. Na x64 platform, w większych **struktury** i **Unii** typy są przekazywane przez odwołanie do pamięci przydzielonej przez obiekt wywołujący; x86 platform, są przekazywane przez wartość na stosie.

Typem wektora jest typ zmiennoprzecinkowy — na przykład **float** lub **double**— lub typ wektora SIMD — na przykład **__m128** lub **__m256**.

Typ HVA jest typu złożonego do czterech elementów członkowskich danych, które mają identyczne typy wektorów. Typ HVA ma ten sam wymóg wyrównania jako typ wektora jego członków. Jest to przykład HVA **struktury** definicji, który zawiera trzy identyczne typy wektorów i ma 32-bajtowe wyrównanie:

```cpp
typedef struct {
   __m256 x;
   __m256 y;
   __m256 z;
} hva3;    // 3 element HVA type on __m256
```

Deklaruj swoje funkcje jawnie z **__vectorcall** — słowo kluczowe w plikach nagłówkowych, aby umożliwić oddzielnie skompilowanemu kodowi utworzenie łącza bez błędów. Funkcje muszą być prototypowane używać **__vectorcall**i nie można użyć `vararg` listy argumentów o zmiennej długości.

Funkcja członka może być zadeklarowana za pomocą **__vectorcall** specyfikator. Ukryte **to** wskaźnik jest przekazywany przez rejestr jako pierwszy argument typu Liczba całkowita.

Na maszynach ARM **__vectorcall** jest akceptowane i ignorowane przez kompilator.

Przypadku niestatycznych funkcji składowych Jeśli funkcja jest zdefiniowana poza wierszem, modyfikator konwencji wywoływania nie ma zostać określony w definicji poza wierszem. Oznacza to dla niestatycznych składowych, przyjmowana jest Konwencja wywoływania określona podczas deklaracji punkcie definicji. Biorąc pod uwagę tę definicję klasy:

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

**__Vectorcall** modyfikator Konwencja wywoływania musi być określona gdy wskaźnik do **__vectorcall** zostanie utworzona funkcja. Następny przykład tworzy **typedef** dla wskaźnika do **__vectorcall** funkcja, która pobiera cztery **double** argumenty i zwraca **__m256**wartość:

```cpp
typedef __m256 (__vectorcall * vcfnptr)(double, double, double, double);
```

## <a name="vectorcall-convention-on-x64"></a>Konwencja __vectorcall x64

**__Vectorcall** konwencji wywoływania na x64 rozszerza standardowe x64 konwencji wywoływania, aby móc korzystać z dodatkowych rejestrów. Zarówno argumenty typu Liczba całkowita, jak i argumentów typu wektor są mapowane do rejestrów na podstawie pozycji na liście argumentów. Argumenty agregatów HVA są przydzielane do nieużywanych rejestrów wektorowych.

Jeśli którekolwiek z pierwszych czterech argumentów w porządku od lewej do prawej są argumentami typu Liczba całkowita, są one przekazywane do rejestru, który odpowiada tej pozycji — RCX, RDX, R8 lub R9. Ukryty **to** wskaźnik jest traktowany jako pierwszy argument typu Liczba całkowita. Jeśli argument HVA w jednym z pierwszych czterech argumentów nie można przekazać w dostępnych rejestrach, odwołanie do pamięci przydzielonej przez obiekt wywołujący jest przekazywane w odpowiednim rejestrze typu Liczba całkowita. Argumenty typu całkowitoliczbowego po czwartej pozycji parametru są przekazywane na stosie.

Jeśli którekolwiek z pierwszych sześciu argumentów w porządku od lewej do prawej są argumentami typu wektor, są one przekazywane przez wartość w rejestrach wektora SSE od 0 do 5, zgodnie z pozycją argumentu. Zmiennoprzecinkowe i **__m128** typy są przekazywane w rejestrach XMM, a **__m256** typy są przekazywane w rejestrach YMM rejestruje. To różni się od standardowego x64 Konwencja wywoływania, ponieważ typy wektorowe są przekazywane przez wartość, a nie przez odwołanie, a używane są dodatkowe rejestry. Obszar stosu cienia przydzielony dla argumentów typu wektor jest ustalony na 8 bajtów i [/homeparams](../build/reference/homeparams-copy-register-parameters-to-stack.md) opcja nie ma zastosowania. Argumenty typu wektora w siódmej i dalszych pozycjach parametru są przekazywane na stosie przez odwołanie do pamięci przydzielonej przez obiekt wywołujący.

Po dla argumentów wektora, dane członków argumentów HVA są przydzielane w kolejności rosnącej do nieużywanych wektorów rejestrujących xmm0 do XMM5 (lub YMM0 do YMM5, dla **__m256** typów), tak długo, jak istnieje niewystarczająca liczba rejestrów dostępne dla całego HVA. Jeśli niewystarczająca liczba rejestrów jest dostępna, argument agregatu HVA jest przekazywany przez odwołanie do pamięci przydzielonej przez obiekt wywołujący. Obszar stosu cienia dla argumentu HVA jest ustalony na 8 bajtów z zawartością niezdefiniowaną. Argumenty agregatów HVA są przypisane do rejestrów w kolejności od lewej do prawej na liście parametrów i może być w dowolnym miejscu. Argumenty agregatów HVA w jednym z pierwszych czterech argumentów, pozycje, które nie są przypisane do rejestrów wektorowych, są przekazywane przez odwołanie w całkowitoliczbowym, które odpowiada tej pozycji. Argumenty agregatów HVA przekazywane przez odwołanie po czwartej pozycji parametru są wypychane na stosie.

Wyniki **__vectorcall** funkcje są zwracane przez wartość w rejestrach, jeżeli jest to możliwe. Wyniki typu Liczba całkowita, włącznie ze strukturami lub związkami 8 bajtów lub mniej, są zwracane według wartości w RAX. Wyniki typu wektor są zwracane przez wartość w XMM0 lub YMM0, w zależności od rozmiaru. Wyniki agregatu HVA mają każdy element danych zwracany przez wartość w rejestrach xmm0: xmm3 lub ymm0: ymm3, w zależności od rozmiaru elementu. Typy wyników, które nie pasują do odpowiednich rejestrów są zwracane przez odwołanie do pamięci przydzielonej przez obiekt wywołujący.

Stos jest utrzymywany przez obiekt wywołujący w x64 implementacji **__vectorcall**. Kod prologu i epilogu wywołującego przydziela i czyści stos dla wywołanej funkcji. Argumenty są wypychane na stosie od prawej do lewej, a cień obszaru stosu jest przydzielany do argumentów przekazywanych do rejestrów.

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

## <a name="vectorcall-convention-on-x86"></a>Konwencja __vectorcall x86

**__Vectorcall** kroczy za Konwencją **__fastcall** Konwencji argumenty typu Liczba całkowita 32-bitowa i wykorzystuje rejestry wektora SSE dla typu wektora i argumentów HVA.

Pierwsze dwa argumenty typu Liczba całkowita znalezione na liście parametrów od lewej do prawej są umieszczone w ECX i EDX, odpowiednio. Ukryty **to** wskaźnik jest traktowany jako pierwszy argument typu Liczba całkowita i przechodzi w ECX. Pierwsze sześć argumentów typu wektor są przekazywane przez wartość przez rejestry wektorów SSE 0-5, w rejestrach XMM lub YMM, w zależności od rozmiaru argumentu.

Vector — pierwsze sześć argumentów typu w kolejności od lewej do prawej są przekazywane przez wartość w rejestrach wektora SSE od 0 do 5. Zmiennoprzecinkowe i **__m128** typy są przekazywane w rejestrach XMM, a **__m256** typy są przekazywane w rejestrach YMM rejestruje. Nie obszar stosu cienia jest przydzielany do argumentów typu wektorowego przekazywanych przez rejestr. Argumenty typu wektora siódmego i kolejnych są przekazywane na stosie przez odwołanie do pamięci przydzielonej przez obiekt wywołujący. Ograniczenie błędu kompilatora [C2719](../error-messages/compiler-errors-2/compiler-error-c2719.md) nie ma zastosowania do tych argumentów.

Po dla argumentów wektora, dane członków argumentów HVA są przydzielane w kolejności rosnącej do nieużywanych wektorów rejestrujących xmm0 do XMM5 (lub YMM0 do YMM5, dla **__m256** typów), tak długo, jak istnieje niewystarczająca liczba rejestrów dostępne dla całego HVA. Jeśli niewystarczająca liczba rejestrów jest dostępna, argument agregatu HVA jest przekazywany w stosie przez odwołanie do pamięci przydzielonej przez obiekt wywołujący. Nie obszar stosu cienia dla argumentu HVA jest przydzielany. Argumenty agregatów HVA są przypisane do rejestrów w kolejności od lewej do prawej na liście parametrów i może być w dowolnym miejscu.

Wyniki **__vectorcall** funkcje są zwracane przez wartość w rejestrach, jeżeli jest to możliwe. Wyniki typu Liczba całkowita, włącznie ze strukturami lub związkami 4 bajtów lub mniej, są zwracane według wartości w EAX. Liczba całkowita typu strukturami lub związkami 8 bajtów lub mniej są zwracane przez wartość w parametrze EDX: EAX. Wyniki typu wektor są zwracane przez wartość w XMM0 lub YMM0, w zależności od rozmiaru. Wyniki agregatu HVA mają każdy element danych zwracany przez wartość w rejestrach xmm0: xmm3 lub ymm0: ymm3, w zależności od rozmiaru elementu. Inne typy wyników są zwracane przez odwołanie do pamięci przydzielonej przez obiekt wywołujący.

X86 implementacji **__vectorcall** następuje po Konwencji argumentów wypychane na stos od prawej do lewej przez wywołującego, po czym wywołana funkcja czyści stos tuż przed zwróceniem. Tylko argumenty, które nie są wprowadzane w rejestrach, są wypychane na stosie.

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

**End specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)