---
title: Klasa CFolderPickerDialog | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog::CFolderPickerDialog
dev_langs: C++
helpviewer_keywords: CFolderPickerDialog [MFC], CFolderPickerDialog
ms.assetid: 8db01684-dd1d-4e9c-989e-07a2318a8156
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2e93bb9c9ac6aa447e3df43d4612bd792df091e9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cfolderpickerdialog-class"></a>Klasa CFolderPickerDialog
Klasa CFolderPickerDialog implementuje CFileDialog w folderze Tryb selektora.  
  
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
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cdialog —](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [CFileDialog](../../mfc/reference/cfiledialog-class.md)  
  
 `CFolderPickerDialog`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdlgs.h  
  
##  <a name="cfolderpickerdialog"></a>CFolderPickerDialog::CFolderPickerDialog  
 Konstruktor.  
  
```  
explicit CFolderPickerDialog(
    LPCTSTR lpszFolder = NULL,  
    DWORD dwFlags = 0,  
    CWnd* pParentWnd = NULL,  
    DWORD dwSize = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFolder`  
 Folder początkowy.  
  
 `dwFlags`  
 Połączenie z jedną lub więcej flag, które pozwalają dostosować okna dialogowego.  
  
 `pParentWnd`  
 Wskaźnik do okna nadrzędnego lub właściciela obiektu okno dialogowe.  
  
 `dwSize`  
 Rozmiar struktury OPENFILENAME.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="_dtorcfolderpickerdialog"></a>CFolderPickerDialog:: ~ CFolderPickerDialog  
 Destruktor.  
  
```  
virtual ~CFolderPickerDialog();
```  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
