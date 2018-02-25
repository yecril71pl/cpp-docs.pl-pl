---
title: "Przeciążanie &gt; &gt; operatora dla własnych klas | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- operator>>
- operator>>, overloading for your own classes
- operator >>, overloading for your own classes
ms.assetid: 40dab4e0-3f97-4745-9cc8-b86e740fa246
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8fb029ee7e20a50ef00c2902bda0cca9fb48dbe2
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
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

