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
ms.openlocfilehash: eddce134c3cda27e57a6a20d709bc4eab08d6e80
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37849018"
---
# <a name="cmfcribbonapplicationbutton-class"></a>Klasa CMFCRibbonApplicationButton
Implementacja specjalny przycisk znajdujący się w lewym górnym rogu okna aplikacji. Po kliknięciu przycisku powoduje otwarcie menu, które zwykle zawiera wspólne **pliku** poleceń, takich jak **Otwórz**, **Zapisz**, i **zakończenia**.  
  
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
|`CMFCRibbonApplicationButton::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|  
|[CMFCRibbonApplicationButton::SetImage](#setimage)|Przypisuje obrazu przycisk wstążki w aplikacji.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak korzystać z różnych metod w `CMFCRibbonApplicationButton` klasy. W przykładzie pokazano, jak przypisać obrazu do przycisku aplikacja i jak ustawić jej etykietki narzędzia. Ten fragment kodu jest częścią [Rysowanie Client sample](../../visual-cpp-samples.md).  
  
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
 *uiBmpResID*  
 Identyfikator zasobu obrazu do wyświetlania na przycisku aplikacji.  
  
 *hBmp*  
 Dojście do mapy bitowej do wyświetlenia na przycisku aplikacji.  
  
### <a name="remarks"></a>Uwagi  
 Przycisk aplikacji wstążki jest specjalny przycisk znajdujący się w lewym górnym rogu okna aplikacji. Gdy użytkownik kliknie ten przycisk, aplikacja zostanie otwarte menu, które zwykle zawiera wspólne **pliku** polecenia, takie jak **Otwórz**, **Zapisz**, i **zakończenia**.  
  
##  <a name="setimage"></a>  CMFCRibbonApplicationButton::SetImage  
 Przypisuje obrazu przycisku aplikacji.  
  
```  
void SetImage(UINT uiBmpResID);  
void SetImage(HBITMAP hBmp);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *uiBmpResID*  
 Identyfikator zasobu obrazu do wyświetlania na przycisku aplikacji.  
  
 [in] *hBmp*  
 Dojście do mapy bitowej do wyświetlenia na przycisku aplikacji.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia przypisywanie nowego obrazu do przycisk wstążki w aplikacji, po utworzeniu przycisku. Przycisk aplikacji znajduje się w lewym górnym rogu okna aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)
