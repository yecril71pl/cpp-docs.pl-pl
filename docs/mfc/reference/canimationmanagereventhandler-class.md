---
title: Klasa CAnimationManagerEventHandler | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::OnManagerStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::SetAnimationController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationManagerEventHandler [MFC], CAnimationManagerEventHandler
- CAnimationManagerEventHandler [MFC], CreateInstance
- CAnimationManagerEventHandler [MFC], OnManagerStatusChanged
- CAnimationManagerEventHandler [MFC], SetAnimationController
ms.assetid: 6089ec07-e661-4805-b227-823b4652aade
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bfc64617002db0536dc3d62e70082c27b260802f
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465061"
---
# <a name="canimationmanagereventhandler-class"></a>Klasa CAnimationManagerEventHandler
Implementuje wywołanie zwrotne, które jest wywoływane przez interfejs API animacji przy zmianie stanu Menedżera animacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CAnimationManagerEventHandler : public CUIAnimationManagerEventHandlerBase<CAnimationManagerEventHandler>;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationManagerEventHandler::CAnimationManagerEventHandler](#canimationmanagereventhandler)|Konstruuje `CAnimationManagerEventHandler` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationManagerEventHandler::CreateInstance](#createinstance)|Tworzy wystąpienie `CAnimationManagerEventHandler` obiektu.|  
|[CAnimationManagerEventHandler::OnManagerStatusChanged](#onmanagerstatuschanged)|Wywoływane po zmianie stanu Menedżera animacji. (Przesłania `CUIAnimationManagerEventHandlerBase::OnManagerStatusChanged`.)|  
|[CAnimationManagerEventHandler::SetAnimationController](#setanimationcontroller)|Przechowuje wskaźnik do kontrolera animacji kierowanie zdarzeń.|  
  
## <a name="remarks"></a>Uwagi  
 Ta procedura obsługi zdarzeń jest tworzony i przekazywany do metody IUIAnimationManager::SetManagerEventHandler podczas wywoływania CAnimationController::EnableAnimationManagerEvent.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationManagerEventHandlerBase`  
  
 `CAnimationManagerEventHandler`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxanimationcontroller.h  
  
##  <a name="canimationmanagereventhandler"></a>  CAnimationManagerEventHandler::CAnimationManagerEventHandler  
 Wymagany jest dodatek SP1 dla programu Visual Studio 2010.  
  
 Tworzy obiekt CAnimationManagerEventHandler.  
  
```  
CAnimationManagerEventHandler();
```  
  
##  <a name="createinstance"></a>  CAnimationManagerEventHandler::CreateInstance  
 Wymagany jest dodatek SP1 dla programu Visual Studio 2010.  
  
 Tworzy wystąpienie obiektu CAnimationManagerEventHandler.  
  
```  
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,  
    IUIAnimationManagerEventHandler** ppManagerEventHandler);
```  
  
### <a name="parameters"></a>Parametry  
 *pAnimationController*  
 Wskaźnik do Kontroler animacji, które zostaną odebrane zdarzenia.  
  
 *ppManagerEventHandler*  
 Dane wyjściowe. Jeśli metoda się powiedzie, zawiera wskaźnik do obiektu COM, który będzie obsługiwać aktualizacje stanu Menedżera animacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda się powiedzie, zwraca wartość S_OK. W przeciwnym razie zwraca kod błędu HRESULT.  
  
##  <a name="onmanagerstatuschanged"></a>  CAnimationManagerEventHandler::OnManagerStatusChanged  
 Wymagany jest dodatek SP1 dla programu Visual Studio 2010.  
  
 Wywoływane po zmianie stanu Menedżera animacji.  
  
```  
IFACEMETHOD(OnManagerStatusChanged)(
  UI_ANIMATION_MANAGER_STATUS newStatus,
  UI_ANIMATION_MANAGER_STATUS previousStatus);
```  
  
### <a name="parameters"></a>Parametry  
 *newStatus*  
 Nowy stan.  
  
 *previousStatus*  
 Poprzedni stan.  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżąca implementacja parametru zawsze zwraca wartość S_OK;  
  
##  <a name="setanimationcontroller"></a>  CAnimationManagerEventHandler::SetAnimationController  
 Wymagany jest dodatek SP1 dla programu Visual Studio 2010.  
  
 Przechowuje wskaźnik do kontrolera animacji kierowanie zdarzeń.  
  
```  
void SetAnimationController(CAnimationController* pAnimationController);
```  
  
### <a name="parameters"></a>Parametry  
 *pAnimationController*  
 Wskaźnik do Kontroler animacji, które zostaną odebrane zdarzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
