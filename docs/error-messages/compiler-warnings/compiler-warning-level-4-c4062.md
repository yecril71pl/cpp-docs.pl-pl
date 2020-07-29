---
title: Ostrzeżenie kompilatora (poziom 4) C4062
ms.date: 04/05/2019
f1_keywords:
- C4062
helpviewer_keywords:
- C4062
ms.assetid: 36d1c6ae-c917-4b08-bf30-2eb49ee94169
ms.openlocfilehash: efe021c9994e20f2630e31537bcc6099783b4308
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220005"
---
# <a name="compiler-warning-level-4-c4062"></a>Ostrzeżenie kompilatora (poziom 4) C4062

> moduł wyliczający "*Identifier*" w instrukcji Switch*wyliczenia "enum" nie*jest obsługiwany

*Identyfikator* modułu wyliczającego nie ma skojarzonego `case` programu obsługi w **`switch`** instrukcji i nie ma **`default`** etykiety, która może go przechwycić. Brakująca sprawa może być nadzorem i jest potencjalnym błędem w kodzie. Aby uzyskać ostrzeżenie dotyczące nieużywanych modułów wyliczających w **`switch`** instrukcjach **`default`** , które mają przypadek, zobacz [C4061](compiler-warning-level-4-c4061.md).

To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji o sposobie włączania ostrzeżeń, które są domyślnie wyłączone, zobacz [ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C4062 i pokazuje, jak go naprawić:

```cpp
// C4062.cpp
// compile with: /EHsc /W4
#pragma warning(default : 4062)
enum E { a, b, c };
void func ( E e ) {
   switch(e) {
      case a:
      case b:
   // case c:  // to fix, uncomment this line
      break;   // no default label
   }   // C4062, enumerator 'c' not handled
}

int main() {
}
```

## <a name="see-also"></a>Zobacz także

[Ostrzeżenie kompilatora (poziom 4) C4061](compiler-warning-level-4-c4061.md)
