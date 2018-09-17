---
title: Klasa CMFCWindowsManagerDialog | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog::CMFCWindowsManagerDialog
dev_langs:
- C++
helpviewer_keywords:
- CMFCWindowsManagerDialog [MFC], CMFCWindowsManagerDialog
ms.assetid: 35b4b0db-33c4-4b22-94d8-5e3396341340
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71c85d3061da7cf4c87abef9549542900e962f64
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707008"
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
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md)
