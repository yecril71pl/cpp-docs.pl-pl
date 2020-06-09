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
ms.openlocfilehash: 54e43c8445bb6b8db4c6a7a4b28890e81be52d6c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616956"
---
# <a name="deriving-controls-from-a-standard-control"></a>Wyprowadzanie formantów z formantu standardowego

Podobnie jak w przypadku dowolnej klasy pochodnej [CWnd](reference/cwnd-class.md), można zmodyfikować zachowanie kontrolki, wprowadzając nową klasę z istniejącej klasy kontrolki.

### <a name="to-create-a-derived-control-class"></a>Aby utworzyć klasę formantów pochodnych

1. Utwórz klasę z istniejącej klasy formantów i opcjonalnie Przesłoń `Create` funkcję członkowską, tak aby dostarcza ona niezbędne argumenty do funkcji klasy podstawowej `Create` .

1. Udostępnianie funkcji elementów członkowskich programu obsługi komunikatów i wpisów mapy komunikatów w celu zmodyfikowania zachowania kontrolki w odpowiedzi na określone komunikaty systemu Windows. Zobacz [Mapowanie komunikatów do funkcji](reference/mapping-messages-to-functions.md).

1. Podaj nowe funkcje członkowskie, aby zwiększyć funkcjonalność formantu (opcjonalnie).

Użycie kontrolki pochodnej w oknie dialogowym wymaga dodatkowej pracy. Typy i położenia kontrolek w oknie dialogowym są zwykle określone w zasobie szablonu okna dialogowego. W przypadku tworzenia klasy formantów pochodnych nie można jej określić w szablonie okna dialogowego, ponieważ kompilator zasobów nie wie niczego o klasie pochodnej.

#### <a name="to-place-your-derived-control-in-a-dialog-box"></a>Aby umieścić formant pochodny w oknie dialogowym

1. Osadź obiekt klasy formantów pochodnych w deklaracji klasy dialogu pochodnego.

1. Przesłoń `OnInitDialog` funkcję członkowską w swojej klasie okna dialogowego, aby wywołać `SubclassDlgItem` funkcję członkowską dla kontrolki pochodnej.

`SubclassDlgItem`"dynamicznie podklasy" kontrolki utworzonej na podstawie szablonu okna dialogowego. Gdy kontrolka jest w sposób dynamiczny podklasą, można przełączać się do systemu Windows, przetwarzać niektóre komunikaty w aplikacji, a następnie przekazać pozostałe komunikaty do systemu Windows. Aby uzyskać więcej informacji, zobacz funkcja członkowska [SubclassDlgItem](reference/cwnd-class.md#subclassdlgitem) klasy `CWnd` w *Kompendium MFC*. Poniższy przykład pokazuje, jak napisać przesłonięcie `OnInitDialog` do wywołania `SubclassDlgItem` :

[!code-cpp[NVC_MFCControlLadenDialog#3](codesnippet/cpp/deriving-controls-from-a-standard-control_1.cpp)]

Ponieważ formant pochodny jest osadzony w klasie okna dialogowego, zostanie skonstruowany podczas konstruowania okna dialogowego i zostanie zniszczony po zniszczeniu okna dialogowego. Porównaj ten kod z przykładem w temacie [Dodawanie kontrolek](adding-controls-by-hand.md).

## <a name="see-also"></a>Zobacz też

[Tworzenie i używanie kontrolek](making-and-using-controls.md)<br/>
[Formanty](controls-mfc.md)
