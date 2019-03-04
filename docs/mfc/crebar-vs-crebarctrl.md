---
title: CReBar a CReBarCtrl
ms.date: 11/04/2016
f1_keywords:
- CReBar
- CReBarCtrl
helpviewer_keywords:
- CReBar class [MFC], vs. CReBarCtrl
- rebar controls [MFC], CReBarCtrl class [MFC]
- GetReBarCtrl class [MFC]
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
ms.openlocfilehash: a1b5cda729e760246449bf197fdc9b32752b96e8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279214"
---
# <a name="crebar-vs-crebarctrl"></a>CReBar a CReBarCtrl

Biblioteka MFC zawiera dwie klasy, aby utworzyć rebars: [CReBar](../mfc/reference/crebar-class.md) i [z CReBarCtrl](../mfc/reference/crebarctrl-class.md) (która opakowuje interfejs API sterowania wspólnej Windows). `CReBar` zapewnia wszystkie funkcje formantu typowego paska pomocniczego i obsługuje wiele wymagane typowe ustawienia kontroli i struktury dla Ciebie.

`CReBarCtrl` jest to klasa otoki dla formantu paska pomocniczego Win32, który może być łatwiejsze do wdrożenia, jeśli nie zamierzasz zintegrować paska pomocniczego architektury MFC. Jeśli planujesz używać `CReBarCtrl` i zintegruj paska pomocniczego architektury MFC, należy zwrócić uwagę dodatkowe do komunikowania się manipulacje kontrolki paska pomocniczego z MFC. Ta informacja nie jest trudne; jest jednak dodatkowej pracy, który jest zbędny w przypadku używania `CReBar`.

Visual C++ zapewnia dwa sposoby, aby móc korzystać z formantu typowego paska pomocniczego.

- Utworzyć przy użyciu paska pomocniczego `CReBar`, a następnie wywołaj [CReBar::GetReBarCtrl](../mfc/reference/crebar-class.md#getrebarctrl) uzyskać dostęp do `CReBarCtrl` funkcji elementów członkowskich.

    > [!NOTE]
    >  `CReBar::GetReBarCtrl` jest funkcją śródwierszową elementu członkowskiego, który rzutuje **to** wskaźnika obiektu paska pomocniczego. Oznacza to, że w czasie wykonywania, wywołanie funkcji ma bez.

- Tworzenie przy użyciu paska pomocniczego [z CReBarCtrl](../mfc/reference/crebarctrl-class.md)przez Konstruktor.

Każda z tych metod zapewni Ci dostęp do funkcji Członkowskich kontrolki paska pomocniczego. Gdy wywołujesz `CReBar::GetReBarCtrl`, zwraca odwołanie do `CReBarCtrl` obiektu, aby można było używać któryś zbiór elementów członkowskich. Zobacz [CReBar](../mfc/reference/crebar-class.md) informacji na temat tworzenia i utworzenie przy użyciu paska pomocniczego `CReBar`.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
