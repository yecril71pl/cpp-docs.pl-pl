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
ms.openlocfilehash: 6a1983d426e97dd8063aee2857dc36557aa20677
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366095"
---
# <a name="coledialog-class"></a>Klasa COleDialog

Udostępnia funkcje typowe dla okien dialogowych ole.

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

Biblioteka klas Microsoft Foundation zawiera `COleDialog`kilka klas pochodzących z:

- [COleInsertDialog](../../mfc/reference/coleinsertdialog-class.md)

- [COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md)

- [COleChangeIconDialog](../../mfc/reference/colechangeicondialog-class.md)

- [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)

- [COleBusyDialog](../../mfc/reference/colebusydialog-class.md)

- [COleUpdateDialog](../../mfc/reference/coleupdatedialog-class.md)

- [COlePasteSpecialDialog](../../mfc/reference/colepastespecialdialog-class.md)

- [COlePropertiesDialog](../../mfc/reference/colepropertiesdialog-class.md)

- [COleChangeSourceDialog](../../mfc/reference/colechangesourcedialog-class.md)

Aby uzyskać więcej informacji na temat okien dialogowych specyficznych dla ole, zobacz [artykuł Okna dialogowe w ole](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CKlogialny](../../mfc/reference/ccommondialog-class.md)

`COleDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxodlgs.h

## <a name="coledialoggetlasterror"></a><a name="getlasterror"></a>COleDialog::GetLastError

Wywołanie `GetLastError` funkcji elementu członkowskiego, `DoModal` aby uzyskać dodatkowe informacje o błędzie po zwróceniu IDABORT.

```
UINT GetLastError() const;
```

### <a name="return-value"></a>Wartość zwracana

Kody błędów `GetLastError` zwracane przez zależą od wyświetlanego określonego okna dialogowego.

### <a name="remarks"></a>Uwagi

Zobacz `DoModal` funkcję elementu członkowskiego w klasach pochodnych, aby uzyskać informacje o określonych komunikatach o błędach.

## <a name="see-also"></a>Zobacz też

[Klasa CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
