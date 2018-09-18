---
title: Błąd kompilatora C3168 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3168
dev_langs:
- C++
helpviewer_keywords:
- C3168
ms.assetid: 4c36fcfb-c351-48ff-b4eb-78d2aa1b4d55
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b2a70af70af5b31ef9a3bf2fe939eef28783369a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106457"
---
# <a name="compiler-error-c3168"></a>Błąd kompilatora C3168

"type": niedozwolony typ podstawowy dla wyliczenia

Bazowy typ określony dla `enum` typ nie jest prawidłowy. Typ podstawowy musi być typu całkowitoliczbowego C++ lub odpowiedni typ CLR.

Poniższy przykład spowoduje wygenerowanie C3168:

```
// C3168.cpp
// compile with: /clr /c
ref class G{};

enum class E : G { e };   // C3168
enum class F { f };   // OK
```
