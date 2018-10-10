---
title: Błąd kompilatora C2872 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2872
dev_langs:
- C++
helpviewer_keywords:
- C2872
ms.assetid: c619ef97-6e0e-41d7-867c-f8d28a07d553
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4bdc67e13db11949371e2f9e3d8a205b146d701
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890119"
---
# <a name="compiler-error-c2872"></a>Błąd kompilatora C2872

"*symbol*": niejednoznaczny symbol

Kompilator nie może określić symbol, który odnosi się do. Więcej niż jeden symbol o określonej nazwie znajduje się w zakresie. Zobacz uwagi na końcu komunikat o błędzie dla lokalizacji plików i deklaracje kompilatora znaleziono niejednoznaczny symbol. Aby rozwiązać ten problem, można pełnej kwalifikacji niejednoznaczny symbol za pomocą jego przestrzeń nazw, na przykład `std::byte` lub `::byte`. Można również użyć [alias przestrzeni nazw](../../cpp/namespaces-cpp.md#namespace_aliases) zapewnienie uwzględnianych przestrzeni nazw wygodne krótką nazwę do użycia podczas usuwania niejednoznaczności w nazwach symboli w kodzie źródłowym.

C2872 może wystąpić, jeśli zawiera plik nagłówkowy [użycie dyrektywy](../../cpp/namespaces-cpp.md#using_directives), i znajduje się plik nagłówkowy kolejnych zawierający typ, który jest również w przestrzeni nazw określonej w `using` dyrektywy. Określ `using` dyrektywy dopiero po wszystkie pliki nagłówkowe są określane za pomocą `#include`.

C2872 może wystąpić w programie Visual Studio 2013, ze względu na konflikt między `Windows::Foundation::Metadata::Platform` wyliczenia typu i C + +/ CX, zdefiniowane `Platform` przestrzeni nazw. Aby obejść ten problem, wykonaj następujące kroki:

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