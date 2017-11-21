---
title: __vectorcall | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
ms.assetid: 1c95ed59-86c6-4857-b4ed-10519193f851
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e61efe58ae718e7381d6404f54c0887f556ac34c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="vectorcall"></a>__vectorcall
**Dotyczące firmy Microsoft**  
  
 `__vectorcall` Konwencji wywoływania Określa, że argumenty funkcji są przekazywane w rejestrach, gdy jest to możliwe. `__vectorcall`używa rejestrów więcej argumentów niż [__fastcall](../cpp/fastcall.md) lub wartość domyślną [x64 konwencji wywoływania](../build/overview-of-x64-calling-conventions.md) użycia. `__vectorcall` Konwencji wywoływania jest obsługiwana tylko w kodzie natywnym na x86 i x64 procesorów, które obejmują Streaming SIMD Extensions 2 (SSE2) lub nowszym. Użyj `__vectorcall` szybkości funkcje, które przejdą kilka liczb zmiennoprzecinkowych lub argumentów wektorów SIMD i wykonywać operacje, które korzystają z argumentów załadowany w rejestrach. Poniższa lista zawiera funkcje, które są wspólne dla implementacji x86 i x64 `__vectorcall`. Różnice zostały omówione w dalszej części tego artykułu.  
  
|Element|Implementacja|  
|-------------|--------------------|  
|Konwencja nazwij dekorację C|Z dwóch "znaków @@ następuje liczba bajtów (dziesiętna) na liście parametrów w" są sufiksem nazwy funkcji.|  
|Konwencja translacji wielkości liter|Nie przypadków tłumaczenia jest wykonywane.|  
  
 Przy użyciu [GV](../build/reference/gd-gr-gv-gz-calling-convention.md) — opcja kompilatora powoduje poszczególnych funkcji w module skompilować jako `__vectorcall` chyba, że funkcja jest funkcją członkowską, jest zadeklarowana z atrybutem powodujące konflikt konwencji wywoływania, używa `vararg` zmiennej Lista argumentów lub ma nazwę `main`.  
  
 Można przekazać trzy rodzaje argumentów przez rejestr w `__vectorcall` funkcji: *typu Liczba całkowita* wartości, *wektorów typu* wartości, i *agregacji jednorodnych wektor* (HVA ) wartości.  
  
 Typu integer spełniający wymagania dwóch: mieści się w rozmiar natywnego rejestru procesora — na przykład 4 bajty na x86 maszyny lub 8 bajtów na x64 maszyny — i do przekonwertowania na liczbę całkowitą z rejestru długości i z powrotem jest ponownie bez zmieniania jego bit reprezentacja wartości. Na przykład dla dowolnego typu, który może być podwyższony do `int` na x86 (`long long` na x64) — na przykład `char` lub `short`— lub mogą być rzutowane na `int` (`long long` na x64) i z powrotem do jej oryginalnej typ bez zmian jest liczbą całkowitą Typ. Typy całkowite obejmują wskaźnika, odwołanie, i `struct` lub `union` typy 4 bajty (8 bajtów x64) lub mniej. Na x64 platform większych `struct` i `union` typy są przekazywane przez odwołanie do pamięci przydzielonej przez obiekt wywołujący; na x86 platformy, są one przekazywane się według wartości na stosie.  
  
 Zmiennoprzecinkowe typu jest typu wektora — na przykład `float` lub `double`— lub typ wektorów SIMD — na przykład `__m128` lub `__m256`.  
  
 Typ HVA jest typu złożonego do czterech elementy członkowskie danych, których typy wektorów identyczne. Typ HVA ma ten sam wymóg wyrównanie jako typ wektora jego elementów członkowskich. Jest to przykład HVA `struct` definicji, która zawiera trzy typy wektorów identyczne i wyrównanie 32 bajtów jest:  
  
