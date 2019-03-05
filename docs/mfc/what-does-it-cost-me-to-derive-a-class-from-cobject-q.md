---
title: Jaki jest koszt wyprowadzenia klasy z obiektu CObject?
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- CObject class [MFC], overhead of derived classes [MFC]
ms.assetid: 9b92c98b-b3dd-48a7-9d24-c3b8554edf90
ms.openlocfilehash: de760a2fd2908595314dc09cf5a317da3581e3bb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326390"
---
# <a name="what-does-it-cost-me-to-derive-a-class-from-cobject"></a>Jaki jest koszt wyprowadzenia klasy z obiektu CObject?

Obciążenie w pochodząca od klasy [CObject](../mfc/reference/cobject-class.md) jest minimalny. Klasa pochodna dziedziczy funkcje wirtualne tylko cztery i jeden [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) obiektu.

## <a name="see-also"></a>Zobacz także

[Klasa CObject: Często zadawane pytania](../mfc/cobject-class-frequently-asked-questions.md)
