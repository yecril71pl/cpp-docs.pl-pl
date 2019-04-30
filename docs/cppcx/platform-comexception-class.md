---
title: Platform::COMException, klasa
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::COMException
- VCCORLIB/Platform::Exception::HResult
- VCCORLIB/Platform::Exception::Message
helpviewer_keywords:
- Platform::COMException Class
ms.assetid: 44fda4e5-574f-4d12-ab5f-4ff3f277448d
ms.openlocfilehash: 5a74184a8cbc4126988da2ba0be61d9f5b2bb71c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383350"
---
# <a name="platformcomexception-class"></a>Platform::COMException, klasa

Reprezentuje błędy COM, które występują podczas wykonywania aplikacji. COMException jest klasą bazową dla zestawu wstępnie zdefiniowanych, standardowych wyjątków.

## <a name="syntax"></a>Składnia

```cpp
public ref class COMException : Exception,    IException,    IPrintable,    IEquatable
```

### <a name="members"></a>Elementy członkowskie

COMException, klasa dziedziczy z klasy i interfejsy IException IPrintable i IEquatable.

COMException ma również następujące rodzaje elementów członkowskich.

**Konstruktory**

|Element członkowski|Opis|
|------------|-----------------|
|[COMException](#ctor)|Inicjuje nowe wystąpienie klasy COMException.|

**Metody**

COMException, klasa dziedziczy metodę Equals(), Finalize(), element GetHashCode(), wartości GetType(), MemberwiseClose() i ToString() metody z [Platform::Object, klasa](../cppcx/platform-object-class.md).

**Właściwości**

COMException, klasa ma następujące właściwości.

|Element członkowski|Opis|
|------------|-----------------|
|[Exception::HResult](#hresult)|Wartość HRESULT, która odnosi się do wyjątku.|
|[Exception::Message](#message)|Komunikat opisujący wyjątek.|

## <a name="derived-exceptions"></a>Pochodne wyjątków

Następujące wstępnie zdefiniowane wyjątki są uzyskiwane z COMException. Różnią się od COMException tylko ich nazwy, nazwa ich konstruktorów i ich podstawowej wartości HRESULT.

|Nazwa|Bazowy HRESULT|Opis|
|----------|------------------------|-----------------|
|COMException|*hresult zdefiniowanych przez użytkownika*|Element zgłaszany, gdy wartość HRESULT nierozpoznany jest zwracany z wywołania metody COM.|
|AccessDeniedException|E_ACCESSDENIED|Element zgłaszany, gdy odmowa dostępu do zasobów lub funkcji.|
|ChangedStateException|E_CHANGED_STATE|Element zgłaszany, gdy metody iteratora kolekcji lub tego widoku kolekcji są wywoływane po zmianie kolekcji nadrzędnej, powodując unieważnienie wyniki metody.|
|ClassNotRegisteredException|REGDB_E_CLASSNOTREG|Element zgłaszany, gdy klasa COM nie został zarejestrowany.|
|DisconnectedException|RPC_E_DISCONNECTED|Element zgłaszany, gdy obiekt jest odłączony od swoich klientów.|
|FailureException|E_FAIL|Element zgłaszany, gdy operacja nie powiedzie się.|
|InvalidArgumentException|E_INVALIDARG|Element zgłaszany, gdy jeden z podanych argumentów metody jest nieprawidłowy.|
|InvalidCastException|E_NOINTERFACE|Element zgłaszany, gdy nie można rzutować typu na inny typ.|
|NotImplementedException|E_NOTIMPL|Element zgłaszany, gdy metoda interfejsu nie została zaimplementowana w klasie.|
|Obiektu NullReferenceException|E_POINTER|Zgłaszany, gdy jest próba wyłuskania odwołanie do obiektu o wartości null.|
|OperationCanceledException|E_ABORT|Element zgłaszany, gdy operacja została przerwana.|
|OutOfBoundsException|E_BOUNDS|Element zgłaszany, gdy operacja próbuje uzyskać dostęp do danych poza prawidłowym zakresem.|
|OutOfMemoryException|E_OUTOFMEMORY|Element zgłaszany, gdy ma za mało pamięci do ukończenia tej operacji.|

### <a name="requirements"></a>Wymagania

**Minimalna obsługiwana klienta:** Windows 8

**Minimalna obsługiwana serwera:** Windows Server 2012

**Namespace:** Platforma

**Metadane:** platform.winmd

## <a name="ctor"></a> Konstruktor COMException::COMException

Aktywuje nowe wystąpienie klasy COMException.

### <a name="syntax"></a>Składnia

```cpp
COMException( int hresult )
```

### <a name="parameters"></a>Parametry

*hresult*<br/>
Błąd HRESULT, który jest reprezentowany przez wyjątek.

## <a name="hresult"></a> Właściwość COMException::HResult

Wartość HRESULT, która odnosi się do wyjątku.

### <a name="syntax"></a>Składnia

```cpp
public:
    property int HResult { int get();}
```

## <a name="property-value"></a>Wartość właściwości

Wartość HRESULT, która określa błędu.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji dotyczących sposobu interpretowania wartości HRESULT, zobacz [struktury COM kody błędów](/windows/desktop/com/structure-of-com-error-codes).

## <a name="message"></a> Właściwość COMException::Message

Komunikat opisujący wyjątek.

### <a name="syntax"></a>Składnia

```cpp
public:property String^ Message {    String^ get();}
```

### <a name="property-value"></a>Wartość właściwości

Opis wyjątku.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)
