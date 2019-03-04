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
ms.openlocfilehash: e0b7ff31576b345ac2911e62a6e10469845eecba
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302322"
---
# <a name="creating-and-displaying-dialog-boxes"></a>Tworzenie i wyświetlanie okien dialogowych

Tworzenie obiektu okna dialogowego jest fazach. Najpierw należy utworzyć obiektu okna dialogowego, a następnie utwórz okna dialogowego. Modalne i Niemodalne okna dialogowe różnią się nieco w procesie, używany do tworzenia i wyświetlania ich. W poniższej tabeli przedstawiono sposób modalne i Niemodalne okna dialogowego pola zwykle są zbudowane i wyświetlane.

### <a name="dialog-creation"></a>Tworzenie okna dialogowego

|Typ okna dialogowego|Jak utworzyć go|
|-----------------|----------------------|
|[Modeless](../mfc/creating-modeless-dialog-boxes.md)|Konstruowania `CDialog`, następnie wywołać `Create` funkcja elementu członkowskiego.|
|[Modal](../mfc/creating-modal-dialog-boxes.md)|Konstruowania `CDialog`, następnie wywołać `DoModal` funkcja elementu członkowskiego.|

Jeśli chcesz, tworzenia dialogowym z [szablonu okna dialogowego w pamięci](../mfc/using-a-dialog-template-in-memory.md) , zostały wykonane, a nie z zasobu szablonu okna dialogowego. Jednak to zaawansowane tematu.

## <a name="see-also"></a>Zobacz także

[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)
