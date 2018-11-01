---
title: Błąd kompilatora C2492
ms.date: 11/04/2016
f1_keywords:
- C2492
helpviewer_keywords:
- C2492
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
ms.openlocfilehash: e2b08ef3e46681147c4efd77cbffadb096bbfc16
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590466"
---
# <a name="compiler-error-c2492"></a>Błąd kompilatora C2492

"*zmiennej*": dane z okresem magazynu wątku nie mogą mieć interfejsu biblioteki dll

Zmienna jest zadeklarowana za pomocą [wątku](../../cpp/thread.md) atrybutu i z biblioteki DLL interfejsu. Adres `thread` zmienna jest nieznany do czasu wykonywania, więc nie można połączyć do biblioteki DLL importu lub eksportu.

Poniższy przykład spowoduje wygenerowanie C2492:

```
// C2492.cpp
// compile with: /c
class C {
public:
   char   ch;
};

__declspec(dllexport) __declspec(thread) C c_1;   // C2492
__declspec(thread) C c_1;   // OK
```