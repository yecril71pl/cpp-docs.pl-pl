---
title: Jedno- i dwuetapowa konstrukcja obiektów
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
ms.openlocfilehash: 871db7abd2682d557bf2e80e9cb97624f0dc53a6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263640"
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>Jedno- i dwuetapowa konstrukcja obiektów

Możesz dokonać wyboru między dwie metody tworzenia obiektów graficznych, takich jak pióra i pędzle:

- *Konstrukcja jednego etapu*: Skonstruuj i inicjują obiekt w ramach jednego etapu, wszystkie za pomocą konstruktora.

- *Dwuetapowa konstrukcja*: Skonstruuj i inicjują obiekt w dwóch etapach oddzielne. Konstruktor tworzy obiekt, a funkcja inicjowania inicjuje ją.

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

## <a name="see-also"></a>Zobacz także

[Obiekty graficzne](../mfc/graphic-objects.md)
