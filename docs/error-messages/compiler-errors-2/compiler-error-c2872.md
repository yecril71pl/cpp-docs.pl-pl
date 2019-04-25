---
title: Błąd kompilatora C2872
ms.date: 11/04/2016
f1_keywords:
- C2872
helpviewer_keywords:
- C2872
ms.assetid: c619ef97-6e0e-41d7-867c-f8d28a07d553
ms.openlocfilehash: 103998c7872b683c7405796ee28bd550246ae9bf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257617"
---
# <a name="compiler-error-c2872"></a>Błąd kompilatora C2872

"*symbol*": niejednoznaczny symbol

Kompilator nie może określić symbol, który odnosi się do. Więcej niż jeden symbol o określonej nazwie znajduje się w zakresie. Zobacz uwagi na końcu komunikat o błędzie dla lokalizacji plików i deklaracje kompilatora znaleziono niejednoznaczny symbol. Aby rozwiązać ten problem, można pełnej kwalifikacji niejednoznaczny symbol za pomocą jego przestrzeń nazw, na przykład `std::byte` lub `::byte`. Można również użyć [alias przestrzeni nazw](../../cpp/namespaces-cpp.md#namespace_aliases) zapewnienie uwzględnianych przestrzeni nazw wygodne krótką nazwę do użycia podczas usuwania niejednoznaczności w nazwach symboli w kodzie źródłowym.

C2872 może wystąpić, jeśli zawiera plik nagłówkowy [użycie dyrektywy](../../cpp/namespaces-cpp.md#using_directives), i znajduje się plik nagłówkowy kolejnych zawierający typ, który jest również w przestrzeni nazw określonej w `using` dyrektywy. Określ `using` dyrektywy dopiero po wszystkie pliki nagłówkowe są określane za pomocą `#include`.

C2872 może wystąpić w programie Visual Studio 2013, ze względu na konflikt między `Windows::Foundation::Metadata::Platform` typu wyliczeniowego i C++/zdefiniowane CX `Platform` przestrzeni nazw. Aby obejść ten problem, wykonaj następujące kroki:

- Usuń klauzulę "za pomocą Windows::Foundation::Metadata przestrzeni nazw" z plików projektu.

- Określ w pełni kwalifikowana nazwa dowolnego typu, który znajduje się w tej przestrzeni nazw.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2872, ponieważ wykonano niejednoznaczne odwołanie do zmiennej o nazwie `i`; dwie zmienne o takiej samej nazwie znajdują się w zakresie:

```cpp
// C2872.cpp
// compile with: cl /EHsc C2872.cpp
namespace A {
   int i;
}

using namespace A;
int i;
int main() {
   ::i++;   // ok, uses i from global namespace
   A::i++;   // ok, uses i from namespace A
   i++;   // C2872 ambiguous: ::i or A::i?
   // To fix this issue, use the fully qualified name
   // for the intended variable.
}
```
