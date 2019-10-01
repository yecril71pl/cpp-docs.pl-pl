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
ms.openlocfilehash: 6d23e4d2c9249ce248eb8092963036f2ba5cacac
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685746"
---
# <a name="creating-and-displaying-dialog-boxes"></a>Tworzenie i wyświetlanie okien dialogowych

Tworzenie obiektu okna dialogowego jest operacją dwuetapową. Najpierw należy skonstruować obiekt okna dialogowego, a następnie utworzyć okno dialogowe. Modalne i Niemodalne okna dialogowe różnią się nieco w procesie używanym do tworzenia i wyświetlania. W poniższej tabeli przedstawiono sposób, w jaki modalne i Niemodalne okna dialogowe są zwykle konstruowane i wyświetlane.

### <a name="dialog-creation"></a>Tworzenie okna dialogowego

|Typ okna dialogowego|Jak go utworzyć|
|-----------------|----------------------|
|[Formularz](../mfc/creating-modeless-dialog-boxes.md)|Skonstruuj `CDialog`, a następnie wywołaj funkcję członkowską `Create`.|
|[Modal](../mfc/creating-modal-dialog-boxes.md)|Skonstruuj `CDialog`, a następnie wywołaj funkcję członkowską `DoModal`.|

W razie potrzeby możesz utworzyć okno dialogowe z [szablonu okna dialogowego w pamięci](../mfc/using-a-dialog-template-in-memory.md) , który został skonstruowany, a nie z zasobu szablon okna dialogowego. Jest to jednak zaawansowana sekcja.

## <a name="see-also"></a>Zobacz także

[Praca z polami okna dialogowego w MFC](../mfc/life-cycle-of-a-dialog-box.md)
