---
title: Dynamiczne tworzenie obiektów
ms.date: 03/27/2020
helpviewer_keywords:
- object creation [MFC], dynamically at run time
- CObject class [MFC], dynamic object creation
- objects [MFC], creating dynamically at run time
- dynamic object creation [MFC]
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
ms.openlocfilehash: 40a17d3ed458d0634fd5bf27b54d0a36a65e35b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364810"
---
# <a name="dynamic-object-creation"></a>Dynamiczne tworzenie obiektów

W tym artykule wyjaśniono, jak dynamicznie utworzyć obiekt w czasie wykonywania. Procedura używa informacji o klasie w czasie wykonywania, jak omówiono w artykule [Uzyskiwanie dostępu do informacji o klasie w czasie wykonywania](../mfc/accessing-run-time-class-information.md).

#### <a name="dynamically-create-an-object-given-its-run-time-class"></a>Dynamicznie tworzenie obiektu, biorąc pod uwagę jego klasę czasu wykonywania

1. Poniższy kod służy do dynamicznego `CreateObject` tworzenia obiektu `CRuntimeClass`za pomocą funkcji programu . W przypadku `CreateObject` awarii zwraca **wartość NULL** zamiast wywoływania wyjątku:

   [!code-cpp[NVC_MFCCObjectSample#6](../mfc/codesnippet/cpp/dynamic-object-creation_1.cpp)]

## <a name="see-also"></a>Zobacz też

[Niszczenie obiektów](tn017-destroying-window-objects.md)
okien[za pomocą CObject](using-cobject.md)
