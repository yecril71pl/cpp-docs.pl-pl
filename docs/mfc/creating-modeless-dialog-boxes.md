---
title: Tworzenie niemodalnych okien dialogowych
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
ms.openlocfilehash: 7da6d82257d1407dfcf4d6d3c15cdadbb8c0fa30
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685660"
---
# <a name="creating-modeless-dialog-boxes"></a>Tworzenie niemodalnych okien dialogowych

W przypadku niemodalnego okna dialogowego musisz podać własny Konstruktor publiczny w swojej klasie okna dialogowego. Aby utworzyć niemodalne okno dialogowe, Wywołaj konstruktora publicznego, a następnie wywołaj funkcję [tworzenia](../mfc/reference/cdialog-class.md#create) członka obiektu okna dialogowego w celu załadowania zasobu okna dialogowego. Można wywołać metodę **Create** w trakcie lub po wywołaniu konstruktora. Jeśli zasób okna dialogowego ma właściwość **WS_VISIBLE**, okno dialogowe pojawi się od razu. W przeciwnym razie należy wywołać funkcję członkowską [Funkcja ShowWindow](../mfc/reference/cwnd-class.md#showwindow) .

## <a name="see-also"></a>Zobacz także

[Praca z polami okna dialogowego w MFC](../mfc/life-cycle-of-a-dialog-box.md)
