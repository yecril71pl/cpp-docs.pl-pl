---
title: Tworzenie niemodalnych okien dialogowych
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
ms.openlocfilehash: 7a6125e84438b0ef2ad541c26bda33051d483c8d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619641"
---
# <a name="creating-modeless-dialog-boxes"></a>Tworzenie niemodalnych okien dialogowych

W przypadku niemodalnego okna dialogowego musisz podać własny Konstruktor publiczny w swojej klasie okna dialogowego. Aby utworzyć niemodalne okno dialogowe, Wywołaj konstruktora publicznego, a następnie wywołaj funkcję [tworzenia](reference/cdialog-class.md#create) członka obiektu okna dialogowego w celu załadowania zasobu okna dialogowego. Można wywołać metodę **Create** w trakcie lub po wywołaniu konstruktora. Jeśli zasób okna dialogowego ma właściwość **WS_VISIBLE**, zostanie wyświetlone okno dialogowe. W przeciwnym razie należy wywołać funkcję członkowską [Funkcja ShowWindow](reference/cwnd-class.md#showwindow) .

## <a name="see-also"></a>Zobacz też

[Praca z oknami dialogowymi w MFC](life-cycle-of-a-dialog-box.md)
