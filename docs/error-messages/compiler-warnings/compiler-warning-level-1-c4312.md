---
title: "Kompilatora (poziom 1) ostrzeżenie C4312 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4312
dev_langs: C++
helpviewer_keywords: C4312
ms.assetid: 541906ed-4f62-4bcb-947f-cf9ae7411bcb
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0a4e6fa46fe9b84b138fffedf206d08ffbb30790
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4312"></a>Kompilator C4312 ostrzegawcze (poziom 1)
'operacja' : konwersja z 'typ1' na 'typ2' o większym rozmiarze  
  
 To ostrzeżenie wykrywa próby przypisać do typu wskaźnika 64-bitowych, na przykład 32-bitową wartość rzutowanie 32-bitowa `int` lub `long` na wskaźnik 64-bitowych.  
  
 Może to być niebezpieczna konwersja nawet dla wartości wskaźników, które mieszczą się w 32-bitowy, gdy występuje znak rozszerzenia. Jeśli ujemna 32-bitowa liczba całkowita jest przypisany do typu wskaźnika 64-bitowych, rozszerzenia znak powoduje, że wartość wskaźnik do odwołania adres pamięci, inna niż wartość liczby całkowitej.  
  
 To ostrzeżenie zostanie wyświetlone tylko dla celów kompilacji w 64-bitowych. Aby uzyskać więcej informacji, zobacz [reguły dla wskaźników przy użyciu](http://msdn.microsoft.com/library/windows/desktop/aa384242).  
  
 Poniższy przykład kodu generuje C4312, gdy jest on skompilowany dla celów 64-bitowe:  
  
```  
// C4312.cpp  
// compile by using: cl /W1 /LD C4312.cpp  
void* f(int i) {  
   return (void*)i;   // C4312 for 64-bit targets  
}  
  
void* f2(__int64 i) {  
   return (void*)i;   // OK  
}  
```