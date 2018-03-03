---
title: Klasa CMFCAcceleratorKeyAssignCtrl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::GetAccel
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsFocused
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsKeyDefined
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::ResetKey
dev_langs:
- C++
helpviewer_keywords:
- CMFCAcceleratorKeyAssignCtrl [MFC], CMFCAcceleratorKeyAssignCtrl
- CMFCAcceleratorKeyAssignCtrl [MFC], GetAccel
- CMFCAcceleratorKeyAssignCtrl [MFC], IsFocused
- CMFCAcceleratorKeyAssignCtrl [MFC], IsKeyDefined
- CMFCAcceleratorKeyAssignCtrl [MFC], PreTranslateMessage
- CMFCAcceleratorKeyAssignCtrl [MFC], ResetKey
ms.assetid: 89fb8e62-596e-4e71-8c9a-32740347aaab
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1aacd22af0b2e0e14a3c1203a42e067b1f339c71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcacceleratorkeyassignctrl-class"></a>Klasa CMFCAcceleratorKeyAssignCtrl
`CMFCAcceleratorKeyAssignCtrl` Rozszerza klasy [klasy CEdit](../../mfc/reference/cedit-class.md) do obsługi dodatkowych systemu przycisków ALT, sterowania i SHIFT.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCAcceleratorKeyAssignCtrl : public CEdit  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl](#cmfcacceleratorkeyassignctrl)|Konstruuje `CMFCAcceleratorKeyAssignCtrl` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel)|Pobiera `ACCEL` struktury dla wciśnięty klawisz skrótu `CMFCAcceleratorKeyAssignCtrl` obiektu.|  
|[CMFCAcceleratorKeyAssignCtrl::IsFocused](#isfocused)||  
|[CMFCAcceleratorKeyAssignCtrl::IsKeyDefined](#iskeydefined)|Określa, czy została zdefiniowana klawisza skrótu.|  
|[CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage](#pretranslatemessage)|Używane przez klasę [CWinApp](../../mfc/reference/cwinapp-class.md) tłumaczenie komunikaty okna przed wysłaniem do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) i [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkcje systemu Windows. (Przesłania [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
|[CMFCAcceleratorKeyAssignCtrl::ResetKey](#resetkey)|Resetuje klawisz skrótu.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa rozszerza funkcjonalność `CEdit` klasy dzięki obsłudze skróty, nazywane również klawiszy skrótów. `CMFCAcceleratorKeyAssignCtrl` Klasy działa jako [CEdit klasy](../../mfc/reference/cedit-class.md) , a także rozpoznają przyciski systemu.  
  
 Ta klasa mapuje kombinacje klawiszy skrótu fizycznych wartości typu string. Załóżmy na przykład, kombinację klawiszy ALT + B jest mapowany na ciąg "Alt + B". Gdy użytkownik naciśnie tej kombinacji klawiszy w `CMFCAcceleratorKeyAssignCtrl` obiekt "Alt + B" jest wyświetlana użytkownikowi. Aby uzyskać więcej informacji na temat mapowanie między klawiszy skrótów i formatu ciągu, zobacz [CMFCAcceleratorKey klasy](../../mfc/reference/cmfcacceleratorkey-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia `CMFCAcceleratorKeyAssignCtrl` obiektu i używać jej `ResetKey` metoda klawisz skrótu.  
  
 [!code-cpp[NVC_MFC_RibbonApp#31](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkeyassignctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 `CMFCAcceleratorKeyAssignCtrl`   
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxacceleratorkeyassignctrl.h  
  
##  <a name="cmfcacceleratorkeyassignctrl"></a>CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl  
 Konstruuje [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) obiektu.  
  
```  
CMFCAcceleratorKeyAssignCtrl();
```  
  
##  <a name="getaccel"></a>CMFCAcceleratorKeyAssignCtrl::GetAccel  
 Pobiera `ACCEL` struktury dla wciśnięty klawisz skrótu [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) obiektu.  
  
```  
ACCEL const* GetAccel() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `ACCEL` Struktury, która opisuje klawisz skrótu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja służy do pobierania `ACCEL` struktury klawisz skrótu, który użytkownik wprowadził do Twojej `CMFCAcceleratorKeyAssignCtrl` obiektu.  
  
##  <a name="isfocused"></a>CMFCAcceleratorKeyAssignCtrl::IsFocused  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsFocused() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="iskeydefined"></a>CMFCAcceleratorKeyAssignCtrl::IsKeyDefined  
 Określa, czy klawisz skrótu został zdefiniowany w [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) obiektu.  
  
```  
BOOL IsKeyDefined() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli użytkownik nacisnął już prawidłową kombinację klucze, które definiują klawisza skrótu. w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja służy do określenia, czy użytkownik wprowadził nieprawidłowy skrót klucza w Twojej `CMFCAcceleratorKeyAssignCtrl` obiektu. Jeśli istnieje klawisz skrótu, możesz użyć [CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel) metodę, aby uzyskać `ACCEL` struktury skojarzone z tym klawisz skrótu.  
  
##  <a name="pretranslatemessage"></a>CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pMsg`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="resetkey"></a>CMFCAcceleratorKeyAssignCtrl::ResetKey  
 Resetuje klawisz skrótu.  
  
```  
void ResetKey();
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja Usuwa tekst kontrolki edycji. W tym wszelkie klawiszy skrótów, które użytkownik kliknął przycisk.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md)
