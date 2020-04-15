---
title: Jedno- i dwuetapowa konstrukcja obiektów
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
ms.openlocfilehash: 8f221ac6b63a06c65f932a695dfbf7b93ae7ac96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375965"
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>Jedno- i dwuetapowa konstrukcja obiektów

Masz do wyboru dwie techniki tworzenia obiektów graficznych, takich jak pióra i pędzle:

- *Konstrukcja jednoetapowa*: Konstruuj i inicjuj obiekt w jednym etapie, wszystko za pomocą konstruktora.

- *Konstrukcja dwustopniowa*: Konstruuj i inicjuj obiekt w dwóch oddzielnych etapach. Konstruktor tworzy obiekt, a funkcja inicjowania inicjuje go.

Dwustopniowa konstrukcja jest zawsze bezpieczniejsza. W konstrukcji jednoetapowej konstruktor może zgłosić wyjątek, jeśli podasz niepoprawne argumenty lub alokacji pamięci nie powiedzie się. Tego problemu unika się przez dwustopniową konstrukcję, chociaż trzeba sprawdzić, czy nie ma awarii. W obu przypadkach zniszczenie obiektu jest tym samym procesem.

> [!NOTE]
> Techniki te mają zastosowanie do tworzenia dowolnych obiektów, a nie tylko obiektów graficznych.

## <a name="example-of-both-construction-techniques"></a>Przykład obu technik budowlanych

Poniższy krótki przykład przedstawia obie metody konstruowania obiektu pióra:

[!code-cpp[NVC_MFCDocViewSDI#6](../mfc/codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz wiedzieć więcej o

- [Obiekty graficzne](../mfc/graphic-objects.md)

- [Wybieranie obiektu graficznego w kontekście urządzenia](../mfc/selecting-a-graphic-object-into-a-device-context.md)

- [Konteksty urządzeń](../mfc/device-contexts.md)

- [Rysowanie w widoku](../mfc/drawing-in-a-view.md)

## <a name="see-also"></a>Zobacz też

[Obiekty graficzne](../mfc/graphic-objects.md)
