---
title: Klasa CAnimationStoryboardEventHandler | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::OnStoryboardStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::OnStoryboardUpdated
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::SetAnimationController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationStoryboardEventHandler [MFC], CAnimationStoryboardEventHandler
- CAnimationStoryboardEventHandler [MFC], CreateInstance
- CAnimationStoryboardEventHandler [MFC], OnStoryboardStatusChanged
- CAnimationStoryboardEventHandler [MFC], OnStoryboardUpdated
- CAnimationStoryboardEventHandler [MFC], SetAnimationController
ms.assetid: 10a7e86b-c02d-4124-9a2e-61ecf8ac62fc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 599164d1bb2eca17b935fc74f13fe9b134fc4f2a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="canimationstoryboardeventhandler-class"></a>Klasa CAnimationStoryboardEventHandler
Implementuje wywołanie zwrotne, które jest wywoływane przez interfejs API animacji w przypadku zmiany stanu scenorysu lub zaktualizowaniu scenorysu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CAnimationStoryboardEventHandler : public CUIAnimationStoryboardEventHandlerBase<CAnimationStoryboardEventHandler>;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler](#canimationstoryboardeventhandler)|Konstruuje `CAnimationStoryboardEventHandler` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationStoryboardEventHandler::CreateInstance](#createinstance)|Tworzy wystąpienie `CAnimationStoryboardEventHandler` wywołania zwrotnego.|  
|[CAnimationStoryboardEventHandler::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|Obsługuje `OnStoryboardStatusChanged` zdarzenia, które występują po zmianie stanu scenorysu (zastępuje `CUIAnimationStoryboardEventHandlerBase::OnStoryboardStatusChanged`.)|  
|[CAnimationStoryboardEventHandler::OnStoryboardUpdated](#onstoryboardupdated)|Obsługuje `OnStoryboardUpdated` zdarzenia, które występują po zaktualizowaniu scenorysu (zastępuje `CUIAnimationStoryboardEventHandlerBase::OnStoryboardUpdated`.)|  
|[CAnimationStoryboardEventHandler::SetAnimationController](#setanimationcontroller)|Przechowuje wskaźnik do kontrolera animacji na zdarzenia trasy.|  
  
## <a name="remarks"></a>Uwagi  
 Ten program obsługi zdarzeń jest tworzony i przekazane do `IUIAnimationStoryboard::SetStoryboardEventHandler` podczas wywoływania metody `CAnimationController::EnableStoryboardEventHandler`.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationStoryboardEventHandlerBase`  
  
 `CAnimationStoryboardEventHandler`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxanimationcontroller.h  
  
##  <a name="canimationstoryboardeventhandler"></a>CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler  
 Tworzy obiekt CAnimationStoryboardEventHandler.  
  
```  
CAnimationStoryboardEventHandler();
```  
  
##  <a name="createinstance"></a>CAnimationStoryboardEventHandler::CreateInstance  
 Tworzy wystąpienie CAnimationStoryboardEventHandler wywołania zwrotnego.  
  
```  
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,  
    IUIAnimationStoryboardEventHandler** ppHandler);
```  
  
### <a name="parameters"></a>Parametry  
 `pAnimationController`  
 Wskaźnik do kontrolera animacji, które będzie odbierało zdarzenia.  
  
 `ppHandler`  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. W przeciwnym wypadku zwraca kod błędu HRESULT.  
  
##  <a name="onstoryboardstatuschanged"></a>CAnimationStoryboardEventHandler::OnStoryboardStatusChanged  
 Obsługuje OnStoryboardStatusChanged zdarzenia, które występują po zmianie stanu scenorysu  
  
```  
IFACEMETHOD(OnStoryboardStatusChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in UI_ANIMATION_STORYBOARD_STATUS newStatus,
    __in UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```  
  
### <a name="parameters"></a>Parametry  
 `storyboard`  
 Wskaźnik do scenorysu, których stan zmienił się.  
  
 `newStatus`  
 Stan nowego scenorysu.  
  
 `previousStatus`  
 Określa stan poprzedniej scenorysu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL.  
  
##  <a name="onstoryboardupdated"></a>CAnimationStoryboardEventHandler::OnStoryboardUpdated  
 Obsługuje OnStoryboardUpdated zdarzenia, które występują po zaktualizowaniu scenorysu  
  
```  
IFACEMETHOD(OnStoryboardUpdated) (__in IUIAnimationStoryboard* storyboard);
```  
  
### <a name="parameters"></a>Parametry  
 `storyboard`  
 Wskaźnik do scenorysu, który został zaktualizowany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL.  
  
##  <a name="setanimationcontroller"></a>CAnimationStoryboardEventHandler::SetAnimationController  
 Przechowuje wskaźnik do kontrolera animacji na zdarzenia trasy.  
  
```  
void SetAnimationController(CAnimationController* pAnimationController);
```  
  
### <a name="parameters"></a>Parametry  
 `pAnimationController`  
 Wskaźnik do kontrolera animacji, które będzie odbierało zdarzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
