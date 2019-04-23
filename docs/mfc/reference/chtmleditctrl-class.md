---
title: CHtmlEditCtrl Class
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
ms.openlocfilehash: 6f5c465a8ec9c8f54af5545e66fb849a08d241af
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420924"
---
# <a name="chtmleditctrl-class"></a>CHtmlEditCtrl Class

Oferuje funkcje formantu WebBrowser ActiveX w oknie programu MFC.

## <a name="syntax"></a>Składnia

```
class CHtmlEditCtrl: public CWnd,
    public CHtmlEditCtrlBase<CHtmlEditCtrl>
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHtmlEditCtrl::CHtmlEditCtrl](#chtmleditctrl)|Konstruuje `CHtmlEditCtrl` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHtmlEditCtrl::Create](#create)|Tworzy formant WebBrowser ActiveX i dołącza je do `CHtmlEditCtrl` obiektu. Ta funkcja automatycznie umieszcza formantu WebBrowser ActiveX do trybu edycji.|
|[CHtmlEditCtrl::GetDHtmlDocument](#getdhtmldocument)|Pobiera [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) interfejs dokumentu załadowanych obecnie do formantu WebBrowser w nich zawarte.|
|[CHtmlEditCtrl::GetStartDocument](#getstartdocument)|Pobiera adres URL do domyślnego dokumentu do załadowania w kontrolce WebBrowser w nich zawarte.|

## <a name="remarks"></a>Uwagi

Hostowanej WebBrowser, które kontrolki są automatycznie umieszczane w trybie edycji, po jego utworzeniu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHtmlEditCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxhtml.h

##  <a name="chtmleditctrl"></a>  CHtmlEditCtrl::CHtmlEditCtrl

Konstruuje `CHtmlEditCtrl` obiektu.

```
CHtmlEditCtrl();
```

##  <a name="create"></a>  CHtmlEditCtrl::Create

Tworzy formant WebBrowser ActiveX i dołącza je do `CHtmlEditCtrl` obiektu. WebBrowser ActiveX kontroli automatycznie przejdzie do domyślnego dokumentu i następnie jest umieszczany w z trybu edycji przez tę funkcję.

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
Ten parametr jest nieużywany.

*dwStyle*<br/>
Ten parametr jest nieużywany.

*Rect*<br/>
Określa rozmiar i położenie formantu.

*pParentWnd*<br/>
Określa okno nadrzędne kontrolki. Nie może być równa NULL.

*nID*<br/>
Określa identyfikator kontrolki.

*pContext*<br/>
Ten parametr jest nieużywany.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

##  <a name="getdhtmldocument"></a>  CHtmlEditCtrl::GetDHtmlDocument

Pobiera [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) interfejs dokumentu załadowanych obecnie do zamkniętego formantu WebBrowser

```
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;
```

### <a name="parameters"></a>Parametry

*ppDocument*<br/>
Interfejs dokumentu.

##  <a name="getstartdocument"></a>  CHtmlEditCtrl::GetStartDocument

Pobiera adres URL do domyślnego dokumentu do załadowania w kontrolce WebBrowser w nich zawarte.

```
virtual LPCTSTR GetStartDocument();
```

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)
