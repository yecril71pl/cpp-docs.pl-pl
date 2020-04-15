---
title: AsyncBase — Klasa
ms.date: 10/08/2018
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase
- async/Microsoft::WRL::AsyncBase::AsyncBase
- async/Microsoft::WRL::AsyncBase::Cancel
- async/Microsoft::WRL::AsyncBase::CheckValidStateForDelegateCall
- async/Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall
- async/Microsoft::WRL::AsyncBase::Close
- async/Microsoft::WRL::AsyncBase::ContinueAsyncOperation
- async/Microsoft::WRL::AsyncBase::CurrentStatus
- async/Microsoft::WRL::AsyncBase::ErrorCode
- async/Microsoft::WRL::AsyncBase::FireCompletion
- async/Microsoft::WRL::AsyncBase::FireProgress
- async/Microsoft::WRL::AsyncBase::get_ErrorCode
- async/Microsoft::WRL::AsyncBase::get_Id
- async/Microsoft::WRL::AsyncBase::get_Status
- async/Microsoft::WRL::AsyncBase::GetOnComplete
- async/Microsoft::WRL::AsyncBase::GetOnProgress
- async/Microsoft::WRL::AsyncBase::OnCancel
- async/Microsoft::WRL::AsyncBase::OnClose
- async/Microsoft::WRL::AsyncBase::OnStart
- async/Microsoft::WRL::AsyncBase::put_Id
- async/Microsoft::WRL::AsyncBase::PutOnComplete
- async/Microsoft::WRL::AsyncBase::PutOnProgress
- async/Microsoft::WRL::AsyncBase::TryTransitionToCompleted
- async/Microsoft::WRL::AsyncBase::TryTransitionToError
helpviewer_keywords:
- Microsoft::WRL::AsyncBase class
- Microsoft::WRL::AsyncBase::AsyncBase, constructor
- Microsoft::WRL::AsyncBase::Cancel method
- Microsoft::WRL::AsyncBase::CheckValidStateForDelegateCall method
- Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall method
- Microsoft::WRL::AsyncBase::Close method
- Microsoft::WRL::AsyncBase::ContinueAsyncOperation method
- Microsoft::WRL::AsyncBase::CurrentStatus method
- Microsoft::WRL::AsyncBase::ErrorCode method
- Microsoft::WRL::AsyncBase::FireCompletion method
- Microsoft::WRL::AsyncBase::FireProgress method
- Microsoft::WRL::AsyncBase::get_ErrorCode method
- Microsoft::WRL::AsyncBase::get_Id method
- Microsoft::WRL::AsyncBase::get_Status method
- Microsoft::WRL::AsyncBase::GetOnComplete method
- Microsoft::WRL::AsyncBase::GetOnProgress method
- Microsoft::WRL::AsyncBase::OnCancel method
- Microsoft::WRL::AsyncBase::OnClose method
- Microsoft::WRL::AsyncBase::OnStart method
- Microsoft::WRL::AsyncBase::put_Id method
- Microsoft::WRL::AsyncBase::PutOnComplete method
- Microsoft::WRL::AsyncBase::PutOnProgress method
- Microsoft::WRL::AsyncBase::TryTransitionToCompleted method
- Microsoft::WRL::AsyncBase::TryTransitionToError method
ms.assetid: 64259b9b-f427-4ffd-a611-e7a2f82362b2
ms.openlocfilehash: 0254aa4dc243eeffa43850c437a833a6530c01e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371862"
---
# <a name="asyncbase-class"></a>AsyncBase — Klasa

Implementuje maszynę stanu asynchroniiowego środowiska wykonawczego systemu Windows.

## <a name="syntax"></a>Składnia

```cpp
template <
    typename TComplete,
    typename TProgress = Details::Nil,
    AsyncResultType resultType = SingleResult
>
class AsyncBase : public AsyncBase<TComplete, Details::Nil, resultType>;

template <typename TComplete, AsyncResultType resultType>
class AsyncBase<TComplete, Details::Nil, resultType> :
    public Microsoft::WRL::Implements<IAsyncInfo>;
```

