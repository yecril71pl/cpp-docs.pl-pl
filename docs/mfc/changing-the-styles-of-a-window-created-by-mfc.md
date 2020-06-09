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
ms.openlocfilehash: f3fd9f83112737e944d83cf00da685d81fe8b2a7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624949"
---
# <a name="changing-the-styles-of-a-window-created-by-mfc"></a>Zmienianie stylów okna utworzonego przez MFC

W swojej wersji `WinMain` funkcji MFC rejestruje kilka klas standardowego okna. Ponieważ zwykle nie edytujesz biblioteki MFC `WinMain` , ta funkcja nie daje możliwości zmiany domyślnych stylów okna MFC. W tym artykule wyjaśniono, jak można zmienić style takich zarejestrowanej klasy okna w istniejącej aplikacji.

## <a name="changing-styles-in-a-new-mfc-application"></a><a name="_core_changing_styles_in_a_new_mfc_application"></a>Zmienianie stylów w nowej aplikacji MFC

Jeśli używasz Visual C++ 2,0 lub nowszej, możesz zmienić domyślne style okna w Kreatorze aplikacji podczas tworzenia aplikacji. Na stronie funkcje interfejsu użytkownika Kreatora aplikacji można zmienić style dla głównego okna ramki i okien podrzędnych MDI. Dla dowolnego typu okna można określić grubość ramki (grubą lub cienką) oraz dowolne z następujących elementów:

- Czy okno ma zminimalizować lub maksymalizuje kontrolki.

- Czy okno jest wyświetlane jako wstępnie zminimalizowane, zmaksymalizowane lub nie.

W przypadku okien głównych ramek można także określić, czy okno ma menu systemowe. W przypadku okien podrzędnych MDI można określić, czy okno obsługuje okienka rozdzielacza.

## <a name="changing-styles-in-an-existing-application"></a><a name="_core_changing_styles_in_an_existing_application"></a>Zmienianie stylów w istniejącej aplikacji

Jeśli zmieniasz atrybuty okna w istniejącej aplikacji, w zamian postępuj zgodnie z instrukcjami w dalszej części tego artykułu.

Aby zmienić domyślne atrybuty okna używane przez aplikację platformy utworzoną za pomocą Kreatora aplikacji, Przesłoń wirtualną funkcję elementu członkowskiego okna [PreCreateWindow](reference/cwnd-class.md#precreatewindow) . `PreCreateWindow`zezwala aplikacji na dostęp do procesu tworzenia zwykle zarządzanego wewnętrznie przez klasę [CDocTemplate](reference/cdoctemplate-class.md) . Struktura wywołuje `PreCreateWindow` przed utworzeniem okna. Modyfikując [strukturę](/windows/win32/api/winuser/ns-winuser-createstructw) isstructure przekazaną do `PreCreateWindow` , aplikacja może zmienić atrybuty używane do tworzenia okna. Na przykład, aby upewnić się, że okno nie używa podpisu, należy użyć następującej operacji bitowej:

[!code-cpp[NVC_MFCDocView#15](codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]

Przykładowa aplikacja [CTRLBARS](../overview/visual-cpp-samples.md) ilustruje tę technikę zmiany atrybutów okna. W zależności od tego, co aplikacja zmienia `PreCreateWindow` , może być konieczne wywołanie implementacji klasy podstawowej funkcji.

W poniższej dyskusji omówiono przypadek SDI i [przypadek MDI](#_core_the_mdi_case).

## <a name="the-sdi-case"></a><a name="_core_the_sdi_case"></a>Przypadek SDI

W aplikacji interfejsu pojedynczego dokumentu (SDI) domyślny styl okna w strukturze jest kombinacją **WS_OVERLAPPEDWINDOW** i **FWS_ADDTOTITLE** style. **FWS_ADDTOTITLE** jest stylem specyficznym dla MFC, który nakazuje platformie dodanie tytułu dokumentu do podpisu okna. Aby zmienić atrybuty okna w aplikacji SDI, Przesłoń `PreCreateWindow` funkcję w klasie pochodnej od `CFrameWnd` (która nazwa Kreatora aplikacji `CMainFrame` ). Przykład:

[!code-cpp[NVC_MFCDocViewSDI#11](codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]

Ten kod tworzy okno głównej ramki bez minimalizowania i maksymalizowania przycisków i bez obramowania o zmiennym rozmiarze. Okno jest początkowo wyśrodkowane na ekranie.

## <a name="the-mdi-case"></a><a name="_core_the_mdi_case"></a>Przypadek MDI

Aby zmienić styl okna podrzędnego w aplikacji interfejsu wielu dokumentów (MDI), wymagana jest nieco więcej pracy. Domyślnie aplikacja MDI utworzona za pomocą Kreatora aplikacji używa domyślnej klasy [CMDIChildWnd](reference/cmdichildwnd-class.md) zdefiniowanej w MFC. Aby zmienić styl okna podrzędnego MDI, należy utworzyć nową klasę z `CMDIChildWnd` i zastąpić wszystkie odwołania do `CMDIChildWnd` w projekcie z odwołaniami do nowej klasy. Najprawdopodobniej tylko odwołanie do aplikacji znajduje się `CMDIChildWnd` w `InitInstance` funkcji składowej aplikacji.

Domyślny styl okna używany w aplikacji MDI jest kombinacją stylów **WS_CHILD**, **WS_OVERLAPPEDWINDOW**i **FWS_ADDTOTITLE** . Aby zmienić atrybuty okna dla okien podrzędnych aplikacji MDI, Zastąp funkcję [PreCreateWindow](reference/cwnd-class.md#precreatewindow) w klasie pochodnej `CMDIChildWnd` . Przykład:

[!code-cpp[NVC_MFCDocView#16](codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]

Ten kod tworzy okna podrzędne MDI bez przycisku Maksymalizuj.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Style systemu Windows](reference/styles-used-by-mfc.md#window-styles)

- [Style okna ramowego](frame-window-styles-cpp.md)

- [Style okna](/windows/win32/winmsg/window-styles)

## <a name="see-also"></a>Zobacz też

[Style okna ramowego](frame-window-styles-cpp.md)
