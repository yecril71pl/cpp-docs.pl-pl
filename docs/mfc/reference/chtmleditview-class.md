---
title: Klasa CHtmlEditView
ms.date: 11/04/2016
f1_keywords:
- CHtmlEditView
- AFXHTML/CHtmlEditView
- AFXHTML/CHtmlEditView::CHtmlEditView
- AFXHTML/CHtmlEditView::Create
- AFXHTML/CHtmlEditView::GetDHtmlDocument
- AFXHTML/CHtmlEditView::GetStartDocument
helpviewer_keywords:
- CHtmlEditView [MFC], CHtmlEditView
- CHtmlEditView [MFC], Create
- CHtmlEditView [MFC], GetDHtmlDocument
- CHtmlEditView [MFC], GetStartDocument
ms.assetid: 166c8ba8-3fb5-4dd7-a9ea-5bca662d00f6
ms.openlocfilehash: 20d4586c1ae45e5f3f56c0adbb1ecb1757084fd7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752323"
---
# <a name="chtmleditview-class"></a>Klasa CHtmlEditView

Zapewnia funkcjonalność platformy edycji WebBrowser w kontekście architektury dokumentu/widoku MFC.

## <a name="syntax"></a>Składnia

```
class CHtmlEditView : public CHtmlView, public CHtmlEditCtrlBase<CHtmlEditView>
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHtmlEditView::CHtmlEditView](#chtmleditview)|Konstruuje `CHtmlEditView` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHtmlEditView::Tworzenie](#create)|Tworzy nowy obiekt okna.|
|[CHtmlEditView::GetDHtmlDocument](#getdhtmldocument)|Zwraca `IHTMLDocument2` interfejs w bieżącym dokumencie.|
|[CHtmlEditView::GetStartDocument](#getstartdocument)|Pobiera nazwę dokumentu domyślnego dla tego widoku.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cview](../../mfc/reference/cview-class.md)

[Cscrollview](../../mfc/reference/cscrollview-class.md)

[Cformview](../../mfc/reference/cformview-class.md)

[Baza CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)

[Chtmlview](../../mfc/reference/chtmlview-class.md)

`CHtmlEditView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxhtml.h

## <a name="chtmleditviewchtmleditview"></a><a name="chtmleditview"></a>CHtmlEditView::CHtmlEditView

Konstruuje `CHtmlEditView` obiekt.

```
CHtmlEditView();
```

## <a name="chtmleditviewcreate"></a><a name="create"></a>CHtmlEditView::Tworzenie

Tworzy nowy obiekt okna.

```
virtual BOOL Create(
    LPCTSTR lpszClassName,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parametry

*lpszClassName (nazwa klasy)*<br/>
Wskazuje ciąg znaków zakończony z wartością null, który nazywa klasę systemu Windows. Nazwa klasy może być dowolną nazwą zarejestrowaną za pomocą funkcji `RegisterClass` globalnej [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) lub funkcji systemu Windows. Jeśli null, używa wstępnie zdefiniowanych domyślnych atrybutów [CFrameWnd.](../../mfc/reference/cframewnd-class.md)

*lpszWindowName*<br/>
Wskazuje ciąg znaków zakończony z wartością null, który reprezentuje nazwę okna.

*Dwstyle*<br/>
Określa atrybuty stylu okna. Domyślnie są ustawione style WS_VISIBLE i WS_CHILD Windows.

*Rect*<br/>
Odwołanie do struktury [RECT](/windows/win32/api/windef/ns-windef-rect) określające rozmiar i położenie okna. Wartość *rectDefault* umożliwia systemowi Windows określenie rozmiaru i położenia nowego okna.

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego formantu.

*Nid*<br/>
Numer identyfikatora widoku. Domyślnie ustawiono AFX_IDW_PANE_FIRST.

*Pcontext*<br/>
Wskaźnik do [CCreateContext](../../mfc/reference/ccreatecontext-structure.md). NULL domyślnie.

### <a name="remarks"></a>Uwagi

Ta metoda wywoła również zawartą `Navigate` metodę WebBrowser w celu załadowania domyślnego dokumentu (zobacz [CHtmlEditView::GetStartDocument](#getstartdocument)).

## <a name="chtmleditviewgetdhtmldocument"></a><a name="getdhtmldocument"></a>CHtmlEditView::GetDHtmlDocument

Zwraca `IHTMLDocument2` interfejs w bieżącym dokumencie.

```
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;
```

### <a name="parameters"></a>Parametry

*ppDocument (Dokument ppDocument)*<br/>
Interfejs [IHTMLDocument2.](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\))

## <a name="chtmleditviewgetstartdocument"></a><a name="getstartdocument"></a>CHtmlEditView::GetStartDocument

Pobiera nazwę dokumentu domyślnego dla tego widoku.

```
virtual LPCTSTR GetStartDocument();
```

## <a name="see-also"></a>Zobacz też

[Przykład htmledytuj](../../overview/visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
