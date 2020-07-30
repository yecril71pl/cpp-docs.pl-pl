---
title: Ostrzeżenie kompilatora (poziom 4) C4459
ms.date: 11/04/2016
f1_keywords:
- C4459
helpviewer_keywords:
- C4459
ms.assetid: ee9f6287-9c70-4b10-82a0-add82a13997f
ms.openlocfilehash: d6d0a802f9f628145fbc5910aca805a5b01b94d2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214376"
---
# <a name="compiler-warning-level-4-c4459"></a>Ostrzeżenie kompilatora (poziom 4) C4459

> Deklaracja elementu "*Identifier*" powoduje ukrycie deklaracji globalnej

Deklaracja *identyfikatora* w zakresie lokalnym powoduje ukrycie deklaracji o identycznym *identyfikatorze* w zakresie globalnym. To ostrzeżenie informuje o tym, że odwołania do *identyfikatora* w tym zakresie są rozpoznawane jako wersja zadeklarowana lokalnie, a nie w wersji globalnej, która może być lub nie być zamiarem. Ogólnie rzecz biorąc, zalecamy zminimalizowanie użycia zmiennych globalnych jako dobrego postępowania inżynieryjnego. Aby zminimalizować zanieczyszczenie globalnej przestrzeni nazw, zalecamy użycie nazwanej przestrzeni nazw dla zmiennych globalnych.

To ostrzeżenie było Nowość w programie Visual Studio 2015 w kompilatorze Microsoft C++ w wersji 18,00. Aby pominąć ostrzeżenia z tej wersji kompilatora lub później podczas migrowania kodu, użyj opcji kompilatora [/WV: 18](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Przykład

Poniższy przykład generuje C4459:

```cpp
// C4459_hide.cpp
// compile with: cl /W4 /EHsc C4459_hide.cpp
int global_or_local = 1;

int main() {
    int global_or_local; // warning C4459
    global_or_local = 2;
}
```

Jednym ze sposobów rozwiązania tego problemu jest utworzenie przestrzeni nazw dla Globals, ale nie użycie **`using`** dyrektywy w celu przeniesienia tej przestrzeni nazw do zakresu, dlatego wszystkie odwołania muszą używać nazw kwalifikowanych niejednoznacznie:

```cpp
// C4459_namespace.cpp
// compile with: cl /W4 /EHsc C4459_namespace.cpp
namespace globals {
    int global_or_local = 1;
}

int main() {
    int global_or_local; // OK
    global_or_local = 2;
    globals::global_or_local = 3;
}
```
