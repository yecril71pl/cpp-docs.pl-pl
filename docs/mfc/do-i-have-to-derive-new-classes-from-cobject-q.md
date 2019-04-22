---
title: Czy muszę wyprowadzać nowe klasy z obiektu CObject?
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
ms.openlocfilehash: 30eb3ce5bbb72ab685ed891644a478a36026ebea
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58772309"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>Czy muszę wyprowadzać nowe klasy z obiektu CObject?

Nie.

Wyprowadzić klasę z [CObject](../mfc/reference/cobject-class.md) gdy będziesz potrzebować urządzeń zapewnia, takich jak serializacji lub creatability dynamicznych. Wiele klas danych muszą być serializowany do plików, więc jest często dobrym pomysłem jest pochodną od `CObject`. Na przykład klasę pochodną `CObject`, zobacz [próbki Bazgroły](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Zobacz także

[Klasa CObject: Często zadawane pytania](../mfc/cobject-class-frequently-asked-questions.md)
