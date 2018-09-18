---
title: Błąd kompilatora C2500 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2500
dev_langs:
- C++
helpviewer_keywords:
- C2500
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b7e24ca520796b63171fe63c2bf841fe8776845
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026676"
---
# <a name="compiler-error-c2500"></a>Błąd kompilatora C2500

"identifier1": "identifier2" jest już bezpośrednią klasą bazową

Klasa lub struktura występuje więcej niż jeden raz na liście klas bazowych.

Bezpośredniej klasy podstawowej jest jednym wymienione na liście bazowych. Pośrednią podstawą jest klasą bazową dla jednej z klas na liście bazowych.

Klasa nie można określić jako bezpośrednią klasą bazową więcej niż jeden raz. Klasa może służyć jako pośrednią klasą bazową więcej niż jeden raz.

Poniższy przykład spowoduje wygenerowanie od C2500:

```
// C2500.cpp
// compile with: /c
class A {};
class B : public A, public A {};    // C2500

// OK
class C : public A {};
class D : public A {};
class E : public C, public D {};
```