---
title: Kompilator ostrzeżenie (poziom 4) C4061
ms.date: 04/05/2019
f1_keywords:
- C4061
helpviewer_keywords:
- C4061
ms.assetid: a99cf88e-7941-4519-8b1b-f6889d914b2f
ms.openlocfilehash: 073e3e9cb1cb5bb6b0f66157c986072227960212
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59237123"
---
# <a name="compiler-warning-level-4-c4061"></a>Kompilator ostrzeżenie (poziom 4) C4061

> Moduł wyliczający "*identyfikator*'w przełączniku Enum'*wyliczenie*" nie jest jawnie obsługiwany przez etykietę case

Określony moduł wyliczający *identyfikator* powoduje nie skojarzony program obsługi `switch` instrukcję, która ma `default` przypadek. Brak przypadku może być nadzoru, lub może być problem. Go może zależeć od tego, czy moduł wyliczający jest obsługiwany przez przypadek domyślny, czy nie. Powiązane ostrzeżenia na nieużywanych moduły wyliczające w `switch` instrukcji, które nie mają `default` przypadku zobacz [C4062](compiler-warning-level-4-c4062.md).

To ostrzeżenie jest domyślnie wyłączona. Aby uzyskać więcej informacji o sposobie włączania ostrzeżeń, które są domyślnie wyłączone, zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4061; Dodaj przypadek dla brakuje typu wyliczeniowego rozwiązać problem:

```cpp
// C4061.cpp
// compile with: /W4
#pragma warning(default : 4061)

enum E { a, b, c };
void func ( E e )
{
   switch(e)
   {
      case a:
      case b:
      default:
         break;
   }   // C4061 c' not handled
}

int main()
{
}
```

## <a name="see-also"></a>Zobacz także

[Ostrzeżenie kompilatora (poziom 4) C4062](compiler-warning-level-4-c4062.md)
