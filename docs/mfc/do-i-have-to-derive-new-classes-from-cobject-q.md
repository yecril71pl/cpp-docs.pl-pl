---
title: Czy muszę wyprowadzać nowe klasy z obiektu CObject?
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
ms.openlocfilehash: c2361967dcfce5e46aeec65ade3d7056b362949d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636608"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>Czy muszę wyprowadzać nowe klasy z obiektu CObject?

Nie.

Wyprowadzić klasę z [CObject](../mfc/reference/cobject-class.md) gdy będziesz potrzebować urządzeń zapewnia, takich jak serializacji lub creatability dynamicznych. Wiele klas danych muszą być serializowany do plików, więc jest często dobrym pomysłem jest pochodną od `CObject`. Na przykład klasę pochodną `CObject`, zobacz [próbki Bazgroły](../visual-cpp-samples.md).

## <a name="see-also"></a>Zobacz też

[Klasa CObject: często zadawane pytania](../mfc/cobject-class-frequently-asked-questions.md)
