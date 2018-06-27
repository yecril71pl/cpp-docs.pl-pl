---
title: Klasa CAnimationVariableChangeHandler | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 58646efaaa0087be2bd73e45acd8ade4a16e9767
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957094"
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
  
##  <a name="onvaluechanged"></a>  CAnimationVariableChangeHandler::OnValueChanged  
 Wywoływane, gdy zmieniono wartość zmiennej animacji.  
  
```  
IFACEMETHOD(OnValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in DOUBLE newValue,
    __in DOUBLE previousValue);
```  
  
### <a name="parameters"></a>Parametry  
 *scenorysu*  
 Scenorysu, który jest animacji zmiennej.  
  
 *Zmienna*  
 Zmienna animacji, który został zaktualizowany.  
  
 *newValue*  
 Nowa wartość.  
  
 *previousValue*  
 Poprzednia wartość.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. W przeciwnym wypadku zwraca kod błędu HRESULT.  
  
##  <a name="setanimationcontroller"></a>  CAnimationVariableChangeHandler::SetAnimationController  
 Przechowuje wskaźnik do kontrolera animacji na zdarzenia trasy.  
  
```  
void SetAnimationController(CAnimationController* pAnimationController);
```  
  
### <a name="parameters"></a>Parametry  
 *pAnimationController*  
 Wskaźnik do kontrolera animacji, które będzie odbierało zdarzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
