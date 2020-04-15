---
title: Zmienianie stylów okna utworzonego przez MFC
ms.date: 11/04/2016
helpviewer_keywords:
- window styles [MFC]
- WS_OVERLAPPEDWINDOW macro [MFC]
- single document interface (SDI), changing window attributes
- MDI [MFC], window styles
- windows [MFC], MFC
- child windows [MFC], styles
- MFC, windows
- CFrameWnd class [MFC], window styles
- CREATESTRUCT macro [MFC]
- CMDIChildWnd class [MFC], changing window styles
- multidocument interface style
- PreCreateWindow method [MFC], window styles
- single document interface (SDI), style
- default window style
- defaults [MFC], window style
- PreCreateWindow method [MFC], changing window styles
- CMainFrame class [MFC]
- styles [MFC], windows
ms.assetid: 77fa4f03-96b4-4687-9ade-41e46f7e4b0a
ms.openlocfilehash: 221092eb25a4f044cda5b379d6774659d9e9d2d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374594"
---
# <a name="changing-the-styles-of-a-window-created-by-mfc"></a>Zmienianie stylów okna utworzonego przez MFC

W swojej wersji `WinMain` funkcji MFC rejestruje kilka standardowych klas okien dla Ciebie. Ponieważ zwykle nie edytujesz `WinMain`MFC, ta funkcja nie daje możliwości zmiany domyślnych stylów okna MFC. W tym artykule wyjaśniono, jak można zmienić style takiej wstępnie zarejestrowanej klasy okna w istniejącej aplikacji.

## <a name="changing-styles-in-a-new-mfc-application"></a><a name="_core_changing_styles_in_a_new_mfc_application"></a>Zmiana stylów w nowej aplikacji MFC

Jeśli używasz programu Visual C++ 2.0 lub nowszego, możesz zmienić domyślne style okien w Kreatorze aplikacji podczas tworzenia aplikacji. Na stronie Funkcje interfejsu użytkownika Kreatora aplikacji można zmieniać style okna ramki głównej i okien podrzędnych MDI. Dla każdego typu okna można określić jego grubość ramki (grubą lub cienką) i dowolną z następujących opcji:

- Czy okno ma minimalizowanie lub maksymalizacji formantów.

- Czy okno pojawia się początkowo zminimalizowane, zmaksymalizowane, czy nie.

W przypadku okien ramek głównych można również określić, czy okno zawiera menu systemowe. W przypadku okien podrzędnych MDI można określić, czy okno obsługuje okienka rozdzielacza.

## <a name="changing-styles-in-an-existing-application"></a><a name="_core_changing_styles_in_an_existing_application"></a>Zmienianie stylów w istniejącej aplikacji

Jeśli zmieniasz atrybuty okna w istniejącej aplikacji, postępuj zgodnie z instrukcjami w pozostałej części tego artykułu.

Aby zmienić domyślne atrybuty okna używane przez aplikację framework utworzoną za pomocą Kreatora aplikacji, należy zastąpić funkcję wirtualnego elementu członkowskiego [okna PreCreateWindow.](../mfc/reference/cwnd-class.md#precreatewindow) `PreCreateWindow`umożliwia aplikacji dostęp do procesu tworzenia zwykle zarządzane wewnętrznie przez [CDocTemplate](../mfc/reference/cdoctemplate-class.md) klasy. Framework wywołuje `PreCreateWindow` tuż przed utworzeniem okna. Modyfikując [CREATESTRUCT](/windows/win32/api/winuser/ns-winuser-createstructw) struktury `PreCreateWindow`przekazywane do aplikacji można zmienić atrybuty używane do tworzenia okna. Na przykład, aby upewnić się, że okno nie używa podpisu, należy użyć następującej operacji bitowej:

[!code-cpp[NVC_MFCDocView#15](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]

Przykładowa aplikacja [CTRLBARS](../overview/visual-cpp-samples.md) demonstruje tę technikę zmiany atrybutów okna. W zależności od tego, co zmienia się w `PreCreateWindow`aplikacji, może być konieczne wywołanie implementacji klasy podstawowej funkcji.

Poniższa dyskusja dotyczy sprawy SDI i [sprawy MDI](#_core_the_mdi_case).

## <a name="the-sdi-case"></a><a name="_core_the_sdi_case"></a>Etui SDI

W aplikacji interfejsu pojedynczego dokumentu (SDI) domyślny styl okna w ramach jest kombinacją **stylów WS_OVERLAPPEDWINDOW** i **FWS_ADDTOTITLE.** **FWS_ADDTOTITLE** jest stylem specyficznym dla MFC, który instruuje platformę, aby dodać tytuł dokumentu do podpisu okna. Aby zmienić atrybuty okna w aplikacji SDI, należy zastąpić `PreCreateWindow` `CFrameWnd` funkcję w klasie `CMainFrame`pochodną (której nazywa Kreator aplikacji ). Przykład:

[!code-cpp[NVC_MFCDocViewSDI#11](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]

Ten kod tworzy okno ramki głównej bez przycisków Minimalizuj i Maksymalizuj oraz bez sporego obramowania. Okno jest początkowo wyśrodkowane na ekranie.

## <a name="the-mdi-case"></a><a name="_core_the_mdi_case"></a>Sprawa MDI

Trochę więcej pracy jest wymagana, aby zmienić styl okna okna podrzędnego w aplikacji interfejsu wielu dokumentów (MDI). Domyślnie aplikacja MDI utworzona za pomocą Kreatora aplikacji używa domyślnej klasy [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) zdefiniowanej w MFC. Aby zmienić styl okna okna podrzędnego MDI, należy `CMDIChildWnd` wyprowadzić nową klasę `CMDIChildWnd` z i zastąpić wszystkie odwołania do projektu odwołaniami do nowej klasy. Najprawdopodobniej jedynym `CMDIChildWnd` odwołaniem do aplikacji znajduje się `InitInstance` w funkcji elementu członkowskiego aplikacji.

Domyślny styl okna używany w aplikacji MDI jest kombinacją stylów **WS_CHILD**, **WS_OVERLAPPEDWINDOW**i **FWS_ADDTOTITLE.** Aby zmienić atrybuty okna okna podrzędnego aplikacji MDI, należy zastąpić funkcję [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) w klasie wywodzącej się z `CMDIChildWnd`. Przykład:

[!code-cpp[NVC_MFCDocView#16](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]

Ten kod tworzy okna podrzędne MDI bez przycisku Maksymalizuj.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz wiedzieć więcej o

- [Style systemu Windows](../mfc/reference/styles-used-by-mfc.md#window-styles)

- [Style ramki i okna](../mfc/frame-window-styles-cpp.md)

- [Style okien](/windows/win32/winmsg/window-styles)

## <a name="see-also"></a>Zobacz też

[Style ramki-okna](../mfc/frame-window-styles-cpp.md)
