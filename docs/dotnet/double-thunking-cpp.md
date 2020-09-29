---
title: Podwójna konwersja bitowa adresów (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- double thunks
- interop [C++], double thunking
- mixed assemblies [C++], double thunking
- /clr compiler option [C++], double thunking
- interoperability [C++], double thunking
ms.assetid: a85090b2-dc3c-498a-b40c-340db229dd6f
ms.openlocfilehash: 3f0fc5567baaa0c4f3fea410770963adf51e8366
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414012"
---
# <a name="double-thunking-c"></a>Podwójna konwersja bitowa adresów (C++)

Podwójny podwójna odnosi się do utraty wydajności, która może wystąpić, gdy wywołanie funkcji w kontekście zarządzanym wywołuje funkcję zarządzaną Visual C++ i gdzie wykonywanie programu wywołuje natywny punkt wejścia funkcji w celu wywołania funkcji zarządzanej. W tym temacie omówiono, gdzie występuje podwójny podwójna oraz jak można uniknąć poprawy wydajności.

## <a name="remarks"></a>Uwagi

Domyślnie podczas kompilowania z **/CLR**, definicja funkcji zarządzanej powoduje, że kompilator generuje zarządzany punkt wejścia i natywny punkt wejścia. Umożliwia to wywoływanie funkcji zarządzanej z natywnych i zarządzanych lokacji wywołań. Jeśli jednak istnieje natywny punkt wejścia, może to być punkt wejścia dla wszystkich wywołań funkcji. W przypadku zarządzania funkcją wywołującą, natywny punkt wejścia będzie wywoływał zarządzany punkt wejścia. W efekcie dwa wywołania są wymagane do wywołania funkcji (w związku z tym podwójne podwójna). Na przykład funkcje wirtualne są zawsze wywoływane za pomocą natywnego punktu wejścia.

Jednym z rozwiązań jest informowanie kompilatora, aby nie generował natywnego punktu wejścia dla funkcji zarządzanej, że funkcja zostanie wywołana tylko z kontekstu zarządzanego, przy użyciu konwencji wywoływania [__clrcall](../cpp/clrcall.md) .

Podobnie, Jeśli eksportujesz ([dllexport, dllimport](../cpp/dllexport-dllimport.md)) funkcję zarządzaną, zostanie wygenerowany natywny punkt wejścia i każda funkcja, która importuje i wywołuje tę funkcję, będzie wywoływała za pomocą natywnego punktu wejścia. Aby uniknąć podwójnego podwójna w tej sytuacji, nie używaj natywnej semantyki eksportu/importu; po prostu Odwołuj się do metadanych za pośrednictwem `#using` (patrz [#using dyrektywa](../preprocessor/hash-using-directive-cpp.md)).

Kompilator został zaktualizowany, aby zmniejszyć niepotrzebne podwójne podwójna. Na przykład każda funkcja z typem zarządzanym w sygnaturze (łącznie z typem zwracanym) zostanie niejawnie oznaczona jako `__clrcall` .

## <a name="example-double-thunking"></a>Przykład: Double podwójna

### <a name="description"></a>Opis

Poniższy przykład ilustruje podwójny podwójna. W przypadku skompilowania natywnego (bez **/CLR**) wywołanie funkcji wirtualnej w programie `main` generuje jedno wywołanie `T` konstruktora kopiującego i jedno wywołanie do destruktora. Podobne zachowanie jest realizowane, gdy funkcja wirtualna jest zadeklarowana z **/CLR** i `__clrcall` . Jednak po prostu skompilowane z **/CLR**wywołanie funkcji generuje wywołanie konstruktora kopiującego, ale istnieje inne wywołanie konstruktora kopiującego ze względu na natywny thunk.

### <a name="code"></a>Kod

```cpp
// double_thunking.cpp
// compile with: /clr
#include <stdio.h>
struct T {
   T() {
      puts(__FUNCSIG__);
   }

   T(const T&) {
      puts(__FUNCSIG__);
   }

   ~T() {
      puts(__FUNCSIG__);
   }

   T& operator=(const T&) {
      puts(__FUNCSIG__);
      return *this;
   }
};

struct S {
   virtual void /* __clrcall */ f(T t) {};
} s;

int main() {
   S* pS = &s;
   T t;

   printf("calling struct S\n");
   pS->f(t);
   printf("after calling struct S\n");
}
```

### <a name="sample-output"></a>Przykładowe dane wyjściowe

```
__thiscall T::T(void)
calling struct S
__thiscall T::T(const struct T &)
__thiscall T::T(const struct T &)
__thiscall T::~T(void)
__thiscall T::~T(void)
after calling struct S
__thiscall T::~T(void)
```

## <a name="example-effect-of-double-thunking"></a>Przykład: efekt podwójnej podwójna

### <a name="description"></a>Opis

W poprzednim przykładzie przedstawiono istnienie podwójnej podwójna. Ten przykład pokazuje jego efekt. **`for`** Pętla wywołuje funkcję wirtualną, a program zgłasza czas wykonywania. Najwolniejszy czas jest raportowany, gdy program jest kompilowany z **/CLR**. Najszybsze czasy są raportowane w przypadku kompilowania bez **/CLR** lub jeśli funkcja wirtualna jest zadeklarowana za pomocą `__clrcall` .

### <a name="code"></a>Kod

```cpp
// double_thunking_2.cpp
// compile with: /clr
#include <time.h>
#include <stdio.h>

#pragma unmanaged
struct T {
   T() {}
   T(const T&) {}
   ~T() {}
   T& operator=(const T&) { return *this; }
};

struct S {
   virtual void /* __clrcall */ f(T t) {};
} s;

int main() {
   S* pS = &s;
   T t;
   clock_t start, finish;
   double  duration;
   start = clock();

   for ( int i = 0 ; i < 1000000 ; i++ )
      pS->f(t);

   finish = clock();
   duration = (double)(finish - start) / (CLOCKS_PER_SEC);
   printf( "%2.1f seconds\n", duration );
   printf("after calling struct S\n");
}
```

### <a name="sample-output"></a>Przykładowe dane wyjściowe

```
4.2 seconds
after calling struct S
```

## <a name="see-also"></a>Zobacz także

[Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)
