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
ms.workload: cplusplus
ms.openlocfilehash: a74d7d2e2c745a4c8e29736c1e3a7fc38892d5f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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