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
ms.openlocfilehash: 367d0b0cd3197623b27ee1a50e804cca797aedf3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398826"
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

template <typename TComplete, AsyncResultType resultType>
class AsyncBase<TComplete, Details::Nil, resultType> :
    public Microsoft::WRL::Implements<IAsyncInfo>;
```

### <a name="parameters"></a>Parametry

*TComplete*<br/>
Obsługa zdarzeń, która jest wywoływana po zakończeniu operacji asynchronicznej.

*TProgress*<br/>
Obsługa zdarzeń, która jest wywołana, gdy operacja działa asynchroniczna raportuje Bieżący postęp operacji.

*resultType*<br/>
Jedną z [asyncresulttype —](asyncresulttype-enumeration.md) wartości wyliczenia. Domyślnie `SingleResult`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                               | Opis
---------------------------------- | -------------------------------------------------
[AsyncBase::AsyncBase](#asyncbase) | Inicjuje wystąpienie `AsyncBase` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                         | Opis
-------------------------------------------- | -------------------------------------------------------------------------------------
[AsyncBase::Cancel](#cancel)                 | Anuluje operację asynchroniczną.
[AsyncBase::Close](#close)                   | Zamyka operację asynchroniczną.
[AsyncBase::FireCompletion](#firecompletion) | Wywołuje program obsługi zdarzenia zakończenia lub resetuje delegata wewnętrznego postępu.
[AsyncBase::FireProgress](#fireprogress)     | Wywołuje Bieżący postęp obsługi zdarzeń.
[AsyncBase::get_ErrorCode](#get-errorcode)   | Pobiera kod błędu dla bieżącej operacji asynchronicznej.
[AsyncBase::get_Id](#get-id)                 | Pobiera uchwyt operację asynchroniczną.
[AsyncBase::get_Status](#get-status)         | Pobiera wartość, która wskazuje stan operacji asynchronicznej.
[AsyncBase::GetOnComplete](#getoncomplete)   | Kopiuje adres bieżącej obsługi zdarzeń zakończenia do określonej zmiennej.
[AsyncBase::GetOnProgress](#getonprogress)   | Kopiuje adres bieżącej obsługi zdarzeń postępu do określonej zmiennej.
[AsyncBase::put_Id](#put-id)                 | Ustawia uchwyt operację asynchroniczną.
[AsyncBase::PutOnComplete](#putoncomplete)   | Ustawia adres procedury obsługi zdarzeń zakończenia z podaną wartością.
[AsyncBase::PutOnProgress](#putonprogress)   | Ustawia adres obsługi zdarzenia postępu z podaną wartością.


### <a name="protected-methods"></a>Metody chronione

Nazwa                                                                         | Opis
---------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[AsyncBase::CheckValidStateForDelegateCall](#checkvalidstatefordelegatecall) | Sprawdza, czy można zmodyfikować właściwości delegata w bieżącym stanie asynchronicznego.
[AsyncBase::CheckValidStateForResultsCall](#checkvalidstateforresultscall)   | Sprawdza, czy wyniki operacji asynchronicznej może być zbierana w bieżącym stanie asynchronicznego.
[AsyncBase::ContinueAsyncOperation](#continueasyncoperation)                 | Określa, czy operacja asynchroniczna przetwarzanie powinno być kontynuowane, czy należy wstrzymać.
[Asyncbase::currentStatus —](#currentstatus)                                   | Pobiera stan bieżącej operacji asynchronicznej.
[AsyncBase::ErrorCode](#errorcode)                                           | Pobiera kod błędu dla bieżącej operacji asynchronicznej.
[AsyncBase::OnCancel](#oncancel)                                             | W przypadku przesłonięcia w klasie pochodnej, anuluje operację asynchroniczną.
[AsyncBase::OnClose](#onclose)                                               | W przypadku przesłonięcia w klasie pochodnej, zamyka operację asynchroniczną.
[AsyncBase::OnStart](#onstart)                                               | W przypadku przesłonięcia w klasie pochodnej, rozpoczyna operację asynchroniczną.
[AsyncBase::Start](#start)                                                   | Rozpoczyna operację asynchroniczną.
[AsyncBase::TryTransitionToCompleted](#trytransitiontocompleted)             | Wskazuje, czy bieżąca operacja asynchroniczna została ukończona.
[AsyncBase::TryTransitionToError](#trytransitiontoerror)                     | Wskazuje, czy określonego kodu błędu, można zmodyfikować stanu błędu wewnętrznego.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`AsyncBase`

`AsyncBase`

## <a name="requirements"></a>Wymagania

**Nagłówek:** async.h

**Namespace:** Microsoft::WRL

## <a name="asyncbase"></a>AsyncBase::AsyncBase

Inicjuje wystąpienie `AsyncBase` klasy.

```cpp
AsyncBase();
```

## <a name="cancel"></a>AsyncBase::Cancel

Anuluje operację asynchroniczną.

```cpp
STDMETHOD(
   Cancel
)(void);
```

### <a name="return-value"></a>Wartość zwracana

Domyślnie zawsze zwraca wartość S_OK.

### <a name="remarks"></a>Uwagi

`Cancel()` jest domyślna Implementacja klasy `IAsyncInfo::Cancel`, a nie rzeczywiste działa. Aby rzeczywiście anulować operację asynchroniczną, Zastąp `OnCancel()` czystej wirtualnej metody.

## <a name="checkvalidstatefordelegatecall"></a>AsyncBase::CheckValidStateForDelegateCall

Sprawdza, czy można zmodyfikować właściwości delegata w bieżącym stanie asynchronicznego.

```cpp
inline HRESULT CheckValidStateForDelegateCall();
```

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli można zmodyfikować właściwości delegata; w przeciwnym razie E_ILLEGAL_METHOD_CALL.

## <a name="checkvalidstateforresultscall"></a>AsyncBase::CheckValidStateForResultsCall

Sprawdza, czy wyniki operacji asynchronicznej może być zbierana w bieżącym stanie asynchronicznego.

```cpp
inline HRESULT CheckValidStateForResultsCall();
```

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli wyniki mogą być zbierane; w przeciwnym razie E_ILLEGAL_METHOD_CALLE_ILLEGAL_METHOD_CALL.

## <a name="close"></a>AsyncBase::Close

Zamyka operację asynchroniczną.

```cpp
STDMETHOD(
   Close
)(void) override;
```

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli operacja zostanie zamknięty lub już zamknięte; w przeciwnym razie E_ILLEGAL_STATE_CHANGE.

### <a name="remarks"></a>Uwagi

`Close()` jest domyślna Implementacja klasy `IAsyncInfo::Close`, a nie rzeczywiste działa. Aby rzeczywiście zamknąć operację asynchroniczną, należy zastąpić `OnClose()` czystej wirtualnej metody.

## <a name="continueasyncoperation"></a>AsyncBase::ContinueAsyncOperation

Określa, czy operacja asynchroniczna przetwarzanie powinno być kontynuowane, czy należy wstrzymać.

```cpp
inline bool ContinueAsyncOperation();
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli bieżący stan operacji asynchronicznej jest *pracę*, co oznacza, że operacja powinno być kontynuowane. W przeciwnym razie **false**, co oznacza, że operacja należy wstrzymać.

