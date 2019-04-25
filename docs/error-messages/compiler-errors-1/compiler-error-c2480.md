---
title: Błąd kompilatora C2480
ms.date: 11/04/2016
f1_keywords:
- C2480
helpviewer_keywords:
- C2480
ms.assetid: 1a58d1c2-971b-4084-96fa-f94aa51c02f1
ms.openlocfilehash: 90016b65d4ddd58da3fb3c5ab6d81322dc0ef394
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187619"
---
# <a name="compiler-error-c2480"></a>Błąd kompilatora C2480

'Identyfikator': "thread" jest prawidłowy tylko dla elementów danych statycznego obszaru

Nie można użyć `thread` atrybut automatycznej zmiennej, niestatycznej składowej danych, parametr funkcji lub w deklaracji lub definicji funkcji.

Użyj `thread` atrybutu dla zmiennych globalnych, elementów członkowskich danych statycznych i statycznych zmiennych lokalnych tylko.

Poniższy przykład spowoduje wygenerowanie C2480:

```
// C2480.cpp
// compile with: /c
__declspec( thread ) void func();   // C2480
__declspec( thread ) static int i;   // OK
```