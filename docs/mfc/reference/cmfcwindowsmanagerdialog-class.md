---
title: Klasa CMFCWindowsManagerDialog | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1f20a93135a6f310b626cbe12f68f72c64e4ce8e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcwindowsmanagerdialog-class"></a>Klasa CMFCWindowsManagerDialog
`CMFCWindowsManagerDialog` Obiektu umożliwia zarządzanie oknami podrzędnymi MDI w aplikacji MDI.  
  
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
 `CMFCWindowsManagerDialog` Zawiera listę okien podrzędnych MDI obecnie otwartych w aplikacji. Użytkownik ręcznie kontrolować stan okien podrzędnych MDI za pomocą tego okna dialogowego.  
  
 `CMFCWindowsManagerDialog`jest osadzony wewnątrz [CMDIFrameWndEx klasy](../../mfc/reference/cmdiframewndex-class.md). `CMFCWindowsManagerDialog` Nie jest klasą należy utworzyć ręcznie. Zamiast tego wywołaj funkcję [CMDIFrameWndEx::ShowWindowsDialog](../../mfc/reference/cmdiframewndex-class.md#showwindowsdialog), i spowoduje utworzenie i wyświetlić `CMFCWindowsManagerDialog` obiektu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia `CMFCWindowsManagerDialog` obiektu przez wywołanie metody `CMDIFrameWndEx::ShowWindowsDialog`. Następujący fragment kodu jest częścią [programu Visual Studio przykład](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#18](../../mfc/codesnippet/cpp/cmfcwindowsmanagerdialog-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cdialog —](../../mfc/reference/cdialog-class.md)  
  
 [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxWindowsManagerDialog.h  
  
##  <a name="cmfcwindowsmanagerdialog"></a>CMFCWindowsManagerDialog::CMFCWindowsManagerDialog  
 Konstruuje [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) obiektu.  
  
```  
CMFCWindowsManagerDialog(
    CMDIFrameWndEx* pMDIFrame,  
    BOOL bHelpButton = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pMDIFrame`  
 Wskaźnik do okna nadrzędnego lub właściciela.  
  
 [in]`bHelpButton`  
 Wartość logiczna parametr, który określa, czy w ramach Wyświetla **pomocy** przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat menedżerów visual zobacz [Menedżer wizualizacji](../../mfc/visualization-manager.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md)
