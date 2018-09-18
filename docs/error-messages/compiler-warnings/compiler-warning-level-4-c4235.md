---
title: Kompilator ostrzeżenie (poziom 4) C4235 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4235
dev_langs:
- C++
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c9e709017e51101efe53a8697bb145014f200871
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031824"
---
# <a name="compiler-warning-level-4-c4235"></a>Kompilator ostrzeżenie (poziom 4) C4235

użyto niestandardowego rozszerzenia: słowo kluczowe "— słowo kluczowe" nie jest obsługiwane w tej architekturze

Kompilator nie obsługuje — słowo kluczowe, których użyto.

To ostrzeżenie zostanie automatycznie podwyższony do błędu. Jeśli chcesz zmienić to zachowanie, użyj [ostrzeżenie #pragma](../../preprocessor/warning.md). Na przykład aby C4235 do włączonego ostrzeżenia poziomu 2, należy użyć następującego kodu

```
#pragma warning(2:4235)
```

w pliku kodu źródłowego.