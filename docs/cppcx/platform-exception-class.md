---
title: 'Platform:: Exception, Klasa'
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
ms.openlocfilehash: bfdd8b3df720073e6b4a19cdb5b34db23e659fd0
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90741973"
---
# <a name="platformexception-class"></a>Platform:: Exception, Klasa

Reprezentuje błędy występujące podczas wykonywania aplikacji. Nie można wyprowadzać klas wyjątków niestandardowych z `Platform::Exception` . Jeśli wymagany jest wyjątek niestandardowy, można użyć `Platform::COMException` i określić wartość HRESULT specyficzną dla aplikacji.

## <a name="syntax"></a>Składnia

```cpp
public ref class Exception : Object,    IException,    IPrintable,    IEquatable
```

### <a name="members"></a>Elementy członkowskie

`Exception`Klasa dziedziczy z `Object` klasy i `IException` `IPrintable` interfejsów,, i `IEquatable` .

`Exception`Klasa ma również następujące rodzaje elementów członkowskich.

### <a name="constructors"></a>Konstruktory

|Członek|Opis|
|------------|-----------------|
|[Wyjątek:: Exception](#ctor)|Inicjuje nowe wystąpienie klasy `Exception`.|

### <a name="methods"></a>Metody

`Exception`Klasa dziedziczy `Equals()` metody,,,, `Finalize()` `GetHashCode()` `GetType()` `MemberwiseClose()` i `ToString()` z [klasy platform:: Object](../cppcx/platform-object-class.md). `Exception`Klasa ma również następującą metodę.

|Członek|Opis|
|------------|-----------------|
|[Wyjątek:: CreateException](#createexception)|Tworzy wyjątek, który reprezentuje określoną wartość HRESULT.|

### <a name="properties"></a>Właściwości

Klasa wyjątku ma również następujące właściwości.

|Członek|Opis|
|------------|-----------------|
|[Wyjątek:: HResult](#hresult)|WYNIK HRESULT, który odnosi się do wyjątku.|
|[Wyjątek:: Message](#message)|Komunikat, który opisuje wyjątek. Ta wartość jest tylko do odczytu i nie można jej modyfikować po `Exception` utworzeniu.|

### <a name="requirements"></a>Wymagania

**Minimalny obsługiwany klient:** System Windows 8

**Minimalny obsługiwany serwer:** System Windows Server 2012

**Przestrzeń nazw:** Platformach

**Metadane:** obiekt platform. winmd

## <a name="exceptioncreateexception-method"></a><a name="createexception"></a> Exception:: CreateException — Metoda

Tworzy platformę:: Exception ^ z określonej wartości HRESULT.

### <a name="syntax"></a>Składnia

```cpp
Exception^ CreateException(int32 hr);
Exception^ CreateException(int32 hr, Platform::String^ message);
```

### <a name="parameters"></a>Parametry

*godz.*<br/>
Wartość HRESULT, która zwykle uzyskuje się z wywołania metody COM. Jeśli wartość wynosi 0, która jest równa S_OK, ta metoda zgłasza [platformę:: InvalidArgumentException](../cppcx/platform-invalidargumentexception-class.md) , ponieważ metody com, które powiodło się, nie powinny generować wyjątków.

*Komunikat*<br/>
Ciąg, który opisuje błąd.

### <a name="return-value"></a>Wartość zwracana

Wyjątek, który reprezentuje błąd HRESULT.

### <a name="remarks"></a>Uwagi

Użyj tej metody, aby utworzyć wyjątek z wynik HRESULT, który jest zwracany, na przykład z wywołania metody interfejsu COM. Można użyć przeciążenia, które pobiera komunikat niestandardowy w ciągu ^.

Zdecydowanie zaleca się użycie elementu CreateException w celu utworzenia wyjątku o jednoznacznie określonym typie zamiast tworzenia [platformy:: COMException](../cppcx/platform-comexception-class.md) , która tylko zawiera wynik HRESULT.

## <a name="exceptionexception-constructor"></a><a name="ctor"></a> Exception:: Exception — Konstruktor

Aktywuje nowe wystąpienie klasy Exception.

### <a name="syntax"></a>Składnia

```cpp
Exception(int32 hresult);
Exception(int32 hresult, ::Platform::String^ message);
```

### <a name="parameters"></a>Parametry

*wynik*<br/>
Błąd HRESULT, który jest reprezentowany przez wyjątek.

*Komunikat*<br/>
Komunikat określony przez użytkownika, taki jak tekst, który jest skojarzony z wyjątkiem. Ogólnie rzecz biorąc należy preferować drugie Przeciążenie, aby zapewnić opisowy komunikat, który jest jak najbardziej specyficzny dla tego, jak i dlaczego wystąpił błąd.

## <a name="exceptionhresult-property"></a><a name="hresult"></a> Exception:: HResult — Właściwość

WYNIK HRESULT, który odnosi się do wyjątku.

### <a name="syntax"></a>Składnia

```cpp
public:
    property int HResult { int get(); }
```

### <a name="property-value"></a>Wartość właściwości

Wartość HRESULT.

### <a name="remarks"></a>Uwagi

Większość wyjątków rozpoczyna się jako błędy COM, które są zwracane jako wartości HRESULT. C++/CX konwertuje te wartości na obiekt platform:: Exception ^, a ta właściwość przechowuje wartość oryginalnego kodu błędu.

## <a name="exceptionmessage-property"></a><a name="message"></a> Exception:: Message — właściwość

Komunikat, który opisuje błąd.

### <a name="syntax"></a>Składnia

```cpp
public:property String^ Message;
```

### <a name="property-value"></a>Wartość właściwości

W wyjątkach, które pochodzą z środowisko wykonawcze systemu Windows, jest to systemowy opis błędu.

### <a name="remarks"></a>Uwagi

W systemie Windows 8 Ta właściwość jest tylko do odczytu, ponieważ wyjątki w tej wersji środowisko wykonawcze systemu Windows są transportowane przez ABI tylko jako HRESULTs. W Windows 8.1, bogatsze informacje o wyjątkach są transportowane przez ABI i można udostępnić niestandardowy komunikat, który inne składniki mogą uzyskać dostęp programowo. Aby uzyskać więcej informacji, zobacz [wyjątki (C++/CX)](../cppcx/exceptions-c-cx.md).

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)
