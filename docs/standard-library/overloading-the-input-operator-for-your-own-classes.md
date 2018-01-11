---
title: "Przeciążanie &gt; &gt; operatora dla własnych klas | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- operator>>
- operator>>, overloading for your own classes
- operator >>, overloading for your own classes
ms.assetid: 40dab4e0-3f97-4745-9cc8-b86e740fa246
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dc6d7662c5072e2fb3fac8c95df05c274fd8cf9e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="overloading-the-gtgt-operator-for-your-own-classes"></a>Przeciążanie &gt; &gt; operatora dla własnych klas
Strumienie wejściowe Użyj wyodrębniania (`>>`) operatora dla standardowych typów. Podobny operatory wyodrębniania może zapisywać do własnych typów; Twój sukces zależy od tego, dokładnie przy użyciu biały znak.  
  
 Oto przykład operator wyodrębniania `Date` klasy przedstawione wcześniej:  
  
```  
istream& operator>> (istream& is, Date& dt)  
{  
    is>> dt.mo>> dt.da>> dt.yr;  
    return is;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Strumienie wejściowe](../standard-library/input-streams.md)

