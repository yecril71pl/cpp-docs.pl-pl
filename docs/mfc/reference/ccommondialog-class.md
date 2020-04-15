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
ms.openlocfilehash: 853a4756df3b70f4f33deb7159b4d1aee610092c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369443"
---
# <a name="ccommondialog-class"></a>Klasa CCommonDialog

Klasa podstawowa dla klas, które hermetyzują funkcjonalność typowych okien dialogowych systemu Windows.

## <a name="syntax"></a>Składnia

```
class CCommonDialog : public CDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCommonDialog::CCommonDialog](#ccommondialog)|Konstruuje `CCommonDialog` obiekt.|

## <a name="remarks"></a>Uwagi

Następujące klasy hermetyzują funkcjonalność typowych okien dialogowych systemu Windows:

- [Cfiledialog](../../mfc/reference/cfiledialog-class.md)

- [CFontDialog](../../mfc/reference/cfontdialog-class.md)

- [CColorDialog (Polski)](../../mfc/reference/ccolordialog-class.md)

- [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)

- [Cprintdialog](../../mfc/reference/cprintdialog-class.md)

- [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md)

- [Cfindreplacedialog](../../mfc/reference/cfindreplacedialog-class.md)

- [COleDialog (Polski)](../../mfc/reference/coledialog-class.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

`CCommonDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdlgs.h

## <a name="ccommondialogccommondialog"></a><a name="ccommondialog"></a>CCommonDialog::CCommonDialog

Konstruuje `CCommonDialog` obiekt.

```
explicit CCommonDialog(CWnd* pParentWnd);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskazuje obiekt okna nadrzędnego lub właściciela (typu [CWnd),](../../mfc/reference/cwnd-class.md)do którego należy obiekt okna dialogowego. Jeśli jest null, okno nadrzędne obiektu okna dialogowego jest ustawiona na okno aplikacji głównej.

### <a name="remarks"></a>Uwagi

Zobacz [CDialog::CDialog](../../mfc/reference/cdialog-class.md#cdialog) pełne informacje.

## <a name="see-also"></a>Zobacz też

[Klasa CDialog](../../mfc/reference/cdialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFileDialog](../../mfc/reference/cfiledialog-class.md)<br/>
[Klasa CFontDialog](../../mfc/reference/cfontdialog-class.md)<br/>
[Klasa CColorDialog](../../mfc/reference/ccolordialog-class.md)<br/>
[Klasa CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)<br/>
[Klasa CPrintDialog](../../mfc/reference/cprintdialog-class.md)<br/>
[Klasa CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)
