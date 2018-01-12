---
title: Klasa CMFCAcceleratorKey | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::Format
- AFXACCELERATORKEY/CMFCAcceleratorKey::SetAccelerator
dev_langs: C++
helpviewer_keywords:
- CMFCAcceleratorKey [MFC], CMFCAcceleratorKey
- CMFCAcceleratorKey [MFC], Format
- CMFCAcceleratorKey [MFC], SetAccelerator
ms.assetid: d140fbf7-23db-45ea-a63e-414a5ec7b3d5
caps.latest.revision: "36"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3303be9f37749436d140028cd5fa45cd4454c8c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcacceleratorkey-class"></a>Klasa CMFCAcceleratorKey
Klasa pomocy, która implementuje wirtualnego mapowania klucza i formatowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCAcceleratorKey : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCAcceleratorKey::CMFCAcceleratorKey](#cmfcacceleratorkey)|Konstruuje `CMFCAcceleratorKey` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCAcceleratorKey::Format](#format)|Wykonuje translację struktury AKCELERACJA do jego wizualnej reprezentacji.|  
|[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)|Ustawia klawisz skrótu `CMFCAcceleratorKey` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Klawisze skrótów są również znane jako klawiszy skrótów. Jeśli chcesz wyświetlić skróty klawiaturowe, które użytkownik wprowadza, [klasy CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) mapy skróty klawiaturowe, takie jak Alt + Shift + S, aby niestandardowym formacie tekstowym, takich jak "Alt + Shift + S". Każdy `CMFCAcceleratorKey` obiekt mapuje klawisza skrótu jednego do formatu tekstowego.  
  
 Aby uzyskać więcej informacji o sposobie używania klawiszy skrótów i tabele akceleratora, zobacz [CKeyboardManager klasy](../../mfc/reference/ckeyboardmanager-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia `CMFCAcceleratorKey` obiektu i sposobu użycia jej `Format` metody.  
  
 [!code-cpp[NVC_MFC_RibbonApp#30](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkey-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMFCAcceleratorKey`   
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxacceleratorkey.h  
  
##  <a name="cmfcacceleratorkey"></a>CMFCAcceleratorKey::CMFCAcceleratorKey  
 Konstruuje [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) obiektu.  
  
```  
CMFCAcceleratorKey();  
CMFCAcceleratorKey(LPACCEL lpAccel);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpAccel`  
 Wskaźnik do klawisza skrótu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli nie podasz klawisz skrótu podczas tworzenia `CMFCAccleratorKey`, użyj [CMFCAcceleratorKey::SetAccelerator](#setaccelerator) do kojarzenia klawisza skrótu z Twojej `CMFCAcceleratorKey` obiektu.  
  
##  <a name="format"></a>CMFCAcceleratorKey::Format  
 Wykonuje translację struktury AKCELERACJA wartość ciągu skojarzone.  
  
```  
void Format(CString& str) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`str`  
 Odwołanie do `CString` obiektu, którego metoda zapisuje klawisz skrótu przetłumaczonego.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda pobiera ciąg formatu klawisz skrótu skojarzony. Można ustawić formatu ciągu [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) przy użyciu konstruktora lub metody [CMFCAcceleratorKey::SetAccelerator](#setaccelerator).  
  
##  <a name="setaccelerator"></a>CMFCAcceleratorKey::SetAccelerator  
 Ustawia klawisz skrótu [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) obiektu.  
  
```  
void SetAccelerator(LPACCEL lpAccel);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpAccel`  
 Wskaźnik do klawisza skrótu.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, aby ustawić klawisz skrótu `CMFCAcceleratorKey` Jeśli nie podano klawisz skrótu podczas tworzenia `CMFCAcceleratorKey`.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)
