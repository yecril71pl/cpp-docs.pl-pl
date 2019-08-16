---
title: Klasa COleLinksDialog
ms.date: 11/04/2016
f1_keywords:
- COleLinksDialog
- AFXODLGS/COleLinksDialog
- AFXODLGS/COleLinksDialog::COleLinksDialog
- AFXODLGS/COleLinksDialog::DoModal
- AFXODLGS/COleLinksDialog::m_el
helpviewer_keywords:
- COleLinksDialog [MFC], COleLinksDialog
- COleLinksDialog [MFC], DoModal
- COleLinksDialog [MFC], m_el
ms.assetid: fb2eb638-2809-46db-ac74-392a732affc7
ms.openlocfilehash: 911108f9a231b752790abfdf86d1b4042d30b149
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504122"
---
# <a name="colelinksdialog-class"></a>Klasa COleLinksDialog

Używane na potrzeby okna dialogowego Edytowanie linków OLE.

## <a name="syntax"></a>Składnia

```
class COleLinksDialog : public COleDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleLinksDialog::COleLinksDialog](#colelinksdialog)|Konstruuje `COleLinksDialog` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleLinksDialog::D oModal](#domodal)|Wyświetla okno dialogowe łącza do edycji OLE.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleLinksDialog::m_el](#m_el)|Struktura typu OLEUIEDITLINKS, która kontroluje zachowanie okna dialogowego.|

## <a name="remarks"></a>Uwagi

Utwórz obiekt klasy `COleLinksDialog` , gdy chcesz wywołać to okno dialogowe. Po skonstruowaniu obiektu można użyć struktury m_el, aby zainicjować wartości lub Stany kontrolek w oknie dialogowym. [](#m_el) `COleLinksDialog` `m_el` Struktura jest typu OLEUIEDITLINKS. Aby uzyskać więcej informacji o używaniu tej klasy okna dialogowego, zobacz funkcja członkowska [DoModal](#domodal) .

> [!NOTE]
>  Kod kontenera wygenerowany przez Kreatora aplikacji używa tej klasy.

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [OLEUIEDITLINKS](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw) w Windows SDK.

Aby uzyskać więcej informacji dotyczących okien dialogowych specyficznych dla OLE, zobacz [okna dialogowe artykułu w OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleLinksDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxodlgs. h

##  <a name="domodal"></a>COleLinksDialog::D oModal

Wyświetla okno dialogowe łącza do edycji OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

Stan ukończenia dla okna dialogowego. Jedna z następujących wartości:

- IDOK, jeśli okno dialogowe zostało wyświetlone pomyślnie.

- IDCANCEL, jeśli użytkownik anulował okno dialogowe.

- IDABORT, jeśli wystąpił błąd. Jeśli IDABORT jest zwracany, wywołaj `COleDialog::GetLastError` funkcję członkowską, aby uzyskać więcej informacji na temat typu błędu, który wystąpił. Listę możliwych błędów można znaleźć w funkcji [OLEUIEDITLINKS](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw) w Windows SDK.

### <a name="remarks"></a>Uwagi

Jeśli chcesz zainicjować różne kontrolki okna dialogowego, ustawiając elementy członkowskie struktury [m_el](#m_el) , należy to zrobić przed wywołaniem `DoModal`, ale po skonstruowaniu obiektu okna dialogowego.

##  <a name="colelinksdialog"></a>COleLinksDialog::COleLinksDialog

Konstruuje `COleLinksDialog` obiekt.

```
COleLinksDialog (
    COleDocument* pDoc,
    CView* pView,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*pDoc*<br/>
Wskazuje dokument OLE zawierający linki do edycji.

*pView*<br/>
Wskazuje bieżący widok w witrynie *PDOC*.

*flagiDW*<br/>
Flaga tworzenia, która zawiera wartość 0 lub ELF_SHOWHELP, aby określić, czy przycisk Pomoc będzie wyświetlany po wyświetleniu okna dialogowego.

*pParentWnd*<br/>
Wskazuje obiekt nadrzędny lub właściciel (typu `CWnd`), do którego należy obiekt okna dialogowego. Jeśli ma wartość NULL, okno dialogowe nadrzędne okna dialogowego jest ustawione na główne okno aplikacji.

### <a name="remarks"></a>Uwagi

Ta funkcja tworzy tylko `COleLinksDialog` obiekt. Aby wyświetlić okno dialogowe, wywołaj funkcję [DoModal](#domodal) .

##  <a name="m_el"></a>COleLinksDialog::m_el

Struktura typu OLEUIEDITLINKS używana do sterowania zachowaniem okna dialogowego Edytowanie linków.

```
OLEUIEDITLINKS m_el;
```

### <a name="remarks"></a>Uwagi

Elementy członkowskie tej struktury można modyfikować bezpośrednio lub za pomocą funkcji składowych.

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [OLEUIEDITLINKS](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Klasa COleDialog](../../mfc/reference/coledialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)
