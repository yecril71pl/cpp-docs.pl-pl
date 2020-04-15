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
ms.openlocfilehash: e3928c0d3ae4f607dceb99c0762277e8ea9ddbde
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319826"
---
# <a name="cmfcwindowsmanagerdialog-class"></a>Klasa CMFCWindowsManagerDialog

Obiekt `CMFCWindowsManagerDialog` umożliwia użytkownikowi zarządzanie oknami podrzędnymi MDI w aplikacji MDI.

## <a name="syntax"></a>Składnia

```
class CMFCWindowsManagerDialog : public CDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCWindowsManagerDialog::CMFCWindowsManagerDialog](#cmfcwindowsmanagerdialog)|Konstruuje `CMFCWindowsManagerDialog` obiekt.|

## <a name="remarks"></a>Uwagi

Zawiera `CMFCWindowsManagerDialog` listę okien podrzędnych MDI, które są obecnie otwarte w aplikacji. Użytkownik może ręcznie kontrolować stan okien podrzędnych MDI za pomocą tego okna dialogowego.

`CMFCWindowsManagerDialog`jest osadzony wewnątrz [klasy CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md). Nie `CMFCWindowsManagerDialog` jest to klasa, którą należy utworzyć ręcznie. Zamiast tego wywołać funkcję [CMDIFrameWndEx::ShowWindowsDialog](../../mfc/reference/cmdiframewndex-class.md#showwindowsdialog), a `CMFCWindowsManagerDialog` spowoduje utworzenie i wyświetlenie obiektu.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak skonstruować obiekt przez `CMFCWindowsManagerDialog` wywołanie `CMDIFrameWndEx::ShowWindowsDialog`. Ten fragment kodu jest częścią [przykładu demo programu Visual Studio.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_VisualStudioDemo#18](../../mfc/codesnippet/cpp/cmfcwindowsmanagerdialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxWindowsManagerDialog.h

## <a name="cmfcwindowsmanagerdialogcmfcwindowsmanagerdialog"></a><a name="cmfcwindowsmanagerdialog"></a>CMFCWindowsManagerDialog::CMFCWindowsManagerDialog

Konstruuje [obiekt CMFCWindowsManagerDialog.](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)

```
CMFCWindowsManagerDialog(
    CMDIFrameWndEx* pMDIFrame,
    BOOL bHelpButton = FALSE);
```

### <a name="parameters"></a>Parametry

*pMDIFrame*<br/>
[w] Wskaźnik do okna nadrzędnego lub właściciela.

*bHelpButton*<br/>
[w] Parametr logiczny określający, czy w ramach jest wyświetlany przycisk **Pomoc.**

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat menedżerów wizualnych, zobacz [Menedżer wizualizacji](../../mfc/visualization-manager.md).

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md)
