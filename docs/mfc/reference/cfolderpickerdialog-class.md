---
title: Klasa CFolderPickerDialog
ms.date: 11/04/2016
f1_keywords:
- CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog::CFolderPickerDialog
helpviewer_keywords:
- CFolderPickerDialog [MFC], CFolderPickerDialog
ms.assetid: 8db01684-dd1d-4e9c-989e-07a2318a8156
ms.openlocfilehash: ba189badaa9b1605e3467526e7b92a18a1bb5a73
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561307"
---
# <a name="cfolderpickerdialog-class"></a>Klasa CFolderPickerDialog

Klasa CFolderPickerDialog cfiledialog w folderze trybu selektora.

## <a name="syntax"></a>Składnia

```
class CFolderPickerDialog : public CFileDialog;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFolderPickerDialog:: ~ CFolderPickerDialog](#cfolderpickerdialog__~cfolderpickerdialog)|Destruktor.|
|[CFolderPickerDialog::CFolderPickerDialog](#cfolderpickerdialog)|Konstruktor.|

## <a name="remarks"></a>Uwagi

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[CFileDialog](../../mfc/reference/cfiledialog-class.md)

`CFolderPickerDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdlgs.h

##  <a name="cfolderpickerdialog"></a>  CFolderPickerDialog::CFolderPickerDialog

Konstruktor.

```
explicit CFolderPickerDialog(
    LPCTSTR lpszFolder = NULL,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL,
    DWORD dwSize = 0);
```

### <a name="parameters"></a>Parametry

*lpszFolder*<br/>
Folder początkowy.

*Flagidw*<br/>
Połączenie jednego lub więcej flagi, które umożliwiają dostosowanie okno dialogowe.

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego lub właściciel obiektu okno dialogowe.

*niezerowego*<br/>
Rozmiar LPSTRFILE struktury.

### <a name="remarks"></a>Uwagi

##  <a name="_dtorcfolderpickerdialog"></a>  CFolderPickerDialog:: ~ CFolderPickerDialog

Destruktor.

```
virtual ~CFolderPickerDialog();
```

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
