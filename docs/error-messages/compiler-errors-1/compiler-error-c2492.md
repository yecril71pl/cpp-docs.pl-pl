---
title: Błąd kompilatora C2492 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2492
dev_langs:
- C++
helpviewer_keywords:
- C2492
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2fcb9058bf1aac584e8b7728616f821bda4b33f6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096278"
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