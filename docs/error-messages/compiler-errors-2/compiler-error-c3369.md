---
title: Błąd kompilatora C3369
ms.date: 11/04/2016
f1_keywords:
- C3369
helpviewer_keywords:
- C3369
ms.assetid: c6ceb9cb-3df9-4334-9a5c-d16db351d476
ms.openlocfilehash: 0cd27da4b73732513afe0bd33a2d7312e6ddbe97
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388735"
---
# <a name="compiler-error-c3369"></a>Błąd kompilatora C3369

"module name": idl_module już zdefiniowany

[Idl_module](../../windows/idl-module.md) użycia, w której definiujesz biblioteki DLL może wystąpić tylko raz w programie.

Poniższy przykład spowoduje wygenerowanie C3369:

```
// C3369.cpp
// compile with: /c
[idl_module(name="name1", dllname="x.dll")]; // C3369
[idl_module(name="name1", dllname="x.dll")];
```