---
title: Platform::Exception, klasa
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
ms.openlocfilehash: d37d55c56e3c23d8d9129c985cb4272d2e3ee47a
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743418"
---
# <a name="platformexception-class"></a>Platform::Exception, klasa

Reprezentuje błędy występujące podczas wykonywania aplikacji. Klasy wyjątków niestandardowych nie mogą pochodzić z `Platform::Exception`. Jeśli potrzebujesz niestandardowego wyjątku, można użyć `Platform::COMException` i określ wartość HRESULT specyficzny dla aplikacji.

## <a name="syntax"></a>Składnia

```cpp
public ref class Exception : Object,    IException,    IPrintable,    IEquatable
```

### <a name="members"></a>Elementy członkowskie

`Exception` Klasa dziedziczy `Object` klasy i `IException`, `IPrintable`, i `IEquatable` interfejsów.

`Exception` Klasa ma również następujące rodzaje elementów członkowskich.

### <a name="constructors"></a>Konstruktorów

|Element członkowski|Opis|
|------------|-----------------|
|[Exception::Exception](#ctor)|Inicjuje nowe wystąpienie klasy `Exception` klasy.|

### <a name="methods"></a>Metody

`Exception` Klasa dziedziczy `Equals()`, `Finalize()`,`GetHashCode()`,`GetType()`,`MemberwiseClose()`, i `ToString()` metody z [Platform::Object, klasa](../cppcx/platform-object-class.md). `Exception` Klasa ma również następującą metodę.

|Element członkowski|Opis|
|------------|-----------------|
|[Exception::CreateException](#createexception)|Tworzy wyjątek, który reprezentuje określoną wartość HRESULT.|

### <a name="properties"></a>Właściwości

Klasy wyjątków ma również następujące właściwości.

|Element członkowski|Opis|
|------------|-----------------|
|[Exception::HResult](#hresult)|Wartość HRESULT, która odnosi się do wyjątku.|
|[Exception::Message](#message)|Komunikat, który opisuje wyjątek. Ta wartość jest tylko do odczytu i nie można zmodyfikować po `Exception` jest konstruowany.|

### <a name="requirements"></a>Wymagania

**Minimalna obsługiwana klienta:** Windows 8

**Minimalna obsługiwana serwera:** Windows Server 2012

**Namespace:** Platforma

**Metadane:** platform.winmd

## <a name="createexception"></a> Metoda Exception::CreateException

Tworzy Platform::Exception ^ od określonej wartości HRESULT.

### <a name="syntax"></a>Składnia

```cpp
Exception^ CreateException(int32 hr);
Exception^ CreateException(int32 hr, Platform::String^ message);
```

### <a name="parameters"></a>Parametry

*godz.*<br/>
Wartość HRESULT, która zazwyczaj można pobrać po wywołaniu metody COM. Jeśli wartość wynosi 0, która jest równa S_OK, ta metoda wyrzuca [Platform::InvalidArgumentException](../cppcx/platform-invalidargumentexception-class.md) ponieważ metody COM, które pomyślnie nie powinna zgłaszać wyjątków.

*komunikat*<br/>
Ciąg, który opisuje błąd.

### <a name="return-value"></a>Wartość zwracana

Wyjątek, który reprezentuje błąd HRESULT.

### <a name="remarks"></a>Uwagi

Metoda ta jest przydatna w celu utworzenia wyjątku poza HRESULT, która jest zwracana, na przykład po wywołaniu metody interfejsu COM. Można użyć przeciążenia, które przyjmuje ciąg ^ parametru, aby podać niestandardowy komunikat.

Jest zdecydowanie zalecane jest, aby umożliwia tworzenie wyjątku silnie typizowane CreateException zamiast tworzenia [Platform::COMException](../cppcx/platform-comexception-class.md) zawiera jedynie HRESULT.

## <a name="ctor"></a>  Konstruktor Exception::Exception

Aktywuje nowe wystąpienie klasy wyjątku.

### <a name="syntax"></a>Składnia

```cpp
Exception(int32 hresult);
Exception(int32 hresult, ::Platform::String^ message);
```

### <a name="parameters"></a>Parametry

*hresult*<br/>
Błąd HRESULT, który jest reprezentowany przez wyjątek.

*komunikat*<br/>
Określone przez użytkownika wiadomości, takich jak normatywne tekst, który jest skojarzony z wyjątkiem. Ogólnie rzecz biorąc preferowaną drugie przeciążenie zapewnić opisowy komunikat, który jest możliwie o jak i dlaczego wystąpił błąd.

## <a name="hresult"></a>  Właściwość Exception::HResult

Wartość HRESULT, która odnosi się do wyjątku.

### <a name="syntax"></a>Składnia

```cpp
public:
    property int HResult { int get(); }
```

## <a name="property-value"></a>Wartość właściwości

Wartość HRESULT.

### <a name="remarks"></a>Uwagi

Większość wyjątków rozpoczyna pracę jako błędy COM, które są zwracane jako wartości HRESULT. C + +/ CX konwertuje te wartości na Platform::Exception ^ obiektów i ta właściwość zawiera wartość oryginalnego kodu błędu.

## <a name="message"></a> Właściwość Exception::Message

Komunikat, który opisuje błąd.

### <a name="syntax"></a>Składnia

```cpp
public:property String^ Message;
```

## <a name="property-value"></a>Wartość właściwości

Wyjątki, które pochodzą ze środowiska wykonawczego Windows jest dostarczany przez system opis błędu.

### <a name="remarks"></a>Uwagi

W systemie Windows 8 ta właściwość jest tylko do odczytu, ponieważ wyjątki w tej wersji środowiska uruchomieniowego Windows są przenoszone przez ABI tylko jako wartości HRESULT. W Windows 8.1 bogatsze informacje o wyjątku są przesyłane między interfejsem ABI, i możesz podać niestandardowy komunikat, że inne składniki mogą uzyskiwać dostęp do programowego. Aby uzyskać więcej informacji, zobacz [wyjątki (C + +/ CX)](../cppcx/exceptions-c-cx.md).

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)
