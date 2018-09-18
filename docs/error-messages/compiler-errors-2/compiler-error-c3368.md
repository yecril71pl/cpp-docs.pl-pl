---
title: Błąd kompilatora C3368 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3368
dev_langs:
- C++
helpviewer_keywords:
- C3368
ms.assetid: 5bfd5be4-dfa9-4b33-9612-010561b40955
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 236bfdfc031544e05d4aa95d9c36720ddb0ebdf8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051300"
---
# <a name="compiler-error-c3368"></a>Błąd kompilatora C3368

"deklaracji funkcji": Nieprawidłowa konwencja wywoływania dla języka IDL

Można używać tylko [__stdcall](../../cpp/stdcall.md) lub [__cdecl](../../cpp/cdecl.md) konwencjach wywoływania w pliku .idl.

Poniższy przykład spowoduje wygenerowanie C3368:

```
// C3368.cpp
// processor: x86
[idl_module(name="Name", dllname="Some.dll")];

[idl_module(name="Name")]
int __fastcall f1();   // C3368
```