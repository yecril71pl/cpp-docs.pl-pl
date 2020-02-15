---
title: Kontener Class::erase
ms.date: 11/04/2016
helpviewer_keywords:
- erase method
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
ms.openlocfilehash: 1fa3fe7dee10f3033b84a671fdc35c193cd6ec3c
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257900"
---
# <a name="container-classerase"></a>Kontener Class::erase

> [!NOTE]
> Ten temat znajduje się w dokumentacji C++ firmy Microsoft jako przykład niefunkcjonalny kontenerów używanych w C++ standardowej bibliotece. Aby uzyskać więcej informacji, zobacz [ C++ Kontenery biblioteki standardowej](../standard-library/stl-containers.md).

Usuwa element.

## <a name="syntax"></a>Składnia

```cpp
iterator erase(
    iterator _Where);

iterator erase(
    iterator first,
    iterator last);
```

## <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska usuwa element kontrolowanej sekwencji wskazywany przez *_Where*. Druga funkcja członkowska usuwa elementy z kontrolowanej sekwencji z zakresu [`first`, `last`). Oba zwracają iterator, który wyznacza pierwszy element pozostały poza elementami usuniętymi lub [kończy](../standard-library/container-class-end.md) , jeśli taki element nie istnieje.

Funkcje członkowskie zwracają wyjątek tylko wtedy, gdy operacja kopiowania zgłasza wyjątek.

## <a name="see-also"></a>Zobacz też

[Sample Container, klasa](../standard-library/sample-container-class.md)
