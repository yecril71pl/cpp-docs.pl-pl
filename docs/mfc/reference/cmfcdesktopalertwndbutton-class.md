---
title: Klasa CMFCDesktopAlertWndButton | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCaptionButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCloseButton
dev_langs: C++
helpviewer_keywords:
- CMFCDesktopAlertWndButton [MFC], IsCaptionButton
- CMFCDesktopAlertWndButton [MFC], IsCloseButton
ms.assetid: df39a0c8-0c39-4ab0-8c64-78c5b2c4ecaf
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ae1153546851e6a34c14dacd33db04091de24557
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcdesktopalertwndbutton-class"></a>Klasa CMFCDesktopAlertWndButton
Umożliwia przycisków, które mają zostać dodane do pulpitu dialogowego alertu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCDesktopAlertWndButton : public CMFCButton  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|`CMFCDesktopAlertWndButton::CMFCDesktopAlertWndButton`|Domyślny konstruktor.|  
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|[CMFCDesktopAlertWndButton::IsCaptionButton](#iscaptionbutton)|Określa, czy przycisk jest wyświetlany w obszarze Podpis okna dialogowego alertu.|  
|[CMFCDesktopAlertWndButton::IsCloseButton](#isclosebutton)|Określa, czy przycisk zamknięcie okna dialogowego alertu.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|Nazwa|Opis|  
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|Wartość logiczna określająca, czy przycisk jest wyświetlany w obszarze Podpis okna dialogowego alertu.|  
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|Wartość logiczna określająca, czy przycisk zamknięcie okna dialogowego alertu.|  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ustawia konstruktora `m_bIsCaptionButton` i `m_bIsCloseButton` elementy członkowskie danych do `FALSE`. Element nadrzędny `CMFCDesktopAlertDialog` obiekt zestawy `m_bIsCaptionButton` do `TRUE` Jeśli przycisku znajduje się w obszarze Podpis okna dialogowego alertu. `CMFCDesktopAlertDialog` Tworzy klasy `CMFCDesktopAlertWndButton` obiekt, który służy jako przycisku, który powoduje zamknięcie okna dialogowego alertu polu i ustawia `m_bIsCloseButton` do `TRUE`.  
  
 Dodaj `CMFCDesktopAlertWndButton` obiekty do `CMFCDesktopAlertDialog` obiektów, jak dowolnego przycisku. Aby uzyskać więcej informacji na temat `CMFCDesktopAlertDialog`, zobacz [CMFCDesktopAlertDialog klasy](../../mfc/reference/cmfcdesktopalertdialog-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia `SetImage` metoda `CMFCDesktopAlertWndButton` klasy. Następujący fragment kodu jest częścią [próbka Demo alertu pulpitu](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#4](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_1.h)]  
[!code-cpp[NVC_MFC_DesktopAlertDemo#5](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCDesktopAlertWndButton](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdesktopalertwnd.h  
  
##  <a name="iscaptionbutton"></a>CMFCDesktopAlertWndButton::IsCaptionButton  
 Określa, czy przycisk jest wyświetlany w obszarze Podpis okna dialogowego alertu.  
  
```  
BOOL IsCaptionButton() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli ten przycisk jest wyświetlany w obszarze Podpis okna dialogowego alertu; w przeciwnym razie wartość 0.  
  
##  <a name="isclosebutton"></a>CMFCDesktopAlertWndButton::IsCloseButton  
 Określa, czy przycisk zamknięcie okna dialogowego alertu.  
  
```  
BOOL IsCloseButton() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli przycisku zamknięcie okna dialogowego alertu; w przeciwnym razie wartość 0.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md)
