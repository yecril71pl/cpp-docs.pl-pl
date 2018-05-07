---
title: C2087 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2087
dev_langs:
- C++
helpviewer_keywords:
- C2087
ms.assetid: 89761e83-415a-4468-a4c6-b6dedfd1dd6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a6012bd49d9d68cbc3318afb390b5f5b411e39f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2087"></a>C2087 błąd kompilatora
'Identyfikator': Brak indeksu dolnego  
  
 Definicja tablicy zawierającej wiele indeksów dolnych brakuje indeksu dolnego wartości wyższej niż jeden wymiar.  
  
 Poniższy przykład generuje C2087:  
  
```  
// C2087.cpp  
int main() {  
   char a[10][];   // C2087  
}  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C2087b.cpp  
int main() {  
   char b[4][5];  
}  
```