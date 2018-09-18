---
title: Kompilator ostrzeżenie (poziom 4) C4019 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4019
dev_langs:
- C++
helpviewer_keywords:
- C4019
ms.assetid: 4ecfe85d-673f-4334-8154-36fe7f0b3444
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 48915f72acdaf0b02acd04de38f10fcdb2a20e93
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065330"
---
# <a name="compiler-warning-level-4-c4019"></a>Kompilator ostrzeżenie (poziom 4) C4019

Instrukcja pusta w globalnym zakresie

Średnik w zakresie globalnym nie jest poprzedzony przez instrukcję.

To ostrzeżenie, mogą zostać rozwiązane, jeśli usuniesz dodatkowe średnikami.

## <a name="example"></a>Przykład

```
// C4019.c
// compile with: /Za /W4
#define declint( varname ) int varname;
declint( a );   // C4019, int a;;
declint( b )   // OK, int b;

int main()
{
}
```