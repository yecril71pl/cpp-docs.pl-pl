---
title: Zmienianie stylów okna utworzonego przez MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 98bcf57cc3a4697fc035fad73d8faf4e577a84b5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420129"
---
# <a name="changing-the-styles-of-a-window-created-by-mfc"></a>Zmienianie stylów okna utworzonego przez MFC

W wersji z `WinMain` funkcji MFC rejestruje kilka klas standardowego okna. Ponieważ zwykle nie Edytuj MFC `WinMain`, że funkcja daje nie możliwości zmiany Style okna domyślne MFC. W tym artykule wyjaśniono, jak można zmieniać style takie klasę okna wyświetlenie wcześniej zarejestrowanych w istniejącej aplikacji.

##  <a name="_core_changing_styles_in_a_new_mfc_application"></a> Zmienianie stylów w nowej aplikacji MFC

Jeśli używasz programu Visual C++ w wersji 2.0 lub nowszej, możesz zmienić domyślne style okna w Kreatorze aplikacji, podczas tworzenia aplikacji. Na stronie funkcje interfejsu użytkownika Kreatora aplikacji możesz zmienić style dla głównej ramki okna i okien podrzędnych MDI. Dla dowolnego typu okna można określić grubość ramki (grubości lub cienkich) i dowolne z następujących czynności:

- Czy okno ma Minimalizuj lub Maksymalizuj formantów.

- Czy pojawi się okno początkowo zminimalizowane zmaksymalizowane, żaden z tych.

W systemie windows głównej ramki można również określić, czy okno ma Menu systemowego. Dla okien podrzędnych MDI można określić, czy okno obsługuje rozdzielacz okienka.

##  <a name="_core_changing_styles_in_an_existing_application"></a> Zmienianie stylów w istniejącej aplikacji

Jeśli zmieniasz atrybutów okna w istniejącej aplikacji, postępuj zgodnie z instrukcjami wyświetlanymi w dalszej części tego artykułu.

Aby zmienić atrybuty okna domyślne, które są używane przez utworzenie aplikacji framework za pomocą Kreatora aplikacji, należy zastąpić okna [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) funkcja wirtualna elementu członkowskiego. `PreCreateWindow` umożliwia aplikacji dostęp do procesu tworzenia, zwykle zarządza wewnętrznie [CDocTemplate](../mfc/reference/cdoctemplate-class.md) klasy. Struktura wywołuje `PreCreateWindow` tuż przed utworzenie okna. Modyfikując [CREATESTRUCT](../mfc/reference/createstruct-structure.md) struktury przekazany do `PreCreateWindow`, aplikacja może zmienić atrybuty użyty do utworzenia okna. Na przykład w celu zapewnienia okna nie używa podpis, należy użyć następującej operacji bitowej:

[!code-cpp[NVC_MFCDocView#15](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]

[CTRLBARS](../visual-cpp-samples.md) przykładowej aplikacji pokazano tej techniki dla Zmienianie atrybutów okna. W zależności od tego, jakie zmiany w aplikacji `PreCreateWindow`, może być konieczne do wywołania implementacji klasy podstawowej funkcji.

Następujące dyskusji obejmuje przypadek SDI i [przypadek MDI](#_core_the_mdi_case).

##  <a name="_core_the_sdi_case"></a> W przypadku SDI

W przypadku aplikacji interfejsu (SDI) pojedynczy dokument domyślny styl okna w ramach jest kombinacją **WS_OVERLAPPEDWINDOW** i **FWS_ADDTOTITLE** style. **FWS_ADDTOTITLE** jest styl specyficzne dla MFC, który powoduje, że platformę, by dodać tytuł dokumentu do okna transkrypcji. Do zmiany atrybutów okna w aplikacji interfejsu SDI, należy zastąpić `PreCreateWindow` funkcja w klasie pochodnej od `CFrameWnd` (który nazwy aplikacji, Kreator `CMainFrame`). Na przykład:

[!code-cpp[NVC_MFCDocViewSDI#11](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]

Ten kod tworzy ramką głównego okna bez przyciski i nie może być zmieniany obramowanie. Okno początkowo skupia się na ekranie.

##  <a name="_core_the_mdi_case"></a> W przypadku MDI

Trochę więcej pracy jest wymagany do zmienia stylu okna okno podrzędne w wielu aplikacji interfejsu (MDI) dokumentu. Domyślnie utworzone za pomocą Kreatora aplikacji Aplikacja MDI używa domyślnie [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) klasy zdefiniowanej w MFC. Aby zmienić styl okna okno podrzędne MDI, musi pochodzić nowa klasa z `CMDIChildWnd` i Zamień wszystkie odwołania do `CMDIChildWnd` w projekcie z odwołaniami do nowej klasy. Najprawdopodobniej tylko odwołanie do `CMDIChildWnd` w aplikacji znajduje się w Twojej aplikacji `InitInstance` funkcja elementu członkowskiego.

Domyślny styl okna używane w aplikacji MDI jest kombinacją **WS_CHILD**, **WS_OVERLAPPEDWINDOW**, i **FWS_ADDTOTITLE** style. Aby zmienić atrybuty okna okien podrzędnych aplikacja MDI, Zastąp [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) funkcja w klasie pochodnej od `CMDIChildWnd`. Na przykład:

[!code-cpp[NVC_MFCDocView#16](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]

Ten kod tworzy elementu podrzędnego MDI systemu windows bez przyciskiem maksymalizacji.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Style Windows](../mfc/reference/styles-used-by-mfc.md#window-styles)

- [Style okna ramki](../mfc/frame-window-styles-cpp.md)

- [Style okna ramowego](https://msdn.microsoft.com/library/windows/desktop/ms632600)

## <a name="see-also"></a>Zobacz też

[Style okna ramki](../mfc/frame-window-styles-cpp.md)

