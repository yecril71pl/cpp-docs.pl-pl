---
title: "Kompilatora (poziom 1) ostrzeżenie C4269 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4269
dev_langs: C++
helpviewer_keywords: C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ee524e998a4d314b7ae3fff74b48b8a6ca6a621f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4269"></a>Kompilator C4269 ostrzegawcze (poziom 1)
"identyfikator": "const" zainicjowano przy użyciu wygenerowanego przez kompilator domyślnego konstruktora danych zwrócił niepewne wyniki  
  
 A **const** automatyczne wystąpienia klasy nieuproszczony została zainicjowana przy użyciu generowane przez kompilator domyślnego konstruktora.  
  
## <a name="example"></a>Przykład  
  
```  
// C4269.cpp  
// compile with: /c /LD /W1  
class X {  
public:  
   int m_data;  
};  
  
void g() {  
   const X x1;   // C4269  
};  
```  
  
 Ponieważ to wystąpienie klasy jest generowany na stosie początkowej wartości `m_data` może być dowolna. Ponieważ jest także **const** wystąpienie wartość `m_data` nigdy nie można zmienić.