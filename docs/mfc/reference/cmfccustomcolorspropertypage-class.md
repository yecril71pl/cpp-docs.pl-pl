---
title: Klasa CMFCCustomColorsPropertyPage | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage::Setup
dev_langs:
- C++
helpviewer_keywords:
- CMFCCustomColorsPropertyPage [MFC], Setup
ms.assetid: 46a45ba2-1fda-440d-8018-d4dcd44f5816
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8123db8e4a8dfba94e469881af8fbb2ecb40e2a0
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37041984"
---
# <a name="cmfccustomcolorspropertypage-class"></a>Klasa CMFCCustomColorsPropertyPage
Reprezentuje stronę właściwości, który można wybrać kolory niestandardowe w oknie dialogowym koloru.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCCustomColorsPropertyPage : public CPropertyPage  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|`CMFCCustomColorsPropertyPage::CMFCCustomColorsPropertyPage`|Domyślny konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|`CMFCCustomColorsPropertyPage::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|`CMFCCustomColorsPropertyPage::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
|[CMFCCustomColorsPropertyPage::Setup](#setup)|Ustawia kolor części strony właściwości.|  
  
### <a name="remarks"></a>Uwagi  
 `CMFCColorDialog` Klasa korzysta z tej klasy do wyświetlenia strony właściwości niestandardowego koloru. Aby uzyskać więcej informacji na temat `CMFCColorDialog`, zobacz [CMFCColorDialog klasy](../../mfc/reference/cmfccolordialog-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia `CMFCCustomColorsPropertyPage` obiektu i ustawić składniki kolor strony właściwości.  
  
 [!code-cpp[NVC_MFC_RibbonApp#35](../../mfc/reference/codesnippet/cpp/cmfccustomcolorspropertypage-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCCustomColorsPropertyPage](../../mfc/reference/cmfccustomcolorspropertypage-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcustomcolorspropertypage.h  
  
##  <a name="setup"></a>  CMFCCustomColorsPropertyPage::Setup  
 Ustawia kolor części strony właściwości.  
  
```  
void Setup(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in] *R*|Czerwony składnik wartości RGB.|  
|[in] *G*|Zielony składnik wartości RGB.|  
|[in] *B*|Niebieski składnik wartości RGB.|  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda aktualizacji bieżącego RGB i skojarzone HLS (hue, jasność i nasycenie) wartości kolorów stronę właściwości. [CMFCColorDialog::SetPageTwo](../../mfc/reference/cmfccolordialog-class.md#setpagetwo) metoda wywołuje tę metodę w ramach inicjuje okno dialogowe kolorów lub naciśnięciu lewego przycisku myszy. Aby uzyskać więcej informacji na temat `CMFCColorDialog`, zobacz [CMFCColorDialog klasy](../../mfc/reference/cmfccolordialog-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)   
 [Klasa CMFCStandardColorsPropertyPage](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)
