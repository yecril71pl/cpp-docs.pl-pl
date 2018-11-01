---
title: Wyprowadzanie formantów z formantu standardowego
ms.date: 11/04/2016
helpviewer_keywords:
- standard controls [MFC], deriving controls from
- common controls [MFC], deriving from
- derived controls
- controls [MFC], derived
- Windows common controls [MFC], deriving from
- standard controls
ms.assetid: a6f84315-7007-4e0e-8576-78be81254802
ms.openlocfilehash: a6ce915102a8b85f135aa2c59e5e824b4fee25cf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666287"
---
# <a name="deriving-controls-from-a-standard-control"></a>Wyprowadzanie formantów z formantu standardowego

Podobnie jak w przypadku dowolnego [CWnd](../mfc/reference/cwnd-class.md)-klasy, można zmodyfikować zachowanie kontrolki wyprowadzanie nowe klasy z istniejącej klasy kontrolki.

### <a name="to-create-a-derived-control-class"></a>Aby utworzyć klasy pochodnej kontroli

1. Klasa dziedziczyć po istniejącej klasy formantu i opcjonalnie zastąpić `Create` funkcję członkowską, dzięki czemu zapewnia wymagane argumenty do klasy bazowej `Create` funkcji.

1. Zapewnia funkcje Członkowskie obsługi wiadomości i wpisy mapy komunikatów, aby zmodyfikować zachowanie kontrolki w odpowiedzi na określone komunikaty Windows. Zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md).

1. Podaj nowe funkcje Członkowskie, aby rozszerzyć funkcjonalność formantu (opcjonalnie).

Używanie pochodnej formantu w oknie dialogowym wymaga dodatkowej pracy. Typy i położenie formantów w oknie dialogowym zazwyczaj są określane w zasobach szablonu okna dialogowego. Po utworzeniu klasy pochodnej kontroli, nie można określić je w szablonu okna dialogowego, ponieważ kompilator zasobów nie zna o swojej klasy pochodnej.

#### <a name="to-place-your-derived-control-in-a-dialog-box"></a>Aby umieścić pochodnej formantu w oknie dialogowym

1. Osadzić obiekt klasy pochodnej kontrolki w deklaracji klasy pochodnej okien dialogowych.

1. Zastąp `OnInitDialog` funkcji składowej WE klasy okien dialogowych do wywołania `SubclassDlgItem` składowa pochodnej kontrolki.

`SubclassDlgItem` "dynamicznie podklasy" kontrolki utworzone na podstawie szablonu okna dialogowego. W wypadku dynamicznie podklasy kontrolki można dołączyć do Windows, przetwarzać komunikaty z żądaniem w swojej aplikacji, a następnie przekazuje komunikaty pozostałe Windows. Aby uzyskać więcej informacji, zobacz [SubclassDlgItem](../mfc/reference/cwnd-class.md#subclassdlgitem) funkcji składowej klasy typu `CWnd` w *odwołanie MFC*. W poniższym przykładzie pokazano, jak można napisać nadpisanie `OnInitDialog` do wywołania `SubclassDlgItem`:

[!code-cpp[NVC_MFCControlLadenDialog#3](../mfc/codesnippet/cpp/deriving-controls-from-a-standard-control_1.cpp)]

Ponieważ osadzone kontroli pochodne klasy okien dialogowych zostanie wykonane, okno dialogowe jest tworzony, gdy zostaną zniszczone, kiedy niszczony jest okno dialogowe. Porównaj ten kod do przykładu w [dodawania formantów By ręcznie](../mfc/adding-controls-by-hand.md).

## <a name="see-also"></a>Zobacz też

[Tworzenie i używanie kontrolek](../mfc/making-and-using-controls.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

