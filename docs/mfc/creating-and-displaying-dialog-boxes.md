---
title: Tworzenie i wyświetlanie okien dialogowych
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- opening dialog boxes
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], displaying
ms.assetid: 1c5219ee-8b46-44bc-9708-83705d4f248b
ms.openlocfilehash: 649d64f8e8b894027b9d6850b62d357d79c1dafa
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616274"
---
# <a name="creating-and-displaying-dialog-boxes"></a>Tworzenie i wyświetlanie okien dialogowych

Tworzenie obiektu okna dialogowego jest operacją dwuetapową. Najpierw należy skonstruować obiekt okna dialogowego, a następnie utworzyć okno dialogowe. Modalne i Niemodalne okna dialogowe różnią się nieco w procesie używanym do tworzenia i wyświetlania. W poniższej tabeli przedstawiono sposób, w jaki modalne i Niemodalne okna dialogowe są zwykle konstruowane i wyświetlane.

### <a name="dialog-creation"></a>Tworzenie okna dialogowego

|Typ okna dialogowego|Jak go utworzyć|
|-----------------|----------------------|
|[Formularz](creating-modeless-dialog-boxes.md)|Utwórz `CDialog` , a następnie Wywołaj `Create` funkcję członkowską.|
|[Modal](creating-modal-dialog-boxes.md)|Utwórz `CDialog` , a następnie Wywołaj `DoModal` funkcję członkowską.|

W razie potrzeby możesz utworzyć okno dialogowe z [szablonu okna dialogowego w pamięci](using-a-dialog-template-in-memory.md) , który został skonstruowany, a nie z zasobu szablon okna dialogowego. Jest to jednak zaawansowana sekcja.

## <a name="see-also"></a>Zobacz też

[Praca z oknami dialogowymi w MFC](life-cycle-of-a-dialog-box.md)
