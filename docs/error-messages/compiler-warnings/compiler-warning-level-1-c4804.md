---
title: Kompilator ostrzeżenie (poziom 1) C4804 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4804
dev_langs:
- C++
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd1d1659ad6c8716cebf37a99f234af7b41f5745
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094809"
---
# <a name="compiler-warning-level-1-c4804"></a>Kompilator ostrzeżenie (poziom 1) C4804

'Operacja': niebezpieczne użycie typu "bool" w operacji

To ostrzeżenie dotyczy sytuacji, gdy używasz `bool` zmiennej lub wartość w nieoczekiwany sposób. Na przykład C4804 jest generowany, gdy używasz operatorów, takich jak operator jednoargumentowy ujemna (**-**) lub operatorem dopełnienia (`~`). Kompilator oblicza wyrażenie.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4804:

```
// C4804.cpp
// compile with: /W1

int main()
{
   bool i = true;
   if (-i)   // C4804, remove the '-' to resolve
   {
      i = false;
   }
}
```