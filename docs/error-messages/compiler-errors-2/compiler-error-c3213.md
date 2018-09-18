---
title: Błąd kompilatora C3213 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3213
dev_langs:
- C++
helpviewer_keywords:
- C3213
ms.assetid: 1f079e36-b3e9-40f8-8e95-08eeba3adc82
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a23f61dc8170ff7cd5638d2b2f394d288f48c5f3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112983"
---
# <a name="compiler-error-c3213"></a>Błąd kompilatora C3213

Klasa bazowa "base_type" jest mniej dostępny niż "derived_type"

Typ, który będzie widoczny z zestawu, należy użyć klas bazowych publicznie widoczne.

Poniższy przykład spowoduje wygenerowanie C3213:

```
// C3213.cpp
// compile with: /clr
private ref struct privateG {
public:
   int i;
};

public ref struct publicG {
public:
   int i;
};

public ref struct V : public privateG {   // C3213
public:
   int j;
};

public ref struct W: public publicG {   // OK
public:
   int j;
};
```