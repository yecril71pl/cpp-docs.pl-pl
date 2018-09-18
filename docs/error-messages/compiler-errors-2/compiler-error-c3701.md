---
title: Błąd kompilatora C3701 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3701
dev_langs:
- C++
helpviewer_keywords:
- C3701
ms.assetid: a7faaa87-d2f5-4d6a-9a2f-5cab2d24a648
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6c3a5d3af9448afe918cc2028655fbf85be81cef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051285"
---
# <a name="compiler-error-c3701"></a>Błąd kompilatora C3701

'Funkcja': event_source — nie ma żadnych zdarzeń

Podjęto próbę użycia [event_source](../../windows/event-source.md) dla klasy, która nie ma żadnych metod zdarzeń. Aby naprawić ten błąd, należy dodać jeden lub więcej zdarzeń do klasy.

Poniższy przykład spowoduje wygenerowanie C3701:

```
// C3701.cpp
[ event_source(native) ]
class CEventSrc {
public:
   // uncomment the following line to resolve this C3701
   // __event void fireEvent(int i);
};   // C3701

int main() {
}
```