---
title: Kompilator ostrzeżenie (poziom 4) C4559 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4559
dev_langs:
- C++
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d5743b33f62aa954c3765b729ab5c0297b20e32
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195579"
---
# <a name="compiler-warning-level-4-c4559"></a>Kompilator ostrzeżenie (poziom 4) C4559

> "*funkcja*": zmiana definicji; __declspec zyski — funkcja (*modyfikator*)

## <a name="remarks"></a>Uwagi

Funkcja została zdefiniowana ponownie lub ponownie zadeklarowany, i dodany drugi definicji lub deklaracji **__declspec** modyfikator (*modyfikator*). To ostrzeżenie ma charakter informacyjny. Aby usunąć to ostrzeżenie, usuń jedną z definicji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4559:

```cpp
// C4559.cpp
// compile with: /W4 /LD
void f();
__declspec(noalias) void f();   // C4559
```