---
title: Błąd kompilatora C2811 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2811
dev_langs:
- C++
helpviewer_keywords:
- C2811
ms.assetid: 6a44b18e-44c1-49d8-9b99-e0545b9a6e7d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e7e3b2d7bb76989b2028846efee6b18d10e1b0ad
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059618"
---
# <a name="compiler-error-c2811"></a>Błąd kompilatora C2811

'Typ1': nie może dziedziczyć po "type2" ref klasy mogą dziedziczyć tylko z klasy interfejsu lub klasy referencyjnej

Próbowano użyć niezarządzane klasy jako klasę bazową dla klasy zarządzanej.

Poniższy przykład spowoduje wygenerowanie C2811:

```
// C2811.cpp
// compile with: /clr /c
struct S{};
ref struct T {};
ref class C : public S {};   // C2811
ref class D : public T {};   // OK
```