---
title: "Asyncbase — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase
dev_langs: C++
helpviewer_keywords: AsyncBase class
ms.assetid: 64259b9b-f427-4ffd-a611-e7a2f82362b2
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c33d48c69852ab22cfa2bfb4f33d45edcc469662
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="asyncbase-class"></a>AsyncBase — Klasa
Implementuje automatu stanów asynchroniczne środowiska wykonawczego systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
template <  
   typename TComplete,  
   typename TProgress = Details::Nil,  
   AsyncResultType resultType = SingleResult  
>  
class AsyncBase : public AsyncBase< TComplete, Details::Nil, resultType >;  
  
template <  
   typename TComplete,  
   AsyncResultType resultType  
>  
class AsyncBase< TComplete, Details::Nil, resultType > : public Microsoft::WRL::Implements< IAsyncInfo >;  
```  
  
#### <a name="parameters"></a>Parametry  
 `TComplete`  
 Obsługa zdarzeń, która jest wywoływana po zakończeniu operacji asynchronicznej.  
  
 `TProgress`  
 Obsługi zdarzeń, który jest wywoływany, gdy działa asynchronicznej operacji raporty Bieżący postęp operacji.  
  
 `resultType`  
 Jeden z [asyncresulttype —](../windows/asyncresulttype-enumeration.md) wartości wyliczenia. Domyślnie SingleResult.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[AsyncBase::AsyncBase, konstruktor](../windows/asyncbase-asyncbase-constructor.md)|Inicjuje wystąpienie klasy asyncbase —.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[AsyncBase::Cancel, metoda](../windows/asyncbase-cancel-method.md)|Anuluje operację asynchroniczną.|  
|[AsyncBase::Close, metoda](../windows/asyncbase-close-method.md)|Zamyka operację asynchroniczną.|  
|[AsyncBase::FireCompletion, metoda](../windows/asyncbase-firecompletion-method.md)|Wywołuje program obsługi zdarzeń zakończenia lub resetuje delegata wewnętrzny postępu.|  
|[AsyncBase::FireProgress, metoda](../windows/asyncbase-fireprogress-method.md)|Wywołuje Bieżący postęp obsługi zdarzeń.|  
|[AsyncBase::get_ErrorCode, metoda](../windows/asyncbase-get-errorcode-method.md)|Pobiera kod błędu dla bieżącej operacji asynchronicznej.|  
|[AsyncBase::get_Id, metoda](../windows/asyncbase-get-id-method.md)|Pobiera dojście operację asynchroniczną.|  
|[AsyncBase::get_Status, metoda](../windows/asyncbase-get-status-method.md)|Pobiera wartość, która wskazuje stan operacji asynchronicznej.|  
|[AsyncBase::GetOnComplete, metoda](../windows/asyncbase-getoncomplete-method.md)|Kopiuje adres bieżącej obsługi zdarzeń zakończenia do określonej zmiennej.|  
|[AsyncBase::GetOnProgress, metoda](../windows/asyncbase-getonprogress-method.md)|Kopiuje adres bieżący postęp obsługi zdarzeń do określonej zmiennej.|  
|[AsyncBase::put_Id, metoda](../windows/asyncbase-put-id-method.md)|Ustawia dojście operację asynchroniczną.|  
|[AsyncBase::PutOnComplete, metoda](../windows/asyncbase-putoncomplete-method.md)|Ustawia adres zakończenia obsługi zdarzeń do określonej wartości.|  
|[AsyncBase::PutOnProgress, metoda](../windows/asyncbase-putonprogress-method.md)|Ustawia adres programu obsługi zdarzeń postępu na określoną wartość.|  
|[AsyncBase::Start, metoda](../windows/asyncbase-start-method.md)|Rozpoczyna operację asynchroniczną.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[AsyncBase::CheckValidStateForDelegateCall, metoda](../windows/asyncbase-checkvalidstatefordelegatecall-method.md)|Sprawdza, czy można modyfikować właściwości delegata w bieżącym stanie asynchronicznego.|  
|[AsyncBase::CheckValidStateForResultsCall, metoda](../windows/asyncbase-checkvalidstateforresultscall-method.md)|Sprawdza, czy wyniki operacji asynchronicznej mogą być zbierane w bieżącym stanie asynchronicznego.|  
|[AsyncBase::ContinueAsyncOperation, metoda](../windows/asyncbase-continueasyncoperation-method.md)|Określa, czy operacja asynchroniczna przetwarzanie powinno być kontynuowane, czy należy zatrzymać.|  
|[AsyncBase::CurrentStatusm metoda](../windows/asyncbase-currentstatus-method.md)|Pobiera stan bieżącego operację asynchroniczną.|  
|[AsyncBase::ErrorCode, metoda](../windows/asyncbase-errorcode-method.md)|Pobiera kod błędu dla bieżącej operacji asynchronicznej.|  
|[AsyncBase::OnCancel, metoda](../windows/asyncbase-oncancel-method.md)|W przypadku przesłonięcia w klasie pochodnej, anuluje operację asynchroniczną.|  
|[AsyncBase::OnClose, metoda](../windows/asyncbase-onclose-method.md)|W przypadku przesłonięcia w klasie pochodnej, zamyka operację asynchroniczną.|  
|[AsyncBase::OnStart, metoda](../windows/asyncbase-onstart-method.md)|W przypadku przesłonięcia w klasie pochodnej, rozpoczyna operację asynchroniczną.|  
|[AsyncBase::TryTransitionToCompleted, metoda](../windows/asyncbase-trytransitiontocompleted-method.md)|Wskazuje, czy bieżąca operacja asynchroniczna została ukończona.|  
|[AsyncBase::TryTransitionToError, metoda](../windows/asyncbase-trytransitiontoerror-method.md)|Wskazuje, czy określonego kodu błędu, można zmodyfikować stanu błędu wewnętrznego.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `AsyncBase`  
  
 `AsyncBase`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)