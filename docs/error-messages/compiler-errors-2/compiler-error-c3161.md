---
title: Błąd kompilatora C3161 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3161
dev_langs:
- C++
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 11396ccad33489b41d18759ba4d2f00b445e94a3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136078"
---
# <a name="compiler-error-c3161"></a>Błąd kompilatora C3161

"interface": zagnieżdżanie klasy, struktury, Unii lub interfejsu w interfejsie jest niedozwolone; Zagnieżdżanie interfejsu w klasy, struktury lub Unii jest niedozwolony

[__Interface](../../cpp/interface.md) może wystąpić tylko w zakresie globalnym lub przestrzeni nazw. Klasy, struktury lub Unii nie są wyświetlane w interfejsie.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3161.

```
// C3161.cpp
// compile with: /c
__interface X {
   __interface Y {};   // C3161 A nested interface
};
```