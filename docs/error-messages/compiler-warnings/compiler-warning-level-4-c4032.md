---
title: Kompilatora (poziom 4) ostrzeżenie C4032 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4032
dev_langs:
- C++
helpviewer_keywords:
- C4032
ms.assetid: 70dd0c85-0239-43f9-bb06-507f6a57d206
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb61588c12378972194305d979ecdd89140ac6f6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4032"></a>Kompilator C4032 ostrzegawcze (poziom 4)
Parametr formalny "number" jest innego typu kiedy jest zwiększany  
  
 Typ parametru nie jest zgodny, za pośrednictwem domyślne promocje, z poziomu typu w poprzedniej deklaracji.  
  
 Jest to błąd w ANSI C ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) i ostrzeżenia w obszarze rozszerzenia Microsoft (/Ze).  
  
## <a name="example"></a>Przykład  
  
```  
// C4032.c  
// compile with: /W4  
void func();  
void func(char);   // C4032, char promotes to int  
  
int main()  
{  
}  
```