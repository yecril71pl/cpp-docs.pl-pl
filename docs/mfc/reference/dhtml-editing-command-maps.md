---
title: "Mapy poleceń edycji DHTML | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: c1b49876-039e-4a26-bb24-ea98ccf254a1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7eba41005864e2389997a75855eaf955ad18b557
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="dhtml-editing-command-maps"></a>Mapy poleceń edycji DHTML
Następujące makra może służyć do mapy poleceń edycji DHTML [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-klas pochodnych. Na przykład ich użycia, zobacz [próbki HTMLEdit](../../visual-cpp-samples.md).  
  
### <a name="dhtml-editing-command-map-macros"></a>Makra mapy poleceń edycji DHTML  
  
|||  
|-|-|  
|[DECLARE_DHTMLEDITING_CMDMAP —](#declare_dhtmlediting_cmdmap)|Deklaruje DHTML mapy poleceń edycji w klasie.|  
|[BEGIN_DHTMLEDITING_CMDMAP —](#begin_dhtmlediting_cmdmap)|Uruchamia definicji DHTML mapy poleceń edycji w obrębie klasy.|  
|[END_DHTMLEDITING_CMDMAP —](#end_dhtmlediting_cmdmap)|Oznacza koniec mapy poleceń edycji DHTML.|  
|[DHTMLEDITING_CMD_ENTRY —](#dhtmlediting_cmd_entry)|Identyfikator polecenia jest mapowany na polecenia edycji HTML.|  
|[DHTMLEDITING_CMD_ENTRY_FUNC —](#dhtmlediting_cmd_entry_func)|Mapuje identyfikator polecenia do obsługi wiadomości i polecenia edycji HTML.|  
|[DHTMLEDITING_CMD_ENTRY_TYPE —](#dhtmlediting_cmd_entry_type)|Identyfikator polecenia jest mapowany na polecenia edycji HTML i elementu interfejsu użytkownika.|  
|[DHTMLEDITING_CMD_ENTRY_FUNC_TYPE —](#dhtmlediting_cmd_entry_func_type)|Mapuje identyfikator polecenia do edycji polecenia, obsługi wiadomości i elementu interfejsu użytkownika HTML.|  
  
##  <a name="declare_dhtmlediting_cmdmap"></a>DECLARE_DHTMLEDITING_CMDMAP —  
 Deklaruje DHTML mapy poleceń edycji w klasie.  
  
```  
DECLARE_DHTMLEDITING_CMDMAP(className)   
```  
  
### <a name="parameters"></a>Parametry  
 `className`  
 Nazwa klasy.  
  
### <a name="remarks"></a>Uwagi  
 To makro ma być używany w definicji [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-klas pochodnych.  
  
 Użyj [begin_dhtmlediting_cmdmap —](#begin_dhtmlediting_cmdmap) mapę implementacji.  
  
### <a name="example"></a>Przykład  
 Zobacz [próbki HTMLEdit](../../visual-cpp-samples.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxhtml.h  
  
##  <a name="begin_dhtmlediting_cmdmap"></a>BEGIN_DHTMLEDITING_CMDMAP —  
 Uruchamia definicji DHTML mapy poleceń edycji w obrębie klasy.  
  
```  
BEGIN_DHTMLEDITING_CMDMAP(className)   
```  
  
### <a name="parameters"></a>Parametry  
 `className`  
 Nazwa klasy zawierającej mapy poleceń edycji DHTML. Ta klasa powinien pochodzić od bezpośrednio lub pośrednio [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) i obejmują [declare_dhtmlediting_cmdmap —](#declare_dhtmlediting_cmdmap) makra w ramach swojej definicji klasy.  
  
### <a name="remarks"></a>Uwagi  
 Dodaj mapy poleceń edycji DHTML na klasę do mapowania polecenia interfejsu użytkownika poleceń edycji HTML.  
  
 Miejsce `BEGIN_DHTMLEDITING_CMDMAP` następuje makra w pliku implementacji (.cpp) klasy [dhtmlediting_cmd_entry —](#dhtmlediting_cmd_entry) makra dla poleceń jest klasę do mapowania (na przykład z **id_edit_cut —** do  **IDM_CUT**). Użyj [end_dhtmlediting_cmdmap —](#end_dhtmlediting_cmdmap) makra w celu oznaczenia zakończenia Mapa zdarzeń.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxhtml.h  
  
##  <a name="end_dhtmlediting_cmdmap"></a>END_DHTMLEDITING_CMDMAP —  
 Oznacza koniec mapy poleceń edycji DHTML.  
  
```  
END_DHTMLEDITING_CMDMAP()   
```  
  
### <a name="remarks"></a>Uwagi  
 Używany w połączeniu z [begin_dhtmlediting_cmdmap —](#begin_dhtmlediting_cmdmap).  
  
### <a name="example"></a>Przykład  
 Zobacz [próbki HTMLEdit](../../visual-cpp-samples.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxhtml.h  
  
##  <a name="dhtmlediting_cmd_entry"></a>DHTMLEDITING_CMD_ENTRY —  
 Identyfikator polecenia jest mapowany na polecenia edycji HTML.  
  
```  
DHTMLEDITING_CMD_ENTRY(cmdID,  dhtmlcmdID)   
```  
  
### <a name="parameters"></a>Parametry  
 `cmdID`  
 Identyfikator polecenia (takich jak **id_edit_copy —**).  
  
 `dhtmlcmdID`  
 HTML, polecenia, do którego edycji `cmdID` mapy (takich jak **IDM_COPY**).  
  
### <a name="example"></a>Przykład  
 Zobacz [próbki HTMLEdit](../../visual-cpp-samples.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxhtml.h  
  
##  <a name="dhtmlediting_cmd_entry_func"></a>DHTMLEDITING_CMD_ENTRY_FUNC —  
 Mapuje identyfikator polecenia do obsługi wiadomości i polecenia edycji HTML.  
  
```  
DHTMLEDITING_CMD_ENTRY_FUNC(cmdID, dhtmlcmdID,  member_func_name)   
```  
  
### <a name="parameters"></a>Parametry  
 `cmdID`  
 Identyfikator polecenia (takich jak **id_edit_copy —**).  
  
 `dhtmlcmdID`  
 HTML, polecenia, do którego edycji `cmdID` mapy (takich jak **IDM_COPY**).  
  
 `member_func_name`  
 Nazwa funkcji obsługi wiadomości zamapowany polecenia.  
  
### <a name="example"></a>Przykład  
 Zobacz [próbki HTMLEdit](../../visual-cpp-samples.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxhtml.h  
  
##  <a name="dhtmlediting_cmd_entry_type"></a>DHTMLEDITING_CMD_ENTRY_TYPE —  
 Identyfikator polecenia jest mapowany na polecenia edycji HTML i elementu interfejsu użytkownika.  
  
```  
DHTMLEDITING_CMD_ENTRY_TYPE(cmdID  ,   dhtmlcmdID  ,    elemType)  
```  
  
### <a name="parameters"></a>Parametry  
 `cmdID`  
 Identyfikator polecenia (takich jak **id_edit_copy —**).  
  
 `dhtmlcmdID`  
 HTML, polecenia, do którego edycji `cmdID` mapy (takich jak **IDM_COPY**).  
  
 `elemType`  
 Typ elementu interfejsu użytkownika; jeden z **AFX_UI_ELEMTYPE_NORMAL**, **AFX_UI_ELEMTYPE_CHECKBOX**, lub **AFX_UI_ELEMTYPE_RADIO**.  
  
### <a name="example"></a>Przykład  
 Zobacz [próbki HTMLEdit](../../visual-cpp-samples.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxhtml.h  
  
##  <a name="dhtmlediting_cmd_entry_func_type"></a>DHTMLEDITING_CMD_ENTRY_FUNC_TYPE —  
 Mapuje identyfikator polecenia do edycji polecenia, obsługi wiadomości i elementu interfejsu użytkownika HTML.  
  
```  
DHTMLEDITING_CMD_ENTRY_FUNC_TYPE(cmdID, dhtmlcmdID, member_func_name,  elemType)   
```  
  
### <a name="parameters"></a>Parametry  
 `cmdID`  
 Identyfikator polecenia (takich jak **id_edit_copy —**).  
  
 `dhtmlcmdID`  
 HTML, polecenia, do którego edycji `cmdID` mapy (takich jak **IDM_COPY**).  
  
 `member_func_name`  
 Nazwa funkcji obsługi wiadomości zamapowany polecenia.  
  
 `elemType`  
 Typ elementu interfejsu użytkownika; jeden z **AFX_UI_ELEMTYPE_NORMAL**, **AFX_UI_ELEMTYPE_CHECKBOX**, lub **AFX_UI_ELEMTYPE_RADIO**.  
  
### <a name="example"></a>Przykład  
 Zobacz [próbki HTMLEdit](../../visual-cpp-samples.md).  

### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxhtml.h  
    
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
