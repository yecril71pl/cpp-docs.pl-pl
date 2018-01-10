---
title: Makra mapy (ATL) komunikatu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlwin/ATL::ALT_MSG_MAP
- atlwin/ATL::BEGIN_MSG_MAP
- atlwin/ATL::CHAIN_MSG_MAP_ALT
- atlwin/ATL::CHAIN_MSG_MAP_ALT_MEMBER
- atlwin/ATL::CHAIN_MSG_MAP
- atlwin/ATL::CHAIN_MSG_MAP_DYNAMIC
- atlwin/ATL::CHAIN_MSG_MAP_MEMBER
- atlwin/ATL::COMMAND_CODE_HANDLER
- atlwin/ATL::COMMAND_HANDLER
- atlwin/ATL::COMMAND_ID_HANDLER
- atlwin/ATL::COMMAND_RANGE_CODE_HANDLER
- atlwin/ATL::COMMAND_RANGE_HANDLER
- atlwin/ATL::DECLARE_EMPTY_MSG_MAP
- atlwin/ATL::DEFAULT_REFLECTION_HANDLER
- atlwin/ATL::END_MSG_MAP
- atlwin/ATL::FORWARD_NOTIFICATIONS
- atlwin/ATL::MESSAGE_HANDLER
- atlwin/ATL::MESSAGE_RANGE_HANDLER
- atlwin/ATL::NOTIFY_CODE_HANDLER
- atlwin/ATL::NOTIFY_HANDLER
- atlwin/ATL::NOTIFY_ID_HANDLER
- atlwin/ATL::NOTIFY_RANGE_CODE_HANDLER
- atlwin/ATL::NOTIFY_RANGE_HANDLER
- atlwin/ATL::REFLECT_NOTIFICATIONS
- atlwin/ATL::REFLECTED_COMMAND_CODE_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_ID_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_RANGE_CODE_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_RANGE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_CODE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_ID_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_RANGE_CODE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_RANGE_HANDLER
dev_langs: C++
ms.assetid: eefdd546-8934-4a30-b263-9c06a8addcbd
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 200d82c9d9b2ca0456ae5de4d6c937be69e212bc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="message-map-macros-atl"></a>Makra mapy komunikatów (ALT)
Te makra zdefiniuj mapy komunikatów i zapisów.  
  
