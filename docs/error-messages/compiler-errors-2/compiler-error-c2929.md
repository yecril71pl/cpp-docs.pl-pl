---
title: Błąd kompilatora C2929 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2929
dev_langs:
- C++
helpviewer_keywords:
- C2929
ms.assetid: 11134027-6adc-4733-b6bd-b94486bd1933
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d7eee14296178fb90d4a3c34a28926032fcb04b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102830"
---
# <a name="compiler-error-c2929"></a>Błąd kompilatora C2929

'Identyfikator': jawne utworzenie wystąpień; Nie można jawnie wymusić i ograniczyć utworzenia wystąpienia składowej klasy szablonu

Nie można jawnie utworzyć wystąpienia identyfikatora podczas uniemożliwiające jego wystąpienia.

Poniższy przykład spowoduje wygenerowanie C2929:

```
// C2929.cpp
// compile with: /c
template<typename T>
class A {
public:
   A() {}
};

template A<int>::A();

extern template A<int>::A();   // C2929
```