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
ms.openlocfilehash: f120678c822749c8f27c3c56c95fcdd54647aca3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374932"
---
# <a name="colelinksdialog-class"></a>Klasa COleLinksDialog

Używane w oknie dialogowym Edycja łącza OLE.

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
|[COleLinksDialog::DoModal](#domodal)|Wyświetla okno dialogowe Edytowanie łączy OLE.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleLinksDialog::m_el](#m_el)|Struktura typu OLEUIEDITLINKS, która steruje zachowaniem okna dialogowego.|

## <a name="remarks"></a>Uwagi

Utwórz obiekt `COleLinksDialog` klasy, jeśli chcesz wywołać to okno dialogowe. Po `COleLinksDialog` skonstruowaniu obiektu można użyć [m_el](#m_el) struktury do zainicjowania wartości lub stanów formantów w oknie dialogowym. Struktura `m_el` jest typu OLEUIEDITLINKS. Aby uzyskać więcej informacji na temat korzystania z tej klasy okna dialogowego, zobacz Funkcję elementu członkowskiego [DoModal.](#domodal)

> [!NOTE]
> Kod kontenera generowany przez Kreatora aplikacji używa tej klasy.

Aby uzyskać więcej informacji, zobacz strukturę [OLEUIEDITLINKS](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw) w programie Windows SDK.

Aby uzyskać więcej informacji dotyczących okien dialogowych specyficznych dla ole, zobacz [okna dialogowe](../../mfc/dialog-boxes-in-ole.md)artykułu OLE .

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CKlogialny](../../mfc/reference/ccommondialog-class.md)

[COleDialog (Polski)](../../mfc/reference/coledialog-class.md)

`COleLinksDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxodlgs.h

## <a name="colelinksdialogdomodal"></a><a name="domodal"></a>COleLinksDialog::DoModal

Wyświetla okno dialogowe Edytowanie łączy OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

Stan ukończenia okna dialogowego. Jedna z następujących wartości:

- IDOK, jeśli okno dialogowe zostało pomyślnie wyświetlone.

- IDCANCEL, jeśli użytkownik anulował okno dialogowe.

- IDABORT, jeśli wystąpił błąd. Jeśli idabort jest zwracany, wywołać funkcję `COleDialog::GetLastError` elementu członkowskiego, aby uzyskać więcej informacji na temat typu błędu, który wystąpił. Aby uzyskać listę możliwych błędów, zobacz [OleUIEditLinks](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw) funkcji w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Jeśli chcesz zainicjować różne formanty okna dialogowego, ustawiając elementy członkowskie [m_el](#m_el) `DoModal`struktury, należy to zrobić przed wywołaniem , ale po skonstruowaniu obiektu okna dialogowego.

## <a name="colelinksdialogcolelinksdialog"></a><a name="colelinksdialog"></a>COleLinksDialog::COleLinksDialog

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
Wskazuje dokument OLE zawierający łącza do edycji.

*pWidok*<br/>
Wskazuje bieżący widok na *pDoc*.

*Dwflags*<br/>
Flaga tworzenia, która zawiera 0 lub ELF_SHOWHELP, aby określić, czy przycisk Pomoc będzie wyświetlany po wyświetleniu okna dialogowego.

*pParentWnd*<br/>
Wskazuje obiekt okna nadrzędnego lub `CWnd`właściciela (typu), do którego należy obiekt okna dialogowego. Jeśli jest null, okno nadrzędne okna dialogowego jest ustawiona na główne okno aplikacji.

### <a name="remarks"></a>Uwagi

Ta funkcja konstruuje tylko `COleLinksDialog` obiekt. Aby wyświetlić okno dialogowe, należy wywołać funkcję [DoModal.](#domodal)

## <a name="colelinksdialogm_el"></a><a name="m_el"></a>COleLinksDialog::m_el

Struktura typu OLEUIEDITLINKS używana do kontrolowania zachowania okna dialogowego Edytowanie łączy.

```
OLEUIEDITLINKS m_el;
```

### <a name="remarks"></a>Uwagi

Elementy członkowskie tej struktury mogą być modyfikowane bezpośrednio lub za pośrednictwem funkcji członkowskich.

Aby uzyskać więcej informacji, zobacz strukturę [OLEUIEDITLINKS](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw) w programie Windows SDK.

## <a name="see-also"></a>Zobacz też

[Klasa COleDialog](../../mfc/reference/coledialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)
