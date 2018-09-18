---
title: Błąd kompilatora C3140 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3140
dev_langs:
- C++
helpviewer_keywords:
- C3140
ms.assetid: 122f8943-fac3-4db8-a3a8-2c5d19233de6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a40cec364af10f4b61c19b9a28646279a8efca43
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111745"
---
# <a name="compiler-error-c3140"></a>Błąd kompilatora C3140

nie może mieć wiele atrybutów "module" w tej samej jednostce kompilacyjnej

[Modułu](../../windows/module-cpp.md) atrybut może zostać zdefiniowany tylko jeden raz na projekt.

Poniższy przykład spowoduje wygenerowanie C3140:

```
// C3140.cpp
// compile with: /c
[emitidl];
[module(name = "MyLibrary")];
[module(name = "MyLibrary2")];   // C3140
```