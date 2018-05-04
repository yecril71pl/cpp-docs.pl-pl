---
title: Klasa CDynamicChain | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDynamicChain
- ATLWIN/ATL::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CallChain
- ATLWIN/ATL::CDynamicChain::RemoveChainEntry
- ATLWIN/ATL::CDynamicChain::SetChainEntry
dev_langs:
- C++
helpviewer_keywords:
- message maps, chaining
- chaining message maps
- CDynamicChain class
ms.assetid: f084b2be-0e77-4836-973d-ae278a1e9da8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08f6d09546d4514950b5b45ffb9494116294d051
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="cdynamicchain-class"></a>Klasa CDynamicChain
Ta klasa zawiera metody pomocnicze dynamiczne tworzenie łańcuchów mapy komunikatów.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CDynamicChain
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDynamicChain::CDynamicChain](#cdynamicchain)|Konstruktor.|  
|[CDynamicChain:: ~ CDynamicChain](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDynamicChain::CallChain](#callchain)|Określa, że wiadomości do innego obiektu mapy komunikatów systemu Windows.|  
|[CDynamicChain::RemoveChainEntry](#removechainentry)|Usuwa wpisu mapy komunikatów z kolekcji.|  
|[CDynamicChain::SetChainEntry](#setchainentry)|Dodaje wpis mapy wiadomości do kolekcji lub modyfikuje istniejący wpis.|  
  
## <a name="remarks"></a>Uwagi  
 `CDynamicChain` Zarządza kolekcją mapy komunikatów, włączanie komunikatów systemu Windows, będą kierowane w czasie wykonywania, do innego obiektu mapy wiadomości.  
  
 Aby dodać obsługę dynamiczne tworzenie łańcuchów mapy komunikatów, wykonaj następujące czynności:  
  
-   Pochodzi z klasy `CDynamicChain`. Mapy wiadomości określ [CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) makro do tworzenia łańcucha mapy komunikatów domyślną innego obiektu.  
  
-   Pochodzi z klasy, co ma być powiązane z [CMessageMap](../../atl/reference/cmessagemap-class.md). `CMessageMap` Umożliwia obiektu do udostępnienia jej mapy wiadomości do innych obiektów.  
  
-   Wywołanie `CDynamicChain::SetChainEntry` do identyfikowania, której obiekt i komunikat, który mapuje możesz do tworzenia łańcucha.  
  
 Na przykład załóżmy, że klasa jest zdefiniowana w następujący sposób:  
  
 [!code-cpp[NVC_ATL_Windowing#88](../../atl/codesnippet/cpp/cdynamicchain-class_1.h)]  
  
 Klient następnie wywołuje `CMyWindow::SetChainEntry`:  
  
 [!code-cpp[NVC_ATL_Windowing#89](../../atl/codesnippet/cpp/cdynamicchain-class_2.cpp)]  
  
 gdzie `chainedObj` jest obiektem łańcuchowa i jest wystąpieniem klasy pochodzącej od `CMessageMap`. Teraz Jeśli `myCtl` odbiera komunikat, który nie jest obsługiwany przez `OnPaint` lub `OnSetFocus`, procedurę okna kieruje do wiadomości `chainedObj`przez mapy komunikat domyślny.  
  
 Aby uzyskać więcej informacji na temat łańcucha mapy komunikatów, zobacz [mapy komunikatów](../../atl/message-maps-atl.md) w artykule "Klas okien ALT".  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  
  
##  <a name="callchain"></a>  CDynamicChain::CallChain  
 Określa, że komunikatów systemu Windows do innego obiektu mapy wiadomości.  
  
```
BOOL CallChain(  
    DWORD dwChainID,
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT& lResult);
```  
  
### <a name="parameters"></a>Parametry  
 `dwChainID`  
 [in] Unikatowy identyfikator skojarzony z łańcuchowa obiekt i jego mapę komunikatów.  
  
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
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** Jeśli komunikat jest w pełni przetworzone; w przeciwnym razie **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj procedurę okna `CallChain`, należy określić [CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) makra mapy wiadomości. Na przykład zobacz [CDynamicChain](../../atl/reference/cdynamicchain-class.md) omówienie.  
  
 `CallChain` poprzednie wywołanie wymaga [SetChainEntry](#setchainentry) do skojarzenia `dwChainID` wartości z obiektu i jego mapę komunikatów.  
  
##  <a name="cdynamicchain"></a>  CDynamicChain::CDynamicChain  
 Konstruktor.  
  
```
CDynamicChain();
```  
  
##  <a name="dtor"></a>  CDynamicChain:: ~ CDynamicChain  
 Destruktor.  
  
```
~CDynamicChain();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie przydzielone zasoby.  
  
##  <a name="removechainentry"></a>  CDynamicChain::RemoveChainEntry  
 Usuwa określony komunikat mapy z kolekcji.  
  
```
BOOL RemoveChainEntry(DWORD dwChainID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwChainID`  
 [in] Unikatowy identyfikator skojarzony z łańcuchowa obiekt i jego mapę komunikatów. Pierwotnie określić tę wartość za pośrednictwem wywołania [SetChainEntry](#setchainentry).  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** Jeśli mapy komunikatów został pomyślnie usunięty z kolekcji. W przeciwnym razie **FALSE**.  
  
##  <a name="setchainentry"></a>  CDynamicChain::SetChainEntry  
 Dodaje określony komunikat mapy do kolekcji.  
  
```
BOOL SetChainEntry(  
    DWORD dwChainID,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `dwChainID`  
 [in] Unikatowy identyfikator skojarzony z łańcuchowa obiekt i jego mapę komunikatów.  
  
 `pObject`  
 [in] Wskaźnik do obiektu łańcuchowa deklarowania map wiadomości. Ten obiekt musi pochodzić od [CMessageMap](../../atl/reference/cmessagemap-class.md).  
  
 `dwMsgMapID`  
 [in] Identyfikator mapę komunikatów w obiekcie łańcuchowych. Wartość domyślna to 0, co identyfikuje mapy komunikatów domyślne zadeklarowana z [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Aby określić mapę komunikatów alternatywny zadeklarowana z [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), Przekaż `msgMapID`.  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** Jeśli mapy komunikatów został pomyślnie dodany do kolekcji. W przeciwnym razie **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `dwChainID` wartość już istnieje w kolekcji, jego skojarzony obiekt i mapy komunikatów są zastępowane przez `pObject` i `dwMsgMapID`odpowiednio. W przeciwnym razie jest dodawany nowy wpis.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CWindowImpl](../../atl/reference/cwindowimpl-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
