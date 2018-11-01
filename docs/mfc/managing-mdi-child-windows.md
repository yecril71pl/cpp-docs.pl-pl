---
title: Zarządzanie oknami podrzędnymi MDI
ms.date: 11/04/2016
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
ms.openlocfilehash: 2055c215392c6805791de729ff6ab8c6a9057308
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629414"
---
# <a name="managing-mdi-child-windows"></a>Zarządzanie oknami podrzędnymi MDI

MDI głównego okna ramowe (po jednej dla aplikacji) zawierają okna specjalnego podrzędnego o nazwie MdiClient — okno. Okno MDICLIENT zarządza obszaru klienckiego okna ramki głównej, a sama platforma okna podrzędne: okna dokumentu pochodną `CMDIChildWnd`. Ponieważ okna dokumentów okien ramowych, samodzielnie (oknami podrzędnymi MDI), mogą również mieć własne elementy podrzędne. We wszystkich tych przypadkach okno nadrzędne zarządza jego okien podrzędnych i przekazuje niektórych poleceń do nich.

W oknie ramki MDI ramki okna zarządza okno MDICLIENT, zmiana jego położenia w połączeniu z pasków sterowania. Okno MDICLIENT, z kolei zarządza wszystkich okien ramek podrzędnych MDI. Na poniższej ilustracji przedstawiono relację między okna ramki MDI, okno MDICLIENT i okien ramowych dokumentu jego podrzędnych.

![Okien podrzędnych w oknie ramki MDI](../mfc/media/vc37gb1.gif "vc37gb1") Windows ramki MDI i elementy podrzędne

Okno ramki MDI działa także w połączeniu z bieżącego okna podrzędnego MDI, jeśli taka istnieje. Okno ramek MDI deleguje komunikaty poleceń do elementu podrzędnego MDI przed ponowną próbą sam je obsłużyć.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Tworzenie okien ramowych dokumentu](../mfc/creating-document-frame-windows.md)

- [Style okna ramki](../mfc/frame-window-styles-cpp.md)

## <a name="see-also"></a>Zobacz też

[Używanie okien ramowych](../mfc/using-frame-windows.md)

