---
title: Jaki jest koszt wyprowadzenia klasy z obiektu CObject? | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CObject
dev_langs:
- C++
helpviewer_keywords:
- CObject class [MFC], overhead of derived classes [MFC]
ms.assetid: 9b92c98b-b3dd-48a7-9d24-c3b8554edf90
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 253982da087dfc4b8ae9878b9788529960ecd8a3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="what-does-it-cost-me-to-derive-a-class-from-cobject"></a>Jaki jest koszt wyprowadzenia klasy z obiektu CObject?
Obciążenie w tworzenia klasy pochodnej z klasy [CObject](../mfc/reference/cobject-class.md) jest minimalny. Pochodne klasy dziedziczy tylko cztery funkcji wirtualnych i jeden [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CObject: często zadawane pytania](../mfc/cobject-class-frequently-asked-questions.md)
