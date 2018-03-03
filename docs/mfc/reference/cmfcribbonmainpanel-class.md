---
title: Klasa CMFCRibbonMainPanel | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonMainPanel
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::Add
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddRecentFilesList
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddToBottom
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddToRight
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::GetCommandsFrame
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonMainPanel [MFC], Add
- CMFCRibbonMainPanel [MFC], AddRecentFilesList
- CMFCRibbonMainPanel [MFC], AddToBottom
- CMFCRibbonMainPanel [MFC], AddToRight
- CMFCRibbonMainPanel [MFC], GetCommandsFrame
ms.assetid: 1af78798-5e75-4365-9c81-a54aa5679602
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f8b5508abdc90c4c566d078f2f75c30822c7a18e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribbonmainpanel-class"></a>Klasa CMFCRibbonMainPanel
Implementuje panelu wstążki wyświetlanym po kliknięciu [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCRibbonMainPanel : public CMFCRibbonPanel  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CMFCRibbonMainPanel::CMFCRibbonMainPanel`|Domyślny konstruktor.|  
|`CMFCRibbonMainPanel::~CMFCRibbonMainPanel`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCRibbonMainPanel::Add](#add)|Dodaje element wstążki do lewego okienka panel przycisku aplikacji. (Przesłania [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).)|  
|[CMFCRibbonMainPanel::AddRecentFilesList](#addrecentfileslist)|Dodaje ciąg tekstowy do menu listy ostatnich plików.|  
|[CMFCRibbonMainPanel::AddToBottom](#addtobottom)|Dodaje element wstążki w dolnym okienku panelu aplikacji wstążki.|  
|[CMFCRibbonMainPanel::AddToRight](#addtoright)|Dodaje element wstążki do prawego okienka panel przycisku aplikacji.|  
|`CMFCRibbonMainPanel::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|[CMFCRibbonMainPanel::GetCommandsFrame](#getcommandsframe)|Zwraca prostokąt, który reprezentuje obszar panelu głównego wstążki.|  
|`CMFCRibbonMainPanel::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
  
## <a name="remarks"></a>Uwagi  
 Wyświetla w ramach `CMFCRibbonMainPanel` po otwarciu panel aplikacji. Ten przewodnik zawiera trzy sekcje:  
  
-   W okienku po lewej stronie zawiera polecenia powiązany z plikami, takie jak **Otwórz**, **zapisać**, **drukowania**, i **Zamknij**. Aby dodać polecenia do w tym okienku, należy wywołać [CMFCRibbonMainPanel::Add](#add).  
  
-   Prawe okienko zawiera opcje, które modyfikują polecenie kliknij w okienku po lewej stronie. Na przykład, jeśli klikniesz przycisk **Zapisz jako** w lewym okienku okienku po prawej stronie można wyświetlić listę typów plików. Aby dodać element do w tym okienku, należy wywołać [CMFCRibbonMainPanel::AddToRight](#addtoright).  
  
-   Dolne okienko zawiera przyciski, który pozwala na zmianę ustawienia aplikacji i zamknąć program. Aby dodać element do w tym okienku, należy wywołać [CMFCRibbonMainPanel::AddToBottom](#addtobottom).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)  
  
 [CMFCRibbonMainPanel](../../mfc/reference/cmfcribbonmainpanel-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxRibbonMainPanel.h  
  
##  <a name="add"></a>CMFCRibbonMainPanel::Add  
 Dodaje element wstążki do lewego okienka panel przycisku aplikacji.  
  
```  
virtual void Add(CMFCRibbonBaseElement* pElem);
```  
  
### <a name="parameters"></a>Parametry  
 [in] [out]`pElem`  
 Wskaźnik do elementu wstążki do dodania do głównego panelu.  
  
### <a name="remarks"></a>Uwagi  
 Dodaje element wstążki do panelu. Elementy dodane za pomocą tej metody będą znajdować się w lewej kolumnie główny panel.  
  
##  <a name="addrecentfileslist"></a>CMFCRibbonMainPanel::AddRecentFilesList  
 Dodaje ciąg tekstowy do menu listy ostatnich plików.  
  
```  
void AddRecentFilesList(
    LPCTSTR lpszLabel,  
    int nWidth = 300);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszLabel`  
 Określa ciąg, aby dodać do listy ostatnio używanych plików.  
  
 `nWidth`  
 Określa szerokość w pikselach, ostatnie panelu listy plików.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="addtobottom"></a>CMFCRibbonMainPanel::AddToBottom  
 Dodaje element wstążki w dolnym okienku panelu aplikacji wstążki.  
  
```  
void AddToBottom(CMFCRibbonMainPanelButton* pElem);
```  
  
### <a name="parameters"></a>Parametry  
 [in] [out]`pElem`  
 Wskaźnik do elementu wstążki do dodania do dołu główny panel.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="addtoright"></a>CMFCRibbonMainPanel::AddToRight  
 Dodaje element wstążki do prawego okienka panel przycisku aplikacji.  
  
```  
void AddToRight(
    CMFCRibbonBaseElement* pElem,  
    int nWidth = 300);
```  
  
### <a name="parameters"></a>Parametry  
 `pElem`  
 Wskaźnik do elementu wstążki do dodania do prawego panelu głównego.  
  
 `nWidth`  
 Określa szerokość w pikselach, prawym panelu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja służy do dodania elementu wstążki do na prawym panelu. Prawy panel zwykle zawiera listy ostatnio używanych plików, ale można dodać wstążki element w tym miejscu.  
  
##  <a name="getcommandsframe"></a>CMFCRibbonMainPanel::GetCommandsFrame  
 Zwraca prostokąt, który reprezentuje obszar panelu głównego wstążki.  
  
```  
CRect GetCommandsFrame() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Prostokąt, który reprezentuje obszar panelu głównego wstążki.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)
