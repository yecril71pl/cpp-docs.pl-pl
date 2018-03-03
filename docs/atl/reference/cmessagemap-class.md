---
title: Klasa CMessageMap | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMessageMap
- ATLWIN/ATL::CMessageMap
- ATLWIN/ATL::CMessageMap::ProcessWindowMessage
dev_langs:
- C++
helpviewer_keywords:
- CMessageMap class
- message maps, ATL
- ATL, message handlers
ms.assetid: 1f97bc16-a8a0-4cf0-b90f-1778813a5c8e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 04aff6922358048fcbd330096eb26a412cdb75ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmessagemap-class"></a>Klasa CMessageMap
Ta klasa umożliwia mapy wiadomości obiektu jako dostępu przez inny obiekt.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class ATL_NO_VTABLE CMessageMap
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMessageMap::ProcessWindowMessage](#processwindowmessage)|Uzyskuje dostęp do mapy komunikatów w `CMessageMap`-klasy.|  
  
## <a name="remarks"></a>Uwagi  
 `CMessageMap`jest to abstrakcyjna klasa podstawowa umożliwiająca komunikat obiektu mapy można uzyskać dostęp przez inny obiekt. Aby dla obiekt do udostępnienia jej mapy komunikatów, jej klasa musi pochodzić od `CMessageMap`.  
  
 ATL używa `CMessageMap` zawarte pomocy technicznej systemu windows i łańcucha mapy wiadomości dynamicznych. Na przykład wszystkie klasy zawierające [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) obiekt musi pochodzić od `CMessageMap`. Poniższy kod jest pobierana z [SUBEDIT](../../visual-cpp-samples.md) próbki. Za pomocą [CComControl](../../atl/reference/ccomcontrol-class.md), `CAtlEdit` automatycznie pochodną klasy `CMessageMap`.  
  
 [!code-cpp[NVC_ATL_Windowing#90](../../atl/codesnippet/cpp/cmessagemap-class_1.h)]  
  
 Ponieważ zawartego okna `m_EditCtrl`, będzie używać mapy komunikatów w klasie zawierającej `CAtlEdit` pochodną `CMessageMap`.  
  
 Aby uzyskać więcej informacji na temat mapy komunikatów, zobacz [mapy wiadomości](../../atl/message-maps-atl.md) w artykule "Klas okien ALT".  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  
  
##  <a name="processwindowmessage"></a>CMessageMap::ProcessWindowMessage  
 Uzyskuje dostęp do mapy komunikatów identyfikowane przez `dwMsgMapID` w `CMessageMap`-klasy.  
  
```
virtual BOOL ProcessWindowMessage(  
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT& lResult,
    DWORD dwMsgMapID) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `hWnd`  
 [in] Dojście do okna odbierania wiadomości.  
  
 `uMsg`  
 [in] Komunikat wysyłany do okna.  
  
 `wParam`  
 [in] Dodatkowe informacje specyficzne dla wiadomości.  
  
 `lParam`  
 [in] Dodatkowe informacje specyficzne dla wiadomości.  
  
 `lResult`  
 [out] Wynik przetwarzania komunikatów.  
  
 `dwMsgMapID`  
 [in] Identyfikator mapę komunikatów, która będzie przetwarzać komunikatu. Domyślną mapę komunikatów zadeklarowana z [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), jest identyfikowany przez 0. Mapy wiadomości alternatywny zadeklarowana z [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), jest identyfikowany przez `msgMapID`.  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** Jeśli komunikat jest w pełni obsługiwany; w przeciwnym razie **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Wywoływane przez procedurę okna z [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) obiektu lub obiektu, który jest dynamicznie tworzenie łańcuchów do mapy wiadomości.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CDynamicChain](../../atl/reference/cdynamicchain-class.md)   
 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)   
 [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)   
 [Przegląd klas](../../atl/atl-class-overview.md)
