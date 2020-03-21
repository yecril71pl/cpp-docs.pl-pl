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
ms.openlocfilehash: 09819c9e8dd924581ce8cd67233d273f7e8d62ca
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079896"
---
# <a name="asyncbase-class"></a>AsyncBase — Klasa

Implementuje asynchroniczną maszynę stanu środowisko wykonawcze systemu Windows.

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

*TComplete*<br/>
Program obsługi zdarzeń, który jest wywoływany po zakończeniu operacji asynchronicznej.

*TProgress*<br/>
Procedura obsługi zdarzeń wywoływana, gdy działająca operacja asynchroniczna zgłosi bieżący postęp operacji.

*Result*<br/>
Jedna z wartości wyliczenia [klasy AsyncResultType](asyncresulttype-enumeration.md) . Domyślnie `SingleResult`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Name (Nazwa)                               | Opis
---------------------------------- | -------------------------------------------------
[AsyncBase:: AsyncBase](#asyncbase) | Inicjuje wystąpienie klasy `AsyncBase`.

### <a name="public-methods"></a>Metody publiczne

Name (Nazwa)                                         | Opis
-------------------------------------------- | -------------------------------------------------------------------------------------
[AsyncBase:: Cancel](#cancel)                 | Anuluje operację asynchroniczną.
[AsyncBase:: Close](#close)                   | Zamyka operację asynchroniczną.
[AsyncBase:: FireCompletion —](#firecompletion) | Wywołuje program obsługi zdarzeń ukończenia lub resetuje delegata postępu wewnętrznego.
[AsyncBase:: FireProgress —](#fireprogress)     | Wywołuje bieżącą procedurę obsługi zdarzeń postępu.
[AsyncBase:: get_ErrorCode](#get-errorcode)   | Pobiera kod błędu dla bieżącej operacji asynchronicznej.
[AsyncBase:: get_Id](#get-id)                 | Pobiera dojście operacji asynchronicznej.
[AsyncBase:: get_Status](#get-status)         | Pobiera wartość wskazującą stan operacji asynchronicznej.
[AsyncBase:: GetOnComplete —](#getoncomplete)   | Kopiuje adres bieżącego programu obsługi zdarzeń ukończenia do określonej zmiennej.
[AsyncBase:: GetOnProgress —](#getonprogress)   | Kopiuje adres bieżącego programu obsługi zdarzeń postępu do określonej zmiennej.
[AsyncBase::p ut_Id](#put-id)                 | Ustawia dojście operacji asynchronicznej.
[AsyncBase::P utOnComplete](#putoncomplete)   | Ustawia adres programu obsługi zdarzeń zakończenia dla określonej wartości.
[AsyncBase::P utOnProgress](#putonprogress)   | Ustawia adres programu obsługi zdarzeń postępu dla określonej wartości.

### <a name="protected-methods"></a>Metody chronione

Name (Nazwa)                                                                         | Opis
---------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[AsyncBase:: CheckValidStateForDelegateCall —](#checkvalidstatefordelegatecall) | Testuje, czy właściwości delegatów mogą być modyfikowane w bieżącym stanie asynchronicznym.
[AsyncBase:: CheckValidStateForResultsCall —](#checkvalidstateforresultscall)   | Testuje, czy wyniki operacji asynchronicznej mogą być zbierane w bieżącym stanie asynchronicznym.
[AsyncBase:: ContinueAsyncOperation —](#continueasyncoperation)                 | Określa, czy operacja asynchroniczna ma kontynuować przetwarzanie lub czy ma zostać zatrzymana.
[AsyncBase:: currentStatus —](#currentstatus)                                   | Pobiera stan bieżącej operacji asynchronicznej.
[AsyncBase:: ErrorCode](#errorcode)                                           | Pobiera kod błędu dla bieżącej operacji asynchronicznej.
[AsyncBase:: OnCancel](#oncancel)                                             | Gdy jest zastępowany w klasie pochodnej, anuluje operację asynchroniczną.
[AsyncBase:: OnClose](#onclose)                                               | Gdy jest zastępowany w klasie pochodnej, zamyka operację asynchroniczną.
[AsyncBase:: OnStart](#onstart)                                               | Gdy jest zastępowany w klasie pochodnej, uruchamia operację asynchroniczną.
[AsyncBase:: Start](#start)                                                   | Uruchamia operację asynchroniczną.
[AsyncBase:: TryTransitionToCompleted —](#trytransitiontocompleted)             | Wskazuje, czy bieżąca operacja asynchroniczna została ukończona.
[AsyncBase:: TryTransitionToError —](#trytransitiontoerror)                     | Wskazuje, czy określony kod błędu może zmodyfikować stan błędu wewnętrznego.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`AsyncBase`

`AsyncBase`

## <a name="requirements"></a>Wymagania

**Nagłówek:** Async. h

**Przestrzeń nazw:** Microsoft:: WRL

## <a name="asyncbaseasyncbase"></a><a name="asyncbase"></a>AsyncBase:: AsyncBase

Inicjuje wystąpienie klasy `AsyncBase`.

```cpp
AsyncBase();
```

## <a name="asyncbasecancel"></a><a name="cancel"></a>AsyncBase:: Cancel

Anuluje operację asynchroniczną.

```cpp
STDMETHOD(
   Cancel
)(void);
```

### <a name="return-value"></a>Wartość zwracana

Domyślnie zawsze zwraca S_OK.

### <a name="remarks"></a>Uwagi

`Cancel()` jest domyślną implementacją `IAsyncInfo::Cancel`i nie ma rzeczywistej pracy. Aby faktycznie anulować operację asynchroniczną, Zastąp `OnCancel()` czystą metodą wirtualną.

## <a name="asyncbasecheckvalidstatefordelegatecall"></a><a name="checkvalidstatefordelegatecall"></a>AsyncBase:: CheckValidStateForDelegateCall —

Testuje, czy właściwości delegatów mogą być modyfikowane w bieżącym stanie asynchronicznym.

```cpp
inline HRESULT CheckValidStateForDelegateCall();
```

### <a name="return-value"></a>Wartość zwracana

S_OK, czy można modyfikować właściwości delegata; w przeciwnym razie E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasecheckvalidstateforresultscall"></a><a name="checkvalidstateforresultscall"></a>AsyncBase:: CheckValidStateForResultsCall —

Testuje, czy wyniki operacji asynchronicznej mogą być zbierane w bieżącym stanie asynchronicznym.

```cpp
inline HRESULT CheckValidStateForResultsCall();
```

### <a name="return-value"></a>Wartość zwracana

S_OK, czy można zbierać wyniki; w przeciwnym razie E_ILLEGAL_METHOD_CALLE_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseclose"></a><a name="close"></a>AsyncBase:: Close

Zamyka operację asynchroniczną.

```cpp
STDMETHOD(
   Close
)(void) override;
```

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli operacja zostanie zamknięta lub jest już ZAMKNIĘTA; w przeciwnym razie E_ILLEGAL_STATE_CHANGE.

### <a name="remarks"></a>Uwagi

`Close()` jest domyślną implementacją `IAsyncInfo::Close`i nie ma rzeczywistej pracy. Aby rzeczywiście zamknąć operację asynchroniczną, Zastąp `OnClose()` czysta metoda wirtualna.

## <a name="asyncbasecontinueasyncoperation"></a><a name="continueasyncoperation"></a>AsyncBase:: ContinueAsyncOperation —

Określa, czy operacja asynchroniczna ma kontynuować przetwarzanie lub czy ma zostać zatrzymana.

```cpp
inline bool ContinueAsyncOperation();
```

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli bieżący stan operacji asynchronicznej jest *rozpoczęty*, co oznacza, że operacja powinna być kontynuowana. W przeciwnym razie **wartość false**, co oznacza, że operacja powinna zostać zatrzymana.

## <a name="asyncbasecurrentstatus"></a><a name="currentstatus"></a>AsyncBase:: currentStatus —

Pobiera stan bieżącej operacji asynchronicznej.

```cpp
inline void CurrentStatus(
   Details::AsyncStatusInternal *status
);
```

### <a name="parameters"></a>Parametry

*Stany*<br/>
Lokalizacja, w której ta operacja przechowuje bieżący stan.

### <a name="remarks"></a>Uwagi

Ta operacja jest bezpieczna wątkowo.

## <a name="asyncbaseerrorcode"></a><a name="errorcode"></a>AsyncBase:: ErrorCode

Pobiera kod błędu dla bieżącej operacji asynchronicznej.

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>Parametry

*Porn*<br/>
Lokalizacja, w której ta operacja przechowuje bieżący kod błędu.

### <a name="remarks"></a>Uwagi

Ta operacja jest bezpieczna wątkowo.

## <a name="asyncbasefirecompletion"></a><a name="firecompletion"></a>AsyncBase:: FireCompletion —

Wywołuje program obsługi zdarzeń ukończenia lub resetuje delegata postępu wewnętrznego.

```cpp
void FireCompletion(
   void
) override;

virtual void FireCompletion();
```

### <a name="remarks"></a>Uwagi

Pierwsza wersja `FireCompletion()` resetuje zmienną oddelegowania postępu wewnętrznego. Druga wersja wywołuje program obsługi zdarzeń zakończenia w przypadku ukończenia operacji asynchronicznej.

## <a name="asyncbasefireprogress"></a><a name="fireprogress"></a>AsyncBase:: FireProgress —

Wywołuje bieżącą procedurę obsługi zdarzeń postępu.

```cpp
void FireProgress(
   const typename ProgressTraits::Arg2Type arg
);
```

### <a name="parameters"></a>Parametry

*ARG*<br/>
Metoda obsługi zdarzeń do wywołania.

### <a name="remarks"></a>Uwagi

`ProgressTraits` pochodzi od [struktury ArgTraitsHelper](argtraitshelper-structure.md).

## <a name="asyncbaseget_errorcode"></a><a name="get-errorcode"></a>AsyncBase:: get_ErrorCode

Pobiera kod błędu dla bieżącej operacji asynchronicznej.

```cpp
STDMETHOD(
   get_ErrorCode
)(HRESULT* errorCode) override;
```

### <a name="parameters"></a>Parametry

*Kodzie*<br/>
Lokalizacja, w której jest przechowywany bieżący kod błędu.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie E_ILLEGAL_METHOD_CALL, jeśli bieżąca operacja asynchroniczna jest zamknięta.

## <a name="asyncbaseget_id"></a><a name="get-id"></a>AsyncBase:: get_Id

Pobiera dojście operacji asynchronicznej.

```cpp
STDMETHOD(
   get_Id
)(unsigned int *id) override;
```

### <a name="parameters"></a>Parametry

*id*<br/>
Lokalizacja, w której ma być przechowywane dojście.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie E_ILLEGAL_METHOD_CALL.

### <a name="remarks"></a>Uwagi

Ta metoda implementuje `IAsyncInfo::get_Id`.

## <a name="asyncbaseget_status"></a><a name="get-status"></a>AsyncBase:: get_Status

Pobiera wartość wskazującą stan operacji asynchronicznej.

```cpp
STDMETHOD(
   get_Status
)(AsyncStatus *status) override;
```

### <a name="parameters"></a>Parametry

*Stany*<br/>
Lokalizacja, w której stan ma być przechowywany. Aby uzyskać więcej informacji, zobacz `Windows::Foundation::AsyncStatus` Enumeration.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie E_ILLEGAL_METHOD_CALL.

### <a name="remarks"></a>Uwagi

Ta metoda implementuje `IAsyncInfo::get_Status`.

## <a name="asyncbasegetoncomplete"></a><a name="getoncomplete"></a>AsyncBase:: GetOnComplete —

Kopiuje adres bieżącego programu obsługi zdarzeń ukończenia do określonej zmiennej.

```cpp
STDMETHOD(
   GetOnComplete
)(TComplete** completeHandler);
```

### <a name="parameters"></a>Parametry

*completeHandler*<br/>
Lokalizacja, w której jest przechowywany adres bieżącego programu obsługi zdarzeń zakończenia.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasegetonprogress"></a><a name="getonprogress"></a>AsyncBase:: GetOnProgress —

Kopiuje adres bieżącego programu obsługi zdarzeń postępu do określonej zmiennej.

```cpp
STDMETHOD(
   GetOnProgress
)(TProgress** progressHandler);
```

### <a name="parameters"></a>Parametry

*progressHandler*<br/>
Lokalizacja, w której jest przechowywany adres bieżącego programu obsługi zdarzeń postępu.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseoncancel"></a><a name="oncancel"></a>AsyncBase:: OnCancel

Gdy jest zastępowany w klasie pochodnej, anuluje operację asynchroniczną.

```cpp
virtual void OnCancel(
   void
) = 0;
```

## <a name="asyncbaseonclose"></a><a name="onclose"></a>AsyncBase:: OnClose

Gdy jest zastępowany w klasie pochodnej, zamyka operację asynchroniczną.

```cpp
virtual void OnClose(
   void
) = 0;
```

## <a name="asyncbaseonstart"></a><a name="onstart"></a>AsyncBase:: OnStart

Gdy jest zastępowany w klasie pochodnej, uruchamia operację asynchroniczną.

```cpp
virtual HRESULT OnStart(
   void
) = 0;
```

## <a name="asyncbaseput_id"></a><a name="put-id"></a>AsyncBase::p ut_Id

Ustawia dojście operacji asynchronicznej.

```cpp
STDMETHOD(
   put_Id
)(const unsigned int id);
```

### <a name="parameters"></a>Parametry

*id*<br/>
Niezerowy uchwyt.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie E_INVALIDARG lub E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseputoncomplete"></a><a name="putoncomplete"></a>AsyncBase::P utOnComplete

Ustawia adres programu obsługi zdarzeń zakończenia dla określonej wartości.

```cpp
STDMETHOD(
   PutOnComplete
)(TComplete* completeHandler);
```

### <a name="parameters"></a>Parametry

*completeHandler*<br/>
Adres, na który jest ustawiony program obsługi zdarzeń ukończenia.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseputonprogress"></a><a name="putonprogress"></a>AsyncBase::P utOnProgress

Ustawia adres programu obsługi zdarzeń postępu dla określonej wartości.

```cpp
STDMETHOD(
   PutOnProgress
)(TProgress* progressHandler);
```

### <a name="parameters"></a>Parametry

*progressHandler*<br/>
Adres, na który jest ustawiony program obsługi zdarzeń postępu.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasestart"></a><a name="start"></a>AsyncBase:: Start

Uruchamia operację asynchroniczną.

```cpp
STDMETHOD(
   Start
)(void);
```

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli operacja jest uruchomiona lub jest już uruchomiona; w przeciwnym razie E_ILLEGAL_STATE_CHANGE.

### <a name="remarks"></a>Uwagi

`Start()` to metoda chroniona, która nie jest widoczna zewnętrznie, ponieważ operacje asynchroniczne "gorąca" są uruchamiane przed powrotem do obiektu wywołującego.

## <a name="asyncbasetrytransitiontocompleted"></a><a name="trytransitiontocompleted"></a>AsyncBase:: TryTransitionToCompleted —

Wskazuje, czy bieżąca operacja asynchroniczna została ukończona.

```cpp
bool TryTransitionToCompleted(
   void
);
```

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli operacja asynchroniczna została ukończona; w przeciwnym razie **false**.

## <a name="asyncbasetrytransitiontoerror"></a><a name="trytransitiontoerror"></a>AsyncBase:: TryTransitionToError —

Wskazuje, czy określony kod błędu może zmodyfikować stan błędu wewnętrznego.

```cpp
bool TryTransitionToError(
   const HRESULT error
);
```

### <a name="parameters"></a>Parametry

*Porn*<br/>
Błąd HRESULT.

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli stan błędu wewnętrznego został zmieniony; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta operacja modyfikuje stan błędu tylko wtedy, gdy stan błędu jest już ustawiony na S_OK. Ta operacja nie działa, jeśli stan błędu to już błąd, anulowany, ukończony lub zamknięty.
