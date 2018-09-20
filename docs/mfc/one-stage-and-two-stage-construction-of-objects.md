---
title: Jedno- i dwuetapowa konstrukcja obiektów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a6454e34830591eccb2b696948d02f74ad8cebfd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426578"
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>Jedno- i dwuetapowa konstrukcja obiektów

Możesz dokonać wyboru między dwie metody tworzenia obiektów graficznych, takich jak pióra i pędzle:

- *Konstrukcja jednego etapu*: konstrukcja i zainicjować obiekt w ramach jednego etapu, za pomocą konstruktora.

- *Dwuetapowa konstrukcja*: konstrukcja i zainicjować obiekt w dwóch etapach oddzielne. Konstruktor tworzy obiekt, a funkcja inicjowania inicjuje ją.

Dwuetapowa konstrukcja jest bezpieczniejsze. W jednym etapie konstrukcji Konstruktor może zgłosić wyjątek, jeśli podasz Niepoprawne argumenty lub alokacja pamięci nie powiedzie się. Ten problem jest unikać wynikające z konstrukcji dwuetapowego, chociaż ma pod kątem błędów. W obu przypadkach zniszczenia obiektu jest tego samego procesu.

> [!NOTE]
>  Techniki te dotyczą tworzenia wszystkie obiekty, obiekty nie tylko graficzne.

## <a name="example-of-both-construction-techniques"></a>Przykład obu tych technik konstrukcji

BRIEF: poniższy kod przedstawia obie metody tworzenia obiekt pen:

[!code-cpp[NVC_MFCDocViewSDI#6](../mfc/codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Obiekty graficzne](../mfc/graphic-objects.md)

- [Wybieranie obiektu graficznego do kontekstu urządzenia](../mfc/selecting-a-graphic-object-into-a-device-context.md)

- [Konteksty urządzenia](../mfc/device-contexts.md)

- [Rysowanie w widoku](../mfc/drawing-in-a-view.md)

## <a name="see-also"></a>Zobacz też

[Obiekty graficzne](../mfc/graphic-objects.md)

