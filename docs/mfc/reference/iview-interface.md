---
title: Interfejs IView | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IView
- AFXWINFORMS/IView
- AFXWINFORMS/IView::OnActivateView
- AFXWINFORMS/IView::OnInitialUpdate
- AFXWINFORMS/IView::OnUpdate
dev_langs: C++
helpviewer_keywords:
- views [MFC]
- IView class [MFC]
- views [MFC], classes
ms.assetid: 9321f299-486e-4551-bee9-d2c4a7b91548
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a4266d8f5ec564dac67d7167c6c9bab4768a0276
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="iview-interface"></a>Interfejs IView
Implementuje kilka metod który [CWinFormsView](../../mfc/reference/cwinformsview-class.md) używa do wysyłania powiadomień widoku do zarządzanego formantu.  
  
## <a name="syntax"></a>Składnia  
  
```  
interface class IView  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IView::OnActivateView](#onactivateview)|Wywoływane przez MFC, gdy widok jest aktywowane lub dezaktywowane.|  
|[IView::OnInitialUpdate](#oninitialupdate)|Wywoływane przez platformę po widoku najpierw jest dołączony do dokumentu, ale przed wyświetleniu widoku.|  
|[IView::OnUpdate](#onupdate)|Metoda wywoływana przez MFC po widoku dokument został zmodyfikowany; Ta funkcja umożliwia widoku, aby zaktualizować jej wyświetlania w celu odzwierciedlenia zmian.|  
  
## <a name="remarks"></a>Uwagi  
 `IView`implementuje kilka metod który `CWinFormsView` używa do przekazywania wspólnej powiadomienia widoku do hostowanej zarządzanego formantu. Są to [OnInitialUpdate](#oninitialupdate), [OnUpdate](#onupdate) i [OnActivateView](#onactivateview).  
  
 `IView`przypomina [CView](../../mfc/reference/cview-class.md), ale jest używana tylko z zarządzanych widoków i kontrolek.  
  
 Aby uzyskać więcej informacji na temat używania formularzy systemu Windows, zobacz [za pomocą formantu użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  

## <a name="requirements"></a>Wymagania  
 Nagłówek: afxwinforms.h (zdefiniowany w zestawie atlmfc\lib\mfcmifc80.dll)  

## <a name="onactivateview"></a>IView::OnActivateView  
Wywoływane przez MFC, gdy widok jest aktywowane lub dezaktywowane.
```
void OnActivateView(bool activate);
```
## <a name="parameters"></a>Parametry
`activate`  
Wskazuje, czy widok jest aktywowane lub dezaktywowane.  

## <a name="oninitialupdate"></a>IView::OnInitialUpdate
Wywoływane przez platformę po widoku najpierw jest dołączony do dokumentu, ale przed wyświetleniu widoku.
```
void OnInitialUpdate();
```

## <a name="onupdate"></a>IView::OnUpdate 
Metoda wywoływana przez MFC, po jego dokument został zmodyfikowany.  
```
void OnUpdate();
```
## <a name="remarks"></a>Uwagi  
Ta funkcja umożliwia widoku, aby zaktualizować jej wyświetlania w celu odzwierciedlenia zmian.

## <a name="see-also"></a>Zobacz też  
 [Klasa CWinFormsView](../../mfc/reference/cwinformsview-class.md)   
 [Klasa CView](../../mfc/reference/cview-class.md)
