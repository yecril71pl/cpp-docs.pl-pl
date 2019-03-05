---
title: Dynamiczne tworzenie obiektów
ms.date: 11/04/2016
helpviewer_keywords:
- object creation [MFC], dynamically at run time
- CObject class [MFC], dynamic object creation
- objects [MFC], creating dynamically at run time
- dynamic object creation [MFC]
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
ms.openlocfilehash: 3478e5481c177e0ebca1e6b5c2cd07509371c5ef
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260130"
---
# <a name="dynamic-object-creation"></a>Dynamiczne tworzenie obiektów

W tym artykule wyjaśniono, jak utworzyć obiekt dynamicznie w czasie wykonywania. Procedura używa informacji o klasie czasu wykonywania, zgodnie z opisem w artykule [uzyskiwania dostępu do środowiska wykonawczego informacji o klasie](../mfc/accessing-run-time-class-information.md).

#### <a name="to-dynamically-create-an-object-given-its-run-time-class"></a>Umożliwia dynamiczne tworzenie dany obiekt na podstawie swojej klasy środowiska wykonawczego

1. Użyj poniższego kodu, aby dynamicznie utworzyć obiekt przy użyciu `CreateObject` funkcji `CRuntimeClass`. Należy pamiętać, że w przypadku awarii `CreateObject` zwraca **NULL** zamiast zgłaszania wyjątku:

   [!code-cpp[NVC_MFCCObjectSample#6](../mfc/codesnippet/cpp/dynamic-object-creation_1.cpp)]

## <a name="see-also"></a>Zobacz także

[Używanie obiektu CObject](../mfc/using-cobject.md)
