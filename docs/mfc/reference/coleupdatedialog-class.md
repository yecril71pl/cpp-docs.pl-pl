---
title: Klasa COleUpdateDialog
ms.date: 11/04/2016
f1_keywords:
- COleUpdateDialog
- AFXODLGS/COleUpdateDialog
- AFXODLGS/COleUpdateDialog::COleUpdateDialog
- AFXODLGS/COleUpdateDialog::DoModal
helpviewer_keywords:
- COleUpdateDialog [MFC], COleUpdateDialog
- COleUpdateDialog [MFC], DoModal
ms.assetid: 699ca980-52b1-4cf8-9ab1-ac6767ad5b0e
ms.openlocfilehash: 9e2c7a8d79ebf5e6483a06354b280e474d7b8e61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374835"
---
# <a name="coleupdatedialog-class"></a>Klasa COleUpdateDialog

Używany w specjalnym przypadku okna dialogowego Edycja łącza OLE, które powinno być używane, gdy trzeba zaktualizować tylko istniejące obiekty połączone lub osadzone w dokumencie.

## <a name="syntax"></a>Składnia

```
class COleUpdateDialog : public COleLinksDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleUpdateDialog::COleUpdateDialog](#coleupdatedialog)|Konstruuje `COleUpdateDialog` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleUpdateDialog::DoModal](#domodal)|Wyświetla okno dialogowe **Edytowanie łączy** w trybie aktualizacji.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji dotyczących okien dialogowych specyficznych dla ole, zobacz [okna dialogowe](../../mfc/dialog-boxes-in-ole.md)artykułu OLE .

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CKlogialny](../../mfc/reference/ccommondialog-class.md)

[COleDialog (Polski)](../../mfc/reference/coledialog-class.md)

[COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)

`COleUpdateDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxodlgs.h

## <a name="coleupdatedialogcoleupdatedialog"></a><a name="coleupdatedialog"></a>COleUpdateDialog::COleUpdateDialog

Konstruuje `COleUpdateDialog` obiekt.

```
explicit COleUpdateDialog(
    COleDocument* pDoc,
    BOOL bUpdateLinks = TRUE,
    BOOL bUpdateEmbeddings = FALSE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*pDoc*<br/>
Wskazuje dokument zawierający łącza, które mogą wymagać aktualizacji.

*bUpdateLinks*<br/>
Flaga, która określa, czy połączone obiekty mają być aktualizowane.

*bUpdateBeddings*<br/>
Flaga, która określa, czy obiekty osadzone mają być aktualizowane.

*pParentWnd*<br/>
Wskazuje obiekt okna nadrzędnego lub `CWnd`właściciela (typu), do którego należy obiekt okna dialogowego. Jeśli jest null, okno nadrzędne okna dialogowego zostanie ustawiona na główne okno aplikacji.

### <a name="remarks"></a>Uwagi

Ta funkcja konstruuje tylko `COleUpdateDialog` obiekt. Aby wyświetlić okno dialogowe, zadzwoń do [DoModal](../../mfc/reference/colelinksdialog-class.md#domodal). Ta klasa powinna być `COleLinksDialog` używana zamiast, gdy chcesz zaktualizować tylko istniejące elementy połączone lub osadzone.

## <a name="coleupdatedialogdomodal"></a><a name="domodal"></a>COleUpdateDialog::DoModal

Wyświetla okno dialogowe Edytowanie łączy w trybie aktualizacji.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

Stan ukończenia okna dialogowego. Jedna z następujących wartości:

- IDOK, jeśli okno dialogowe wróciło pomyślnie.

- IDCANCEL jeśli żaden z połączonych lub osadzonych elementów w bieżącym dokumencie nie wymaga aktualizacji.

- IDABORT, jeśli wystąpił błąd. Jeśli idabort jest zwracany, wywołać [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) funkcji elementu członkowskiego, aby uzyskać więcej informacji na temat typu błędu, który wystąpił. Aby uzyskać listę możliwych błędów, zobacz [OleUIEditLinks](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw) funkcji w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Wszystkie łącza i/lub osadzanie są aktualizowane, chyba że użytkownik wybierze przycisk Anuluj.

## <a name="see-also"></a>Zobacz też

[Próbka MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[Klasa COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)
