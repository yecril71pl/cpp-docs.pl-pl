---
title: Klasa CHtmlEditCtrl
ms.date: 11/04/2016
f1_keywords:
- CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::Create
- AFXHTML/CHtmlEditCtrl::GetDHtmlDocument
- AFXHTML/CHtmlEditCtrl::GetStartDocument
helpviewer_keywords:
- CHtmlEditCtrl [MFC], CHtmlEditCtrl
- CHtmlEditCtrl [MFC], Create
- CHtmlEditCtrl [MFC], GetDHtmlDocument
- CHtmlEditCtrl [MFC], GetStartDocument
ms.assetid: 0fc4a238-b05f-4874-9edc-6a6701f064d9
ms.openlocfilehash: 05063c62e9f7a5d88d3fecde842f979725200f98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366840"
---
# <a name="chtmleditctrl-class"></a>Klasa CHtmlEditCtrl

Zapewnia funkcjonalność WebBrowser ActiveX kontroli w oknie MFC.

## <a name="syntax"></a>Składnia

```
class CHtmlEditCtrl: public CWnd,
    public CHtmlEditCtrlBase<CHtmlEditCtrl>
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHtmlEditCtrl::CHtmlEditCtrl](#chtmleditctrl)|Konstruuje `CHtmlEditCtrl` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHtmlEditCtrl::Utwórz](#create)|Tworzy formant ActiveX przeglądarki WebBrowser `CHtmlEditCtrl` i dołącza go do obiektu. Ta funkcja automatycznie przełącza kontrolki WebBrowser ActiveX w tryb edycji.|
|[CHtmlEditCtrl::GetDHtmlDocument](#getdhtmldocument)|Pobiera interfejs [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) w dokumencie aktualnie załadowanym w formancie zawierającego webbrowsera.|
|[CHtmlEditCtrl::GetStartDocument](#getstartdocument)|Pobiera adres URL do domyślnego dokumentu, aby załadować w kontrolce zawartej przeglądarki WebBrowser.|

## <a name="remarks"></a>Uwagi

Hostowany formant webbrowser jest automatycznie umieszczany w trybie edycji po jego utworzeniu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Baza CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CHtmlEditCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxhtml.h

## <a name="chtmleditctrlchtmleditctrl"></a><a name="chtmleditctrl"></a>CHtmlEditCtrl::CHtmlEditCtrl

Konstruuje `CHtmlEditCtrl` obiekt.

```
CHtmlEditCtrl();
```

## <a name="chtmleditctrlcreate"></a><a name="create"></a>CHtmlEditCtrl::Utwórz

Tworzy formant ActiveX przeglądarki WebBrowser `CHtmlEditCtrl` i dołącza go do obiektu. Formant WebBrowser ActiveX automatycznie przechodzi do dokumentu domyślnego, a następnie jest umieszczany w trybie edycji przez tę funkcję.

```
virtual BOOL Create(
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parametry

*lpszWindowName*<br/>
Ten parametr jest nieużywane.

*Dwstyle*<br/>
Ten parametr jest nieużywane.

*Rect*<br/>
Określa rozmiar i położenie formantu.

*pParentWnd*<br/>
Określa okno nadrzędne formantu. Nie może być null.

*Nid*<br/>
Określa identyfikator formantu.

*Pcontext*<br/>
Ten parametr jest nieużywane.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

## <a name="chtmleditctrlgetdhtmldocument"></a><a name="getdhtmldocument"></a>CHtmlEditCtrl::GetDHtmlDocument

Pobiera interfejs [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) w dokumencie aktualnie załadowanym w kontrolce zawartej w uprzeglądarce Sieci Web

```
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;
```

### <a name="parameters"></a>Parametry

*ppDocument (Dokument ppDocument)*<br/>
Interfejs dokumentu.

## <a name="chtmleditctrlgetstartdocument"></a><a name="getstartdocument"></a>CHtmlEditCtrl::GetStartDocument

Pobiera adres URL do domyślnego dokumentu, aby załadować w kontrolce zawartej przeglądarki WebBrowser.

```
virtual LPCTSTR GetStartDocument();
```

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)
