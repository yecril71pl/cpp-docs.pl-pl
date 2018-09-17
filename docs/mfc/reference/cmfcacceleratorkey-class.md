---
title: Klasa CMFCAcceleratorKey | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::Format
- AFXACCELERATORKEY/CMFCAcceleratorKey::SetAccelerator
dev_langs:
- C++
helpviewer_keywords:
- CMFCAcceleratorKey [MFC], CMFCAcceleratorKey
- CMFCAcceleratorKey [MFC], Format
- CMFCAcceleratorKey [MFC], SetAccelerator
ms.assetid: d140fbf7-23db-45ea-a63e-414a5ec7b3d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7d87b7a2a76ea73989a9ab7dd845666625e91aa0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711597"
---
# <a name="cmfcacceleratorkey-class"></a>Klasa CMFCAcceleratorKey
Klasa pomocnika, która implementuje wirtualne mapowanie i formatowanie kluczy.  
  
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
|[CMFCAcceleratorKey::Format](#format)|Wykonuje translację strukturę AKCELERACJA jego wizualnej reprezentacji.|  
|[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)|Ustawia klawisz skrótu `CMFCAcceleratorKey` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Klawisze skrótów są również nazywane klawiszy skrótów. Jeśli chcesz wyświetlić skróty klawiaturowe, które użytkownik wprowadza, [klasa CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) mapy skróty klawiaturowe, takich jak klawisze Alt + Shift + S do formatu niestandardowego tekstu, takie jak "Alt + Shift + S". Każdy `CMFCAcceleratorKey` obiektu mapy klawisza pojedynczego skrótu do formatu tekstowego.  
  
 Aby uzyskać więcej informacji o tym, jak używać klawiszy skrótów i tabel akceleratora, zobacz [klasa CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia `CMFCAcceleratorKey` obiektu i sposobu używania jej `Format` metody.  
  
 [!code-cpp[NVC_MFC_RibbonApp#30](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkey-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMFCAcceleratorKey`   
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxacceleratorkey.h  
  
##  <a name="cmfcacceleratorkey"></a>  CMFCAcceleratorKey::CMFCAcceleratorKey  
 Konstruuje [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) obiektu.  
  
```  
CMFCAcceleratorKey();  
CMFCAcceleratorKey(LPACCEL lpAccel);
```  
  
### <a name="parameters"></a>Parametry  
*lpAccel*<br/>
[in] Wskaźnik do klawisza skrótu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli nie podasz klawisz skrótu podczas tworzenia `CMFCAccleratorKey`, użyj [CMFCAcceleratorKey::SetAccelerator](#setaccelerator) metoda powiązania klawisza skrótu z Twojej `CMFCAcceleratorKey` obiektu.  
  
##  <a name="format"></a>  CMFCAcceleratorKey::Format  
 Wykonuje translację struktury AKCELERACJA do wartości ciągu skojarzone.  
  
```  
void Format(CString& str) const;  
```  
  
### <a name="parameters"></a>Parametry  
*str*<br/>
[out] Odwołanie do `CString` obiektu, którego metoda zapisuje klawisza skrótu tłumaczenia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda pobiera format ciągu klawisza skrótu skojarzone. Można ustawić format ciągu [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) przy użyciu konstruktora lub metody [CMFCAcceleratorKey::SetAccelerator](#setaccelerator).  
  
##  <a name="setaccelerator"></a>  CMFCAcceleratorKey::SetAccelerator  
 Ustawia klawisz skrótu [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) obiektu.  
  
```  
void SetAccelerator(LPACCEL lpAccel);
```  
  
### <a name="parameters"></a>Parametry  
*lpAccel*<br/>
[in] Wskaźnik do klawisza skrótu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia ustawianie klawisz skrótu `CMFCAcceleratorKey` Jeśli nie podano klawisz skrótu podczas tworzenia `CMFCAcceleratorKey`.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)
