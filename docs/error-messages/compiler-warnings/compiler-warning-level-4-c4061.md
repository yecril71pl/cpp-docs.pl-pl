---
title: Kompilatora (poziom 4) ostrzeżenie C4061 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/30/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4061
dev_langs:
- C++
helpviewer_keywords:
- C4061
ms.assetid: a99cf88e-7941-4519-8b1b-f6889d914b2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d0086ea5e590c7183024bc4dcc93e2f2522f483
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292623"
---
# <a name="compiler-warning-level-4-c4061"></a>Kompilator C4061 ostrzegawcze (poziom 4)

> Moduł wyliczający "*identyfikator*"w switch wyliczenia"*wyliczenie*" nie jest jawnie obsługiwany przez etykietę case

Moduł wyliczający nie ma żadnych skojarzony program obsługi w `switch` instrukcji.

To ostrzeżenie jest domyślnie wyłączone. Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4061; Dodawanie przypadku dla brakujących modułu wyliczającego ustalenie:

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