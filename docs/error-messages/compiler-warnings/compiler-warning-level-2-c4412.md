---
title: Kompilator ostrzeżenie (poziom 2) C4412
ms.date: 11/04/2016
f1_keywords:
- C4412
helpviewer_keywords:
- C4412
ms.assetid: f28dc531-1a98-497b-a366-0a13e1bc81c7
ms.openlocfilehash: 2c9d50fc3433321c0ca92366a512892212545754
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665520"
---
# <a name="compiler-warning-level-2-c4412"></a>Kompilator ostrzeżenie (poziom 2) C4412

> "*funkcja*': podpis funkcji podpis zawiera typ"*typu*'; Obiekty C++ są bezpieczne przekazywanie między kodem czystym i mieszanym lub macierzystym.

## <a name="remarks"></a>Uwagi

**/CLR: pure** — opcja kompilatora jest przestarzała w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017. Jeśli masz kod, który musi być czysty, firma Microsoft zaleca przenosi go na C#.

Kompilator wykrył potencjalnie niebezpieczną sytuację, która może spowodować błąd w czasie wykonywania: wykonywane jest wywołanie z **/CLR: pure** compiland — do funkcji, który został zaimportowany za pośrednictwem dllimport i sygnatura funkcji zawiera niezabezpieczonego typu . Typ jest niebezpieczne, jeśli zawiera funkcję członkowską, lub ma element członkowski danych, który jest niezabezpieczonego typu lub pośrednio do niezabezpieczonego typu.

To jest niebezpieczne ze względu na różnice w domyślnej Konwencji między kod czysty i natywnych wywoływania (lub mieszanych natywnego i zarządzanego). Podczas importowania (za pośrednictwem `dllimport`) funkcji do **/CLR: pure** compiland —, upewnij się, że deklaracje każdego typu w podpisie są identyczne z tymi w compiland —, które eksportuje — funkcja (ostrożność szczególnie różnice w niejawne konwencji wywoływania.)

Funkcja wirtualna elementu członkowskiego jest szczególnie podatne na dawać nieoczekiwane wyniki.  Jednak nawet funkcję niewirtualną powinien zostać przetestowany, aby upewnić się, że masz prawidłowe wyniki. Jeśli masz pewność, że pojawiają się poprawne wyniki, możesz zignorować to ostrzeżenie.

C4412 jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) i [dllexport i dllimport](../../cpp/dllexport-dllimport.md) Aby uzyskać więcej informacji.

Aby rozwiązać tego ostrzeżenia, należy usunąć wszystkie funkcje z typu.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4412.

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

## <a name="example"></a>Przykład

Poniższy przykład jest plik nagłówka, który deklaruje dwa typy. `Unsafe` Typu jest niebezpieczne, ponieważ ma on funkcję członkowską.

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

## <a name="example"></a>Przykład

W tym przykładzie eksportuje funkcje przy użyciu typów zdefiniowanych w pliku nagłówkowym.

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

## <a name="example"></a>Przykład

Domyślną konwencję wywoływania **/CLR: pure** kompilacja różni się od natywnej kompilacji.  Gdy wchodzi C4412.h `Test` wartość domyślna to `__clrcall`. Jeśli możesz skompilować i uruchomić ten program (nie używaj **/c**), program spowoduje zgłoszenie wyjątku.

Poniższy przykład spowoduje wygenerowanie C4412.

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