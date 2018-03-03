---
title: Klasa CAnimationVariableChangeHandler | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::OnValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::SetAnimationController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationVariableChangeHandler [MFC], OnValueChanged
- CAnimationVariableChangeHandler [MFC], SetAnimationController
ms.assetid: 2ea4996d-5c04-4dfc-be79-d42d55050795
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f70e8d59e291362496ec2555cf2838bf2df41d3a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="canimationvariablechangehandler-class"></a>Klasa CAnimationVariableChangeHandler
Implementuje wywołanie zwrotne, które jest wywoływane przez interfejs API animacji, gdy zmienia się wartość zmiennej animacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CAnimationVariableChangeHandler : public CUIAnimationVariableChangeHandlerBase<CAnimationVariableChangeHandler>;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CAnimationVariableChangeHandler::CAnimationVariableChangeHandler`|Konstruuje `CAnimationVariableChangeHandler` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CAnimationVariableChangeHandler::CreateInstance`|Tworzy wystąpienie `CAnimationVariableChangeHandler` obiektu.|  
|[CAnimationVariableChangeHandler::OnValueChanged](#onvaluechanged)|Wywoływane, gdy zmieniono wartość zmiennej animacji. (Przesłania `CUIAnimationVariableChangeHandlerBase::OnValueChanged`.)|  
|[CAnimationVariableChangeHandler::SetAnimationController](#setanimationcontroller)|Przechowuje wskaźnik do kontrolera animacji na zdarzenia trasy.|  
  
## <a name="remarks"></a>Uwagi  
 Ten program obsługi zdarzeń jest tworzony i przekazane do `IUIAnimationVariable::SetVariableChangeHandler` podczas wywoływania metody `CAnimationVariable::EnableValueChangedEvent` lub `CAnimationBaseObject::EnableValueChangedEvent` (co pozwala to zdarzenie wszystkich zmiennych animacji hermetyzowany w obiekcie animacji).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationVariableChangeHandlerBase`  
  
 `CAnimationVariableChangeHandler`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxanimationcontroller.h  
  
##  <a name="onvaluechanged"></a>CAnimationVariableChangeHandler::OnValueChanged  
 Wywoływane, gdy zmieniono wartość zmiennej animacji.  
  
```  
IFACEMETHOD(OnValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in DOUBLE newValue,
    __in DOUBLE previousValue);
```  
  
### <a name="parameters"></a>Parametry  
 `storyboard`  
 Scenorysu, który jest animacji zmiennej.  
  
 `variable`  
 Zmienna animacji, który został zaktualizowany.  
  
 `newValue`  
 Nowa wartość.  
  
 `previousValue`  
 Poprzednia wartość.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. W przeciwnym wypadku zwraca kod błędu HRESULT.  
  
##  <a name="setanimationcontroller"></a>CAnimationVariableChangeHandler::SetAnimationController  
 Przechowuje wskaźnik do kontrolera animacji na zdarzenia trasy.  
  
```  
void SetAnimationController(CAnimationController* pAnimationController);
```  
  
### <a name="parameters"></a>Parametry  
 `pAnimationController`  
 Wskaźnik do kontrolera animacji, które będzie odbierało zdarzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
