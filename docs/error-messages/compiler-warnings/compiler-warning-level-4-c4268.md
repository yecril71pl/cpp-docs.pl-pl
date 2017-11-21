---
title: "Kompilatora (poziom 4) ostrzeżenie C4268 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4268
dev_langs: C++
helpviewer_keywords: C4268
ms.assetid: d0511e80-904f-4ee1-b4d7-39b5c0bd8234
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ef285e3c093dec39c181e92071fd7b16161d4377
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4268"></a>Kompilator C4268 ostrzegawcze (poziom 4)
"identyfikator": "const" statyczne/globalne dane zainicjowano przy użyciu wygenerowanego przez kompilator domyślnego konstruktora, który wypełnił obiekt zerami  
  
 A **const** globalnych lub statycznych wystąpienia klasy nieuproszczony została zainicjowana przy użyciu generowane przez kompilator domyślnego konstruktora.  
  
## <a name="example"></a>Przykład  
  
```  
// C4268.cpp  
// compile with: /c /LD /W4  
class X {  
public:  
   int m_data;  
};  
  
const X x1;   // C4268  
```  
  
 Ponieważ jest to wystąpienie klasy **const**, wartość `m_data` nie można zmienić.