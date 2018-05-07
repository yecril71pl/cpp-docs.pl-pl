---
title: Kompilatora (poziom 1) ostrzeżenie C4526 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4526
dev_langs:
- C++
helpviewer_keywords:
- C4526
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5a38d629d61e16b038701522d4bb27a4de7391d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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