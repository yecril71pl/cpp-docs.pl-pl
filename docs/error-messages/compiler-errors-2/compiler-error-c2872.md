---
title: Błąd kompilatora C2872
ms.date: 11/04/2016
f1_keywords:
- C2872
helpviewer_keywords:
- C2872
ms.assetid: c619ef97-6e0e-41d7-867c-f8d28a07d553
ms.openlocfilehash: f57b250f87bd7f2c5808b5a681ddfe49dfa5e876
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228898"
---
# <a name="compiler-error-c2872"></a>Błąd kompilatora C2872

"*symbol*": niejednoznaczny symbol

Kompilator nie może określić, do którego symbolu odwołuje się. Więcej niż jeden symbol o określonej nazwie znajduje się w zakresie. Zobacz uwagi poniżej komunikatu o błędzie dla lokalizacji plików i deklaracji, które kompilator znalazł dla niejednoznacznego symbolu. Aby rozwiązać ten problem, można w pełni kwalifikować niejednoznaczny symbol przy użyciu jego przestrzeni nazw, na przykład `std::byte` lub `::byte` . Można również użyć [aliasu przestrzeni nazw](../../cpp/namespaces-cpp.md#namespace_aliases) , aby nadać dołączonej przestrzeni nazw dogodną krótką nazwę do użycia podczas niejednoznaczności symboli w kodzie źródłowym.

C2872 może wystąpić, jeśli plik nagłówkowy zawiera [dyrektywę using](../../cpp/namespaces-cpp.md#using_directives)i zostanie dołączony kolejny plik nagłówkowy zawierający typ, który jest również w przestrzeni nazw określonej w **`using`** dyrektywie. Należy określić **`using`** dyrektywę tylko po określeniu wszystkich plików nagłówkowych przy użyciu `#include` .

C2872 może wystąpić w Visual Studio 2013 ze względu na konflikt między `Windows::Foundation::Metadata::Platform` typem wyliczenia a `Platform` przestrzenią nazw C++/CX-Defined. Aby obejść ten problem, wykonaj następujące kroki:

- Usuń klauzulę "Używanie przestrzeni nazw Windows:: Foundation:: Metadata" z plików projektu.

- Określ w pełni kwalifikowaną nazwę dowolnego typu, który jest zawarty w tej przestrzeni nazw.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2872, ponieważ niejednoznaczne odwołanie do zmiennej o nazwie `i` ; dwie zmienne o tej samej nazwie znajdują się w zakresie:

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
