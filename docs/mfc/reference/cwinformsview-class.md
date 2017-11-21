---
title: Klasa CWinFormsView | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinFormsView
- AFXWINFORMS/CWinFormsView
- AFXWINFORMS/CWinFormsView::CWinFormsView
- AFXWINFORMS/CWinFormsView::GetControl
dev_langs: C++
helpviewer_keywords:
- CWinFormsView [MFC], CWinFormsView
- CWinFormsView [MFC], GetControl
ms.assetid: d597e397-6529-469b-88f5-7f65a6b9e895
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0d3551252d04dc97f6e2b4dd13df61edda576744
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cwinformsview-class"></a>Klasa CWinFormsView
Udostępnia ogólne funkcje do hostowania kontrolki Windows Forms jako widoku MFC.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CWinFormsView : public CView;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CWinFormsView::CWinFormsView](#cwinformsview)|Konstruuje `CWinFormsView` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CWinFormsView::GetControl](#getcontrol)|Pobiera wskaźnik do formantu formularzy systemu Windows.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa||  
|----------|-|  
|[Formant CWinFormsView::operator ^](#operator_control)|Rzutuje typu jako wskaźnik do formantu formularzy systemu Windows.|  
  
## <a name="remarks"></a>Uwagi  
 Używa MFC `CWinFormsView` klasy do hostowania formantu formularzy systemu Windows programu .NET Framework w widoku MFC. Kontrolka jest elementem podrzędnym natywnego widoku i zajmuje obszaru klienckiego całego widoku MFC. Wynik jest podobny do `CFormView` widoku umożliwia korzystanie z projektanta formularzy systemu Windows i czas działania do tworzenia zaawansowanych widoków opartych na formularzach.  
  
 Aby uzyskać więcej informacji na temat używania formularzy systemu Windows, zobacz [za pomocą formantu użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
> [!NOTE]
>  Integracja MFC Windows Forms działa tylko w projektach, które łącze dynamicznie z MFC (projekty, w których zdefiniowano AFXDLL).  
  
> [!NOTE]
>  CWinFormsView nie obsługuje okna podziału MFC ( [CSplitterWnd klasy](../../mfc/reference/csplitterwnd-class.md)). Obecnie tylko systemu Windows Forms rozdzielacz jest obsługiwany.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwinforms.h  
  
##  <a name="cwinformsview"></a>CWinFormsView::CWinFormsView  
 Konstruuje `CWinFormsView` obiektu.  
  
```  
CWinFormsView(System::Type^ pManagedViewType);  
```  
  
### <a name="parameters"></a>Parametry  
 `pManagedViewType`  
 Wskaźnik do typu danych formantu użytkownika formularzy systemu Windows.   
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie `CUserView` klasa dziedziczy `CWinFormsView` i przekazuje typ `UserControl1` do `CWinFormsView` konstruktora. `UserControl1`jest kontrolki niestandardowej w ControlLibrary1.dll.  
  
 [!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]  
  
 [!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]  
  
##  <a name="getcontrol"></a>CWinFormsView::GetControl  
 Pobiera wskaźnik do formantu formularzy systemu Windows.  
  
```  
System::Windows::Forms::Control^ GetControl() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `System.Windows.Forms.Control` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Na przykład dotyczące używania formularzy systemu Windows, temacie [za pomocą formantu użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
##  <a name="operator_control"></a>Formant CWinFormsView::operator ^  
 Rzutuje typu jako wskaźnik do formantu formularzy systemu Windows.  
  
```  
operator System::Windows::Forms::Control^() const;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ten operator umożliwia przekazywanie `CWinFormsView` widoku do funkcji, które akceptują wskaźnik do formantu formularzy systemu Windows typu <xref:System.Windows.Forms.Control>.  
  
### <a name="example"></a>Przykład  
  Zobacz [CWinFormsView::GetControl](#getcontrol).  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md)   
 [Klasa CWinFormsDialog](../../mfc/reference/cwinformsdialog-class.md)   
 [Klasa CFormView](../../mfc/reference/cformview-class.md)