## <a name="currentstatus"></a>Asyncbase::currentStatus —

Pobiera stan bieżącej operacji asynchronicznej.

```cpp
inline void CurrentStatus(
   Details::AsyncStatusInternal *status
);
```

### <a name="parameters"></a>Parametry

*status*<br/>
Lokalizacja, w którym ta operacja zapisuje bieżący stan.

### <a name="remarks"></a>Uwagi

Ta operacja jest metodą o bezpiecznych wątkach.

## <a name="errorcode"></a>AsyncBase::ErrorCode

Pobiera kod błędu dla bieżącej operacji asynchronicznej.

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>Parametry

*Błąd*<br/>
Lokalizacja, w której przechowuje bieżący kod błędu w tej operacji.

### <a name="remarks"></a>Uwagi

Ta operacja jest metodą o bezpiecznych wątkach.

## <a name="firecompletion"></a>AsyncBase::FireCompletion

Wywołuje program obsługi zdarzenia zakończenia lub resetuje delegata wewnętrznego postępu.

```cpp
void FireCompletion(
   void
) override;

virtual void FireCompletion();
```

### <a name="remarks"></a>Uwagi

Pierwsza wersja `FireCompletion()` resetuje zmiennej delegata wewnętrznego postępu. Druga wersja wywołuje program obsługi zdarzeń uzupełniania, jeśli operacja asynchroniczna została zakończona.

## <a name="fireprogress"></a>AsyncBase::FireProgress

Wywołuje Bieżący postęp obsługi zdarzeń.

```cpp
void FireProgress(
   const typename ProgressTraits::Arg2Type arg
);
```

### <a name="parameters"></a>Parametry

*ARG*<br/>
Metoda obsługi zdarzeń do wywołania.

### <a name="remarks"></a>Uwagi

`ProgressTraits` jest tworzony na podstawie [argtraitshelper — struktura](argtraitshelper-structure.md).

## <a name="get-errorcode"></a>AsyncBase::get_ErrorCode

Pobiera kod błędu dla bieżącej operacji asynchronicznej.

```cpp
STDMETHOD(
   get_ErrorCode
)(HRESULT* errorCode) override;
```

### <a name="parameters"></a>Parametry

*errorCode*<br/>
Lokalizacja przechowywania bieżący kod błędu.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie E_ILLEGAL_METHOD_CALL, jeśli bieżąca operacja asynchroniczna jest zamknięty.

## <a name="get-id"></a>AsyncBase::get_Id

Pobiera uchwyt operację asynchroniczną.

```cpp
STDMETHOD(
   get_Id
)(unsigned int *id) override;
```

### <a name="parameters"></a>Parametry

*id*<br/>
Lokalizacja, gdzie ma być przechowywany uchwytu.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie E_ILLEGAL_METHOD_CALL.

### <a name="remarks"></a>Uwagi

Ta metoda implementuje `IAsyncInfo::get_Id`.

