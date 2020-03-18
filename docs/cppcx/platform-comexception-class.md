---
title: 'Platform:: COMException, Klasa'
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::COMException
- VCCORLIB/Platform::COMException::HResult
- VCCORLIB/Platform::COMException::Message
helpviewer_keywords:
- Platform::COMException Class
ms.assetid: 44fda4e5-574f-4d12-ab5f-4ff3f277448d
ms.openlocfilehash: 1d0d36ec16303d6bdaa5f2344cd5d48fba03c8bf
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444296"
---
# <a name="platformcomexception-class"></a>Platform:: COMException, Klasa

Reprezentuje błędy COM występujące podczas wykonywania aplikacji. COMException jest klasą bazową dla zestawu wstępnie zdefiniowanych, standardowych wyjątków.

## <a name="syntax"></a>Składnia

```cpp
public ref class COMException : Exception,    IException,    IPrintable,    IEquatable
```

### <a name="members"></a>Elementy członkowskie

Klasa COMException dziedziczy z klasy Object i interfejsów IException, IPrintable i IEquatable.

COMException mają również następujące typy elementów członkowskich.

**Konstruktory**

|Członek|Opis|
|------------|-----------------|
|[COMException](#ctor)|Inicjuje nowe wystąpienie klasy COMException.|

**Metody**

Klasa COMException dziedziczy metody Equals (), Finalize (), GetHashCode (), GetType (), MemberwiseClose () i ToString () z [klasy platform:: Object](../cppcx/platform-object-class.md).

**Właściwości**

Klasa COMException ma następujące właściwości.

|Członek|Opis|
|------------|-----------------|
|[Wyjątek:: HResult](#hresult)|WYNIK HRESULT, który odnosi się do wyjątku.|
|[Wyjątek:: Message](#message)|Komunikat, który opisuje wyjątek.|

## <a name="derived-exceptions"></a>Wyjątki pochodne

Następujące wstępnie zdefiniowane wyjątki pochodzą od COMException. Różnią się one od COMException tylko pod nazwą, nazwą jego konstruktora i podstawową wartością HRESULT.

|Name (Nazwa)|Bazowy wynik HRESULT|Opis|
|----------|------------------------|-----------------|
|COMException|*wartość HRESULT zdefiniowana przez użytkownika*|Zgłaszany, gdy Nierozpoznana wartość HRESULT jest zwracana z wywołania metody COM.|
|AccessDeniedException|E_ACCESSDENIED|Zgłaszany w przypadku odmowy dostępu do zasobu lub funkcji.|
|ChangedStateException|E_CHANGED_STATE|Zgłaszany, gdy metody iteratora kolekcji lub widok kolekcji są wywoływane po zmianie kolekcji nadrzędnej, unieważnienie wyników metody.|
|ClassNotRegisteredException|REGDB_E_CLASSNOTREG|Zgłaszany, gdy nie zarejestrowano klasy COM.|
|DisconnectedException|RPC_E_DISCONNECTED|Zgłaszane po odłączeniu obiektu od jego klientów.|
|FailureException|E_FAIL|Zgłaszany, gdy operacja nie powiedzie się.|
|InvalidArgumentException|E_INVALIDARG|Zgłaszany, gdy jeden z argumentów dostarczonych do metody jest nieprawidłowy.|
|InvalidCastException|E_NOINTERFACE|Zgłaszany, gdy typ nie może być rzutowany na inny typ.|
|NotImplementedException|E_NOTIMPL|Zgłaszany, jeśli metoda interfejsu nie została zaimplementowana w klasie.|
|NullReferenceException|E_POINTER|Zgłaszany, gdy istnieje próba odwołująca się do odwołania do obiektu o wartości null.|
|OperationCanceledException|E_ABORT|Zgłaszany, gdy operacja zostanie przerwana.|
|OutOfBoundsException|E_BOUNDS|Zgłaszany, gdy operacja próbuje uzyskać dostęp do danych poza prawidłowym zakresem.|
|OutOfMemoryException|E_OUTOFMEMORY|Zgłaszany, gdy jest za mało pamięci, aby ukończyć operację.|

### <a name="requirements"></a>Wymagania

**Minimalny obsługiwany klient:** System Windows 8

**Minimalny obsługiwany serwer:** System Windows Server 2012

**Przestrzeń nazw:** Platformach

**Metadane:** obiekt platform. winmd

## <a name="ctor"></a>COMException:: COMException — Konstruktor

Aktywuje nowe wystąpienie klasy COMException.

### <a name="syntax"></a>Składnia

```cpp
COMException( int hresult )
```

### <a name="parameters"></a>Parametry

*wynik*<br/>
Błąd HRESULT, który jest reprezentowany przez wyjątek.

## <a name="hresult"></a>COMException:: HResult — Właściwość

WYNIK HRESULT, który odnosi się do wyjątku.

### <a name="syntax"></a>Składnia

```cpp
public:
    property int HResult { int get();}
```

## <a name="property-value"></a>Wartość właściwości

Wartość HRESULT, która określa błąd.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat interpretowania wartości HRESULT, zobacz [struktury kodów błędów modelu COM](/windows/win32/com/structure-of-com-error-codes).

## <a name="message"></a>COMException:: Message — właściwość

Komunikat, który opisuje wyjątek.

### <a name="syntax"></a>Składnia

```cpp
public:property String^ Message {    String^ get();}
```

### <a name="property-value"></a>Wartość właściwości

Opis wyjątku.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)
