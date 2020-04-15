---
title: Platforma::Klasa wyjątku
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Exception::Exception
- VCCORLIB/Platform::Exception::CreateException
- VCCORLIB/Platform::Exception::HResult
- VCCORLIB/Platform::Exception::Message
helpviewer_keywords:
- Platform::Exception Class
ms.assetid: ca1d5a67-3a5a-48fe-8099-f9c38a2d2dce
ms.openlocfilehash: 4604769d9d1bc5fa848d15459327dc87d82f7016
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363783"
---
# <a name="platformexception-class"></a>Platforma::Klasa wyjątku

Reprezentuje błędy, które występują podczas wykonywania aplikacji. Niestandardowe klasy wyjątków nie `Platform::Exception`mogą pochodzić z . Jeśli potrzebujesz wyjątku niestandardowego, `Platform::COMException` możesz użyć i określić hresult specyficzne dla aplikacji.

## <a name="syntax"></a>Składnia

```cpp
public ref class Exception : Object,    IException,    IPrintable,    IEquatable
```

### <a name="members"></a>Elementy członkowskie

Klasa `Exception` dziedziczy z `Object` klasy `IException`i `IPrintable`, `IEquatable` , i interfejsów.

Klasa `Exception` ma również następujące rodzaje elementów członkowskich.

### <a name="constructors"></a>Konstruktorów

|Członek|Opis|
|------------|-----------------|
|[Wyjątek::Wyjątek](#ctor)|Inicjuje nowe wystąpienie klasy `Exception`.|

### <a name="methods"></a>Metody

Klasa `Exception` dziedziczy `Equals()`, `Finalize()``GetHashCode()`,`GetType()``MemberwiseClose()`, `ToString()` i metody z [Platform::Object Class](../cppcx/platform-object-class.md). Klasa `Exception` ma również następującą metodę.

|Członek|Opis|
|------------|-----------------|
|[Wyjątek::CreateException](#createexception)|Tworzy wyjątek, który reprezentuje określoną wartość HRESULT.|

### <a name="properties"></a>Właściwości

Klasa Exception ma również następujące właściwości.

|Członek|Opis|
|------------|-----------------|
|[Wyjątek::HResult](#hresult)|HRESULT, który odpowiada wyjątku.|
|[Wyjątek::Wiadomość](#message)|Komunikat, który opisuje wyjątek. Ta wartość jest tylko do odczytu `Exception` i nie można zmodyfikować po skonstruowaniu.|

### <a name="requirements"></a>Wymagania

**Minimalny obsługiwany klient:** Windows 8

**Minimalny obsługiwany serwer:** System Windows Server 2012

**Obszar nazw:** Platformy

**Metadane:** platform.winmd

## <a name="exceptioncreateexception-method"></a><a name="createexception"></a>Wyjątek::CreateException Metoda

Tworzy platformę::Exception^ z określonej wartości HRESULT.

### <a name="syntax"></a>Składnia

```cpp
Exception^ CreateException(int32 hr);
Exception^ CreateException(int32 hr, Platform::String^ message);
```

### <a name="parameters"></a>Parametry

*Hr*<br/>
Wartość HRESULT, które zazwyczaj można uzyskać z wywołania do metody COM. Jeśli wartość jest 0, który jest równy S_OK, ta metoda zgłasza [Platform::InvalidArgumentException](../cppcx/platform-invalidargumentexception-class.md) ponieważ metody COM, które zakończyć się pomyślnie nie powinny zgłaszać wyjątki.

*Komunikat*<br/>
Ciąg opisujący błąd.

### <a name="return-value"></a>Wartość zwracana

Wyjątek reprezentujący błąd HRESULT.

### <a name="remarks"></a>Uwagi

Ta metoda służy do tworzenia wyjątku z HRESULT, który jest zwracany, na przykład z wywołania do metody interfejsu COM. Można użyć przeciążenia, które zajmuje String^ parametr, aby zapewnić wiadomość niestandardową.

Zdecydowanie zaleca się użycie CreateException do tworzenia silnie typizowanego wyjątku, a nie tworzenia [platformy::COMException,](../cppcx/platform-comexception-class.md) która zawiera tylko HRESULT.

## <a name="exceptionexception-constructor"></a><a name="ctor"></a>Wyjątek::Konstruktor wyjątków

Intializes nowe wystąpienie Exception klasy.

### <a name="syntax"></a>Składnia

```cpp
Exception(int32 hresult);
Exception(int32 hresult, ::Platform::String^ message);
```

### <a name="parameters"></a>Parametry

*Hresult*<br/>
Błąd HRESULT, który jest reprezentowany przez wyjątek.

*Komunikat*<br/>
Komunikat określony przez użytkownika, taki jak tekst nakazowy, skojarzony z wyjątkiem. Ogólnie rzecz biorąc należy preferować drugie przeciążenie, aby zapewnić opisowy komunikat, który jest jak najbardziej szczegółowy o tym, jak i dlaczego wystąpił błąd.

## <a name="exceptionhresult-property"></a><a name="hresult"></a>Wyjątek::Właściwość HResult

HRESULT, który odpowiada wyjątku.

### <a name="syntax"></a>Składnia

```cpp
public:
    property int HResult { int get(); }
```

## <a name="property-value"></a>Wartość właściwości

Wartość HRESULT.

### <a name="remarks"></a>Uwagi

Większość wyjątków rozpoczyna się jako błędy COM, które są zwracane jako wartości HRESULT. C++/CX konwertuje te wartości na platform::Exception^ obiektów i ta właściwość przechowuje wartość oryginalnego kodu błędu.

## <a name="exceptionmessage-property"></a><a name="message"></a>Wyjątek::Message Właściwość

Komunikat opisujący błąd.

### <a name="syntax"></a>Składnia

```cpp
public:property String^ Message;
```

## <a name="property-value"></a>Wartość właściwości

W wyjątkach, które pochodzą ze środowiska wykonawczego systemu Windows, jest to opis błędu dostarczony przez system.

### <a name="remarks"></a>Uwagi

W systemie Windows 8 ta właściwość jest tylko do odczytu, ponieważ wyjątki w tej wersji środowiska wykonawczego systemu Windows są transportowane przez ABI tylko jako HRESULTS. W systemie Windows 8.1 bogatsze informacje o wyjątkach są transportowane przez usługę ABI i można podać niestandardowy komunikat, do którego inne składniki mogą uzyskać dostęp programowo. Aby uzyskać więcej informacji, zobacz [Wyjątki (C++/CX)](../cppcx/exceptions-c-cx.md).

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)
