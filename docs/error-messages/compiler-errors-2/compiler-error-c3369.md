---
title: Błąd kompilatora C3369
ms.date: 11/04/2016
f1_keywords:
- C3369
helpviewer_keywords:
- C3369
ms.assetid: c6ceb9cb-3df9-4334-9a5c-d16db351d476
ms.openlocfilehash: 3b2e6f38e93514154b20e674139a2d771dcf586e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503240"
---
# <a name="compiler-error-c3369"></a>Błąd kompilatora C3369

"Nazwa modułu": idl_module już zdefiniowane

Użycie [idl_module](../../windows/attributes/idl-module.md) , w którym można zdefiniować bibliotekę DLL, może wystąpić tylko raz w programie.

Poniższy przykład generuje C3369:

```cpp
// C3369.cpp
// compile with: /c
[idl_module(name="name1", dllname="x.dll")]; // C3369
[idl_module(name="name1", dllname="x.dll")];
```
