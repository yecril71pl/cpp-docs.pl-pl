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
ms.openlocfilehash: d4b4a4876f47452361b13837b0279f5bf98f8658
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283686"
---
# <a name="managing-mdi-child-windows"></a>Zarządzanie oknami podrzędnymi MDI

MDI głównego okna ramowe (po jednej dla aplikacji) zawierają okna specjalnego podrzędnego o nazwie MdiClient — okno. Okno MDICLIENT zarządza obszaru klienckiego okna ramki głównej, a sama platforma okna podrzędne: okna dokumentu pochodną `CMDIChildWnd`. Ponieważ okna dokumentów okien ramowych, samodzielnie (oknami podrzędnymi MDI), mogą również mieć własne elementy podrzędne. We wszystkich tych przypadkach okno nadrzędne zarządza jego okien podrzędnych i przekazuje niektórych poleceń do nich.

W oknie ramki MDI ramki okna zarządza okno MDICLIENT, zmiana jego położenia w połączeniu z pasków sterowania. Okno MDICLIENT, z kolei zarządza wszystkich okien ramek podrzędnych MDI. Na poniższej ilustracji przedstawiono relację między okna ramki MDI, okno MDICLIENT i okien ramowych dokumentu jego podrzędnych.

![Okien podrzędnych w oknie ramki MDI](../mfc/media/vc37gb1.gif "okien podrzędnych w oknie ramki MDI") <br/>
Windows ramki MDI i elementy podrzędne

Okno ramki MDI działa także w połączeniu z bieżącego okna podrzędnego MDI, jeśli taka istnieje. Okno ramek MDI deleguje komunikaty poleceń do elementu podrzędnego MDI przed ponowną próbą sam je obsłużyć.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Tworzenie okien ramowych dokumentu](../mfc/creating-document-frame-windows.md)

- [Style okna ramki](../mfc/frame-window-styles-cpp.md)

## <a name="see-also"></a>Zobacz także

[Używanie okien ramowych](../mfc/using-frame-windows.md)
