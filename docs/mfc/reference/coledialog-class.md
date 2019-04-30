---
title: Klasa COleDialog
ms.date: 11/04/2016
f1_keywords:
- COleDialog
- AFXODLGS/COleDialog
- AFXODLGS/COleDialog::GetLastError
helpviewer_keywords:
- COleDialog [MFC], GetLastError
ms.assetid: b1ed0aca-3914-4b00-af34-4a4fb491aec7
ms.openlocfilehash: 353e2ed312fa7dbb9ef7bdfabc2b174abf8e1e1d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375720"
---
# <a name="coledialog-class"></a>Klasa COleDialog

Zapewnia funkcje wspólne do okien dialogowych dla mechanizmu OLE.

## <a name="syntax"></a>Składnia

```
class COleDialog : public CCommonDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDialog::GetLastError](#getlasterror)|Pobiera kod błędu zwrócony przez okno dialogowe.|

## <a name="remarks"></a>Uwagi

Biblioteki klas Microsoft Foundation dostarcza kilka klas pochodnych `COleDialog`:

- [COleInsertDialog](../../mfc/reference/coleinsertdialog-class.md)

- [COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md)

- [COleChangeIconDialog](../../mfc/reference/colechangeicondialog-class.md)

- [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)

- [COleBusyDialog](../../mfc/reference/colebusydialog-class.md)

- [COleUpdateDialog](../../mfc/reference/coleupdatedialog-class.md)

- [COlePasteSpecialDialog](../../mfc/reference/colepastespecialdialog-class.md)

- [COlePropertiesDialog](../../mfc/reference/colepropertiesdialog-class.md)

- [COleChangeSourceDialog](../../mfc/reference/colechangesourcedialog-class.md)

Aby uzyskać więcej informacji o okna dialogowe OLE specyficzne artykuł [okna dialogowe w OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`COleDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxodlgs.h

##  <a name="getlasterror"></a>  COleDialog::GetLastError

Wywołaj `GetLastError` funkcję elementu członkowskiego, aby uzyskać dodatkowe informacje o błędzie podczas `DoModal` zwraca IDABORT.

```
UINT GetLastError() const;
```

### <a name="return-value"></a>Wartość zwracana

Kodów błędów zwróconych przez `GetLastError` są zależne od określonych dialogowego wyświetlanego.

### <a name="remarks"></a>Uwagi

Zobacz `DoModal` funkcja elementu członkowskiego w klasach pochodnych, aby uzyskać informacje o określone komunikaty o błędach.

## <a name="see-also"></a>Zobacz także

[Klasa CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
