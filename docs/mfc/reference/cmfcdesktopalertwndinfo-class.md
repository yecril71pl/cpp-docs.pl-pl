---
title: Klasa CMFCDesktopAlertWndInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_hIcon
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_nURLCmdID
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strText
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strURL
dev_langs:
- C++
helpviewer_keywords:
- CMFCDesktopAlertWndInfo [MFC], m_hIcon
- CMFCDesktopAlertWndInfo [MFC], m_nURLCmdID
- CMFCDesktopAlertWndInfo [MFC], m_strText
- CMFCDesktopAlertWndInfo [MFC], m_strURL
ms.assetid: 5c9bb84e-6c96-4748-8e74-6951b6ae8e84
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2f257575abbf405177b2524c4c803c0b3d250187
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcdesktopalertwndinfo-class"></a>Klasa CMFCDesktopAlertWndInfo
`CMFCDesktopAlertWndInfo` Klasa jest używana z [CMFCDesktopAlertWnd klasy](../../mfc/reference/cmfcdesktopalertwnd-class.md). Określa formantów, które są wyświetlane, gdy pulpitu alertu wyświetlone okno podręczne.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCDesktopAlertWndInfo  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CMFCDesktopAlertWndInfo::~CMFCDesktopAlertWndInfo`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCDesktopAlertWndInfo::operator =](#operator_eq)||  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon)|Dojście do ikonę, która jest wyświetlana.|  
|[CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid)|Identyfikator polecenia skojarzony z łączem w oknie alert pulpitu.|  
|[CMFCDesktopAlertWndInfo::m_strText](#m_strtext)|Tekst wyświetlany w oknie alert pulpitu.|  
|[CMFCDesktopAlertWndInfo::m_strURL](#m_strurl)|Łącze, które jest wyświetlane w oknie alert pulpitu.|  
  
## <a name="remarks"></a>Uwagi  
 `CMFCDesktopAlertWndInfo` Klasy jest przekazywana do [CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) metodę, aby określić elementy, które są wyświetlane w oknie dialogowym domyślne pulpitu okna alertu. Domyślne okno dialogowe może zawierać trzy elementy:  
  
-   Ikona, który jest ustawiony przez wywołanie metody [CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon).  
  
-   Etykieta lub wiadomości tekstowej, który jest ustawiony przez wywołanie metody [CMFCDesktopAlertWndInfo::m_strText](#m_strtext).  
  
-   Link, który jest ustawiony przez wywołanie metody [CMFCDesktopAlertWndInfo::m_strURL](#m_strurl). Aby ustawić polecenia, który zostanie wykonany po kliknięciu łącza, należy wywołać [CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid).  
  
 Jeśli domyślne okno dialogowe nie jest wystarczająca, możesz tworzyć niestandardowe okno dialogowe i przekaż go do [CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) metody zamiast za pomocą tej klasy. Aby uzyskać więcej informacji, zobacz [CMFCDesktopAlertDialog klasy](../../mfc/reference/cmfcdesktopalertdialog-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia różnych elementów członkowskich w `CMFCDesktopAlertWndInfo` klasy. W przykładzie pokazano, jak ustawić dojście do ikonę, która jest wyświetlany tekst, który jest wyświetlany na oknie alertu pulpitu, link jest wyświetlany w oknie alert pulpitu i identyfikator polecenia skojarzony z łączem w oknie alert pulpitu. Ten przykład jest częścią [próbka Demo alertu pulpitu](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#3](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndinfo-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxDesktopAlertDialog.h  
  
##  <a name="operator_eq"></a>CMFCDesktopAlertWndInfo::operator =  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCDesktopAlertWndInfo& operator=(CMFCDesktopAlertWndInfo& src);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`src`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_hicon"></a>CMFCDesktopAlertWndInfo::m_hIcon  
 Dojście do ikonę, która jest wyświetlana.  
  
```  
HICON m_hIcon;  
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_nurlcmdid"></a>CMFCDesktopAlertWndInfo::m_nURLCmdID  
 Identyfikator polecenia skojarzony z łączem w oknie alert pulpitu.  
  
```  
UINT m_nURLCmdID;  
```  
  
### <a name="remarks"></a>Uwagi  
 Identyfikator polecenia jest wysyłany do właściciela okna podręcznego, gdy użytkownik kliknie łącze, określony przez [CMFCDesktopAlertWndInfo::m_strURL](#m_strurl).  
  
##  <a name="m_strtext"></a>CMFCDesktopAlertWndInfo::m_strText  
 Tekst wyświetlany w oknie alert pulpitu.  
  
```  
CString m_strText;  
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_strurl"></a>CMFCDesktopAlertWndInfo::m_strURL  
 Łącze, które jest wyświetlane w oknie alert pulpitu.  
  
```  
CString m_strURL;  
```  
  
### <a name="remarks"></a>Uwagi  
 Gdy użytkownik kliknie łącze, polecenie mający [CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid) identyfikator polecenia zostaną wysłane do właściciela tego okna.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)   
 [CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)   
 [Klasa CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md)
