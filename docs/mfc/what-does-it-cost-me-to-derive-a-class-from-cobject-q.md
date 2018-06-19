---
title: Jaki jest koszt wyprowadzenia klasy z obiektu CObject? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CObject
dev_langs:
- C++
helpviewer_keywords:
- CObject class [MFC], overhead of derived classes [MFC]
ms.assetid: 9b92c98b-b3dd-48a7-9d24-c3b8554edf90
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3ffff35cdef6cf2f730687334bbb56bc078371a7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381680"
---
# <a name="what-does-it-cost-me-to-derive-a-class-from-cobject"></a>Jaki jest koszt wyprowadzenia klasy z obiektu CObject?
Obciążenie w tworzenia klasy pochodnej z klasy [CObject](../mfc/reference/cobject-class.md) jest minimalny. Pochodne klasy dziedziczy tylko cztery funkcji wirtualnych i jeden [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CObject: często zadawane pytania](../mfc/cobject-class-frequently-asked-questions.md)
