---
title: Kompilator ostrzegawcze (poziom 3) C4608 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4608
dev_langs: C++
helpviewer_keywords: C4608
ms.assetid: 8b8f5f28-8ce9-457e-9d3d-a8c0efce9b6a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3b766c507db60a312f62b3fa84d4963fdf1f718b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4608"></a>Ostrzeżenie kompilatora (poziom 3) C4608
"union_member" został już zainicjowany przez inny element członkowski typu union na liście inicjatora "union_member"  
  
 Dwa elementy członkowskie tej samej Unii zostały zainicjowane w listy inicjowania. Dostępne są tylko jeden element członkowski Unii.  
  
 Poniższy przykład generuje C4608:  
  
```  
// C4608.cpp  
// compile with: /W3 /c  
class X {  
public:  
   X(char c) : m_i( c + 1), m_c(c) {}   // C4608  
   // try the following line instead  
   // X(char c) : m_c(c) {}  
  
private:  
   union {  
      int m_i;  
      char m_c;  
   };  
};  
  
union Y {  
public:  
   Y(char * name) : m_number(0.3), m_string( name ) {} // C4608  
  
private:  
   double m_number;  
   char * m_string;  
};  
```