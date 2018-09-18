---
title: Błąd kompilatora C3387 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3387
dev_langs:
- C++
helpviewer_keywords:
- C3387
ms.assetid: c54d9925-ed14-4976-b8db-e8d4dc84e536
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0dafe972db1b3210e9243e34cc02e7a0366bdd65
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030758"
---
# <a name="compiler-error-c3387"></a>Błąd kompilatora C3387

'składowa': __declspec(dllexport) /\__declspec(dllimport) nie można zastosować do członka zarządzanej lub typu WinRT

`dllimport` i [dllexport](../../cpp/dllexport-dllimport.md) `__declspec` modyfikatorów nie są prawidłowe w zarządzanej członków lub typ środowiska uruchomieniowego Windows.

Poniższy przykład generuje C3387 i pokazuje, jak go naprawić:

```
// C3387a.cpp
// compile with: /clr /c
ref class X2 {
   void __declspec(dllexport) mf() {   // C3387
   // try the following line instead
   // void mf() {
   }
};
```