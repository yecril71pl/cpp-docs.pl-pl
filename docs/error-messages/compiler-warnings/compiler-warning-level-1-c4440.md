---
title: Kompilator ostrzeżenie (poziom 1) C4440
ms.date: 11/04/2016
f1_keywords:
- C4440
helpviewer_keywords:
- C4440
ms.assetid: 78b9642a-a93e-401e-9d92-372f6451bc5d
ms.openlocfilehash: ccd7c14cbd078d4740795d25ad772bdc78840a60
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660063"
---
# <a name="compiler-warning-level-1-c4440"></a>Kompilator ostrzeżenie (poziom 1) C4440

wywoływanie ponowną definicję Konwencji wywołań z "calling_convention1" do "calling_convention2" zignorowany

Próba zmiany konwencja wywołania została zignorowana.

Poniższy przykład spowoduje wygenerowanie C4440:

```
// C4440.cpp
// compile with: /W1 /LD /clr
typedef void __clrcall F();
typedef F __cdecl *PFV;   // C4440
```