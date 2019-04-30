---
title: Kompilator ostrzeżenie (poziom 1) C4440
ms.date: 11/04/2016
f1_keywords:
- C4440
helpviewer_keywords:
- C4440
ms.assetid: 78b9642a-a93e-401e-9d92-372f6451bc5d
ms.openlocfilehash: ccd7c14cbd078d4740795d25ad772bdc78840a60
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408280"
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