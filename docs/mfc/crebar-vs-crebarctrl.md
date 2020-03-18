---
title: CReBar vs. CReBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- CReBar class [MFC], vs. CReBarCtrl
- rebar controls [MFC], CReBarCtrl class [MFC]
- GetReBarCtrl class [MFC]
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
ms.openlocfilehash: 94f889be453a17a55357a260bd2a0c07037f6ded
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445285"
---
# <a name="crebar-vs-crebarctrl"></a>CReBar vs. CReBarCtrl

MFC udostępnia dwie klasy do tworzenia pasków: [CReBar](../mfc/reference/crebar-class.md) i [Korzystanie CReBarCtrl](../mfc/reference/crebarctrl-class.md) (które zawijają interfejs API usługi Common Control systemu Windows). `CReBar` oferuje wszystkie funkcje paska pomocniczego wspólnego formantu i obsługuje wiele wymaganych wspólnych ustawień i struktur kontroli.

`CReBarCtrl` jest klasą otoki dla kontrolki Win32 paska pomocniczego i dlatego może być łatwiejsza do wdrożenia, jeśli nie zamierzasz zintegrować paska pomocniczego z architekturą MFC. Jeśli zamierzasz używać `CReBarCtrl` i zintegrować paska pomocniczego z architekturą MFC, musisz zadbać o to, aby przekazywać manipulowanie formantami paska pomocniczego do MFC. Ta komunikacja nie jest trudna. Jednak w przypadku korzystania z `CReBar`nie jest to dodatkowe działanie, które jest niepotrzebne.

Wizualizacja C++ zapewnia dwa sposoby korzystania ze wspólnej kontroli paska pomocniczego.

- Utwórz paska pomocniczego przy użyciu `CReBar`, a następnie Wywołaj [CReBar:: GetReBarCtrl](../mfc/reference/crebar-class.md#getrebarctrl) , aby uzyskać dostęp do `CReBarCtrl` funkcji Członkowskich.

    > [!NOTE]
    >  `CReBar::GetReBarCtrl` to wbudowana funkcja członkowska, która rzutuje wskaźnik **tego** obiektu paska pomocniczego. Oznacza to, że w czasie wykonywania wywołanie funkcji nie ma żadnych kosztów.

- Utwórz paska pomocniczego za pomocą konstruktora [Korzystanie CReBarCtrl](../mfc/reference/crebarctrl-class.md).

Każda metoda zapewnia dostęp do funkcji Członkowskich formantu paska pomocniczego. Po wywołaniu `CReBar::GetReBarCtrl`zwraca odwołanie do obiektu `CReBarCtrl`, aby można było użyć dowolnego zestawu funkcji Członkowskich. Zobacz [CReBar](../mfc/reference/crebar-class.md) , aby uzyskać informacje dotyczące konstruowania i tworzenia paska pomocniczego przy użyciu `CReBar`.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
