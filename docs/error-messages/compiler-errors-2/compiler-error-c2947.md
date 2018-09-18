---
title: Błąd kompilatora C2947 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2947
dev_langs:
- C++
helpviewer_keywords:
- C2947
ms.assetid: 6c056f62-ec90-4883-8a67-aeeb6ec13546
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 508c2ae29b0290332cc7c2b49aac0a1ecb10528f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054522"
---
# <a name="compiler-error-c2947"></a>Błąd kompilatora C2947

Oczekiwano ">" zakończenie konstrukcji, znaleziono "składni"

Generyczny lub szablonu listy argumentów nie zostały prawidłowo zakończony.

C2947 mogą być też generowane przez błędy składniowe.

Poniższy przykład spowoduje wygenerowanie C2947:

```
// C2947.cpp
// compile with: /c
template <typename T>=   // C2947
// try the following line instead
// template <typename T>
struct A {};
```