---
title: Pochodne klasy okien
ms.date: 11/04/2016
helpviewer_keywords:
- window class hierarchy
- hierarchies, window classes
- classes [MFC], derived
- CWnd class [MFC], classes derived from
- derived classes [MFC], window classes
- window classes [MFC], derived
ms.assetid: 6f7e437e-fbde-4a06-bfab-72d9dbf05292
ms.openlocfilehash: e86ca139b8470dce614564f0c0134a611adeda2c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270322"
---
# <a name="derived-window-classes"></a>Pochodne klasy okien

Można również tworzyć okna bezpośrednio z [CWnd](../mfc/reference/cwnd-class.md), lub wyprowadzać nowe klasy okna z `CWnd`. Jest to sposób zwykle tworzysz własne niestandardowe okna. Jednak większość okien używanych w ramach programu jest tworzonych w zamian z jednego z `CWnd`-pochodne klasy okien ramowych dostarczonych przez MFC.

## <a name="frame-window-classes"></a>Klasy okien ramowych

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
Używane dla SDI ramki okna tworzy jednolity dokumentu i jej widok. W oknie ramki jest zarówno ramką głównego okna aplikacji, jak i oknem ramki dla bieżącego dokumentu.

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)<br/>
Używane jako głównej ramki okna dla aplikacji MDI. Okno głównych ramek jest kontenerem dla wszystkich okien dokumentu MDI i udostępnia im swój pasek menu. Okno ramki MDI jest oknem najwyższego poziomu, który pojawia się na pulpicie.

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
Używane dla poszczególnych dokumentów utworzonych w oknie głównym ramki MDI. Każdy dokument i jego widok jest otoczony oknem ramki podrzędnego MDI zawartych w ramce głównej okna MDI. Okno podrzędne MDI wygląda tak, jak okno typowej ramki, ale znajduje się wewnątrz okna ramki MDI zamiast "siedzieć" na pulpicie. Jednak okno podrzędne MDI nie posiada własnego paska menu i musi dzielić pasek menu z oknem ramki aplikacji MDI zawierający go.

Aby uzyskać więcej informacji, zobacz [Windows ramki](../mfc/frame-windows.md).

## <a name="other-window-classes-derived-from-cwnd"></a>Inne klasy okna pochodzące od CWnd

Oprócz ramki okien, kilka innych kategorii głównych systemu windows są uzyskiwane z `CWnd`:

*Widoki*<br/>
Widoki są tworzone przy użyciu `CWnd`-klasy pochodnej [CView](../mfc/reference/cview-class.md) (lub jeden z jej klas pochodnych). Widok jest dołączony do dokumentu i działa jako pośrednik między dokumentem i użytkownikiem. Widok jest oknem podrzędnym (nie podrzędnym MDI), które zwykle wypełnia obszar kliencki ramki okna SDI lub ramki okna podrzędnego MDI (lub część obszaru klienckiego nie pasuje do żadnego paska narzędzi lub paska stanu).

*Okna dialogowe*<br/>
Okna dialogowe są tworzone przy użyciu `CWnd`-klasy pochodnej [CDialog](../mfc/reference/cdialog-class.md).

*Formularze*<br/>
Widoki formularzy oparte na zasobach szablonów dialogowych, takich jak okna dialogowe są tworzone przy użyciu klas [CFormView](../mfc/reference/cformview-class.md), [CRecordView](../mfc/reference/crecordview-class.md), lub [CDaoRecordView](../mfc/reference/cdaorecordview-class.md).

*Kontrolki*<br/>
Formanty, takie jak przyciski, pola listy i pola kombi są tworzone przy użyciu innych klas pochodzących z `CWnd`. Zobacz [kontrolować tematy](../mfc/controls-mfc.md).

*Paski sterowania*<br/>
Okna podrzędne, które zawierają formanty. Przykłady obejmują paski narzędzi i stanu. Zobacz [paski sterowania](../mfc/control-bars.md).

## <a name="window-class-hierarchy"></a>Hierarchia klas okna

Zapoznaj się [MFC wykresu hierarchii](../mfc/hierarchy-chart.md) w *odwołanie MFC*. Widoki są wyjaśnione w [architektury dokument/widok](../mfc/document-view-architecture.md). Okna dialogowe są wyjaśnione w [okna dialogowe](../mfc/dialog-boxes.md).

## <a name="creating-your-own-special-purpose-window-classes"></a>Tworzenie własnych klas okien specjalnego przeznaczenia

Oprócz klas okien dostarczonych przez bibliotekę klas możesz potrzebować okien specjalnego przeznaczenia podrzędnych. Aby utworzyć takie okno, Utwórz swoje własne [CWnd](../mfc/reference/cwnd-class.md)-klasy pochodnej, co okno podrzędne ono ramki lub widoku. Mieć na uwadze, że szablon zarządza zakresem obszaru klienckiego okna ramki dokumentu. Większość obszaru klienta jest zarządzana przez widok, ale inne okna, takie jak kontrola pasków lub własne niestandardowe okna mogą dzielić przestrzeń z widoku. Może być konieczne do interakcji z mechanizmami w klasach [CView](../mfc/reference/cview-class.md) i [CControlBar](../mfc/reference/ccontrolbar-class.md) do pozycjonowania okien podrzędnych w obszarze klienta ramki okna.

[Tworzenie Windows](../mfc/creating-windows.md) omawia Tworzenie obiektów okien oraz okien, którymi zarządzają.

## <a name="see-also"></a>Zobacz także

[Obiekty okna](../mfc/window-objects.md)
