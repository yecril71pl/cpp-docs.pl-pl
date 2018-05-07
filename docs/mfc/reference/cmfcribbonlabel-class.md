---
title: Klasa CMFCRibbonLabel | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::SetACCData
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonLabel [MFC], CMFCRibbonLabel
- CMFCRibbonLabel [MFC], SetACCData
ms.assetid: 0346c891-83bf-4f20-b8a1-c84cf2aadced
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fcbc552560325e844cf0812a3002088f829d6c60
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcribbonlabel-class"></a>Klasa CMFCRibbonLabel
Implementuje etykietę tekstową nieaktywne dla wstążki.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCRibbonLabel : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCRibbonLabel::CMFCRibbonLabel](#cmfcribbonlabel)|Tworzy i inicjuje `CMFCRibbonLabel` obiektu z określonym tekstem.|  
|`CMFCRibbonLabel::~CMFCRibbonLabel`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CMFCRibbonLabel::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|`CMFCRibbonLabel::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
|[CMFCRibbonLabel::SetACCData](#setaccdata)|Określa dane ułatwień dostępu dla bieżącego elementu label wstążki. (Przesłania [CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|  
  
### <a name="remarks"></a>Uwagi  
 Po utworzeniu etykiety wstążki, dodaj go do panelu wywołując [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).  
  
 Nie można dodać etykietę wstążki do paska narzędzi Szybki dostęp.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxRibbonLabel.h  
  
##  <a name="cmfcribbonlabel"></a>  CMFCRibbonLabel::CMFCRibbonLabel  
 Tworzy i inicjuje [CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md) obiekt, który wyświetla określony tekst.  
  
```  
CMFCRibbonLabel(
    LPCTSTR lpszText,  
    BOOL bIsMultiLine = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `lpszText`  
 Tekst wyświetlany w etykiecie.  
  
 [in] `bIsMultiLine`  
 `TRUE` Aby określić, czy etykieta jest etykieta wielowierszowego; w przeciwnym razie `FALSE`.  
  
##  <a name="setaccdata"></a>  CMFCRibbonLabel::SetACCData  
 Określa dane ułatwień dostępu dla bieżącego elementu label wstążki.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pParent`  
 Reprezentuje okno nadrzędne bieżącej etykiety wstążki.  
  
 [out] `data`  
 Obiekt typu `CAccessibilityData` który jest wypełniane przy użyciu danych dostępności bieżącej etykiety wstążki.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli `data` parametr został pomyślnie wypełnione przy użyciu danych dostępności bieżącej etykiety wstążki; w przeciwnym razie `FALSE`.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)
