---
title: Klasa CMultiPageDHtmlDialog
ms.date: 03/27/2019
f1_keywords:
- CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog::CMultiPageDHtmlDialog
helpviewer_keywords:
- CMultiPageDHtmlDialog [MFC], CMultiPageDHtmlDialog
ms.assetid: 971accc1-824d-4df4-b4c1-b1a20e0f7e4f
ms.openlocfilehash: 89e4830c3b5c6cb663ca2d2935adaaae3f356958
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319662"
---
# <a name="cmultipagedhtmldialog-class"></a>Klasa CMultiPageDHtmlDialog

Wielostronicowe okno dialogowe wyświetla kolejno wiele stron HTML i obsługuje zdarzenia z każdej strony.

## <a name="syntax"></a>Składnia

```
class CMultiPageDHtmlDialog : public CDHtmlDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMultiPageDHtmlDialog::CMultiPageDHtmlDialog](#cmultipagedhtmldialog)|Konstruuje wielostronicowy obiekt okna dialogowego DHTML w stylu wielostronicowym.|
|[CMultiPageDHtmlDialog::~CMultiPageDHtmlDialog](#_dtorcmultipagedhtmldialog)|Niszczy wielostronicowy obiekt okna dialogowego DHTML.|

## <a name="remarks"></a>Uwagi

Mechanizmem w tym celu jest [mapa zdarzeń DHTML i URL](dhtml-event-maps.md), która zawiera osadzone mapy zdarzeń dla każdej strony.

## <a name="example"></a>Przykład

To wielostronicowe okno dialogowe zakłada trzy zasoby HTML, które definiują proste funkcje podobne do kreatora. Pierwsza strona ma przycisk **Dalej,** drugi przycisk **Prev** i **Next,** a trzeci przycisk **Prev.** Po naciśnięciu jednego z przycisków funkcja obsługi wywołuje [CDHtmlDialog::LoadFromResource,](../../mfc/reference/cdhtmldialog-class.md#loadfromresource) aby załadować odpowiednią nową stronę.

Odpowiednie części deklaracji klasy (w CMyMultiPageDlg.h):

[!code-cpp[NVC_MFCDocView#181](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_1.h)]

Odpowiednie części implementacji klasy (w CMyMultipageDlg.cpp):

[!code-cpp[NVC_MFCDocView#182](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CDHtmlSinkHandlerBase2`

`CDHtmlSinkHandlerBase1`

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

`CDHtmlSinkHandler`

[Cwnd](../../mfc/reference/cwnd-class.md)

`CDHtmlEventSink`

[Cdialog](../../mfc/reference/cdialog-class.md)

[CdHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)

`CMultiPageDHtmlDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdhtml.h

## <a name="cmultipagedhtmldialogcmultipagedhtmldialog"></a><a name="cmultipagedhtmldialog"></a>CMultiPageDHtmlDialog::CMultiPageDHtmlDialog

Konstruuje wielostronicowy obiekt okna dialogowego DHTML w stylu wielostronicowym.

```
CMultiPageDHtmlDialog(
    LPCTSTR lpszTemplateName,
    LPCTSTR szHtmlResID = NULL,
    CWnd* pParentWnd = NULL);

CMultiPageDHtmlDialog(
    UINT nIDTemplate,
    UINT nHtmlResID = 0,
    CWnd* pParentWnd = NULL);

CMultiPageDHtmlDialog();
```

### <a name="parameters"></a>Parametry

*lpszTemplateName*<br/>
Ciąg zakończony z wartością null, który jest nazwą zasobu szablonu okna dialogowego.

*SzHtmlResID ( szhtmlResID )*<br/>
Ciąg zakończony z wartością null, który jest nazwą zasobu HTML.

*pParentWnd*<br/>
Wskaźnik do obiektu okna nadrzędnego lub właściciela (typu [CWnd),](../../mfc/reference/cwnd-class.md)do którego należy obiekt okna dialogowego. Jeśli jest null, okno nadrzędne obiektu okna dialogowego jest ustawiona na okno aplikacji głównej.

*nIDTemplate*<br/>
Zawiera numer identyfikatora zasobu szablonu okna dialogowego.

*nHtmlResID (nHtmlResID)*<br/>
Zawiera numer identyfikatora zasobu HTML.

## <a name="cmultipagedhtmldialogcmultipagedhtmldialog"></a><a name="_dtorcmultipagedhtmldialog"></a>CMultiPageDHtmlDialog::~CMultiPageDHtmlDialog

Niszczy wielostronicowy obiekt okna dialogowego DHTML.

```
virtual ~CMultiPageDHtmlDialog();
```

## <a name="see-also"></a>Zobacz też

[Klasa CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)