```cpp  
typedef struct {  
   __m256 x;  
   __m256 y;  
   __m256 z;  
} hva3;    // 3 element HVA type on __m256  
  
```  
  
 Deklarowanie funkcji jawnie z `__vectorcall` — słowo kluczowe w pliki nagłówkowe, aby umożliwić oddzielnie skompilowany kod, aby połączyć się bez błędów. Funkcje musi być prototypowana do użycia `__vectorcall`i nie można użyć `vararg` listy argumentów o zmiennej długości.  
  
 Funkcja członkowska mogą być deklarowane jako za pomocą `__vectorcall` specyfikator. Ukrytego `this` wskaźnika jest przekazywana przez rejestru jako pierwszy argument typu Liczba całkowita.  
  
 Na maszynach ARM `__vectorcall` i akceptowany jest ignorowana przez kompilator.  
  
 Dla klasy niestatycznej funkcji członkowskiej Jeśli funkcja jest zdefiniowane poza zewnętrznych, modyfikatora konwencji wywoływania nie ma określonych w definicji wiersza. Oznacza to elementów członkowskich klas niestatyczna, Konwencja wywoływania określona podczas deklaracji przyjęto, że w punkcie definicji. Biorąc pod uwagę tę definicję klasy:  
  
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
  
 `__vectorcall` Modyfikatora konwencji wywoływania musi być określona gdy wskaźnik do `__vectorcall` tworzenia funkcji. W następnym przykładzie jest tworzony `typedef` dla wskaźnika do `__vectorcall` funkcja, która przyjmuje cztery `double` argumentów i zwraca `__m256` wartość:  
  
```cpp  
typedef __m256 (__vectorcall * vcfnptr)(double, double, double, double);  
```  
  
## <a name="vectorcall-convention-on-x64"></a>__vectorcall Konwencja na x64  
 `__vectorcall` Konwencji wywoływania na x64 rozszerza x64 standardowej konwencji, aby móc korzystać z dodatkowych rejestrów wywoływania. Zarówno argumentów typu Liczba całkowita, jak i argumentów typu wektora są mapowane do rejestrów na podstawie pozycji w liście argumentów. Argumenty HVA są przydzielone do rejestrów nieużywane wektora.  
  
 Po pierwsze cztery argumenty w kolejności od lewej do prawej są argumentów typu Liczba całkowita, są przekazywane do rejestru, który odpowiada w odpowiednim miejscu — RCX, RDX, R8 lub R9. Ukryty `this` wskaźnika jest traktowany jako pierwszy argument typu Liczba całkowita. Jeśli argument HVA pierwsze cztery argumenty nie mogą być przekazywane w rejestrach dostępne, odwołanie do pamięć przydzielona wywołującego jest przekazywany w rejestrze odpowiedniego typu Liczba całkowita. Argumentów typu Liczba całkowita po czwartym pozycja parametru są przekazywane na stosie.  
  
 Jeśli dowolny argument pierwszych sześciu w kolejności od lewej do prawej czy wektorów argumentów typu, są one przekazywane przez wartość w rejestrach wektor SSE 0 – 5, zgodnie z pozycja argumentu. Zmiennoprzecinkowe i `__m128` typy są przekazywane w rejestrach XMM i `__m256` typy są przekazywane w YMM rejestruje. To różni się od standardowego x64 wywoływanie Konwencji, ponieważ typy wektorów są przekazywane przez wartość, a nie przez odwołanie, i są używane rejestry dodatkowe. Miejsca stosu w tle przydzielone dla argumentów typu wektora jest ustalony na 8 bajtów i [/homeparams](../build/reference/homeparams-copy-register-parameters-to-stack.md) opcja nie dotyczy. Argumentów typu wektora w pozycji siódmego i nowsze parametrów są przekazywane na stosie w odniesieniu do pamięci przydzielonej przez obiekt wywołujący.  
  
 Po rejestrów są przydzielone dla argumentów wektora, elementy członkowskie danych argumentów HVA są przydzielone, rosnąco do nieużywanych wektor rejestrach XMM0 XMM5 (lub YMM0 do YMM5, dla `__m256` typy), jak długo są dostępne dla wystarczającej liczby rejestrów cały HVA. Jeśli nie wystarczającej liczby rejestrów są dostępne, HVA argument jest przekazywana przez odwołanie do pamięci przydzielonej przez obiekt wywołujący. Miejsca stosu w tle dla argumentu HVA ustala się na 8 bajtów z zawartością niezdefiniowany. Argumenty HVA są przypisane do rejestrów w kolejności od lewej do prawej na liście parametrów i może znajdować się w dowolnym miejscu. HVA argumentów w jednym z pierwszych czterech argumentu pozycji, które nie są przypisane do wektorów rejestrów są przekazywane przez odwołanie w rejestrze liczba całkowita, która odpowiada na tej pozycji. Argumenty HVA przekazywana przez odwołanie, po czwartym pozycja parametru są przenoszone na stosie.  
  
 Wyniki `__vectorcall` funkcje są zwracane przez wartość w rejestrach, gdy jest to możliwe. Typu Liczba całkowita, tym struktury lub Unii 8 bajtów lub mniej, są zwracane przez wartość w RAX. Wektor typu są zwracane przez wartość XMM0 lub YMM0, w zależności od wielkości. Wyniki HVA muszą każdego elementu danych zwracanych przez wartość w rejestrach XMM0:XMM3 lub YMM0:YMM3, w zależności od rozmiaru elementu. Typy wyników, które nie mieszczą się w rejestrach odpowiedniego są zwracane przez odwołanie do pamięci przydzielonej przez obiekt wywołujący.  
  
 Stos jest obsługiwana przez obiekt wywołujący w x64 implementacja `__vectorcall`. Prolog i epilog kod wywołujący przydziela i spowoduje wyczyszczenie stosu dla wywołanej funkcji. Argumenty są przenoszone na stosie od prawej do lewej, a tle stosu miejsce jest przydzielane dla argumentów przekazywane w rejestrach.  
  
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
  
