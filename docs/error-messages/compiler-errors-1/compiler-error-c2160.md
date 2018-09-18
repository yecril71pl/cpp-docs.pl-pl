---
title: Błąd kompilatora C2160 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2160
dev_langs:
- C++
helpviewer_keywords:
- C2160
ms.assetid: a1f694a7-fb16-4437-b7f5-a1af6da94bc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e823d841eabb4494d549721320f8f29d5cd8774
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111488"
---
# <a name="compiler-error-c2160"></a>Błąd kompilatora C2160

' ##' nie może występować na początku definicji makra

Definicja makra rozpoczął się operator wklejania tokenu (##).

Poniższy przykład spowoduje wygenerowanie C2160:

```
// C2160.cpp
// compile with: /c
#define mac(a,b) #a   // OK
#define mac(a,b) ##a   // C2160
```