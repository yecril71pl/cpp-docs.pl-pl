---
title: Czy muszę wyprowadzać nowe klasy z obiektu CObject?
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
ms.openlocfilehash: 371ede0f0921182c066b4cb224e66b18eb6f1208
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616737"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>Czy muszę wyprowadzać nowe klasy z obiektu CObject?

Nie.

Utwórz klasę z [CObject](reference/cobject-class.md) , gdy potrzebujesz udostępnianych przez nią obiektów, takich jak Serializacja lub dynamiczne tworzenie. Wiele klas danych musi być serializowanych do plików, więc często dobrym pomysłem jest uzyskanie ich z `CObject` . Przykład klasy pochodzącej od elementu `CObject` można znaleźć w przykładowym [bazgrołie](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Zobacz też

[Klasa CObject: często zadawane pytania](cobject-class-frequently-asked-questions.md)
