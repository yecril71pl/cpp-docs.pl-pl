---
title: Kompilator ostrzeżenie (poziom 4) C4565 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4565
dev_langs:
- C++
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c25f2f1fc16c6d45a7d1eddec8d3efe62db142f2
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211265"
---
# <a name="compiler-warning-level-4-c4565"></a>Kompilator ostrzeżenie (poziom 4) C4565

> "*funkcja*": zmiana definicji; symbol został poprzednio zadeklarowany za pomocą __declspec (*modyfikator*)

## <a name="remarks"></a>Uwagi

Symbol został ponownie zdefiniować lub ponownie zadeklarowany, a drugi definicji lub deklaracji, w odróżnieniu od pierwszej definicji lub deklaracji, nie ma `__declspec` modyfikator (*modyfikator*). To ostrzeżenie ma charakter informacyjny. Aby usunąć to ostrzeżenie, usuń jedną z definicji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4565:

```cpp
// C4565.cpp
// compile with: /W4 /LD
__declspec(noalias) void f();
void f();   // C4565
```