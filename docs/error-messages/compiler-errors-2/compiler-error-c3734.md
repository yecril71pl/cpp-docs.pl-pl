---
title: Błąd kompilatora C3734 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3734
dev_langs:
- C++
helpviewer_keywords:
- C3734
ms.assetid: 4e2afdcc-7da9-45a1-9c96-85f25e2986e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d304b3853986b54f9844f9e4968f7bb7d6a8af5a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072748"
---
# <a name="compiler-error-c3734"></a>Błąd kompilatora C3734

"class": zarządzanej lub klasa WinRT nie może być klasą coclass

[Coclass](../../windows/coclass.md) atrybut nie może być używany z zarządzanego lub klasach WinRT.

Poniższy przykład generuje C3734 i pokazuje, jak go naprawić:

```
// C3734.cpp
// compile with: /clr /c
[module(name="x")];

[coclass]
ref class CMyClass {   // C3734 remove the ref keyword to resolve
};
```
