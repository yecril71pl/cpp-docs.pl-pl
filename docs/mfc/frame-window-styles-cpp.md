---
title: Style okna ramowego (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- window styles [MFC]
- PreCreateWindow method, setting window styles
- windows [MFC], MFC
- frame windows [MFC], styles
- MFC, frame windows
- styles [MFC], windows
ms.assetid: fc5058c1-eec8-48d8-9f76-3fc01cfa53f7
ms.openlocfilehash: 3c22944537370a44aee1af1cf71281264ed4969b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626455"
---
# <a name="frame-window-styles-c"></a>Style okna ramowego (C++)

Ramki systemu Windows, które są używane w środowisku, są odpowiednie dla większości programów, ale możesz uzyskać dodatkową elastyczność, korzystając z zaawansowanych funkcji [PreCreateWindow](reference/cwnd-class.md#precreatewindow) i globalną funkcję MFC [AfxRegisterWndClass —](reference/application-information-and-management.md#afxregisterwndclass). `PreCreateWindow`jest funkcją składową `CWnd` .

Jeśli zastosujesz style **WS_HSCROLL** i **WS_VSCROLL** do okna ramki głównej, zostaną one zastosowane do okna **MDICLIENT** , aby użytkownicy mogli przewijać obszar **MDICLIENT** .

Jeśli ustawiono **FWS_ADDTOTITLE** stylu okna (domyślnie jest to ustawienie domyślne), widok informuje okno ramki o tytule, który ma być wyświetlany w pasku tytułu okna na podstawie nazwy dokumentu widoku.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Zarządzanie oknami podrzędnymi MDI (MDICLIENT)](managing-mdi-child-windows.md), oknem w ramce MDI zawierającym okna podrzędne MDI

- [Zmienianie stylów okna utworzonego przez MFC](changing-the-styles-of-a-window-created-by-mfc.md)

- [Style okna](reference/styles-used-by-mfc.md#window-styles)

## <a name="see-also"></a>Zobacz też

[Okna ramowe](frame-windows.md)
