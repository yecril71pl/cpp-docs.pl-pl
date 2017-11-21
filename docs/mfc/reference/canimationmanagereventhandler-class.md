---
title: Klasa CAnimationManagerEventHandler | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::OnManagerStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::SetAnimationController
dev_langs: C++
helpviewer_keywords:
- CAnimationManagerEventHandler [MFC], CAnimationManagerEventHandler
- CAnimationManagerEventHandler [MFC], CreateInstance
- CAnimationManagerEventHandler [MFC], OnManagerStatusChanged
- CAnimationManagerEventHandler [MFC], SetAnimationController
ms.assetid: 6089ec07-e661-4805-b227-823b4652aade
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fcb3021f3473fdaf7bd182325e5e4b130ebccd58
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="canimationmanagereventhandler-class"></a>Klasa CAnimationManagerEventHandler
Implementuje wywołanie zwrotne, które jest wywoływana przez interfejs API animacji przy zmianie stanu Menedżera animacji.  
  
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
|[CAnimationManagerEventHandler::SetAnimationController](#setanimationcontroller)|Przechowuje wskaźnik do kontrolera animacji na zdarzenia trasy.|  
  
## <a name="remarks"></a>Uwagi  
 Ten program obsługi zdarzeń jest tworzony i przekazane do metody IUIAnimationManager::SetManagerEventHandler podczas wywoływania CAnimationController::EnableAnimationManagerEvent.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationManagerEventHandlerBase`  
  
 `CAnimationManagerEventHandler`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxanimationcontroller.h  
  
##  <a name="canimationmanagereventhandler"></a>CAnimationManagerEventHandler::CAnimationManagerEventHandler  
 [!INCLUDE[dev10_sp1required](../../mfc/reference/includes/dev10_sp1required_md.md)]  
  
 Tworzy obiekt CAnimationManagerEventHandler.  
  
```  
CAnimationManagerEventHandler();
```  
  
##  <a name="createinstance"></a>CAnimationManagerEventHandler::CreateInstance  
 [!INCLUDE[dev10_sp1required](../../mfc/reference/includes/dev10_sp1required_md.md)]  
  
 Tworzy wystąpienie obiektu CAnimationManagerEventHandler.  
  
```  
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,  
    IUIAnimationManagerEventHandler** ppManagerEventHandler);
```  
  
### <a name="parameters"></a>Parametry  
 `pAnimationController`  
 Wskaźnik do kontrolera animacji, które będzie odbierało zdarzenia.  
  
 `ppManagerEventHandler`  
 Dane wyjściowe. Jeśli metoda go zawiera wskaźnik do obiektu COM, który będzie obsługiwać aktualizacje stanu Menedżera animacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. W przeciwnym wypadku zwraca kod błędu HRESULT.  
  
##  <a name="onmanagerstatuschanged"></a>CAnimationManagerEventHandler::OnManagerStatusChanged  
 [!INCLUDE[dev10_sp1required](../../mfc/reference/includes/dev10_sp1required_md.md)]  
  
 Wywoływane po zmianie stanu Menedżera animacji.  
  
```  
IFACEMETHOD(OnManagerStatusChanged)(
  UI_ANIMATION_MANAGER_STATUS newStatus,
  UI_ANIMATION_MANAGER_STATUS previousStatus);
```  
  
### <a name="parameters"></a>Parametry  
 `newStatus`  
 Nowy stan.  
  
 `previousStatus`  
 Poprzedniego stanu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżąca implementacja zawsze zwraca wartość S_OK;  
  
##  <a name="setanimationcontroller"></a>CAnimationManagerEventHandler::SetAnimationController  
 [!INCLUDE[dev10_sp1required](../../mfc/reference/includes/dev10_sp1required_md.md)]  
  
 Przechowuje wskaźnik do kontrolera animacji na zdarzenia trasy.  
  
```  
void SetAnimationController(CAnimationController* pAnimationController);
```  
  
### <a name="parameters"></a>Parametry  
 `pAnimationController`  
 Wskaźnik do kontrolera animacji, które będzie odbierało zdarzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
