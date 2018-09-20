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
ms.openlocfilehash: e41f9060ce24b89a0a7faae54ca6207c740475f3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443244"
---
# <a name="what-does-it-cost-me-to-derive-a-class-from-cobject"></a>Jaki jest koszt wyprowadzenia klasy z obiektu CObject?

Obciążenie w pochodząca od klasy [CObject](../mfc/reference/cobject-class.md) jest minimalny. Klasa pochodna dziedziczy funkcje wirtualne tylko cztery i jeden [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) obiektu.

## <a name="see-also"></a>Zobacz też

[Klasa CObject: często zadawane pytania](../mfc/cobject-class-frequently-asked-questions.md)
