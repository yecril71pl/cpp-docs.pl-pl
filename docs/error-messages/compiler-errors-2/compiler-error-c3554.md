---
title: Błąd kompilatora C3554 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3554
dev_langs:
- C++
helpviewer_keywords:
- C3554
ms.assetid: aede18d5-fefc-4da9-9b69-adfe90bfa742
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b1760607a335d4dd56ec711eef76f5a68550d64
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089505"
---
# <a name="compiler-error-c3554"></a>Błąd kompilatora C3554

"decltype" nie można łączyć z jakimkolwiek innym specyfikatorem typu

Nie kwalifikujesz się do `decltype()` — słowo kluczowe ze specyfikatorem dowolnego typu. Na przykład poniższy fragment kodu powoduje błąd C3554.

```
int x;
unsigned decltype(x); // C3554
```