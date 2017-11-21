---
title: "Magazyn złożeń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- storage, union
- union keyword [C], storage
- union keyword [C]
ms.assetid: b33d246a-8d20-41c4-89b2-ab05f1428792
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cb349b2c1649b6e4e46fcc92829de87043d0c50a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="storage-of-unions"></a>Magazyn złożeń
Magazyn skojarzone ze zmienną Unii jest magazynu wymaganego przez największy element członkowski Unii. Gdy mniejszych elementu członkowskiego jest przechowywana, union zmienna może zawierać miejsca nieużywanej pamięci. Wszystkie elementy członkowskie są przechowywane w tym samym obszarze pamięci i Rozpocznij od tego samego adresu. Wartość przechowywana jest zastępowany zawsze, gdy wartość jest przypisany do innego członka. Na przykład:  
  
```  
union         /* Defines a union named x */  
{  
    char *a, b;  
    float f[20];  
} x;  
```  
  
 Elementy członkowskie `x` są Unii, w kolejności ich deklaracji wskaźnika do `char` wartości, `char` wartość i tablicę **float** wartości. Magazyn przydzielony do `x` jest magazynu wymaganego przez 20-elementowa tablica `f`, ponieważ `f` jest najdłuższym element członkowski Unii. Ponieważ brak tagu jest skojarzona z Unii, jego typ jest bez nazwy lub "anonymous".  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje złożeń](../c-language/union-declarations.md)