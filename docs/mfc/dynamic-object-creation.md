---
title: Dynamiczne tworzenie obiektów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- object creation [MFC], dynamically at run time
- CObject class [MFC], dynamic object creation
- objects [MFC], creating dynamically at run time
- dynamic object creation [MFC]
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 19f6a895eb48b3ae1816edc45747c865e7e03b96
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420156"
---
# <a name="dynamic-object-creation"></a>Dynamiczne tworzenie obiektów

W tym artykule wyjaśniono, jak utworzyć obiekt dynamicznie w czasie wykonywania. Procedura używa informacji o klasie czasu wykonywania, zgodnie z opisem w artykule [uzyskiwania dostępu do środowiska wykonawczego informacji o klasie](../mfc/accessing-run-time-class-information.md).

#### <a name="to-dynamically-create-an-object-given-its-run-time-class"></a>Umożliwia dynamiczne tworzenie dany obiekt na podstawie swojej klasy środowiska wykonawczego

1. Użyj poniższego kodu, aby dynamicznie utworzyć obiekt przy użyciu `CreateObject` funkcji `CRuntimeClass`. Należy pamiętać, że w przypadku awarii `CreateObject` zwraca **NULL** zamiast zgłaszania wyjątku:

     [!code-cpp[NVC_MFCCObjectSample#6](../mfc/codesnippet/cpp/dynamic-object-creation_1.cpp)]

## <a name="see-also"></a>Zobacz też

[Używanie obiektu CObject](../mfc/using-cobject.md)

