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
ms.openlocfilehash: 778ee0cbb154c65b0cc74a207a175354c2e2a90b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431086"
---
# <a name="creating-and-displaying-dialog-boxes"></a>Tworzenie i wyświetlanie okien dialogowych

Tworzenie obiektu okna dialogowego jest fazach. Najpierw należy utworzyć obiektu okna dialogowego, a następnie utwórz okna dialogowego. Modalne i Niemodalne okna dialogowe różnią się nieco w procesie, używany do tworzenia i wyświetlania ich. W poniższej tabeli przedstawiono sposób modalne i Niemodalne okna dialogowego pola zwykle są zbudowane i wyświetlane.

### <a name="dialog-creation"></a>Tworzenie okna dialogowego

|Typ okna dialogowego|Jak utworzyć go|
|-----------------|----------------------|
|[Niemodalne](../mfc/creating-modeless-dialog-boxes.md)|Konstruowania `CDialog`, następnie wywołać `Create` funkcja elementu członkowskiego.|
|[Modalne](../mfc/creating-modal-dialog-boxes.md)|Konstruowania `CDialog`, następnie wywołać `DoModal` funkcja elementu członkowskiego.|

Jeśli chcesz, tworzenia dialogowym z [szablonu okna dialogowego w pamięci](../mfc/using-a-dialog-template-in-memory.md) , zostały wykonane, a nie z zasobu szablonu okna dialogowego. Jednak to zaawansowane tematu.

## <a name="see-also"></a>Zobacz też

[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

