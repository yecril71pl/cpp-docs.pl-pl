---
title: Błąd kompilatora C2055 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2055
dev_langs:
- C++
helpviewer_keywords:
- C2055
ms.assetid: 6cec79cc-6bec-443f-9897-fbf5452718c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6c63d79325417fbd9b1f451fb4a51f13957b4df
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019345"
---
# <a name="compiler-error-c2055"></a>Błąd kompilatora C2055

Oczekiwano formalnej listy parametrów, nie listy typów

Definicja funkcji zawiera listę typów parametrów zamiast formalnej listy parametrów. ANSI C wymaga parametrów formalnych w nazwanych, chyba że są one void lub wielokropkiem (`...`).

Poniższy przykład spowoduje wygenerowanie C2055:

```
// C2055.c
// compile with: /c
void func(int, char) {}  // C2055
void func (int i, char c) {}   // OK
```