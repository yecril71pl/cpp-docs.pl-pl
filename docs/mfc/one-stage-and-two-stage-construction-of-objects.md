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
ms.openlocfilehash: 7c53f99932887acad4d2eab5c15ed73b66b359fd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346015"
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>Jedno- i dwuetapowa konstrukcja obiektów
Masz wybór między dwie metody tworzenia obiektów graficznych, takich jak pióra i pędzle:  
  
-   *Jednym etapie konstrukcji*: konstrukcja i zainicjować obiektu w ramach jednego etapu, wszystko w konstruktorze.  
  
-   *Dwuetapowa konstrukcja*: konstrukcja i zainicjować obiektu w dwóch etapach oddzielne. Konstruktor tworzy obiekt i inicjowane błędu funkcji inicjowania.  
  
 Dwuetapowa konstrukcja jest bezpieczniejsze. W jednym etapie konstrukcji Konstruktor może wywoływać wyjątek, jeśli musisz podać Niepoprawne argumenty lub alokacja pamięci nie powiodło się. Ten problem jest uniknąć przez dwuetapowa konstrukcja, mimo że trzeba sprawdzić awarii. W obu przypadkach zniszczenie obiektu jest ten sam proces.  
  
> [!NOTE]
>  Te techniki dotyczą tworzenia żadnych obiektów, nie tylko graficzne obiektów.  
  
## <a name="example-of-both-construction-techniques"></a>Przykład obie techniki konstrukcji  
 W poniższym przykładzie krótki przedstawiono obie metody konstruowania obiektu pióra:  
  
 [!code-cpp[NVC_MFCDocViewSDI#6](../mfc/codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Obiekty graficzne](../mfc/graphic-objects.md)  
  
-   [Wybieranie obiektu graficznego do kontekstu urządzenia](../mfc/selecting-a-graphic-object-into-a-device-context.md)  
  
-   [Konteksty urządzenia](../mfc/device-contexts.md)  
  
-   [Rysowanie w widoku](../mfc/drawing-in-a-view.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty graficzne](../mfc/graphic-objects.md)

