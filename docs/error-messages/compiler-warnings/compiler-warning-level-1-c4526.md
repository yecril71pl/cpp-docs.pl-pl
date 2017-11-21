---
title: "Kompilatora (poziom 1) ostrzeżenie C4526 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4526
dev_langs: C++
helpviewer_keywords: C4526
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 00ffa9e20781d8d5d1405d6bf5546b47a6530b88
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4526"></a>Kompilator C4526 ostrzegawcze (poziom 1)
"function": funkcja statyczny element członkowski nie może przesłonić funkcji wirtualnej "wirtualnego function'override ignorowane, funkcja wirtualna zostanie ukryta  
  
 Funkcja statycznego elementu członkowskiego spełnia kryteria do przesłonięcia funkcji wirtualnej, co sprawia, że funkcja członkowska wirtualnej i statyczne.  
  
 Poniższy kod generuje C4526:  
  
```  
// C4526.cpp  
// compile with: /W1 /c  
// C4526 expected  
struct myStruct1 {  
   virtual void __stdcall func( int ) = 0;  
};  
  
struct myStruct2: public myStruct1 {  
   static void __stdcall func( int );  
};  
```  
  
 Poniżej przedstawiono możliwe poprawki:  
  
-   Jeśli funkcja jest przeznaczona do przesłonięcia funkcji wirtualnej klasy podstawowej, Usuń specyfikator statycznej.  
  
-   Jeśli funkcja ma być statycznej funkcji członkowskiej, należy ją zmienić, więc nie koliduje to z funkcji wirtualnej klasy podstawowej.