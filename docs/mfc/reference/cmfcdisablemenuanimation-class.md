---
title: Klasa CMFCDisableMenuAnimation | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation::Restore
dev_langs:
- C++
helpviewer_keywords:
- CMFCDisableMenuAnimation [MFC], Restore
ms.assetid: c6eb07da-c382-43d6-8028-007f2320e50e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3a7a2449fe65a0b17bf770ea2bfb8f3fe750cba0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcdisablemenuanimation-class"></a>Klasa CMFCDisableMenuAnimation
Wyłącza menu podręczne animacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCDisableMenuAnimation  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|Konstruuje `CMFCDisableMenuAnimation` obiektu.|  
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|[CMFCDisableMenuAnimation::Restore](#restore)|Przywraca poprzednie animacji, używany w ramach do wyświetlenia menu podręcznego.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|Nazwa|Opis|  
|`CMFCDisableMenuAnimation::m_animType`|Przechowuje poprzedni typ animacji menu podręczne.|  
  
### <a name="remarks"></a>Uwagi  
 Klasa pomocnika używana do tymczasowego wyłączenia animacji menu podręcznego (na przykład podczas przetwarzania polecenia za pomocą klawiatury lub myszy).  
  
 A `CMFCDisableMenuAnimation` obiektu wyłącza menu podręczne animacji przez jego okres istnienia. Konstruktor przechowuje bieżącego typu animacji menu podręcznego w `m_animType` pola i ustawia typ bieżącego animacji `CMFCPopupMenu::NO_ANIMATION`. Destruktor przywraca poprzedni typ animacji.  
  
 Można utworzyć `CMFCDisableMenuAnimation` obiektu na stosie, aby wyłączyć menu podręczne animacji w jednej funkcji. Jeśli chcesz wyłączyć animacji menu podręcznego pomiędzy funkcjami, Utwórz `CMFCDisableMenuAnimation` obiektów na stercie, a następnie usuń ją, jeśli chcesz przywrócić animacji menu podręczne.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie stosu można tymczasowo wyłączyć menu animacji.  
  
 [!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CMFCDisableMenuAnimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxpopupmenu.h  
  
##  <a name="restore"></a>  CMFCDisableMenuAnimation::Restore  
 Przywraca poprzednie animacji, używany w ramach do wyświetlenia menu podręcznego.  
  
```  
void Restore ();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez `CMFCDisableMenuAnimation` destruktora do przywrócenia poprzedniej animacji, używany w ramach do wyświetlenia menu podręcznego.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)
