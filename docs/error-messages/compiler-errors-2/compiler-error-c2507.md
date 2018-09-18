---
title: Błąd kompilatora C2507 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2507
dev_langs:
- C++
helpviewer_keywords:
- C2507
ms.assetid: f102aff5-de7d-4c3f-9cac-2ddf9ce02b14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16cc9c5f21618f3b681fbefbfadfd66b0219d5ac
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022724"
---
# <a name="compiler-error-c2507"></a>Błąd kompilatora C2507

'Identyfikator': zbyt wiele modyfikatorów virtual dla klasy bazowej

Klasy lub struktury jest zadeklarowany jako `virtual` więcej niż jeden raz. Tylko jeden `virtual` modyfikator mogą być wyświetlane dla każdej klasy na liście klas bazowych.

Poniższy przykład spowoduje wygenerowanie C2507:

```
// C2507.cpp
// compile with: /c
class A {};
class B : virtual virtual public A {};   // C2507
class C : virtual public A {};   // OK
```