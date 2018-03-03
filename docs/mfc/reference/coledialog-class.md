---
title: Klasa COleDialog | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDialog
- AFXODLGS/COleDialog
- AFXODLGS/COleDialog::GetLastError
dev_langs:
- C++
helpviewer_keywords:
- COleDialog [MFC], GetLastError
ms.assetid: b1ed0aca-3914-4b00-af34-4a4fb491aec7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ae60b9e5a0d2e79d2bf6d9cc06eebfa9df0c6e23
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="coledialog-class"></a>Klasa COleDialog
Zapewnia funkcje wspólne dla okien dialogowych OLE.  
  
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
 Microsoft Foundation Class Library zawiera kilka klas pochodnych `COleDialog`:  
  
- [COleInsertDialog](../../mfc/reference/coleinsertdialog-class.md)  
  
- [COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md)  
  
- [COleChangeIconDialog](../../mfc/reference/colechangeicondialog-class.md)  
  
- [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)  
  
- [COleBusyDialog](../../mfc/reference/colebusydialog-class.md)  
  
- [COleUpdateDialog](../../mfc/reference/coleupdatedialog-class.md)  
  
- [COlePasteSpecialDialog](../../mfc/reference/colepastespecialdialog-class.md)  
  
- [COlePropertiesDialog](../../mfc/reference/colepropertiesdialog-class.md)  
  
- [COleChangeSourceDialog](../../mfc/reference/colechangesourcedialog-class.md)  
  
 Aby uzyskać informacje o oknach dialogowych OLE specyficzne, zobacz artykuł [okna dialogowe w OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cdialog —](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `COleDialog`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxodlgs.h  
  
##  <a name="getlasterror"></a>COleDialog::GetLastError  
 Wywołanie `GetLastError` funkcji członkowskiej, aby uzyskać dodatkowe informacje o błędzie podczas `DoModal` zwraca **IDABORT**.  
  
```  
UINT GetLastError() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kodów błędów zwróconych przez `GetLastError` są zależne od określonych oknie wyświetlane.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz `DoModal` funkcji Członkowskich w klasach pochodnych informacji o określone komunikaty o błędach.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CCommonDialog](../../mfc/reference/ccommondialog-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



