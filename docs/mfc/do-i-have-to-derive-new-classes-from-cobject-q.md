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
ms.openlocfilehash: ec080e556b57afadbc3d958f4dba5ac6393108aa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408911"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>Czy muszę wyprowadzać nowe klasy z obiektu CObject?

Nie.

Wyprowadzić klasę z [CObject](../mfc/reference/cobject-class.md) gdy będziesz potrzebować urządzeń zapewnia, takich jak serializacji lub creatability dynamicznych. Wiele klas danych muszą być serializowany do plików, więc jest często dobrym pomysłem jest pochodną od `CObject`. Na przykład klasę pochodną `CObject`, zobacz [próbki Bazgroły](../visual-cpp-samples.md).

## <a name="see-also"></a>Zobacz też

[Klasa CObject: często zadawane pytania](../mfc/cobject-class-frequently-asked-questions.md)
