---
title: Klasa CAnimationTimerEventHandler | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnPostUpdate
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnPreUpdate
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnRenderingTooSlow
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::SetAnimationController
dev_langs: C++
helpviewer_keywords:
- CAnimationTimerEventHandler [MFC], CreateInstance
- CAnimationTimerEventHandler [MFC], OnPostUpdate
- CAnimationTimerEventHandler [MFC], OnPreUpdate
- CAnimationTimerEventHandler [MFC], OnRenderingTooSlow
- CAnimationTimerEventHandler [MFC], SetAnimationController
ms.assetid: 188dea3b-4b5e-4f6b-8df9-09d993a21619
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 35e59a74be574913b6605bd9bce0934280bbb542
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="canimationtimereventhandler-class"></a>Klasa CAnimationTimerEventHandler
Implementuje wywołanie zwrotne, które jest wywoływana przez interfejs API animacji, w przypadku wystąpienia zdarzenia czasowe.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CAnimationTimerEventHandler : public CUIAnimationTimerEventHandlerBase<CAnimationTimerEventHandler>;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationTimerEventHandler::CreateInstance](#createinstance)|Tworzy wystąpienie `CAnimationTimerEventHandler` wywołania zwrotnego.|  
|[CAnimationTimerEventHandler::OnPostUpdate](#onpostupdate)|Uchwyty zdarzeń, które są wykonywane po zakończeniu aktualizacji animacji. (Przesłania `CUIAnimationTimerEventHandlerBase::OnPostUpdate`.)|  
|[CAnimationTimerEventHandler::OnPreUpdate](#onpreupdate)|Uchwyty zdarzeń przed rozpoczęciem aktualizacji animacji. (Przesłania `CUIAnimationTimerEventHandlerBase::OnPreUpdate`.)|  
|[CAnimationTimerEventHandler::OnRenderingTooSlow](#onrenderingtooslow)|Obsługi zdarzeń występujących podczas renderowania szybkość animacji spadnie poniżej minimalna szybkość pożądane. (Przesłania `CUIAnimationTimerEventHandlerBase::OnRenderingTooSlow`.)|  
|[CAnimationTimerEventHandler::SetAnimationController](#setanimationcontroller)|Przechowuje wskaźnik do kontrolera animacji na zdarzenia trasy.|  
  
## <a name="remarks"></a>Uwagi  
 Ten program obsługi zdarzeń jest tworzony i przekazane do IUIAnimationTimer::SetTimerEventHandler podczas wywoływania CAnimationController::EnableAnimationTimerEventHandler.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationTimerEventHandlerBase`  
  
 `CAnimationTimerEventHandler`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxanimationcontroller.h  
  
##  <a name="createinstance"></a>CAnimationTimerEventHandler::CreateInstance  
 Tworzy wystąpienie CAnimationTimerEventHandler wywołania zwrotnego.  
  
```  
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,  
    IUIAnimationTimerEventHandler** ppTimerEventHandler);
```  
  
### <a name="parameters"></a>Parametry  
 `pAnimationController`  
 Wskaźnik do kontrolera animacji, które będzie odbierało zdarzenia.  
  
 `ppTimerEventHandler`  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. W przeciwnym wypadku zwraca kod błędu HRESULT.  
  
##  <a name="onpostupdate"></a>CAnimationTimerEventHandler::OnPostUpdate  
 Uchwyty zdarzeń, które są wykonywane po zakończeniu aktualizacji animacji.  
  
```  
IFACEMETHOD(OnPostUpdate)();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL.  
  
##  <a name="onpreupdate"></a>CAnimationTimerEventHandler::OnPreUpdate  
 Uchwyty zdarzeń przed rozpoczęciem aktualizacji animacji.  
  
```  
IFACEMETHOD(OnPreUpdate)();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL.  
  
##  <a name="onrenderingtooslow"></a>CAnimationTimerEventHandler::OnRenderingTooSlow  
 Obsługi zdarzeń występujących podczas renderowania szybkość animacji spadnie poniżej minimalna szybkość pożądane.  
  
```  
IFACEMETHOD(OnRenderingTooSlow)(UINT32 fps);
```  
  
### <a name="parameters"></a>Parametry  
 `fps`  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL.  
  
##  <a name="setanimationcontroller"></a>CAnimationTimerEventHandler::SetAnimationController  
 Przechowuje wskaźnik do kontrolera animacji na zdarzenia trasy.  
  
```  
void SetAnimationController(CAnimationController* pAnimationController);
```  
  
### <a name="parameters"></a>Parametry  
 `pAnimationController`  
 Wskaźnik do kontrolera animacji, które będzie odbierało zdarzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
