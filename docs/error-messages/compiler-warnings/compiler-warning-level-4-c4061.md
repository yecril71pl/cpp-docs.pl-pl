---
title: "Kompilatora (poziom 4) ostrzeżenie C4061 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4061
dev_langs: C++
helpviewer_keywords: C4061
ms.assetid: a99cf88e-7941-4519-8b1b-f6889d914b2f
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 930cca345b23cc9a9122aea14a55e499f01ae710
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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