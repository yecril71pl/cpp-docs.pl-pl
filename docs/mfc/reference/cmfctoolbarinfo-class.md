---
title: Klasa CMFCToolBarInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo::m_uiColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuResID
dev_langs: C++
helpviewer_keywords:
- CMFCToolBarInfo [MFC], m_uiColdResID
- CMFCToolBarInfo [MFC], m_uiDisabledResID
- CMFCToolBarInfo [MFC], m_uiHotResID
- CMFCToolBarInfo [MFC], m_uiLargeColdResID
- CMFCToolBarInfo [MFC], m_uiLargeDisabledResID
- CMFCToolBarInfo [MFC], m_uiLargeHotResID
- CMFCToolBarInfo [MFC], m_uiMenuDisabledResID
- CMFCToolBarInfo [MFC], m_uiMenuResID
ms.assetid: 6dc84482-eaaa-491f-aa5d-dd7a57886b46
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 817e710546a695addaa6cae0e266bd1ff1ddc701
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cmfctoolbarinfo-class"></a>Klasa CMFCToolBarInfo
Zawiera identyfikatorów obrazów paska narzędzi w zależności od różnych stanów zasobów. `CMFCToolBarInfo`Klasa pomocy, który jest używany jako parametr typu jest [CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCToolBarInfo  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCToolBarInfo::m_uiColdResID](#m_uicoldresid)|Identyfikator zasobu mapy bitowej narzędzi, która zawiera obrazy regularne paska narzędzi (zimny).|  
|[CMFCToolBarInfo::m_uiDisabledResID](#m_uidisabledresid)|Identyfikator zasobu mapy bitowej narzędzi, który zawiera wyłączenia narzędzi obrazów.|  
|[CMFCToolBarInfo::m_uiHotResID](#m_uihotresid)|Identyfikator zasobu mapy bitowej narzędzi, która zawiera obrazy wybranych narzędzi (gorących).|  
|[CMFCToolBarInfo::m_uiLargeColdResID](#m_uilargecoldresid)|Identyfikator zasobu mapy bitowej narzędzi, która zawiera obrazy dużych, regularne paska narzędzi.|  
|[CMFCToolBarInfo::m_uiLargeDisabledResID](#m_uilargedisabledresid)|Identyfikator zasobu mapy bitowej narzędzi, która zawiera dużą, wyłączona obrazy pasków narzędzi.|  
|[CMFCToolBarInfo::m_uiLargeHotResID](#m_uilargehotresid)|Identyfikator zasobu mapy bitowej narzędzi, która zawiera dużą, wybrane obrazy pasków narzędzi.|  
|[CMFCToolBarInfo::m_uiMenuDisabledResID](#m_uimenudisabledresid)|Identyfikator zasobu mapy bitowej narzędzi, który zawiera wyłączenia menu obrazów.|  
|[CMFCToolBarInfo::m_uiMenuResID](#m_uimenuresid)|Identyfikator zasobu mapy bitowej narzędzi, która zawiera menu obrazów.|  
  
## <a name="remarks"></a>Uwagi  
 Mapy bitowej narzędzi Pełny składa się z małych narzędzi obrazów (przyciski) o stałym rozmiarze. Każdy identyfikator zasobu, który jest przechowywany w `CMFCToolBarInfo` obiekt jest mapą bitową zawierający pełny zestaw narzędzi obrazów w pojedynczego stanu (na przykład, wybrane, wyłączona dużych lub obrazów menu).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxtoolbar.h  
  
##  <a name="m_uicoldresid"></a>CMFCToolBarInfo::m_uiColdResID  
 Określa identyfikator zasobu dla wszystkich regularne obrazy dla przycisków paska narzędzi.  
  
```  
UINT m_uiColdResID;  
```  
  
##  <a name="m_uidisabledresid"></a>CMFCToolBarInfo::m_uiDisabledResID  
 Określa identyfikator zasobu dla obrazów niedostępny przycisku paska narzędzi.  
  
```  
UINT m_uiDisabledResID;  
```  
  
##  <a name="m_uihotresid"></a>CMFCToolBarInfo::m_uiHotResID  
 Określa identyfikator zasobu dla wszystkich obrazów podświetlony przycisk paska narzędzi.  
  
```  
UINT m_uiHotResID  
```  
  
##  <a name="m_uilargecoldresid"></a>CMFCToolBarInfo::m_uiLargeColdResID  
 Określa identyfikator zasobu dla wszystkich dużych regularne obrazy dla przycisków paska narzędzi.  
  
```  
UINT m_uiLargeColdResID  
```  
  
##  <a name="m_uilargedisabledresid"></a>CMFCToolBarInfo::m_uiLargeDisabledResID  
 Określa identyfikator zasobu dla wszystkich dużych wyłączone obrazy dla przycisków paska narzędzi.  
  
```  
UINT m_uiLargeDisabledResID;  
```  
  
##  <a name="m_uilargehotresid"></a>CMFCToolBarInfo::m_uiLargeHotResID  
 Określa identyfikator zasobu dużych obrazów wyróżnione paska narzędzi.  
  
```  
UINT m_uiLargeHotResID;  
```  
  
##  <a name="m_uimenudisabledresid"></a>CMFCToolBarInfo::m_uiMenuDisabledResID  
 Określa identyfikator zasobu dla polecenia — niedostępna obrazów paska narzędzi.  
  
```  
UINT m_uiMenuDisabledResID;  
```  
  
##  <a name="m_uimenuresid"></a>CMFCToolBarInfo::m_uiMenuResID  
 Określa identyfikator zasobu do wszystkich obrazów elementów menu regularne paska narzędzi.  
  
```  
UINT m_uiMenuResID;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)
