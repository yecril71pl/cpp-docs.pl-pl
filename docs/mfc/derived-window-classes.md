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
ms.openlocfilehash: c84284b765e740fa0a13972e9902e7737e15bbab
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623172"
---
# <a name="derived-window-classes"></a>Pochodne klasy okien

Możesz utworzyć system Windows bezpośrednio z [CWnd](reference/cwnd-class.md)lub uzyskać nowe klasy okna z `CWnd` . Jest to sposób, w jaki zazwyczaj tworzysz własne niestandardowe okna. Jednak większość okien używanych w programie ramowym jest tworzona na podstawie jednej z `CWnd` klas okien ramowych pochodnych dostarczonych przez MFC.

## <a name="frame-window-classes"></a>Klasy okien ramowych

[CFrameWnd](reference/cframewnd-class.md)<br/>
Używane dla okien ramowych interfejsu SDI, które dzielą pojedynczy dokument i jego widok. Okno ramy jest zarówno głównym oknem ramki aplikacji, jak i oknem ramki dla bieżącego dokumentu.

[CMDIFrameWnd](reference/cmdiframewnd-class.md)<br/>
Używane jako główne okno ramek dla aplikacji MDI. Główne okno ramek jest kontenerem dla wszystkich okien dokumentu MDI i udostępnia jego pasek menu. Okno ramek MDI jest oknem najwyższego poziomu, które pojawia się na pulpicie.

[CMDIChildWnd](reference/cmdichildwnd-class.md)<br/>
Używany do poszczególnych dokumentów otwartych w głównym oknie ramki MDI. Każdy dokument i jego widok są umieszczane w ramce przez okno ramki podrzędnej MDI zawarte w głównym oknie ramka MDI. Okno potomne MDI wygląda podobnie jak w przypadku typowego okna ramki, ale jest zawarte wewnątrz okna ramki MDI zamiast na pulpicie. Jednak okno podrzędne MDI nie ma własnego paska menu i musi udostępniać pasek menu w oknie ramka MDI, które go zawiera.

Aby uzyskać więcej informacji, zobacz [okna ramek](frame-windows.md).

## <a name="other-window-classes-derived-from-cwnd"></a>Inne klasy okna pochodne od CWnd

Oprócz okien ramowych, kilka innych głównych kategorii systemu Windows pochodzi z `CWnd` :

*Widoki*<br/>
Widoki są tworzone przy użyciu `CWnd` klasy pochodnej [CView](reference/cview-class.md) (lub jednej z jej klas pochodnych). Widok jest dołączony do dokumentu i działa jako pośrednik między dokumentem a użytkownikiem. Widok jest oknem podrzędnym (nie jest elementem podrzędnym MDI), który zwykle wypełnia obszar klienta okna ramka SDI lub okno ramki podrzędnej MDI (lub część obszaru klienckiego, który nie jest objęty przez pasek narzędzi i/lub pasek stanu).

*Okna dialogowe*<br/>
Okna dialogowe są tworzone przy użyciu `CWnd` -pochodnej klasy [CDialog](reference/cdialog-class.md).

*Formularze*<br/>
Widoki formularzy oparte na zasobach szablonów okien dialogowych, takich jak okna dialogowe, są tworzone przy użyciu klas [CFormView](reference/cformview-class.md), [formularzy CRecordView](reference/crecordview-class.md)lub [CDaoRecordView](reference/cdaorecordview-class.md).

*Formanty*<br/>
Kontrolki, takie jak przyciski, pola listy i pola kombi, są tworzone przy użyciu innych klas pochodnych z `CWnd` . Zobacz [Tematy sterujące](controls-mfc.md).

*Paski sterowania*<br/>
Okna podrzędne zawierające formanty. Przykłady obejmują paski narzędzi i paski stanu. Zobacz [Paski kontroli](control-bars.md).

## <a name="window-class-hierarchy"></a>Hierarchia klas okien

Zapoznaj się z [wykresem hierarchii MFC](hierarchy-chart.md) w *dokumentacji MFC*. Widoki są objaśnione w temacie [Document/View Architecture](document-view-architecture.md). Okna dialogowe są wyjaśnione [w oknach dialogowych](dialog-boxes.md).

## <a name="creating-your-own-special-purpose-window-classes"></a>Tworzenie własnych klas okien specjalnego przeznaczenia

Oprócz klas okien dostarczonych przez bibliotekę klas, mogą być potrzebne specjalne okna podrzędne. Aby utworzyć takie okno, należy utworzyć własną klasę pochodną [CWnd](reference/cwnd-class.md)i uczynić ją oknem podrzędnym ramki lub widoku. Należy pamiętać, że struktura zarządza zakresem obszaru klienta okna ramki dokumentu. Większość obszaru klienta jest zarządzana przez widok, ale inne okna, takie jak paski sterowania lub własne niestandardowe okna, mogą udostępniać miejsce z widokiem. Może być konieczne współdziałanie z mechanizmami w klasach [CView](reference/cview-class.md) i [CControlBar](reference/ccontrolbar-class.md) w celu umieszczenia okien podrzędnych w obszarze klienckim okna ramki.

[Tworzenie systemu Windows](creating-windows.md) omawia tworzenie obiektów okien i systemu Windows, którymi zarządzają.

## <a name="see-also"></a>Zobacz też

[Obiekty okien](window-objects.md)
