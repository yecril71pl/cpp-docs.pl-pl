---
title: C2390 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2390
dev_langs:
- C++
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a32a9ca77ba43e5f2866baed91b99103224dbc0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198719"
---
# <a name="compiler-error-c2390"></a>C2390 błąd kompilatora
'Identyfikator': niepoprawna Klasa magazynu "specyfikatora"  
  
 Klasa magazynu jest nieprawidłowa dla identyfikatora zakresu globalnego. Domyślna klasa magazynu jest używany zamiast nieprawidłowa klasa.  
  
 Możliwe rozwiązania:  
  
-   Jeśli identyfikator jest funkcją, Zadeklaruj ją z `extern` magazynu.  
  
-   Jeśli identyfikator jest formalny parametr lub zmienna lokalna, Zadeklaruj ją z magazynem automatycznie.  
  
-   Jeśli identyfikator jest zmienną globalną, Zadeklaruj ją z Brak klasy magazynu (automatycznie magazynu).  
  
## <a name="example"></a>Przykład  
  
-   Poniższy przykład generuje C2390:  
  
```  
// C2390.cpp  
register int i;   // C2390  
  
int main() {  
   register int j;   // OK  
}  
```