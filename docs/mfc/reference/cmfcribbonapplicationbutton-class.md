---
title: Klasa CMFCRibbonApplicationButton | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::SetImage
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonApplicationButton [MFC], CMFCRibbonApplicationButton
- CMFCRibbonApplicationButton [MFC], SetImage
ms.assetid: beb81757-fabd-4641-9130-876ba8505b78
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b2b2e8adccd77862b445d7e91df0b808967a31d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcribbonapplicationbutton-class"></a>Klasa CMFCRibbonApplicationButton
Implementuje przycisk specjalne znajduje się w lewym górnym rogu okna aplikacji. Po kliknięciu przycisku otwiera menu, które zwykle zawiera typowe **pliku** poleceń, takich jak **Otwórz**, **zapisać**, i **zakończenia**.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCRibbonApplicationButton : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCRibbonApplicationButton::CMFCRibbonApplicationButton](#cmfcribbonapplicationbutton)|Tworzy i inicjuje `CMFCRibbonApplicationButton` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CMFCRibbonApplicationButton::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|`CMFCRibbonApplicationButton::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
|[CMFCRibbonApplicationButton::SetImage](#setimage)|Przypisuje obrazu na Wstążce przycisk aplikacji.|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia różnych metod w `CMFCRibbonApplicationButton` klasy. W przykładzie pokazano, jak przypisać obrazu przycisku aplikacji i jak ustawić jej etykietka narzędzia. Następujący fragment kodu jest częścią [rysowania klienta — przykład](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient#4](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_1.h)]  
[!code-cpp[NVC_MFC_DrawClient#5](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxRibbonBar.h  
  
##  <a name="cmfcribbonapplicationbutton"></a>  CMFCRibbonApplicationButton::CMFCRibbonApplicationButton  
 Tworzy i inicjuje [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md) obiektu.  
  
```  
CMFCRibbonApplicationButton();  
CMFCRibbonApplicationButton(UINT uiBmpResID);  
  CMFCRibbonApplicationButton(HBITMAP hBmp);
```  
  
### <a name="parameters"></a>Parametry  
 `uiBmpResID`  
 Identyfikator zasobu obrazu do wyświetlania na przycisku aplikacji.  
  
 `hBmp`  
 Dojście do mapy bitowej do wyświetlenia na przycisku aplikacji.  
  
### <a name="remarks"></a>Uwagi  
 Przycisk aplikacji wstążki jest specjalne przycisku, który znajduje się w lewym górnym rogu okna aplikacji. Po kliknięciu tego przycisku aplikacja otwiera menu, które zwykle zawiera typowe **pliku** polecenia, takie jak **Otwórz**, **zapisać**, i **zakończenia**.  
  
##  <a name="setimage"></a>  CMFCRibbonApplicationButton::SetImage  
 Przypisuje obrazu przycisku aplikacji.  
  
```  
void SetImage(UINT uiBmpResID);  
void SetImage(HBITMAP hBmp);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `uiBmpResID`  
 Identyfikator zasobu obrazu do wyświetlania na przycisku aplikacji.  
  
 [in] `hBmp`  
 Dojście do mapy bitowej do wyświetlenia na przycisku aplikacji.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody można przypisać nowy obraz na Wstążce przycisk aplikacji po utworzeniu przycisku. Przycisk aplikacji znajduje się w lewym górnym rogu okna aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)
