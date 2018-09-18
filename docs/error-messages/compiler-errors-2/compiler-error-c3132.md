---
title: Błąd kompilatora C3132 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3132
dev_langs:
- C++
helpviewer_keywords:
- C3132
ms.assetid: d54a3d12-336a-4ed0-ad4e-43cddac33b5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ffa46ef8e7f56d4be7ca88d2553623910cbcd43f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091650"
---
# <a name="compiler-error-c3132"></a>Błąd kompilatora C3132

"parametr funkcji": tablice parametrów można stosować tylko do formalnego argumentu typu "single-dimensional tablicy zarządzanej"

[ParamArray](https://msdn.microsoft.com/library/system.paramarrayattribute.aspx) atrybut został zastosowany do parametru, który nie był tablicy jednowymiarowej.

Poniższy przykład spowoduje wygenerowanie C3132:

```
// C3132.cpp
// compile with: /clr /c
using namespace System;
void f( [ParamArray] Int32[,] );   // C3132
void g( [ParamArray] Int32[] );   // C3132

void h( [ParamArray] array<Char ^> ^ MyArray );   // OK

```