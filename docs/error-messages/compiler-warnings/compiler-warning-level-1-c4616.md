---
title: Kompilator ostrzeżenie (poziom 1) C4616
ms.date: 11/04/2016
f1_keywords:
- C4616
helpviewer_keywords:
- C4616
ms.assetid: 71e15265-c5bc-42ce-a6a9-4879892472b1
ms.openlocfilehash: d63e1abffce617a48ac1a5cd8c61feba941b31ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599093"
---
# <a name="compiler-warning-level-1-c4616"></a>Kompilator ostrzeżenie (poziom 1) C4616

\#warning elementu pragma: numeru ostrzeżenia 'numer' nie jest prawidłowym ostrzeżeniem kompilatora

Podany numer ostrzeżenia [ostrzeżenie](../../preprocessor/warning.md) pragma nie może zostać przypisany. Pragma została zignorowana.

Poniższy przykład spowoduje wygenerowanie C4616:

```
// C4616.cpp
// compile with: /W1 /c
#pragma warning( disable : 0 )   // C4616
#pragma warning( disable : 999 )   // OK
#pragma warning( disable : 4998 )   // OK
```