---
title: Czy muszę wyprowadzać nowe klasy z obiektu CObject?
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
ms.openlocfilehash: d38e589f371fc56f5566c56de7b19c366065a503
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446926"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>Czy muszę wyprowadzać nowe klasy z obiektu CObject?

Nie.

Utwórz klasę z [CObject](../mfc/reference/cobject-class.md) , gdy potrzebujesz udostępnianych przez nią obiektów, takich jak Serializacja lub dynamiczne tworzenie. Wiele klas danych musi być serializowanych do plików, więc często dobrym pomysłem jest uzyskanie ich z `CObject`. Przykład klasy pochodzącej od `CObject`można znaleźć w [przykładowym bazgrołie](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Zobacz też

[Klasa CObject: często zadawane pytania](../mfc/cobject-class-frequently-asked-questions.md)
