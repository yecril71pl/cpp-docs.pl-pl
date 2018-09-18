---
title: Kompilator ostrzeżenie (poziom 1) C4616 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4616
dev_langs:
- C++
helpviewer_keywords:
- C4616
ms.assetid: 71e15265-c5bc-42ce-a6a9-4879892472b1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 59b81211b61db6b2537a007a20697c61a02a290a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094450"
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