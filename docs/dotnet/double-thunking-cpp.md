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
ms.openlocfilehash: 984a20d701b159820a94483fe9d3743f015b71f6
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741962"
---
# <a name="double-thunking-c"></a>Podwójna konwersja bitowa adresów (C++)

Podwójna konwersja bitowa odnosi się do utraty wydajności występujący podczas wywołania funkcji w wywołaniach kontekście zarządzanych, Visual C++ zarządzane funkcji i których wykonywania programu wywołuje — funkcja natywnego punktu wejścia w celu wywołania funkcji zarządzanej. W tym temacie omówiono, gdzie występuje podwójna i jak można uniknąć, aby zwiększyć wydajność.

## <a name="remarks"></a>Uwagi

Domyślnie podczas kompilowania za pomocą **/CLR**, definicja funkcji zarządzanej powoduje, że kompilator do generowania punktem wejścia zarządzanego i natywnego punktu wejścia. Dzięki temu funkcji zarządzanej do wywoływania z wywołania natywnego i zarządzanego. Jednak jeśli istnieje natywnego punktu wejścia, może być punkt wejścia dla wszystkich wywołań funkcji. Jeśli funkcja wywołująca jest zarządzany, natywnego punktu wejścia zostanie następnie wywołać zarządzany punkt wejścia. W efekcie dwóch wywołań są wymagane do wywołania funkcji (z tego powodu podwójna konwersja bitowa adresów). Na przykład funkcje wirtualne zawsze są wywoływane za pośrednictwem natywnego punktu wejścia.

Można poinformować kompilator, aby nie generować natywnego punktu wejścia dla funkcji zarządzanych, czy funkcja będzie zostać wywołana tylko z zarządzanych kontekstu przy użyciu [__clrcall](../cpp/clrcall.md) konwencji wywoływania.

Podobnie jeśli eksportujesz ([dllexport i dllimport](../cpp/dllexport-dllimport.md)) funkcji zarządzanej, generowany jest natywnego punktu wejścia i wywoła żadnej funkcji, które importuje i wywołuje tę funkcję za pomocą natywnego punktu wejścia. Aby uniknąć podwójna w takiej sytuacji, należy używać importu/eksportu natywny semantyki; po prostu odwoływać się do metadanych za pomocą `#using` (zobacz [# dyrektywa using](../preprocessor/hash-using-directive-cpp.md)).

Kompilator został zaktualizowany tak, aby ograniczyć niepotrzebne podwójna konwersja bitowa. Na przykład dowolnej funkcji z zarządzanym typem w sygnaturze (łącznie z typem zwracanym) zostanie niejawnie oznaczone jako `__clrcall`. Aby uzyskać więcej informacji na temat zniesienie podwójnego thunk, zobacz [ https://msdn.microsoft.com/msdnmag/issues/05/01/COptimizations/default.aspx ](https://msdn.microsoft.com/msdnmag/issues/05/01/COptimizations/default.aspx).

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

W poniższym przykładzie pokazano, Podwójna. Podczas kompilowania natywne (bez **/CLR**), wywołanie funkcji wirtualnej w `main` generuje jedno wywołanie `T`firmy kopiowanie konstruktora i jedno wywołanie destruktora. Podobne zachowanie jest osiągana, gdy funkcja wirtualna jest zadeklarowana za pomocą **/CLR** i `__clrcall`. Jednak gdy tylko skompilowano z opcją **/CLR**, wywołanie funkcji generuje wywołanie konstruktora kopiującego, ale ma inne wywołanie konstruktora kopiującego, ze względu na thunk native zarządzane.

### <a name="code"></a>Kod

```
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

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poprzedni przykład przedstawione na istnienie podwójna. Niniejszy przykład pokazuje jego wpływu. `for` Pętli wywołuje funkcję wirtualną i czas wykonywania raportów programu. Najwolniejsze czas jest zgłaszany, gdy program jest skompilowany przy użyciu **/CLR**. Najszybszy czas, w którym są zgłaszane podczas kompilowania kodu bez **/CLR** lub jeśli funkcja wirtualna jest zadeklarowana za pomocą `__clrcall`.

### <a name="code"></a>Kod

```
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
