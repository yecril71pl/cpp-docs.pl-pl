---
title: "C2943 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2943
dev_langs: C++
helpviewer_keywords: C2943
ms.assetid: ede6565e-d892-44c0-8eee-c69545f3be2e
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1bbd2a3310bb3f5cd18c241f9923d051acde58eb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2943"></a>C2943 błąd kompilatora
"class": typ klasy identyfikator ponownie zdefiniować jako argument typu szablonu  
  
 Klasy ogólne lub szablonu nie można użyć zamiast symbolu, jako argumentu typu ogólnego lub szablonu.  
  
 Poniższy przykład generuje C2943:  
  
```  
// C2943.cpp  
// compile with: /c  
template<class T>  
class List {};  
  
template<class List<int> > class MyList;   // C2943  
template<class T >  class MyList;  
```