---
title: Błąd kompilatora C3896 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3896
dev_langs:
- C++
helpviewer_keywords:
- C3896
ms.assetid: eb8be0f6-5b4e-4d71-8285-8a2a94f8ba29
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6714d356fa2f09bdfce2750ff31432b5b4e14461
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109733"
---
# <a name="compiler-error-c3896"></a>Błąd kompilatora C3896

"członek": niewłaściwy inicjator: ten literał składowej danych może być inicjowane tylko z "nullptr"

A [literału](../../windows/literal-cpp-component-extensions.md) element członkowski danych został niepoprawnie zainicjowany.  Zobacz [nullptr](../../windows/nullptr-cpp-component-extensions.md) Aby uzyskać więcej informacji.

Poniższy przykład spowoduje wygenerowanie C3896:

```
// C3896.cpp
// compile with: /clr /c
ref class R{};

value class V {
   literal R ^ r = "test";   // C3896
   literal R ^ r2 = nullptr;   // OK
};
```