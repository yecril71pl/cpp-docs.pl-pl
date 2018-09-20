---
title: Asyncbase — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase
dev_langs:
- C++
helpviewer_keywords:
- AsyncBase class
ms.assetid: 64259b9b-f427-4ffd-a611-e7a2f82362b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 087ecf151b17c7c505b4b70d01913a44e113ad29
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428684"
---
# <a name="asyncbase-class"></a>AsyncBase — Klasa

Implementuje automatu stanów asynchronicznych środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```cpp
template <
   typename TComplete,
   typename TProgress = Details::Nil,
   AsyncResultType resultType = SingleResult
>
class AsyncBase : public AsyncBase<TComplete, Details::Nil, resultType>;

template <
   typename TComplete,
   AsyncResultType resultType
>
class AsyncBase<TComplete, Details::Nil, resultType> : public Microsoft::WRL::Implements<IAsyncInfo>;
```

### <a name="parameters"></a>Parametry

*TComplete*<br/>
Obsługa zdarzeń, która jest wywoływana po zakończeniu operacji asynchronicznej.

*TProgress*<br/>
Obsługa zdarzeń, która jest wywołana, gdy operacja działa asynchroniczna raportuje Bieżący postęp operacji.

*Typ resultType*<br/>
Jedną z [asyncresulttype —](../windows/asyncresulttype-enumeration.md) wartości wyliczenia. Domyślnie `SingleResult`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[AsyncBase::AsyncBase, konstruktor](../windows/asyncbase-asyncbase-constructor.md)|Inicjuje wystąpienie **AsyncBase** klasy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[AsyncBase::Cancel, metoda](../windows/asyncbase-cancel-method.md)|Anuluje operację asynchroniczną.|
|[AsyncBase::Close, metoda](../windows/asyncbase-close-method.md)|Zamyka operację asynchroniczną.|
|[AsyncBase::FireCompletion, metoda](../windows/asyncbase-firecompletion-method.md)|Wywołuje program obsługi zdarzenia zakończenia lub resetuje delegata wewnętrznego postępu.|
|[AsyncBase::FireProgress, metoda](../windows/asyncbase-fireprogress-method.md)|Wywołuje Bieżący postęp obsługi zdarzeń.|
|[AsyncBase::get_ErrorCode, metoda](../windows/asyncbase-get-errorcode-method.md)|Pobiera kod błędu dla bieżącej operacji asynchronicznej.|
|[AsyncBase::get_Id, metoda](../windows/asyncbase-get-id-method.md)|Pobiera uchwyt operację asynchroniczną.|
|[AsyncBase::get_Status, metoda](../windows/asyncbase-get-status-method.md)|Pobiera wartość, która wskazuje stan operacji asynchronicznej.|
|[AsyncBase::GetOnComplete, metoda](../windows/asyncbase-getoncomplete-method.md)|Kopiuje adres bieżącej obsługi zdarzeń zakończenia do określonej zmiennej.|
|[AsyncBase::GetOnProgress, metoda](../windows/asyncbase-getonprogress-method.md)|Kopiuje adres bieżącej obsługi zdarzeń postępu do określonej zmiennej.|
|[AsyncBase::put_Id, metoda](../windows/asyncbase-put-id-method.md)|Ustawia uchwyt operację asynchroniczną.|
|[AsyncBase::PutOnComplete, metoda](../windows/asyncbase-putoncomplete-method.md)|Ustawia adres procedury obsługi zdarzeń zakończenia z podaną wartością.|
|[AsyncBase::PutOnProgress, metoda](../windows/asyncbase-putonprogress-method.md)|Ustawia adres obsługi zdarzenia postępu z podaną wartością.|
|[AsyncBase::Start, metoda](../windows/asyncbase-start-method.md)|Rozpoczyna operację asynchroniczną.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[AsyncBase::CheckValidStateForDelegateCall, metoda](../windows/asyncbase-checkvalidstatefordelegatecall-method.md)|Sprawdza, czy można zmodyfikować właściwości delegata w bieżącym stanie asynchronicznego.|
|[AsyncBase::CheckValidStateForResultsCall, metoda](../windows/asyncbase-checkvalidstateforresultscall-method.md)|Sprawdza, czy wyniki operacji asynchronicznej może być zbierana w bieżącym stanie asynchronicznego.|
|[AsyncBase::ContinueAsyncOperation, metoda](../windows/asyncbase-continueasyncoperation-method.md)|Określa, czy operacja asynchroniczna przetwarzanie powinno być kontynuowane, czy należy wstrzymać.|
|[AsyncBase::CurrentStatusm metoda](../windows/asyncbase-currentstatus-method.md)|Pobiera stan bieżącej operacji asynchronicznej.|
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

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)