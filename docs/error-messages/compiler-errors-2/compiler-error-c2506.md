---
title: Błąd kompilatora C2506 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2506
dev_langs:
- C++
helpviewer_keywords:
- C2506
ms.assetid: cfed21cd-2404-46f2-985e-d0c2c3820830
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4967c410dfdce781a4191c9ac848883228ba4d3a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093418"
---
# <a name="compiler-error-c2506"></a>Błąd kompilatora C2506

'składowa': "__declspec(modifier)" nie można zastosować do tego symbolu

Nie można zadeklarować każdego procesu lub dla domeny appdomain dla statycznych elementów członkowskich klasy zarządzanej.

Zobacz [appdomain](../../cpp/appdomain.md) Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2506.

```
// C2506.cpp
// compile with: /clr /c
ref struct R {
   __declspec(process) static int n;   // C2506
   int o;   // OK
};
```