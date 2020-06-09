---
title: CReBar vs. CReBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- CReBar class [MFC], vs. CReBarCtrl
- rebar controls [MFC], CReBarCtrl class [MFC]
- GetReBarCtrl class [MFC]
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
ms.openlocfilehash: 05decc095e43426044c4487b9aca05268642f915
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620460"
---
# <a name="crebar-vs-crebarctrl"></a>CReBar vs. CReBarCtrl

MFC udostępnia dwie klasy do tworzenia pasków: [CReBar](reference/crebar-class.md) i [Korzystanie CReBarCtrl](reference/crebarctrl-class.md) (które zawijają interfejs API usługi Common Control systemu Windows). `CReBar`oferuje wszystkie funkcje formantu paska pomocniczego Common i obsługuje wiele wymaganych wspólnych ustawień i struktur kontroli.

`CReBarCtrl`jest klasą otoki dla kontrolki Win32 paska pomocniczego i dlatego może być łatwiejsza do wdrożenia, jeśli nie zamierzasz zintegrować paska pomocniczego z architekturą MFC. Jeśli planujesz używać `CReBarCtrl` paska pomocniczego i zintegrujesz ją z architekturą MFC, musisz zadbać o to, aby przekazywać manipulowanie formantami paska pomocniczego do biblioteki MFC. Ta komunikacja nie jest trudna. Jednak w przypadku korzystania z programu jest to dodatkowa niepotrzebna `CReBar` .

Visual C++ zapewnia dwa sposoby korzystania ze wspólnej kontroli paska pomocniczego.

- Utwórz paska pomocniczego za pomocą `CReBar` , a następnie Wywołaj [CReBar:: GetReBarCtrl](reference/crebar-class.md#getrebarctrl) , aby uzyskać dostęp do `CReBarCtrl` funkcji składowych.

    > [!NOTE]
    >  `CReBar::GetReBarCtrl`jest wbudowaną funkcją składową, która rzutuje wskaźnik **tego** obiektu paska pomocniczego. Oznacza to, że w czasie wykonywania wywołanie funkcji nie ma żadnych kosztów.

- Utwórz paska pomocniczego za pomocą konstruktora [Korzystanie CReBarCtrl](reference/crebarctrl-class.md).

Każda metoda zapewnia dostęp do funkcji Członkowskich formantu paska pomocniczego. Po wywołaniu `CReBar::GetReBarCtrl` , zwraca odwołanie do `CReBarCtrl` obiektu, aby można było użyć dowolnego zestawu funkcji Członkowskich. Zobacz [CReBar](reference/crebar-class.md) , aby uzyskać informacje dotyczące konstruowania i tworzenia paska pomocniczego przy użyciu `CReBar` .

## <a name="see-also"></a>Zobacz też

[Korzystanie z CReBarCtrl](using-crebarctrl.md)<br/>
[Formanty](controls-mfc.md)
