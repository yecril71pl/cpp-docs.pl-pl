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
ms.openlocfilehash: 150e78b7880a61343db21c3c787ffdd1f0b734a5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503169"
---
# <a name="coleupdatedialog-class"></a>Klasa COleUpdateDialog

Używane w specjalnym przypadku okna dialogowego Edytowanie linków OLE, które ma być używane, gdy trzeba zaktualizować tylko istniejące obiekty połączone lub osadzone w dokumencie.

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
|[COleUpdateDialog::D oModal](#domodal)|Wyświetla okno dialogowe **Edytowanie linków** w trybie aktualizacji.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji dotyczących okien dialogowych specyficznych dla OLE, zobacz [okna dialogowe artykułu w OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

[COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)

`COleUpdateDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxodlgs. h

##  <a name="coleupdatedialog"></a>COleUpdateDialog::COleUpdateDialog

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
Wskazuje dokument zawierający linki, które mogą wymagać aktualizacji.

*bUpdateLinks*<br/>
Flaga określająca, czy obiekty połączone mają być aktualizowane.

*bUpdateEmbeddings*<br/>
Flaga określająca, czy obiekty osadzone mają być aktualizowane.

*pParentWnd*<br/>
Wskazuje obiekt nadrzędny lub właściciel (typu `CWnd`), do którego należy obiekt okna dialogowego. Jeśli ma wartość NULL, okno dialogowe nadrzędne okna dialogowego zostanie ustawione na główne okno aplikacji.

### <a name="remarks"></a>Uwagi

Ta funkcja tworzy tylko `COleUpdateDialog` obiekt. Aby wyświetlić okno dialogowe, wywołaj [DoModal](../../mfc/reference/colelinksdialog-class.md#domodal). Ta klasa powinna być używana zamiast, `COleLinksDialog` gdy chcesz zaktualizować tylko istniejące elementy połączone lub osadzone.

##  <a name="domodal"></a>COleUpdateDialog::D oModal

Wyświetla okno dialogowe Edytowanie linków w trybie aktualizacji.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

Stan ukończenia dla okna dialogowego. Jedna z następujących wartości:

- IDOK, jeśli okno dialogowe zostało pomyślnie zwrócone.

- IDCANCEL, jeśli żaden z elementów połączonych lub osadzonych w bieżącym dokumencie nie wymaga aktualizacji.

- IDABORT, jeśli wystąpił błąd. Jeśli IDABORT jest zwracany, wywołaj funkcję członkowską [COleDialog:: GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) , aby uzyskać więcej informacji na temat typu błędu, który wystąpił. Listę możliwych błędów można znaleźć w funkcji [OLEUIEDITLINKS](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw) w Windows SDK.

### <a name="remarks"></a>Uwagi

Wszystkie linki i/lub osadzenia są aktualizowane, chyba że użytkownik wybierze przycisk Anuluj.

## <a name="see-also"></a>Zobacz także

[Przykład OCLIENT MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)