|||  
|-|-|  
|[ALT_MSG_MAP](#alt_msg_map)|Oznacza początek mapy komunikatów alternatywny.|  
|[BEGIN_MSG_MAP](#begin_msg_map)|Oznacza początek mapy komunikat domyślny.|  
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Tworzy łańcuch mapy komunikatów alternatywny w klasie podstawowej.|  
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Tworzy łańcuch mapy komunikatów alternatywny w element członkowski danych klasy.|  
|[CHAIN_MSG_MAP](#chain_msg_map)|Tworzy łańcuch mapy komunikatów domyślnego w klasie podstawowej.|  
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Tworzy łańcuch mapy komunikatów w innej klasy w czasie wykonywania.|  
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Tworzy łańcuch domyślną mapę komunikatów w element członkowski danych klasy.|  
|[COMMAND_CODE_HANDLER](#command_code_handler)|Mapy **WM_COMMAND** wiadomość do funkcji programu obsługi, na podstawie kodu powiadomienia.|  
|[COMMAND_HANDLER](#command_handler)|Mapy **WM_COMMAND** wiadomość do funkcji programu obsługi, na podstawie kodu powiadomień i identyfikator elementu menu, kontroli lub akceleratora.|  
|[COMMAND_ID_HANDLER](#command_id_handler)|Mapy **WM_COMMAND** wiadomość do funkcji programu obsługi, na podstawie identyfikatora elementu menu, kontroli lub akceleratora.|  
|[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)|Mapy **WM_COMMAND** wiadomość do funkcji programu obsługi, na podstawie kodu powiadomień i ciągły zakres identyfikatorów formantu.|  
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Mapy **WM_COMMAND** wiadomość do funkcji programu obsługi, oparte na ciągły zakres identyfikatorów formantu.|  
|[DECLARE_EMPTY_MSG_MAP](#declare_empty_msg_map)|Implementuje mapy pusty komunikat.|  
|[DEFAULT_REFLECTION_HANDLER](#default_reflection_handler)|Udostępnia domyślny program obsługi komunikatów odbitych, które nie są obsługiwane w przeciwnym razie wartość.|  
|[END_MSG_MAP](#end_msg_map)|Oznacza koniec mapy komunikatów.|  
|[FORWARD_NOTIFICATIONS](#forward_notifications)|Przekazuje komunikaty powiadomień do okna nadrzędnego.|  
|[MESSAGE_HANDLER](#message_handler)|Mapuje funkcji obsługi komunikatów systemu Windows.|  
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Mapy wiadomości ciągły zakres systemu Windows do obsługi funkcji.|  
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Mapy **WM_NOTIFY** wiadomość do funkcji programu obsługi, na podstawie kodu powiadomienia.|  
|[NOTIFY_HANDLER](#notify_handler)|Mapy **WM_NOTIFY** wiadomość do funkcji programu obsługi, na podstawie kodu powiadomień i identyfikator formantu.|  
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Mapy **WM_NOTIFY** wiadomość do funkcji programu obsługi, na podstawie identyfikatora formantu.|  
|[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)|Mapy **WM_NOTIFY** wiadomość do funkcji programu obsługi, na podstawie kodu powiadomień i ciągły zakres identyfikatorów formantu.|  
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Mapy **WM_NOTIFY** wiadomość do funkcji programu obsługi, oparte na ciągły zakres identyfikatorów formantu.|  
|[REFLECT_NOTIFICATIONS](#reflect_notifications)|Odzwierciedla powiadomień wiadomości do okna je wysłać.|  
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Mapuje odbite **WM_COMMAND** wiadomość do funkcji programu obsługi, na podstawie kodu powiadomienia.|  
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Mapuje odbite **WM_COMMAND** wiadomość do funkcji programu obsługi, na podstawie kodu powiadomień i identyfikator elementu menu, kontroli lub akceleratora.|  
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Mapuje odbite **WM_COMMAND** wiadomość do funkcji programu obsługi, na podstawie identyfikatora elementu menu, kontroli lub akceleratora.|  
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Mapuje odbite **WM_COMMAND** wiadomość do funkcji programu obsługi, na podstawie kodu powiadomień i ciągły zakres identyfikatorów formantu.|  
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Mapuje odbite **WM_COMMAND** wiadomość do funkcji programu obsługi, oparte na ciągły zakres identyfikatorów formantu.|  
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Mapuje odbite **WM_NOTIFY** wiadomość do funkcji programu obsługi, na podstawie kodu powiadomienia.|  
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Mapuje odbite **WM_NOTIFY** wiadomość do funkcji programu obsługi, na podstawie kodu powiadomień i identyfikator formantu.|  
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Mapuje odbite **WM_NOTIFY** wiadomość do funkcji programu obsługi, na podstawie identyfikatora formantu.|  
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Mapuje odbite **WM_NOTIFY** wiadomość do funkcji programu obsługi, na podstawie kodu powiadomień i ciągły zakres identyfikatorów formantu.|  
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Mapuje odbite **WM_NOTIFY** wiadomość do funkcji programu obsługi, oparte na ciągły zakres identyfikatorów formantu.|  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  

##  <a name="alt_msg_map"></a>ALT_MSG_MAP  
 Oznacza początek mapy komunikatów alternatywny.  
  
```
ALT_MSG_MAP(msgMapID)
```  
  
### <a name="parameters"></a>Parametry  
 `msgMapID`  
 [in] Identyfikator mapy wiadomości.  
  
### <a name="remarks"></a>Uwagi  
 ATL identyfikuje każdego mapy komunikatów liczbą. Domyślne mapy komunikatów (zadeklarowana z `BEGIN_MSG_MAP` makro) jest identyfikowane przez 0. Mapy wiadomości alternatywny jest identyfikowany przez `msgMapID`.  
  
 Mapy komunikatów są używane do przetwarzania komunikatów wysyłanych do okna. Na przykład [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) pozwala określić identyfikator mapy komunikatów w zawierającego go obiektu. [CContainedWindow::WindowProc](ccontainedwindowt-class.md#windowproc) następnie używa tej mapy wiadomości do kierowania wiadomości zawartego okna funkcji obsługi odpowiedniego lub do innego mapy wiadomości. Aby uzyskać listę makra deklarujące funkcje programu obsługi, zobacz [BEGIN_MSG_MAP](#begin_msg_map).  
  
 Zawsze rozpocząć mapy komunikatów z `BEGIN_MSG_MAP`. Następnie można zadeklarować mapy kolejnych komunikatów alternatywny.  
  
 [END_MSG_MAP](#end_msg_map) makro oznacza koniec mapy komunikatów. Należy pamiętać, że zawsze dokładnie jedno wystąpienie `BEGIN_MSG_MAP` i `END_MSG_MAP`.  
  
 Aby uzyskać więcej informacji o używaniu mapy komunikatów w ATL, zobacz [mapy wiadomości](../../atl/message-maps-atl.md).  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono domyślne mapy komunikatów i jeden komunikat alternatywny mapy, każda z nich zawiera jedną funkcję programu obsługi:  
  
 [!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]  
  
 W kolejnym przykładzie pokazano dwa mapy komunikatów alternatywny. Mapy wiadomości domyślny jest pusta.  
  
 [!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h   

##  <a name="begin_msg_map"></a>BEGIN_MSG_MAP  
 Oznacza początek mapy komunikat domyślny.  
  
```
BEGIN_MSG_MAP(theClass)
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 [in] Nazwa klasy zawierającej mapę komunikatów.  
  
### <a name="remarks"></a>Uwagi  
 [CWindowImpl::WindowProc](cwindowimpl-class.md#windowproc) używa domyślnej mapy wiadomości do przetwarzania komunikatów wysyłanych do okna. Mapy wiadomości kieruje komunikaty do funkcji obsługi odpowiednich lub innego mapy komunikatów.  

  
 Następujące makra mapy wiadomości do funkcji programu obsługi. Ta funkcja musi być zdefiniowana w `theClass`.  
  
|Makra|Opis|  
|-----------|-----------------|  
|[MESSAGE_HANDLER](#message_handler)|Mapuje funkcji obsługi komunikatów systemu Windows.|  
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Mapy wiadomości ciągły zakres systemu Windows do obsługi funkcji.|  
|[COMMAND_HANDLER](#command_handler)|Mapy **WM_COMMAND** wiadomość do funkcji programu obsługi, na podstawie kodu powiadomień i identyfikator elementu menu, kontroli lub akceleratora.|  
|[COMMAND_ID_HANDLER](#command_id_handler)|Mapy **WM_COMMAND** wiadomość do funkcji programu obsługi, na podstawie identyfikatora elementu menu, kontroli lub akceleratora.|  
|[COMMAND_CODE_HANDLER](#command_handler)|Mapy **WM_COMMAND** wiadomość do funkcji programu obsługi, na podstawie kodu powiadomienia.|  
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Mapuje ciągły zakres **WM_COMMAND** wiadomości do obsługi funkcji, na podstawie identyfikatora elementu menu, kontroli lub akceleratora.|  
|[NOTIFY_HANDLER](#notify_handler)|Mapy **WM_NOTIFY** wiadomość do funkcji programu obsługi, na podstawie kodu powiadomień i identyfikator formantu.|  
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Mapy **WM_NOTIFY** wiadomość do funkcji programu obsługi, na podstawie identyfikatora formantu.|  
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Mapy **WM_NOTIFY** wiadomość do funkcji programu obsługi, na podstawie kodu powiadomienia.|  
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Mapuje ciągły zakres **WM_NOTIFY** komunikatów do funkcji programu obsługi, oparte na identyfikator formantu.|  
  
 Następujące makra bezpośrednie wiadomości do innego mapy wiadomości. Ten proces jest nazywany "łańcucha".  
  
|Makra|Opis|  
|-----------|-----------------|  
|[CHAIN_MSG_MAP](#chain_msg_map)|Tworzy łańcuch mapy komunikatów domyślnego w klasie podstawowej.|  
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Tworzy łańcuch domyślną mapę komunikatów w element członkowski danych klasy.|  
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Tworzy łańcuch mapy komunikatów alternatywny w klasie podstawowej.|  
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Tworzy łańcuch mapy komunikatów alternatywny w element członkowski danych klasy.|  
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Tworzy łańcuch domyślną mapę komunikatów w innej klasy w czasie wykonywania.|  
  
 Następujące makra bezpośrednie "odzwierciedlone" komunikaty okna nadrzędnego. Na przykład formantu zwykle wysyła komunikaty powiadomień do jej okna nadrzędnego przetwarzania, ale okno nadrzędne można odzwierciedlać komunikat do formantu.  
  
|Makra|Opis|  
|-----------|-----------------|  
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Mapuje odbite **WM_COMMAND** wiadomość do funkcji programu obsługi, na podstawie kodu powiadomień i identyfikator elementu menu, kontroli lub akceleratora.|  
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Mapuje odbite **WM_COMMAND** wiadomość do funkcji programu obsługi, na podstawie identyfikatora elementu menu, kontroli lub akceleratora.|  
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Mapuje odbite **WM_COMMAND** wiadomość do funkcji programu obsługi, na podstawie kodu powiadomienia.|  
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Mapuje odbite **WM_COMMAND** wiadomość do funkcji programu obsługi, oparte na ciągły zakres identyfikatorów formantu.|  
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Mapuje odbite **WM_COMMAND** wiadomość do funkcji programu obsługi, na podstawie kodu powiadomień i ciągły zakres identyfikatorów formantu.|  
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Mapuje odbite **WM_NOTIFY** wiadomość do funkcji programu obsługi, na podstawie kodu powiadomień i identyfikator formantu.|  
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Mapuje odbite **WM_NOTIFY** wiadomość do funkcji programu obsługi, na podstawie identyfikatora formantu.|  
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Mapuje odbite **WM_NOTIFY** wiadomość do funkcji programu obsługi, na podstawie kodu powiadomienia.|  
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Mapuje odbite **WM_NOTIFY** wiadomość do funkcji programu obsługi, oparte na ciągły zakres identyfikatorów formantu.|  
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Mapuje odbite **WM_NOTIFY** wiadomość do funkcji programu obsługi, na podstawie kodu powiadomień i ciągły zakres identyfikatorów formantu.|  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#102](../../atl/codesnippet/cpp/message-map-macros-atl_3.h)]  
  
 Gdy `CMyExtWindow` obiekt odbiera `WM_PAINT` wiadomości, wiadomość zostaje skierowany do `CMyExtWindow::OnPaint` rzeczywiste przetwarzanie. Jeśli `OnPaint` oznacza komunikat wymaga dalsze przetwarzanie, zostanie komunikat, a następnie przekierowanie do domyślnego mapę komunikatów w `CMyBaseWindow`.  
  
 Oprócz domyślnego mapy wiadomości, można zdefiniować Mapa alternatywny wiadomości z [ALT_MSG_MAP](#alt_msg_map). Zawsze rozpocząć mapy komunikatów z `BEGIN_MSG_MAP`. Następnie można zadeklarować mapy kolejnych komunikatów alternatywny. W poniższym przykładzie przedstawiono domyślne mapy komunikatów i jeden komunikat alternatywny mapy, każda z nich zawiera jedną funkcję programu obsługi:  
  
 [!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]  
  
 W kolejnym przykładzie pokazano dwa mapy komunikatów alternatywny. Mapy wiadomości domyślny jest pusta.  
  
 [!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]  
  
 [END_MSG_MAP](#end_msg_map) makro oznacza koniec mapy komunikatów. Należy pamiętać, że zawsze dokładnie jedno wystąpienie `BEGIN_MSG_MAP` i `END_MSG_MAP`.  
  
 Aby uzyskać więcej informacji o używaniu mapy komunikatów w ATL, zobacz [mapy wiadomości](../../atl/message-maps-atl.md).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h   
  
##  <a name="chain_msg_map_alt"></a>CHAIN_MSG_MAP_ALT  
 Określa wpis w mapie komunikatów.  
  
```
CHAIN_MSG_MAP_ALT(theChainClass, msgMapID)
```  
  
### <a name="parameters"></a>Parametry  
 `theChainClass`  
 [in] Nazwa klasy podstawowej zawierającego mapy komunikatów.  
  
 `msgMapID`  
 [in] Identyfikator mapy wiadomości.  
  
### <a name="remarks"></a>Uwagi  
 `CHAIN_MSG_MAP_ALT`kieruje komunikaty do mapowania alternatywnej wiadomości w klasie podstawowej. Musi zadeklarować to mapowanie alternatywny wiadomości z [ALT_MSG_MAP(msgMapID)](#alt_msg_map). Do kierowania wiadomości do mapy komunikatów domyślną klasę podstawową (zadeklarowana z [BEGIN_MSG_MAP](#begin_msg_map)), użyj `CHAIN_MSG_MAP`. Na przykład zobacz [CHAIN_MSG_MAP](#chain_msg_map).  
  
> [!NOTE]
>  Zawsze rozpocząć mapy komunikatów z `BEGIN_MSG_MAP`. Następnie można zadeklarować mapy kolejnych komunikatów alternatywne z `ALT_MSG_MAP`. [END_MSG_MAP](#end_msg_map) makro oznacza koniec mapy komunikatów. Każdy mapy wiadomości musi mieć dokładnie jedno wystąpienie `BEGIN_MSG_MAP` i `END_MSG_MAP`.  
  
 Aby uzyskać więcej informacji o używaniu mapy komunikatów w ATL, zobacz [mapy wiadomości](../../atl/message-maps-atl.md).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h   
  
##  <a name="chain_msg_map_alt_member"></a>CHAIN_MSG_MAP_ALT_MEMBER  
 Określa wpis w mapie komunikatów.  
  
```
CHAIN_MSG_MAP_ALT_MEMBER(theChainMember, msgMapID)
```  
  
### <a name="parameters"></a>Parametry  
 `theChainMember`  
 [in] Nazwa elementu członkowskiego danych zawierającego mapy komunikatów.  
  
 `msgMapID`  
 [in] Identyfikator mapy wiadomości.  
  
### <a name="remarks"></a>Uwagi  
 `CHAIN_MSG_MAP_ALT_MEMBER`kieruje komunikaty do mapowania alternatywnej komunikat w elemencie członkowskim danych. Musi zadeklarować to mapowanie alternatywny wiadomości z [ALT_MSG_MAP(msgMapID)](#alt_msg_map). Do kierowania wiadomości z mapą komunikat domyślny element członkowski danych (zadeklarowana z [BEGIN_MSG_MAP](#begin_msg_map)), użyj `CHAIN_MSG_MAP_MEMBER`. Na przykład zobacz [CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member).  
  
> [!NOTE]
>  Zawsze rozpocząć mapy komunikatów z `BEGIN_MSG_MAP`. Następnie można zadeklarować mapy kolejnych komunikatów alternatywne z `ALT_MSG_MAP`. [END_MSG_MAP](#end_msg_map) makro oznacza koniec mapy komunikatów. Każdy mapy wiadomości musi mieć dokładnie jedno wystąpienie `BEGIN_MSG_MAP` i `END_MSG_MAP`.  
  
 Aby uzyskać więcej informacji o używaniu mapy komunikatów w ATL, zobacz [mapy wiadomości](../../atl/message-maps-atl.md).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h   
  
##  <a name="chain_msg_map"></a>CHAIN_MSG_MAP  
 Określa wpis w mapie komunikatów.  
  
```
CHAIN_MSG_MAP(theChainClass)
```  
  
### <a name="parameters"></a>Parametry  
 `theChainClass`  
 [in] Nazwa klasy podstawowej zawierającego mapy komunikatów.  
  
### <a name="remarks"></a>Uwagi  
 `CHAIN_MSG_MAP`kieruje komunikaty do mapy komunikatów domyślną klasę podstawową (zadeklarowana z [BEGIN_MSG_MAP](#begin_msg_map)). Do kierowania wiadomości do mapy komunikatów alternatywny klasę podstawową (zadeklarowana z [ALT_MSG_MAP](#alt_msg_map)), użyj [CHAIN_MSG_MAP_ALT](#chain_msg_map_alt).  
  
> [!NOTE]
>  Zawsze rozpocząć mapy komunikatów z `BEGIN_MSG_MAP`. Następnie można zadeklarować mapy kolejnych komunikatów alternatywne z `ALT_MSG_MAP`. [END_MSG_MAP](#end_msg_map) makro oznacza koniec mapy komunikatów. Każdy mapy wiadomości musi mieć dokładnie jedno wystąpienie `BEGIN_MSG_MAP` i `END_MSG_MAP`.  
  
 Aby uzyskać więcej informacji o używaniu mapy komunikatów w ATL, zobacz [mapy wiadomości](../../atl/message-maps-atl.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#107](../../atl/codesnippet/cpp/message-map-macros-atl_4.h)]  
  
 W tym przykładzie przedstawiono poniżej:  
  
-   Jeśli używa procedurę okna `CMyClass`na mapę komunikatów w domyślnej i `OnPaint` nie obsługi wiadomości, wiadomość zostaje skierowany do `CMyBaseClass`w domyślnej mapy komunikatów do przetworzenia.  
  
-   Czy procedurę okna używa pierwszego mapę komunikatów alternatywny w `CMyClass`, wszystkie komunikaty są kierowane do `CMyBaseClass`w mapy komunikat domyślny.  
  
-   Jeśli używa procedurę okna `CMyClass`na drugi komunikat alternatywny mapowania i `OnChar` nie obsługi wiadomości, wiadomość zostaje skierowany do mapy określony komunikat alternatywny w `CMyBaseClass`. `CMyBaseClass`musi zadeklarować tej mapy komunikatów z `ALT_MSG_MAP(1)`.  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h   
  
##  <a name="chain_msg_map_dynamic"></a>CHAIN_MSG_MAP_DYNAMIC  
 Określa wpis w mapie komunikatów.  
  
```
CHAIN_MSG_MAP_DYNAMIC(dynaChainID)
```  
  
### <a name="parameters"></a>Parametry  
 *dynaChainID*  
 [in] Unikatowy identyfikator dla obiekt mapy komunikatów.  
  
### <a name="remarks"></a>Uwagi  
 `CHAIN_MSG_MAP_DYNAMIC`Określa, że komunikaty, w czasie wykonywania, aby domyślną mapę komunikatów w innym obiekcie. Obiekt i jego mapę komunikatów, które są skojarzone z *dynaChainID*, która jest definiowana za pomocą [CDynamicChain::SetChainEntry](cdynamicchain-class.md#setchainentry). Musi pochodzić z klasy `CDynamicChain` aby można było używać `CHAIN_MSG_MAP_DYNAMIC`. Na przykład zobacz [CDynamicChain](../../atl/reference/cdynamicchain-class.md) omówienie.  

  
> [!NOTE]
>  Zawsze rozpocząć mapy komunikatów z [BEGIN_MSG_MAP](#begin_msg_map). Następnie można zadeklarować mapy kolejnych komunikatów alternatywne z `ALT_MSG_MAP`. [END_MSG_MAP](#end_msg_map) makro oznacza koniec mapy komunikatów. Każdy mapy wiadomości musi mieć dokładnie jedno wystąpienie `BEGIN_MSG_MAP` i `END_MSG_MAP`.  
  
 Aby uzyskać więcej informacji o używaniu mapy komunikatów w ATL, zobacz [mapy wiadomości](../../atl/message-maps-atl.md).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h   
  
##  <a name="chain_msg_map_member"></a>CHAIN_MSG_MAP_MEMBER  
 Określa wpis w mapie komunikatów.  
  
```
CHAIN_MSG_MAP_MEMBER(theChainMember)
```  
  
### <a name="parameters"></a>Parametry  
 `theChainMember`  
 [in] Nazwa elementu członkowskiego danych zawierającego mapy komunikatów.  
  
### <a name="remarks"></a>Uwagi  
 `CHAIN_MSG_MAP_MEMBER`kieruje komunikaty do mapy komunikat domyślny element członkowski danych (zadeklarowana z [BEGIN_MSG_MAP](#begin_msg_map)). Do kierowania wiadomości do mapy komunikatów alternatywny element członkowski danych (zadeklarowana z [ALT_MSG_MAP](#alt_msg_map)), użyj [CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member).  
  
> [!NOTE]
>  Zawsze rozpocząć mapy komunikatów z `BEGIN_MSG_MAP`. Następnie można zadeklarować mapy kolejnych komunikatów alternatywne z `ALT_MSG_MAP`. [END_MSG_MAP](#end_msg_map) makro oznacza koniec mapy komunikatów. Każdy mapy wiadomości musi mieć dokładnie jedno wystąpienie `BEGIN_MSG_MAP` i `END_MSG_MAP`.  
  
 Aby uzyskać więcej informacji o używaniu mapy komunikatów w ATL, zobacz [mapy wiadomości](../../atl/message-maps-atl.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#108](../../atl/codesnippet/cpp/message-map-macros-atl_5.h)]  
  
 W tym przykładzie przedstawiono poniżej:  
  
-   Jeśli używa procedurę okna `CMyClass`na mapę komunikatów w domyślnej i `OnPaint` nie obsługi wiadomości, wiadomość zostaje skierowany do `m_obj`w domyślnej mapy komunikatów do przetworzenia.  
  
-   Czy procedurę okna używa pierwszego mapę komunikatów alternatywny w `CMyClass`, wszystkie komunikaty są kierowane do `m_obj`w mapy komunikat domyślny.  
  
-   Jeśli używa procedurę okna `CMyClass`na drugi komunikat alternatywny mapowania i `OnChar` nie obsługi wiadomości, wiadomość zostaje skierowany do mapy określony komunikat alternatywny `m_obj`. Klasa `CMyContainedClass` musi zadeklarować tej mapy komunikatów z `ALT_MSG_MAP(1)`.  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h   
  
##  <a name="command_code_handler"></a>COMMAND_CODE_HANDLER  
 Podobnie jak [COMMAND_HANDLER](#command_handler), ale mapuje [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) wiadomości tylko na podstawie powiadomień kodu.  
  
```
COMMAND_CODE_HANDLER(code, func)
```  
  
### <a name="parameters"></a>Parametry  
 `code`  
 [in] Kod powiadomienia.  
  
 `func`  
 [in] Nazwa funkcji obsługi wiadomości.  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h   
  
##  <a name="command_handler"></a>COMMAND_HANDLER  
 Określa wpis w mapie komunikatów.  
  
```
COMMAND_HANDLER(id, code, func)
```    
  
### <a name="parameters"></a>Parametry  
 `id`  
 [in] Identyfikator elementu menu, kontroli lub akceleratora.  
  
 `code`  
 [in] Kod powiadomienia.  
  
 `func`  
 [in] Nazwa funkcji obsługi wiadomości.  
  
### <a name="remarks"></a>Uwagi  
 `COMMAND_HANDLER`mapuje [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) wiadomości określona Obsługa funkcji, na podstawie kodu powiadomień i identyfikator formantu. Na przykład:  
  
 [!code-cpp[NVC_ATL_Windowing#119](../../atl/codesnippet/cpp/message-map-macros-atl_6.h)]  
  
 Dowolnej funkcji określone w `COMMAND_HANDLER` makro musi być zdefiniowana w następujący sposób:  
  
 `LRESULT CommandHandler(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled);`  
  
 Ustawia mapy komunikatów `bHandled` do **TRUE** przed `CommandHandler` jest wywoływana. Jeśli `CommandHandler` nie obsługuje pełni komunikatu, należy ją ustawić `bHandled` do **FALSE** wskazująca wiadomość wymaga dalsze przetwarzanie.  
  
> [!NOTE]
>  Zawsze rozpocząć mapy komunikatów z [BEGIN_MSG_MAP](#begin_msg_map). Następnie można zadeklarować mapy kolejnych komunikatów alternatywne z [ALT_MSG_MAP](#alt_msg_map). [END_MSG_MAP](#end_msg_map) makro oznacza koniec mapy komunikatów. Każdy mapy wiadomości musi mieć dokładnie jedno wystąpienie `BEGIN_MSG_MAP` i `END_MSG_MAP`.  
  
 Oprócz `COMMAND_HANDLER`, można użyć [MESSAGE_HANDLER](#message_handler) do mapowania **WM_COMMAND** komunikat niezależnie identyfikatora lub kodu. W takim przypadku `MESSAGE_HANDLER(WM_COMMAND, OnHandlerFunction)` kieruje wszystkie **WM_COMMAND** komunikaty `OnHandlerFunction`.  
  
 Aby uzyskać więcej informacji o używaniu mapy komunikatów w ATL, zobacz [mapy wiadomości](../../atl/message-maps-atl.md).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h   
  
##  <a name="command_id_handler"></a>COMMAND_ID_HANDLER  
 Podobnie jak [COMMAND_HANDLER](#command_handler), ale mapuje [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) wiadomości tylko na podstawie identyfikatora elementu menu, kontroli lub akceleratora.  
  
```
COMMAND_ID_HANDLER(id, func)
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [in] Identyfikator elementu menu, kontroli lub akceleratora wysyłania wiadomości.  
  
 `func`  
 [in] Nazwa funkcji obsługi wiadomości.  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h   
  
##  <a name="command_range_code_handler"></a>COMMAND_RANGE_CODE_HANDLER  
 Podobnie jak [COMMAND_RANGE_HANDLER](#command_range_handler), ale mapuje [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) wiadomości z kodem określonym powiadomień z zakresu kontroli funkcji obsługi jednego.  
  
```
COMMAND_RANGE_CODE_HANDLER(idFirst, idLast, code, func)
```    
  
### <a name="parameters"></a>Parametry  
 `idFirst`  
 [in] Oznacza początek ciągły zakres identyfikatorów formantu.  
  
 `idLast`  
 [in] Oznacza koniec ciągły zakres identyfikatorów formantu.  
  
 `code`  
 [in] Kod powiadomienia.  
  
 `func`  
 [in] Nazwa funkcji obsługi wiadomości.  
  
### <a name="remarks"></a>Uwagi  
 Ten zakres jest oparty na identyfikator elementu menu, kontroli lub akceleratora wysyłania wiadomości.  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h   
  
##  <a name="command_range_handler"></a>COMMAND_RANGE_HANDLER  
 Podobnie jak [COMMAND_HANDLER](#command_handler), ale mapuje [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) wiadomości z zakresu kontroli funkcji obsługi pojedynczego.  
  
```
COMMAND_RANGE_HANDLER( idFirst, idLast, func)
```    
  
### <a name="parameters"></a>Parametry  
 `idFirst`  
 [in] Oznacza początek ciągły zakres identyfikatorów formantu.  
  
 `idLast`  
 [in] Oznacza koniec ciągły zakres identyfikatorów formantu.  
  
 `func`  
 [in] Nazwa funkcji obsługi wiadomości.  
  
### <a name="remarks"></a>Uwagi  
 Ten zakres jest oparty na identyfikator elementu menu, kontroli lub akceleratora wysyłania wiadomości.  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h   
  
##  <a name="declare_empty_msg_map"></a>DECLARE_EMPTY_MSG_MAP  
 Deklaruje mapy pusty komunikat.  
  
```
DECLARE_EMPTY_MSG_MAP()
```  
  
### <a name="remarks"></a>Uwagi  
 `DECLARE_EMPTY_MSG_MAP`to makro wygody, która wywołuje makra [BEGIN_MSG_MAP](#begin_msg_map) i [END_MSG_MAP](#end_msg_map) utworzyć mapę pusty komunikat:  
  
 [!code-cpp[NVC_ATL_Windowing#122](../../atl/codesnippet/cpp/message-map-macros-atl_7.h)]  
  
##  <a name="default_reflection_handler"></a>DEFAULT_REFLECTION_HANDLER  
 Udostępnia domyślny program obsługi dla okna podrzędnego (kontrola), który będzie otrzymywał odzwierciedlone wiadomości. Program obsługi poprawnie przekazuje nieobsługiwany wiadomości `DefWindowProc`.  
  
```
DEFAULT_REFLECTION_HANDLER()
```  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h   
  
##  <a name="end_msg_map"></a>END_MSG_MAP  
 Oznacza koniec mapy komunikatów.  
  
```
END_MSG_MAP()
```  
  
### <a name="remarks"></a>Uwagi  
 Zawsze używaj [BEGIN_MSG_MAP](#begin_msg_map) makra, aby oznaczyć początek mapy komunikatów. Użyj [ALT_MSG_MAP](#alt_msg_map) do deklarowania map kolejnych komunikatów Szukaj komunikatu alternatywny.  
  
 Należy pamiętać, że zawsze dokładnie jedno wystąpienie `BEGIN_MSG_MAP` i `END_MSG_MAP`.  
  
 Aby uzyskać więcej informacji o używaniu mapy komunikatów w ATL, zobacz [mapy wiadomości](../../atl/message-maps-atl.md).  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono domyślne mapy komunikatów i jeden komunikat alternatywny mapy, każda z nich zawiera jedną funkcję programu obsługi:  
  
 [!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]  
  
 W kolejnym przykładzie pokazano dwa mapy komunikatów alternatywny. Mapy wiadomości domyślny jest pusta.  
  
 [!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h   
  
##  <a name="forward_notifications"></a>FORWARD_NOTIFICATIONS  
 Przekazuje komunikaty powiadomień do okna nadrzędnego.  
  
```
FORWARD_NOTIFICATIONS()
```  
  
### <a name="remarks"></a>Uwagi  
 Określ to makro jako część mapy wiadomości.  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h   
  
##  <a name="message_handler"></a>MESSAGE_HANDLER  
 Określa wpis w mapie komunikatów.  
  
```
MESSAGE_HANDLER( msg, func )
```  
  
### <a name="parameters"></a>Parametry  
 `msg`  
 [in] Komunikat systemu Windows.  
  
 `func`  
 [in] Nazwa funkcji obsługi wiadomości.  
  
### <a name="remarks"></a>Uwagi  
 `MESSAGE_HANDLER`mapuje funkcja określona Obsługa komunikatów systemu Windows.  
  
 Dowolnej funkcji określone w `MESSAGE_HANDLER` makro musi być zdefiniowana w następujący sposób:  
  
 `LRESULT MessageHandler(UINT uMsg, WPARAM wParam, LPARAM lParam, BOOL& bHandled);`  
  
 Ustawia mapy komunikatów `bHandled` do **TRUE** przed `MessageHandler` jest wywoływana. Jeśli `MessageHandler` nie obsługuje pełni komunikatu, należy ją ustawić `bHandled` do **FALSE** wskazująca wiadomość wymaga dalsze przetwarzanie.  
  
> [!NOTE]
>  Zawsze rozpocząć mapy komunikatów z [BEGIN_MSG_MAP](#begin_msg_map). Następnie można zadeklarować mapy kolejnych komunikatów alternatywne z [ALT_MSG_MAP](#alt_msg_map). [END_MSG_MAP](#end_msg_map) makro oznacza koniec mapy komunikatów. Każdy mapy wiadomości musi mieć dokładnie jedno wystąpienie `BEGIN_MSG_MAP` i `END_MSG_MAP`.  
  
 Oprócz `MESSAGE_HANDLER`, można użyć [COMMAND_HANDLER](#command_handler) i [NOTIFY_HANDLER](#notify_handler) do mapowania [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) i [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583) komunikaty, odpowiednio.  
  
 Aby uzyskać więcej informacji o używaniu mapy komunikatów w ATL, zobacz [mapy wiadomości](../../atl/message-maps-atl.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#129](../../atl/codesnippet/cpp/message-map-macros-atl_8.h)]  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h   
  
##  <a name="message_range_handler"></a>MESSAGE_RANGE_HANDLER  
 Podobnie jak [MESSAGE_HANDLER](#message_handler), ale map zakres Windows komunikatów do funkcji obsługi jednego.  
  
```
MESSAGE_RANGE_HANDLER( msgFirst, msgLast, func )
```  
  
### <a name="parameters"></a>Parametry  
 *msgFirst*  
 [in] Oznacza początek ciągły zakres wiadomości.  
  
 *msgLast*  
 [in] Oznacza koniec ciągły zakres wiadomości.  
  
 `func`  
 [in] Nazwa funkcji obsługi wiadomości.  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h   
  
##  <a name="notify_code_handler"></a>NOTIFY_CODE_HANDLER  
 Podobnie jak [NOTIFY_HANDLER](#notify_handler), ale mapuje [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583) wiadomości tylko na podstawie powiadomień kodu.  
  
```
NOTIFY_CODE_HANDLER(cd, func)
```  
  
### <a name="parameters"></a>Parametry  
 `cd`  
 [in] Kod powiadomienia.  
  
 `func`  
 [in] Nazwa funkcji obsługi wiadomości.  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h   
  
##  <a name="notify_handler"></a>NOTIFY_HANDLER  
 Określa wpis w mapie komunikatów.  
  
```
NOTIFY_HANDLER( id, cd, func )
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [in] Identyfikator formantu wysyłania wiadomości.  
  
 `cd`  
 [in] Kod powiadomienia.  
  
 `func`  
 [in] Nazwa funkcji obsługi wiadomości.  
  
### <a name="remarks"></a>Uwagi  
 `NOTIFY_HANDLER`mapuje [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583) wiadomości określona Obsługa funkcji, na podstawie kodu powiadomień i identyfikator formantu.  
  
 Dowolnej funkcji określone w `NOTIFY_HANDLER` makro musi być zdefiniowana w następujący sposób:  
  
 `LRESULT NotifyHandler(int idCtrl, LPNMHDR pnmh, BOOL& bHandled);`  
  
 Ustawia mapy komunikatów `bHandled` do **TRUE** przed `NotifyHandler` jest wywoływana. Jeśli `NotifyHandler` nie obsługuje pełni komunikatu, należy ją ustawić `bHandled` do **FALSE** wskazująca wiadomość wymaga dalsze przetwarzanie.  
  
> [!NOTE]
>  Zawsze rozpocząć mapy komunikatów z [BEGIN_MSG_MAP](#begin_msg_map). Następnie można zadeklarować mapy kolejnych komunikatów alternatywne z [ALT_MSG_MAP](#alt_msg_map). [END_MSG_MAP](#end_msg_map) makro oznacza koniec mapy komunikatów. Każdy mapy wiadomości musi mieć dokładnie jedno wystąpienie `BEGIN_MSG_MAP` i `END_MSG_MAP`.  
  
 Oprócz `NOTIFY_HANDLER`, można użyć [MESSAGE_HANDLER](#message_handler) do mapowania **WM_NOTIFY** komunikat niezależnie identyfikatora lub kodu. W takim przypadku `MESSAGE_HANDLER(WM_NOTIFY, OnHandlerFunction)` kieruje wszystkie **WM_NOTIFY** komunikaty `OnHandlerFunction`.  
  
 Aby uzyskać więcej informacji o używaniu mapy komunikatów w ATL, zobacz [mapy wiadomości](../../atl/message-maps-atl.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#130](../../atl/codesnippet/cpp/message-map-macros-atl_9.h)]  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h   
  
##  <a name="notify_id_handler"></a>NOTIFY_ID_HANDLER  
 Podobnie jak [NOTIFY_HANDLER](#notify_handler), ale mapy [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583) komunikat oparte tylko na podstawie identyfikatora formantu.  
  
```
NOTIFY_ID_HANDLER( id, func )
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [in] Identyfikator formantu wysyłania wiadomości.  
  
 `func`  
 [in] Nazwa funkcji obsługi wiadomości.  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h   
  
##  <a name="notify_range_code_handler"></a>NOTIFY_RANGE_CODE_HANDLER  
 Podobnie jak [NOTIFY_RANGE_HANDLER](#notify_range_handler), ale mapuje [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583) wiadomości z kodem określonym powiadomień z zakresu kontroli funkcji obsługi jednego.  
  
```
NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```  
  
### <a name="parameters"></a>Parametry  
 `idFirst`  
 [in] Oznacza początek ciągły zakres identyfikatorów formantu.  
  
 `idLast`  
 [in] Oznacza koniec ciągły zakres identyfikatorów formantu.  
  
 `cd`  
 [in] Kod powiadomienia.  
  
 `func`  
 [in] Nazwa funkcji obsługi wiadomości.  
  
### <a name="remarks"></a>Uwagi  
 Ten zakres jest na podstawie identyfikatora formantu wysyłania wiadomości.  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h   
  
##  <a name="notify_range_handler"></a>NOTIFY_RANGE_HANDLER  
 Podobnie jak [NOTIFY_HANDLER](#notify_handler), ale mapuje [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583) wiadomości z zakresu kontroli funkcji obsługi pojedynczego.  
  
```
NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```  
  
### <a name="parameters"></a>Parametry  
 `idFirst`  
 [in] Oznacza początek ciągły zakres identyfikatorów formantu.  
  
 `idLast`  
 [in] Oznacza koniec ciągły zakres identyfikatorów formantu.  
  
 `func`  
 [in] Nazwa funkcji obsługi wiadomości.  
  
### <a name="remarks"></a>Uwagi  
 Ten zakres jest na podstawie identyfikatora formantu wysyłania wiadomości.  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h   
  
##  <a name="reflect_notifications"></a>REFLECT_NOTIFICATIONS  
 Odzwierciedla powiadomień wiadomości do okna podrzędnego (kontrola) je wysłać.  
  
```
REFLECT_NOTIFICATIONS()
```  
  
### <a name="remarks"></a>Uwagi  
 Określ to makro jako część mapy komunikatów okno nadrzędne.  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h   
  
##  <a name="reflected_command_code_handler"></a>REFLECTED_COMMAND_CODE_HANDLER  
 Podobnie jak [COMMAND_CODE_HANDLER](#command_code_handler), ale mapy polecenia uwzględnione okna nadrzędnego.  
  
```
REFLECTED_COMMAND_CODE_HANDLER( code, func )
```  
  
### <a name="parameters"></a>Parametry  
 `code`  
 [in] Kod powiadomienia.  
  
 `func`  
 [in] Nazwa funkcji obsługi wiadomości.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  
   
##  <a name="reflected_command_handler"></a>REFLECTED_COMMAND_HANDLER  
 Podobnie jak [COMMAND_HANDLER](#command_handler), ale mapy polecenia uwzględnione okna nadrzędnego.  
  
```
REFLECTED_COMMAND_HANDLER( id, code, func )
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [in] Identyfikator elementu menu, kontroli lub akceleratora.  
  
 `code`  
 [in] Kod powiadomienia.  
  
 `func`  
 [in] Nazwa funkcji obsługi wiadomości.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  

##  <a name="reflected_command_id_handler"></a>REFLECTED_COMMAND_ID_HANDLER  
 Podobnie jak [COMMAND_ID_HANDLER](#command_id_handler), ale mapy polecenia uwzględnione okna nadrzędnego.  
  
```
REFLECTED_COMMAND_ID_HANDLER( id, func )
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [in] Identyfikator elementu menu, kontroli lub akceleratora.  
  
 `func`  
 [in] Nazwa funkcji obsługi wiadomości.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  

##  <a name="reflected_command_range_code_handler"></a>REFLECTED_COMMAND_RANGE_CODE_HANDLER  
 Podobnie jak [COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler), ale mapy polecenia uwzględnione okna nadrzędnego.  
  
```
REFLECTED_COMMAND_RANGE_CODE_HANDLER( idFirst, idLast, code, func )
```  
  
### <a name="parameters"></a>Parametry  
 `idFirst`  
 [in] Oznacza początek ciągły zakres identyfikatorów formantu.  
  
 `idLast`  
 [in] Oznacza koniec ciągły zakres identyfikatorów formantu.  
  
 `code`  
 [in] Kod powiadomienia.  
  
 `func`  
 [in] Nazwa funkcji obsługi wiadomości.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  

##  <a name="reflected_command_range_handler"></a>REFLECTED_COMMAND_RANGE_HANDLER  
 Podobnie jak [COMMAND_RANGE_HANDLER](#command_range_handler), ale mapy polecenia uwzględnione okna nadrzędnego.  
  
```
REFLECTED_COMMAND_RANGE_HANDLER( idFirst, idLast, func )
```  
  
### <a name="parameters"></a>Parametry  
 `idFirst`  
 [in] Oznacza początek ciągły zakres identyfikatorów formantu.  
  
 `idLast`  
 [in] Oznacza koniec ciągły zakres identyfikatorów formantu.  
  
 `func`  
 [in] Nazwa funkcji obsługi wiadomości.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  

##  <a name="reflected_notify_code_handler"></a>REFLECTED_NOTIFY_CODE_HANDLER  
 Podobnie jak [NOTIFY_CODE_HANDLER](#notify_code_handler), ale mapuje powiadomienia odzwierciedlonej z okna nadrzędnego.  
  
```
REFLECTED_NOTIFY_CODE_HANDLER_EX( cd, func )
```  
  
### <a name="parameters"></a>Parametry  
 `cd`  
 [in] Kod powiadomienia.  
  
 `func`  
 [in] Nazwa funkcji obsługi wiadomości.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  

##  <a name="reflected_notify_handler"></a>REFLECTED_NOTIFY_HANDLER  
 Podobnie jak [NOTIFY_HANDLER](#notify_handler), ale mapuje powiadomienia odzwierciedlonej z okna nadrzędnego.  
  
```
REFLECTED_NOTIFY_HANDLER( id, cd, func )
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [in] Identyfikator elementu menu, kontroli lub akceleratora.  
  
 `cd`  
 [in] Kod powiadomienia.  
  
 `func`  
 [in] Nazwa funkcji obsługi wiadomości.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  

##  <a name="reflected_notify_id_handler"></a>REFLECTED_NOTIFY_ID_HANDLER  
 Podobnie jak [NOTIFY_ID_HANDLER](#notify_id_handler), ale mapuje powiadomienia odzwierciedlonej z okna nadrzędnego.  
  
```
REFLECTED_NOTIFY_ID_HANDLER( id, func )
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [in] Identyfikator elementu menu, kontroli lub akceleratora.  
  
 `func`  
 [in] Nazwa funkcji obsługi wiadomości.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  

##  <a name="reflected_notify_range_code_handler"></a>REFLECTED_NOTIFY_RANGE_CODE_HANDLER  
 Podobnie jak [NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler), ale mapuje powiadomienia odzwierciedlonej z okna nadrzędnego.  
  
```
REFLECTED_NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```    
  
### <a name="parameters"></a>Parametry  
 `idFirst`  
 [in] Oznacza początek ciągły zakres identyfikatorów formantu.  
  
 `idLast`  
 [in] Oznacza koniec ciągły zakres identyfikatorów formantu.  
  
 `cd`  
 [in] Kod powiadomienia.  
  
 `func`  
 [in] Nazwa funkcji obsługi wiadomości.  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h   
  
##  <a name="reflected_notify_range_handler"></a>REFLECTED_NOTIFY_RANGE_HANDLER  
 Podobnie jak [NOTIFY_RANGE_HANDLER](#notify_range_handler), ale mapuje powiadomienia odzwierciedlonej z okna nadrzędnego.  
  
```
REFLECTED_NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```  
  
### <a name="parameters"></a>Parametry  
 `idFirst`  
 [in] Oznacza początek ciągły zakres identyfikatorów formantu.  
  
 `idLast`  
 [in] Oznacza koniec ciągły zakres identyfikatorów formantu.  
  
 `func`  
 [in] Nazwa funkcji obsługi wiadomości.  
  
## <a name="see-also"></a>Zobacz też  
 [Makra](../../atl/reference/atl-macros.md)
