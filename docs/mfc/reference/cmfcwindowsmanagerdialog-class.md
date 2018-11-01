---
title: Klasa CMFCWindowsManagerDialog
ms.date: 11/04/2016
f1_keywords:
- CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog::CMFCWindowsManagerDialog
helpviewer_keywords:
- CMFCWindowsManagerDialog [MFC], CMFCWindowsManagerDialog
ms.assetid: 35b4b0db-33c4-4b22-94d8-5e3396341340
ms.openlocfilehash: 67fbd1ed066b47cdedf1b5ea2952b042c69bd978
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554313"
---
# <a name="cmfcwindowsmanagerdialog-class"></a>Klasa CMFCWindowsManagerDialog

`CMFCWindowsManagerDialog` Obiekt umożliwia użytkownikowi zarządzanie oknami podrzędnymi MDI w aplikacji MDI.

## <a name="syntax"></a>Składnia

```
class CMFCWindowsManagerDialog : public CDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCWindowsManagerDialog::CMFCWindowsManagerDialog](#cmfcwindowsmanagerdialog)|Konstruuje `CMFCWindowsManagerDialog` obiektu.|

## <a name="remarks"></a>Uwagi

`CMFCWindowsManagerDialog` Znajduje się lista oknami podrzędnymi MDI, które są aktualnie otwarte w aplikacji. Użytkownik ręcznie można kontrolować stan oknami podrzędnymi MDI za pomocą tego okna dialogowego.

`CMFCWindowsManagerDialog` jest osadzony [klasa CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md). `CMFCWindowsManagerDialog` Nie jest klasą, który należy utworzyć ręcznie. Zamiast tego należy wywołać funkcję [CMDIFrameWndEx::ShowWindowsDialog](../../mfc/reference/cmdiframewndex-class.md#showwindowsdialog), a spowoduje to utworzenie i wyświetlić `CMFCWindowsManagerDialog` obiektu.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano sposób tworzenia `CMFCWindowsManagerDialog` obiektu przez wywołanie metody `CMDIFrameWndEx::ShowWindowsDialog`. Ten fragment kodu jest częścią [Visual Studio przykład](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#18](../../mfc/codesnippet/cpp/cmfcwindowsmanagerdialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxWindowsManagerDialog.h

##  <a name="cmfcwindowsmanagerdialog"></a>  CMFCWindowsManagerDialog::CMFCWindowsManagerDialog

Konstruuje [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) obiektu.

```
CMFCWindowsManagerDialog(
    CMDIFrameWndEx* pMDIFrame,
    BOOL bHelpButton = FALSE);
```

### <a name="parameters"></a>Parametry

*pMDIFrame*<br/>
[in] Wskaźnik do okna nadrzędnego lub właściciela.

*bHelpButton*<br/>
[in] Parametr logiczny, który określa, czy w ramach Wyświetla **pomocy** przycisku.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat menedżerów wizualnych zobacz [Menedżer wizualizacji](../../mfc/visualization-manager.md).

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md)
