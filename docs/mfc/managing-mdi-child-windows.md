---
title: Zarządzanie oknami podrzędnymi MDI
ms.date: 11/19/2018
f1_keywords:
- MDICLIENT
helpviewer_keywords:
- MDI [MFC], child windows
- child windows [MFC], and MDICLIENT window
- MDICLIENT window [MFC]
- windows [MFC], MDI
- frame windows [MFC], MDI child windows
- child windows [MFC]
- MDI [MFC], frame windows
ms.assetid: 1828d96e-a561-48ae-a661-ba9701de6bee
ms.openlocfilehash: 6e8e3d0aa51eeea112597485a9221dcba4feda87
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618362"
---
# <a name="managing-mdi-child-windows"></a>Zarządzanie oknami podrzędnymi MDI

Główne ramki interfejsu MDI (jeden na aplikację) zawierają specjalne okno podrzędne o nazwie okno MDICLIENT. Okno MDICLIENT zarządza obszarem klienckim okna głównej ramki, a sama sama ma okna podrzędne: okna dokumentów pochodne `CMDIChildWnd` . Ponieważ okna dokumentów są samymi oknami ramek (podrzędnymi oknami MDI), mogą również mieć własne elementy podrzędne. We wszystkich tych przypadkach okno nadrzędne zarządza jego podrzędnymi oknami i przekazuje je do nich.

W oknie ramka MDI okno ramka zarządza oknem MDICLIENT, umieszczając je w połączeniu z paskami sterowania. Okno MDICLIENT, z kolei, zarządza wszystkimi oknami podrzędnymi ramek MDI. Poniższy rysunek przedstawia relację między oknem ramki MDI, oknem MDICLIENT i jego podrzędnymi oknami ramek dokumentu.

![Okna podrzędne w oknie ramka MDI](../mfc/media/vc37gb1.gif "Okna podrzędne w oknie ramka MDI") <br/>
Okna ramek MDI i elementy podrzędne

Okno ramki MDI działa również w połączeniu z bieżącym oknem podrzędnym MDI, jeśli istnieje. Okno ramka MDI deleguje komunikaty poleceń do elementu podrzędnego MDI, zanim spróbuje je obsłużyć.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Tworzenie okien ramowych dokumentu](creating-document-frame-windows.md)

- [Style okna ramowego](frame-window-styles-cpp.md)

## <a name="see-also"></a>Zobacz też

[Używanie okien ramowych](using-frame-windows.md)
