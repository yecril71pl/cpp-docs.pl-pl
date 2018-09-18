---
title: Błąd kompilatora C2458 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2458
dev_langs:
- C++
helpviewer_keywords:
- C2458
ms.assetid: ed21901f-1067-42f5-b275-19b480decf5c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 94a95ab1eab00424774d5117e3ae37685a2ac1fc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035472"
---
# <a name="compiler-error-c2458"></a>Błąd kompilatora C2458

'Identyfikator': ponowna definicja w ramach definicji

Klasy, struktury, Unii lub wyliczenie zostanie ponownie zdefiniowana w jego własnej deklaracji.

Poniższy przykład spowoduje wygenerowanie C2458:

```
// C2458.cpp
class C {
   enum i { C };   // C2458
};
```