---
title: Ostrzeżenie kompilatora (poziom 2) C4412
ms.date: 11/04/2016
f1_keywords:
- C4412
helpviewer_keywords:
- C4412
ms.assetid: f28dc531-1a98-497b-a366-0a13e1bc81c7
ms.openlocfilehash: 79b4ac95fbac344ff86922b84870e01c6681ed69
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684996"
---
# <a name="compiler-warning-level-2-c4412"></a>Ostrzeżenie kompilatora (poziom 2) C4412

> "*Function*": Sygnatura funkcji zawiera typ "*Type*"; Obiekty C++ nie mogą być przekazywane między czystym kodem a mieszaniem i natywnym.

## <a name="remarks"></a>Uwagi

**/CLR: Pure** kompilator Option jest przestarzały w programie visual Studio 2015 i nieobsługiwany w programie visual Studio 2017. Jeśli masz kod, który musi być czysty, zalecamy przekazanie go do języka C#.

Kompilator wykrył potencjalnie niebezpieczną sytuację, która może spowodować błąd w czasie wykonywania: wywołanie jest wykonywane z **/CLR: Pure** jednostka kompilacji do funkcji zaimportowanej za pośrednictwem elementu dllimport, a sygnatura funkcji zawiera niebezpieczny typ. Typ jest niebezpieczny, jeśli zawiera funkcję członkowską lub ma element członkowski danych, który jest niebezpiecznym typem lub pośrednim do niebezpiecznego typu.

Jest to niebezpieczne z powodu różnic w domyślnych konwencjach wywoływania między kodem czystym i natywnym (lub mieszanym natywnym i zarządzanym). Podczas importowania (za pośrednictwem `dllimport` ) funkcji do **/CLR: Pure** jednostka kompilacji upewnij się, że deklaracje każdego typu w podpisie są identyczne z tymi w jednostka kompilacji, które eksportują funkcję (są szczególnie ważne w przypadku różnic w niejawnych konwencjach wywoływania).

Wirtualna funkcja członkowska jest szczególnie podatna na zadawanie nieoczekiwanych wyników.  Jednak nawet niewirtualna funkcja powinna być testowana, aby upewnić się, że są odpowiednie wyniki. Jeśli masz pewność, że otrzymujesz poprawne wyniki, możesz zignorować to ostrzeżenie.

C4412 jest domyślnie wyłączona. Zobacz [ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md) i [dllexport, dllimport,](../../cpp/dllexport-dllimport.md) Aby uzyskać więcej informacji.

Aby usunąć to ostrzeżenie, Usuń wszystkie funkcje z typu.

## <a name="examples"></a>Przykłady

Poniższy przykład generuje C4412.

```cpp
// C4412.cpp
// compile with: /c /W2 /clr:pure
#pragma warning (default : 4412)

struct Unsafe {
   virtual void __cdecl Test();
};

struct Safe {
   int i;
};

__declspec(dllimport) Unsafe * __cdecl func();
__declspec(dllimport) Safe * __cdecl func2();

int main() {
   Unsafe *pUnsafe = func();   // C4412
   // pUnsafe->Test();

   Safe *pSafe = func2();   // OK
}
```

Poniższy przykład to plik nagłówka, który deklaruje dwa typy. `Unsafe`Typ jest niebezpieczny, ponieważ ma funkcję członkowską.

```cpp
// C4412.h
struct Unsafe {
   // will be __clrcall if #included in pure compilation
   // defaults to __cdecl in native or mixed mode compilation
   virtual void Test(int * pi);

   // try the following line instead
   // virtual void __cdecl Test(int * pi);
};

struct Safe {
   int i;
};
```

Ten przykład eksportuje funkcje z typami zdefiniowanymi w pliku nagłówkowym.

```cpp
// C4412_2.cpp
// compile with: /LD
#include "C4412.h"

void Unsafe::Test(int * pi) {
   *pi++;
}

__declspec(dllexport) Unsafe * __cdecl func() { return new Unsafe; }
__declspec(dllexport) Safe * __cdecl func2() { return new Safe; }
```

Domyślna konwencja wywoływania w funkcji **/CLR: Pure** kompilacja różni się od kompilacji natywnej.  Gdy zostanie uwzględniony C4412. h, `Test` wartością domyślną jest `__clrcall` . W przypadku kompilowania i uruchamiania tego programu (nie należy używać **/c**) program zgłosi wyjątek.

Poniższy przykład generuje C4412.

```cpp
// C4412_3.cpp
// compile with: /W2 /clr:pure /c /link C4412_2.lib
#pragma warning (default : 4412)
#include "C4412.h"

__declspec(dllimport) Unsafe * __cdecl func();
__declspec(dllimport) Safe * __cdecl func2();

int main() {
   int n = 7;
   Unsafe *pUnsafe = func();   // C4412
   pUnsafe->Test(&n);

   Safe *pSafe = func2();   // OK
}
```
