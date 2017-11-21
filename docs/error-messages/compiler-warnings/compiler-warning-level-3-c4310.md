---
title: "Kompilatora (poziom 3) ostrzeżenie C4310 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4310
dev_langs: C++
helpviewer_keywords: C4310
ms.assetid: cba3eca1-f1ed-499c-9243-337446bdbdd8
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8e831459aaf2161d83a62cd1241673780293c02d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4310"></a>Kompilator C4310 ostrzegawcze (poziom 3)
Rzutowanie obcina stałą wartość  
  
 Stała wartość jest rzutowania na mniejszy typ. Kompilator wykonuje rzutowania, w którym obcina danych. Poniższy przykład generuje C4310:  
  
```  
// C4310.cpp  
// compile with: /W4  
int main() {  
   long int a;  
   a = (char) 128;   // C4310, use value 0-127 to resolve  
}  
```