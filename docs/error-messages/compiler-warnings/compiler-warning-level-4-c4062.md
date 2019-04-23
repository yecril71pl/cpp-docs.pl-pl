---
title: Kompilator ostrzeżenie (poziom 4) C4062
ms.date: 04/05/2019
f1_keywords:
- C4062
helpviewer_keywords:
- C4062
ms.assetid: 36d1c6ae-c917-4b08-bf30-2eb49ee94169
ms.openlocfilehash: 79658afc31565b708cdbd8a88f49b887cdd10cf3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59237188"
---
# <a name="compiler-warning-level-4-c4062"></a>Kompilator ostrzeżenie (poziom 4) C4062

> Moduł wyliczający "*identyfikator*'w przełączniku Enum'*wyliczenie*" nie jest obsługiwany

Moduł wyliczający *identyfikator* nie ma przypisanego skojarzone `case` obsługi w `switch` instrukcji i ma nie `default` etykietę, która może przechwycić go. Brak przypadku może być nadzoru i potencjalny błąd w kodzie. Powiązane ostrzeżenia na nieużywanych moduły wyliczające w `switch` instrukcje, które `default` przypadku zobacz [C4061](compiler-warning-level-4-c4061.md).

To ostrzeżenie jest domyślnie wyłączona. Aby uzyskać więcej informacji o sposobie włączania ostrzeżeń, które są domyślnie wyłączone, zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

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
