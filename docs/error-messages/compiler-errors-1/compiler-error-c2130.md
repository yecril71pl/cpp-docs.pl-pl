---
title: Błąd kompilatora C2130 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2130
dev_langs:
- C++
helpviewer_keywords:
- C2130
ms.assetid: c6fd5a7e-8f28-4f67-99d1-95a13b0dff90
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 954930522651fcee6c29bf019f366e056fe681ef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071533"
---
# <a name="compiler-error-c2130"></a>Błąd kompilatora C2130

\#wiersz oczekiwany ciąg zawierający nazwę pliku, znaleziono "token"

Token następujący nazwy pliku opcjonalne [#line](../../preprocessor/hash-line-directive-c-cpp.md) `linenumber` musi być ciągiem.

Poniższy przykład spowoduje wygenerowanie C2130:

```
// C2130.cpp
int main() {
   #line 1000 test   // C2130
   #line 1000 "test"   // OK
}
```