---
title: Czy muszę wyprowadzać nowe klasy z obiektu CObject? | Microsoft Docs
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
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 51904ac06ae6c2db5586f8dc405f85145c5b1f30
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343063"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>Czy muszę wyprowadzać nowe klasy z obiektu CObject?
Nie, nie.  
  
 Klasa wyprowadzona z [CObject](../mfc/reference/cobject-class.md) gdy będziesz potrzebować urządzenia udostępnia, np. serializacji lub creatability dynamicznych. Wiele klas danych konieczne zserializowana do plików, dlatego często dobrym pomysłem pochodzić od `CObject`. Na przykład klasa pochodzi od `CObject`, zobacz [próbki bazgrołów](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CObject: często zadawane pytania](../mfc/cobject-class-frequently-asked-questions.md)
