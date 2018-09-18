---
title: Błąd kompilatora C2821 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2821
dev_langs:
- C++
helpviewer_keywords:
- C2821
ms.assetid: e8d71988-a968-4484-94db-e8c3bad74a4a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52525062a07c7c55dd323109be87667d9e0847d6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098228"
---
# <a name="compiler-error-c2821"></a>Błąd kompilatora C2821

pierwszy formalny parametr dla "operator new" musi być "unsigned int"

Pierwszy formalny parametr [nowy operator](../../standard-library/new-operators.md#op_new) musi być typ unsigned `int`.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2821:

```cpp
// C2821.cpp
// compile with: /c
void * operator new( /* unsigned int,*/ void * );   // C2821
void * operator new( unsigned int, void * );
```