## <a name="vectorcall-convention-on-x86"></a>__vectorcall Konwencja na x86  
 `__vectorcall` Następujące konwencji wywoływania `__fastcall` Konwencji dla argumentów typu Liczba całkowita 32-bitowe i wykorzystuje rejestrów wektor SSE argumenty HVA i typu wektora.  
  
 Pierwszy całkowitą dwóch argumentów typu znaleziona na liście parametrów od lewej do prawej są umieszczane w ECX i EDX, odpowiednio Ukryty `this` wskaźnika jest traktowany jako pierwszy argument typu Liczba całkowita i jest przekazywany ECX. Pierwszy argumentów typu wektora sześciu są przekazywane przez wartość za pośrednictwem rejestrów wektor SSE 0 – 5, w rejestrach XMM lub YMM, w zależności od wielkości argumentu.  
  
 Pierwszy sześciu wektorów argumentów typu w kolejności od lewej do prawej są przekazywane przez wartość w rejestrach wektor SSE 0 – 5. Zmiennoprzecinkowe i `__m128` typy są przekazywane w rejestrach XMM i `__m256` typy są przekazywane w YMM rejestruje. Nie miejsca na stosie tle został przydzielony dla argumentów typu wektora przekazany przez rejestr. Wektor siódmego i kolejne argumenty typu są przekazywane na stosie w odniesieniu do pamięci przydzielonej przez obiekt wywołujący. Błąd kompilatora ograniczenia [C2719](../error-messages/compiler-errors-2/compiler-error-c2719.md) nie ma zastosowania do tych argumentów.  
  
 Po rejestrów są przydzielone dla argumentów wektora, dane członkami HVA argumenty są przydzielane w kolejności rosnącej do nieużywanych wektor rejestruje XMM0 do XMM5 (lub YMM0 do YMM5, dla `__m256` typy), jak długo są dostępne dla całej wystarczającej liczby rejestrów HVA. Jeśli nie wystarczającej liczby rejestrów są dostępne, HVA argument jest przekazywany na stosie w odniesieniu do pamięci przydzielonej przez obiekt wywołujący. Nie miejsca na stosie tle argumentu HVA został przydzielony. Argumenty HVA są przypisane do rejestrów w kolejności od lewej do prawej na liście parametrów i może znajdować się w dowolnym miejscu.  
  
 Wyniki `__vectorcall` funkcje są zwracane przez wartość w rejestrach, gdy jest to możliwe. Typu Liczba całkowita, tym struktury lub Unii 4 bajty lub mniej, są zwracane przez wartość EAX. Unie 8 bajtów lub mniej lub struktur typu Liczba całkowita są zwracane przez wartość EDX:EAX. Wektor typu są zwracane przez wartość XMM0 lub YMM0, w zależności od wielkości. Wyniki HVA muszą każdego elementu danych zwracanych przez wartość w rejestrach XMM0:XMM3 lub YMM0:YMM3, w zależności od rozmiaru elementu. Inne typy wyników są zwracane przez odwołanie do pamięci przydzielonej przez obiekt wywołujący.  
  
 X86 implementacja `__vectorcall` następujące Konwencji argumenty wypychana na stosie od prawej do lewej przez wywołującego i wywołana funkcja spowoduje wyczyszczenie stosu tuż przed zwraca. Tylko argumenty, które nie znajdują się w rejestrach są przenoszone na stosie.  
  
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
  
 **Końcowy określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)