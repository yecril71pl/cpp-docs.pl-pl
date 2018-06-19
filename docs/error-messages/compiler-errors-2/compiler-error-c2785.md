---
title: C2785 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2785
dev_langs:
- C++
helpviewer_keywords:
- C2785
ms.assetid: d8d13360-0d00-4815-8475-b49c7f0dc0f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc0ca6235e0fd4bdd22330e807464e96280ae461
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234032"
---
# <a name="compiler-error-c2785"></a>C2785 błąd kompilatora
"declaration1" i "declaration2" mają różne typy zwracane  
  
 Zwracany typ specjalizacja szablonu funkcji różni się od zwracanego typu szablonu podstawowej funkcji.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź wszystkie specjalizacji szablonu funkcji spójności.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2785:  
  
```  
// C2785.cpp  
// compile with: /c  
template<class T> void f(T);  
  
template<> int f(int); // C2785  
template<> void f(int); // OK  
```