### <a name="parameters"></a>Parametry

*TKompleks*<br/>
Program obsługi zdarzeń, który jest wywoływany po zakończeniu operacji asynchroniiowej.

*TProgress (Ruch Tprogress)*<br/>
Program obsługi zdarzeń, który jest wywoływany, gdy uruchomiona operacja asynchroniza raportuje bieżący postęp operacji.

*resultType*<br/>
Jedna z wartości [wyliczenia AsyncResultType.](asyncresulttype-enumeration.md) Domyślnie `SingleResult`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                               | Opis
---------------------------------- | -------------------------------------------------
[Baza AsyncBase::Baza AsyncBase](#asyncbase) | Inicjuje wystąpienie klasy `AsyncBase`.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                         | Opis
-------------------------------------------- | -------------------------------------------------------------------------------------
[AsyncBase::Anuluj](#cancel)                 | Anuluje operację asynchronizacyjną.
[AsyncBase::Zamknij](#close)                   | Zamyka operację asynchronicznie.
[AsyncBase::FireCompletion](#firecompletion) | Wywołuje program obsługi zdarzeń ukończenia lub resetuje delegata postępu wewnętrznego.
[Baza AsyncBase::FireProgress](#fireprogress)     | Wywołuje bieżący program obsługi zdarzeń postępu.
[Baza AsyncBase::get_ErrorCode](#get-errorcode)   | Pobiera kod błędu dla bieżącej operacji asynchroniiowej.
[Baza AsyncBase::get_Id](#get-id)                 | Pobiera dojście operacji asynchroniiowej.
[Baza AsyncBase::get_Status](#get-status)         | Pobiera wartość, która wskazuje stan operacji asynchroniiowej.
[Baza AsyncBase::GetOnComplete](#getoncomplete)   | Kopiuje adres bieżącego programu obsługi zdarzeń zakończenia do określonej zmiennej.
[Baza AsyncBase::GetOnProgress](#getonprogress)   | Kopiuje adres bieżącego programu obsługi zdarzeń postępu do określonej zmiennej.
[AsyncBase::put_Id](#put-id)                 | Ustawia uchwyt operacji asynchroniiowej.
[AsyncBase::PutOnComplete](#putoncomplete)   | Ustawia adres programu obsługi zdarzeń zakończenia na określoną wartość.
[AsyncBase::PutOnProgress](#putonprogress)   | Ustawia adres programu obsługi zdarzeń postępu na określoną wartość.

### <a name="protected-methods"></a>Metody chronione

Nazwa                                                                         | Opis
---------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[AsyncBase::CheckValidStateForDelegateCall](#checkvalidstatefordelegatecall) | Sprawdza, czy właściwości delegata mogą być modyfikowane w bieżącym stanie asynchronicznym.
[AsyncBase::CheckValidStateForResultsCall](#checkvalidstateforresultscall)   | Sprawdza, czy wyniki operacji asynchronicznym mogą być zbierane w bieżącym stanie asynchronicznym.
[AsyncBase::ContinueAsyncOperation](#continueasyncoperation)                 | Określa, czy operacja asynchroniza powinna kontynuować przetwarzanie lub powinna zostać zatrzymana.
[Baza AsyncBase::Aktualnastasz](#currentstatus)                                   | Pobiera stan bieżącej operacji asynchroniiowej.
[AsyncBase::Kod błędu](#errorcode)                                           | Pobiera kod błędu dla bieżącej operacji asynchroniiowej.
[AsyncBase::OnCancel](#oncancel)                                             | Po zastąpieniu w klasie pochodnej, anuluje operację asynchroniza.
[AsyncBase::OnClose](#onclose)                                               | Po zastąpieniu w klasie pochodnej, zamyka operację asynchronicznie.
[Baza AsyncBase::OnStart](#onstart)                                               | Po zastąpieniu w klasie pochodnej, rozpoczyna operację asynchroniczną.
[AsyncBase::Start](#start)                                                   | Rozpoczyna operację asynchroniczną.
[AsyncBase::TryTransitionToKończony](#trytransitiontocompleted)             | Wskazuje, czy bieżąca operacja asynchroniza została ukończona.
[AsyncBase::TryTransitionToError](#trytransitiontoerror)                     | Wskazuje, czy określony kod błędu może modyfikować stan błędu wewnętrznego.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`AsyncBase`

`AsyncBase`

## <a name="requirements"></a>Wymagania

**Nagłówek:** async.h

**Obszar nazw:** Microsoft::WRL

## <a name="asyncbaseasyncbase"></a><a name="asyncbase"></a>Baza AsyncBase::Baza AsyncBase

Inicjuje wystąpienie klasy `AsyncBase`.

```cpp
AsyncBase();
```

## <a name="asyncbasecancel"></a><a name="cancel"></a>AsyncBase::Anuluj

Anuluje operację asynchronizacyjną.

```cpp
STDMETHOD(
   Cancel
)(void);
```

### <a name="return-value"></a>Wartość zwracana

Domyślnie zawsze zwraca S_OK.

### <a name="remarks"></a>Uwagi

`Cancel()`jest domyślną `IAsyncInfo::Cancel`implementacją programu i nie wykonuje żadnej rzeczywistej pracy. Aby faktycznie anulować operację asynchroniza, `OnCancel()` należy zastąpić metodę wirtualną czystego.

## <a name="asyncbasecheckvalidstatefordelegatecall"></a><a name="checkvalidstatefordelegatecall"></a>AsyncBase::CheckValidStateForDelegateCall

Sprawdza, czy właściwości delegata mogą być modyfikowane w bieżącym stanie asynchronicznym.

```cpp
inline HRESULT CheckValidStateForDelegateCall();
```

### <a name="return-value"></a>Wartość zwracana

S_OK, czy można zmodyfikować właściwości delegata; w przeciwnym razie E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasecheckvalidstateforresultscall"></a><a name="checkvalidstateforresultscall"></a>AsyncBase::CheckValidStateForResultsCall

Sprawdza, czy wyniki operacji asynchronicznym mogą być zbierane w bieżącym stanie asynchronicznym.

```cpp
inline HRESULT CheckValidStateForResultsCall();
```

### <a name="return-value"></a>Wartość zwracana

S_OK, czy można zbierać wyniki; w przeciwnym razie E_ILLEGAL_METHOD_CALLE_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseclose"></a><a name="close"></a>AsyncBase::Zamknij

Zamyka operację asynchronicznie.

```cpp
STDMETHOD(
   Close
)(void) override;
```

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli operacja zostanie zamknięta lub jest już zamknięta; w przeciwnym razie E_ILLEGAL_STATE_CHANGE.

### <a name="remarks"></a>Uwagi

`Close()`jest domyślną `IAsyncInfo::Close`implementacją programu i nie wykonuje żadnej rzeczywistej pracy. Aby faktycznie zamknąć operację asynchronicznie, `OnClose()` należy zastąpić metodę wirtualną czystego.

## <a name="asyncbasecontinueasyncoperation"></a><a name="continueasyncoperation"></a>AsyncBase::ContinueAsyncOperation

Określa, czy operacja asynchroniza powinna kontynuować przetwarzanie lub powinna zostać zatrzymana.

```cpp
inline bool ContinueAsyncOperation();
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli bieżący stan operacji asynchroniiowej jest *uruchomiony,* co oznacza, że operacja powinna być kontynuowana. W przeciwnym razie **false**, co oznacza, że operacja powinna zostać zatrzymana.

## <a name="asyncbasecurrentstatus"></a><a name="currentstatus"></a>Baza AsyncBase::Aktualnastasz

Pobiera stan bieżącej operacji asynchroniiowej.

```cpp
inline void CurrentStatus(
   Details::AsyncStatusInternal *status
);
```

### <a name="parameters"></a>Parametry

*Stan*<br/>
Lokalizacja, w której ta operacja przechowuje bieżący stan.

### <a name="remarks"></a>Uwagi

Ta operacja jest bezpieczna dla wątków.

## <a name="asyncbaseerrorcode"></a><a name="errorcode"></a>AsyncBase::Kod błędu

Pobiera kod błędu dla bieżącej operacji asynchroniiowej.

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>Parametry

*error*<br/>
Lokalizacja, w której ta operacja przechowuje bieżący kod błędu.

### <a name="remarks"></a>Uwagi

Ta operacja jest bezpieczna dla wątków.

## <a name="asyncbasefirecompletion"></a><a name="firecompletion"></a>AsyncBase::FireCompletion

Wywołuje program obsługi zdarzeń ukończenia lub resetuje delegata postępu wewnętrznego.

```cpp
void FireCompletion(
   void
) override;

virtual void FireCompletion();
```

### <a name="remarks"></a>Uwagi

Pierwsza wersja `FireCompletion()` resetuje zmienną delegata postępu wewnętrznego. Druga wersja wywołuje program obsługi zdarzeń zakończenia, jeśli operacja asynchroniza została ukończona.

## <a name="asyncbasefireprogress"></a><a name="fireprogress"></a>Baza AsyncBase::FireProgress

Wywołuje bieżący program obsługi zdarzeń postępu.

```cpp
void FireProgress(
   const typename ProgressTraits::Arg2Type arg
);
```

### <a name="parameters"></a>Parametry

*Arg*<br/>
Metoda obsługi zdarzeń do wywołania.

### <a name="remarks"></a>Uwagi

`ProgressTraits`pochodzi z [ArgTraitsHelper Structure](argtraitshelper-structure.md).

## <a name="asyncbaseget_errorcode"></a><a name="get-errorcode"></a>Baza AsyncBase::get_ErrorCode

Pobiera kod błędu dla bieżącej operacji asynchroniiowej.

```cpp
STDMETHOD(
   get_ErrorCode
)(HRESULT* errorCode) override;
```

### <a name="parameters"></a>Parametry

*Errorcode*<br/>
Lokalizacja, w której jest przechowywany bieżący kod błędu.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie E_ILLEGAL_METHOD_CALL, jeśli bieżąca operacja asynchroniza jest zamknięta.

## <a name="asyncbaseget_id"></a><a name="get-id"></a>Baza AsyncBase::get_Id

Pobiera dojście operacji asynchroniiowej.

```cpp
STDMETHOD(
   get_Id
)(unsigned int *id) override;
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
Miejsce przechowywania uchwytu.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie E_ILLEGAL_METHOD_CALL.

### <a name="remarks"></a>Uwagi

Ta metoda `IAsyncInfo::get_Id`implementuje .

## <a name="asyncbaseget_status"></a><a name="get-status"></a>Baza AsyncBase::get_Status

Pobiera wartość, która wskazuje stan operacji asynchroniiowej.

```cpp
STDMETHOD(
   get_Status
)(AsyncStatus *status) override;
```

### <a name="parameters"></a>Parametry

*Stan*<br/>
Lokalizacja, w której ma być przechowywany stan. Aby uzyskać więcej `Windows::Foundation::AsyncStatus` informacji, zobacz wyliczenie.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie E_ILLEGAL_METHOD_CALL.

### <a name="remarks"></a>Uwagi

Ta metoda `IAsyncInfo::get_Status`implementuje .

## <a name="asyncbasegetoncomplete"></a><a name="getoncomplete"></a>Baza AsyncBase::GetOnComplete

Kopiuje adres bieżącego programu obsługi zdarzeń zakończenia do określonej zmiennej.

```cpp
STDMETHOD(
   GetOnComplete
)(TComplete** completeHandler);
```

### <a name="parameters"></a>Parametry

*completeHandler*<br/>
Lokalizacja, w której jest przechowywany adres bieżącego programu obsługi zdarzeń zakończenia.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasegetonprogress"></a><a name="getonprogress"></a>Baza AsyncBase::GetOnProgress

Kopiuje adres bieżącego programu obsługi zdarzeń postępu do określonej zmiennej.

```cpp
STDMETHOD(
   GetOnProgress
)(TProgress** progressHandler);
```

### <a name="parameters"></a>Parametry

*progressHandler (uchwyt progressHandler)*<br/>
Lokalizacja, w której przechowywany jest adres bieżącego programu obsługi zdarzeń postępu.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseoncancel"></a><a name="oncancel"></a>AsyncBase::OnCancel

Po zastąpieniu w klasie pochodnej, anuluje operację asynchroniza.

```cpp
virtual void OnCancel(
   void
) = 0;
```

## <a name="asyncbaseonclose"></a><a name="onclose"></a>AsyncBase::OnClose

Po zastąpieniu w klasie pochodnej, zamyka operację asynchronicznie.

```cpp
virtual void OnClose(
   void
) = 0;
```

## <a name="asyncbaseonstart"></a><a name="onstart"></a>Baza AsyncBase::OnStart

Po zastąpieniu w klasie pochodnej, rozpoczyna operację asynchroniczną.

```cpp
virtual HRESULT OnStart(
   void
) = 0;
```

## <a name="asyncbaseput_id"></a><a name="put-id"></a>AsyncBase::put_Id

Ustawia uchwyt operacji asynchroniiowej.

```cpp
STDMETHOD(
   put_Id
)(const unsigned int id);
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
Uchwyt niezerowy.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie E_INVALIDARG lub E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseputoncomplete"></a><a name="putoncomplete"></a>AsyncBase::PutOnComplete

Ustawia adres programu obsługi zdarzeń zakończenia na określoną wartość.

```cpp
STDMETHOD(
   PutOnComplete
)(TComplete* completeHandler);
```

### <a name="parameters"></a>Parametry

*completeHandler*<br/>
Adres, na który jest ustawiony program obsługi zdarzeń zakończenia.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseputonprogress"></a><a name="putonprogress"></a>AsyncBase::PutOnProgress

Ustawia adres programu obsługi zdarzeń postępu na określoną wartość.

```cpp
STDMETHOD(
   PutOnProgress
)(TProgress* progressHandler);
```

### <a name="parameters"></a>Parametry

*progressHandler (uchwyt progressHandler)*<br/>
Adres, na który jest ustawiony program obsługi zdarzeń postępu.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasestart"></a><a name="start"></a>AsyncBase::Start

Rozpoczyna operację asynchroniczną.

```cpp
STDMETHOD(
   Start
)(void);
```

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli operacja zostanie uruchomiona lub jest już uruchomiona; w przeciwnym razie E_ILLEGAL_STATE_CHANGE.

### <a name="remarks"></a>Uwagi

`Start()`jest chroniona metoda, która nie jest widoczna zewnętrznie, ponieważ operacje asynchronicznego "hot start" przed powrotem do wywołującego.

## <a name="asyncbasetrytransitiontocompleted"></a><a name="trytransitiontocompleted"></a>AsyncBase::TryTransitionToKończony

Wskazuje, czy bieżąca operacja asynchroniza została ukończona.

```cpp
bool TryTransitionToCompleted(
   void
);
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli operacja asynchroniza zakończona; w przeciwnym razie **false**.

## <a name="asyncbasetrytransitiontoerror"></a><a name="trytransitiontoerror"></a>AsyncBase::TryTransitionToError

Wskazuje, czy określony kod błędu może modyfikować stan błędu wewnętrznego.

```cpp
bool TryTransitionToError(
   const HRESULT error
);
```

### <a name="parameters"></a>Parametry

*error*<br/>
Błąd HRESULT.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli stan błędu wewnętrznego został zmieniony; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta operacja modyfikuje stan błędu tylko wtedy, gdy stan błędu jest już ustawiony na S_OK. Ta operacja nie ma wpływu, jeśli stan błędu jest już błąd, anulowane, zakończone lub zamknięte.
