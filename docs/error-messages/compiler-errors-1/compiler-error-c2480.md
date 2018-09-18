---
title: Błąd kompilatora C2480 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2480
dev_langs:
- C++
helpviewer_keywords:
- C2480
ms.assetid: 1a58d1c2-971b-4084-96fa-f94aa51c02f1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8b5d8f80293c05b651ad01e725ae501288005dfe
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102589"
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