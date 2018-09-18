---
title: Błąd kompilatora C2195 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2195
dev_langs:
- C++
helpviewer_keywords:
- C2195
ms.assetid: 9f9f035c-9c51-4173-a8ea-c6f907fc5c63
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ec81b9c720d1dfc5a629faaa74fb321cdf93b4b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020607"
---
# <a name="compiler-error-c2195"></a>Błąd kompilatora C2195

'Identyfikator': jest segmentem danych

`code_seg` Pragma korzysta z nazwą segmentu, w ramach `data_seg` pragmy.

Poniższy przykład spowoduje wygenerowanie C2195:

```
// C2195.cpp
#pragma data_seg("MYDATA")
#pragma code_seg("MYDATA")   // C2195
#pragma code_seg("MYDATA2")   // OK
```