## <a name="get-status"></a>AsyncBase::get_Status

Pobiera wartość, która wskazuje stan operacji asynchronicznej.

```cpp
STDMETHOD(
   get_Status
)(AsyncStatus *status) override;
```

### <a name="parameters"></a>Parametry

*status*<br/>
Lokalizacja, w których stan ma być przechowywany. Aby uzyskać więcej informacji, zobacz `Windows::Foundation::AsyncStatus` wyliczenia.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie E_ILLEGAL_METHOD_CALL.

### <a name="remarks"></a>Uwagi

Ta metoda implementuje `IAsyncInfo::get_Status`.

## <a name="getoncomplete"></a>AsyncBase::GetOnComplete

Kopiuje adres bieżącej obsługi zdarzeń zakończenia do określonej zmiennej.

```cpp
STDMETHOD(
   GetOnComplete
)(TComplete** completeHandler);
```

### <a name="parameters"></a>Parametry

*completeHandler*<br/>
Lokalizacja przechowywania adres bieżącej obsługi zdarzeń zakończenia.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie E_ILLEGAL_METHOD_CALL.

## <a name="getonprogress"></a>AsyncBase::GetOnProgress

Kopiuje adres bieżącej obsługi zdarzeń postępu do określonej zmiennej.

```cpp
STDMETHOD(
   GetOnProgress
)(TProgress** progressHandler);
```

### <a name="parameters"></a>Parametry

*progressHandler*<br/>
Lokalizacja przechowywania adres bieżącej obsługi zdarzeń postępu.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie E_ILLEGAL_METHOD_CALL.

## <a name="oncancel"></a>AsyncBase::OnCancel

W przypadku przesłonięcia w klasie pochodnej, anuluje operację asynchroniczną.

```cpp
virtual void OnCancel(
   void
) = 0;
```

## <a name="onclose"></a>AsyncBase::OnClose

W przypadku przesłonięcia w klasie pochodnej, zamyka operację asynchroniczną.

```cpp
virtual void OnClose(
   void
) = 0;
```

## <a name="onstart"></a>AsyncBase::OnStart

W przypadku przesłonięcia w klasie pochodnej, rozpoczyna operację asynchroniczną.

```cpp
virtual HRESULT OnStart(
   void
) = 0;
```

## <a name="put-id"></a>AsyncBase::put_Id

Ustawia uchwyt operację asynchroniczną.

```cpp
STDMETHOD(
   put_Id
)(const unsigned int id);
```

### <a name="parameters"></a>Parametry

*id*<br/>
Dojście wartość różną od zera.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie E_INVALIDARG lub E_ILLEGAL_METHOD_CALL.

## <a name="putoncomplete"></a>AsyncBase::PutOnComplete

Ustawia adres procedury obsługi zdarzeń zakończenia z podaną wartością.

```cpp
STDMETHOD(
   PutOnComplete
)(TComplete* completeHandler);
```

### <a name="parameters"></a>Parametry

*completeHandler*<br/>
Adres, do którego program obsługi zdarzeń zakończenia jest ustawiony.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie E_ILLEGAL_METHOD_CALL.

## <a name="putonprogress"></a>AsyncBase::PutOnProgress

Ustawia adres obsługi zdarzenia postępu z podaną wartością.

```cpp
STDMETHOD(
   PutOnProgress
)(TProgress* progressHandler);
```

### <a name="parameters"></a>Parametry

*progressHandler*<br/>
Adres, w którym ustawiono program obsługi zdarzeń postępu.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie E_ILLEGAL_METHOD_CALL.

## <a name="start"></a>AsyncBase::Start

Rozpoczyna operację asynchroniczną.

```cpp
STDMETHOD(
   Start
)(void);
```

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli operacja rozpoczyna się lub jest już uruchomiona; w przeciwnym razie E_ILLEGAL_STATE_CHANGE.

### <a name="remarks"></a>Uwagi

`Start()` jest metodą chronionych, który nie jest widoczna na zewnątrz, ponieważ operacje asynchroniczne oznaczenie "gorąca start" przed zwróceniem do obiektu wywołującego.

## <a name="trytransitiontocompleted"></a>AsyncBase::TryTransitionToCompleted

Wskazuje, czy bieżąca operacja asynchroniczna została ukończona.

```cpp
bool TryTransitionToCompleted(
   void
);
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli operacja asynchroniczna została ukończona; w przeciwnym razie **false**.

## <a name="trytransitiontoerror"></a>AsyncBase::TryTransitionToError

Wskazuje, czy określonego kodu błędu, można zmodyfikować stanu błędu wewnętrznego.

```cpp
bool TryTransitionToError(
   const HRESULT error
);
```

### <a name="parameters"></a>Parametry

*Błąd*<br/>
Błąd HRESULT.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli stan wewnętrzny błąd zostało zmienione; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta operacja modyfikuje stanu błędu, tylko wtedy, gdy stan błędu są już ustawione na S_OK. Ta operacja nie obowiązuje, jeśli stan błędu jest już błędu, anulowany, ukończone lub zamknięte.
