---
title: Klasa CCommonDialog
ms.date: 11/04/2016
f1_keywords:
- CCommonDialog
- AFXDLGS/CCommonDialog
- AFXDLGS/CCommonDialog::CCommonDialog
helpviewer_keywords:
- CCommonDialog [MFC], CCommonDialog
ms.assetid: 1f68d65f-a0fd-4778-be22-ebbe51a95f95
ms.openlocfilehash: 4fa7aa51d1ce482e00f68365045cd35c3fb7939b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264875"
---
# <a name="ccommondialog-class"></a>Klasa CCommonDialog

Klasa bazowa dla klas, które zapewniają funkcjonalność wspólnych okien dialogowych Windows.

## <a name="syntax"></a>Składnia

```
class CCommonDialog : public CDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCommonDialog::CCommonDialog](#ccommondialog)|Konstruuje `CCommonDialog` obiektu.|

## <a name="remarks"></a>Uwagi

Następujące klasy hermetyzacji wspólnych okien dialogowych Windows funkcji:

- [CFileDialog](../../mfc/reference/cfiledialog-class.md)

- [CFontDialog](../../mfc/reference/cfontdialog-class.md)

- [CColorDialog](../../mfc/reference/ccolordialog-class.md)

- [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)

- [CPrintDialog](../../mfc/reference/cprintdialog-class.md)

- [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md)

- [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)

- [COleDialog](../../mfc/reference/coledialog-class.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`CCommonDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdlgs.h

##  <a name="ccommondialog"></a>  CCommonDialog::CCommonDialog

Konstruuje `CCommonDialog` obiektu.

```
explicit CCommonDialog(CWnd* pParentWnd);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskazuje na obiekt okna nadrzędnego lub właściciela (typu [CWnd](../../mfc/reference/cwnd-class.md)) do którego należy obiekt okna dialogowego. Jeśli ma wartość NULL, okna nadrzędnego obiektu okna dialogowego jest ustawiony na okna głównego aplikacji.

### <a name="remarks"></a>Uwagi

Zobacz [CDialog::CDialog](../../mfc/reference/cdialog-class.md#cdialog) pełne informacje.

## <a name="see-also"></a>Zobacz także

[Klasa CDialog](../../mfc/reference/cdialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFileDialog](../../mfc/reference/cfiledialog-class.md)<br/>
[Klasa CFontDialog](../../mfc/reference/cfontdialog-class.md)<br/>
[Klasa CColorDialog](../../mfc/reference/ccolordialog-class.md)<br/>
[Klasa CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)<br/>
[Klasa CPrintDialog](../../mfc/reference/cprintdialog-class.md)<br/>
[Klasa CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)
