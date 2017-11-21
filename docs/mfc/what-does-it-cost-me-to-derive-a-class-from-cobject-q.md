---
title: Jaki jest koszt wyprowadzenia klasy z obiektu CObject? | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CObject
dev_langs: C++
helpviewer_keywords: CObject class [MFC], overhead of derived classes [MFC]
ms.assetid: 9b92c98b-b3dd-48a7-9d24-c3b8554edf90
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e440897bd3c047a5f6598187004808defb4f6eaa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="what-does-it-cost-me-to-derive-a-class-from-cobject"></a>Jaki jest koszt wyprowadzenia klasy z obiektu CObject?
Obciążenie w tworzenia klasy pochodnej z klasy [CObject](../mfc/reference/cobject-class.md) jest minimalny. Pochodne klasy dziedziczy tylko cztery funkcji wirtualnych i jeden [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CObject: Często zadawane pytania](../mfc/cobject-class-frequently-asked-questions.md)
