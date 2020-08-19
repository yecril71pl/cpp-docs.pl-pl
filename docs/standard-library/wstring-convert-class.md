---
title: wstring_convert — Klasa
ms.date: 11/04/2016
f1_keywords:
- wstring/stdext::cvt::wstring_convert
- locale/std::wstring_convert::byte_string
- locale/std::wstring_convert::wide_string
- locale/std::wstring_convert::state_type
- locale/std::wstring_convert::int_type
- locale/std::wstring_convert::from_bytes
- locale/std::wstring_convert::to_bytes
- locale/std::wstring_convert::converted
- locale/std::wstring_convert::state
helpviewer_keywords:
- stdext::cvt [C++], wstring_convert
- std::wstring_convert [C++], byte_string
- std::wstring_convert [C++], wide_string
- std::wstring_convert [C++], state_type
- std::wstring_convert [C++], int_type
- std::wstring_convert [C++], from_bytes
- std::wstring_convert [C++], to_bytes
- std::wstring_convert [C++], converted
- std::wstring_convert [C++], state
ms.assetid: e34f5b65-d572-4bdc-ac69-20778712e376
ms.openlocfilehash: 01754ca4239d89a64fdb67a85e82b90c5a24872d
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560755"
---
# <a name="wstring_convert-class"></a>wstring_convert — Klasa

Szablon klasy `wstring_convert` wykonuje konwersje między ciągiem szerokim i ciągiem bajtowym.

## <a name="syntax"></a>Składnia

```cpp
template <class Codecvt, class Elem = wchar_t>
class wstring_convert
```

### <a name="parameters"></a>Parametry

*Codecvt*\
Zestaw reguł [ustawień regionalnych](../standard-library/locale-class.md) , który reprezentuje obiekt konwersji.

*Elem*\
Typ elementu dwubajtowego.

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje obiekt, który kontroluje konwersje między obiektami szerokiego ciągu obiektów klasy `std::basic_string<Elem>` i ciągu bajtowego klasy `std::basic_string<char>` (znanego również jako `std::string` ). Szablon klasy definiuje typy `wide_string` i `byte_string` jako synonimy dla tych dwóch typów. Konwersja między sekwencją `Elem` wartości (przechowywanych w `wide_string` obiekcie) i sekwencjami wielobajtowymi (przechowywanych w `byte_string` obiekcie) jest wykonywana przez obiekt klasy `Codecvt<Elem, char, std::mbstate_t>` , który spełnia wymagania standardowego aspektu konwersji kodu `std::codecvt<Elem, char, std::mbstate_t>` .

Obiekt tego szablonu klasy przechowuje:

- Ciąg bajtowy do wyświetlenia w przypadku błędów

- Szeroki ciąg do wyświetlenia w przypadku błędów

- Wskaźnik do przydzielony obiekt konwersji (który jest zwalniany, gdy obiekt wbuffer_convert jest niszczony)

- Obiekt stanu konwersji typu [state_type](#state_type)

- Liczba konwersji

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[wstring_convert](#wstring_convert)|Konstruuje obiekt typu `wstring_convert` .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[byte_string](#byte_string)|Typ, który reprezentuje ciąg bajtowy.|
|[wide_string](#wide_string)|Typ, który reprezentuje ciąg szeroki.|
|[state_type](#state_type)|Typ, który reprezentuje stan konwersji.|
|[int_type](#int_type)|Typ, który reprezentuje liczbę całkowitą.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[from_bytes](#from_bytes)|Konwertuje ciąg bajtowy na ciąg szeroki.|
|[to_bytes](#to_bytes)|Konwertuje szeroki ciąg na ciąg bajtowy.|
|[skonwertowana](#converted)|Zwraca liczbę pomyślnych konwersji.|
|[Państwu](#state)|Zwraca obiekt reprezentujący stan konwersji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<locale>

**Przestrzeń nazw:** std

## <a name="wstring_convertbyte_string"></a><a name="byte_string"></a> wstring_convert:: byte_string

Typ, który reprezentuje ciąg bajtowy.

```cpp
typedef std::basic_string<char> byte_string;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `std::basic_string<char>` .

## <a name="wstring_convertconverted"></a><a name="converted"></a> wstring_convert:: przekonwertował

Zwraca liczbę pomyślnych konwersji.

```cpp
size_t converted() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba pomyślnych konwersji.

### <a name="remarks"></a>Uwagi

Liczba pomyślnych konwersji jest przechowywana w obiekcie liczba konwersji.

## <a name="wstring_convertfrom_bytes"></a><a name="from_bytes"></a> wstring_convert:: from_bytes

Konwertuje ciąg bajtowy na ciąg szeroki.

```cpp
wide_string from_bytes(char Byte);
wide_string from_bytes(const char* ptr);
wide_string from_bytes(const byte_string& Bstr);
wide_string from_bytes(const char* first, const char* last);
```

### <a name="parameters"></a>Parametry

*Bajc*\
Sekwencja bajtów pojedynczego elementu do przekonwertowania.

*PTR*\
Styl języka C, sekwencja znaków zakończona znakiem null do przekonwertowania.

*Ani*\
[Byte_string](#byte_string) do przekonwertowania.

*pierwszego*\
Pierwszy znak w zakresie znaków do przekonwertowania.

*ostatniego*\
Ostatni znak w zakresie znaków do przekonwertowania.

### <a name="return-value"></a>Wartość zwracana

Obiekt ciągu szerokiego wynikający z konwersji.

### <a name="remarks"></a>Uwagi

Jeśli obiekt [stanu konwersji](../standard-library/wstring-convert-class.md) *nie* został skonstruowany z wartością jawną, jest ustawiany na jego wartość domyślną (początkowy stan konwersji) przed rozpoczęciem konwersji. W przeciwnym razie pozostaje niezmieniona.

Liczba pomyślnie przekonwertowanych elementów wejściowych jest zapisywana w obiekcie licznika konwersji. Jeśli błąd konwersji nie wystąpi, funkcja członkowska zwraca przekonwertowany ciąg szeroki. W przeciwnym razie, jeśli obiekt został skonstruowany przy użyciu inicjatora komunikatu o błędzie o szerokim ciągu, funkcja członkowska zwraca obiekt komunikatu o błędzie o szerokim ciągu. W przeciwnym razie funkcja członkowska zgłasza obiekt klasy [range_error](../standard-library/range-error-class.md).

## <a name="wstring_convertint_type"></a><a name="int_type"></a> wstring_convert:: int_type

Typ, który reprezentuje liczbę całkowitą.

```cpp
typedef typename wide_string::traits_type::int_type int_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `wide_string::traits_type::int_type` .

## <a name="wstring_convertstate"></a><a name="state"></a> wstring_convert:: State

Zwraca obiekt reprezentujący stan konwersji.

```cpp
state_type state() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt [stanu konwersji](../standard-library/wstring-convert-class.md) , który reprezentuje stan konwersji.

### <a name="remarks"></a>Uwagi

## <a name="wstring_convertstate_type"></a><a name="state_type"></a> wstring_convert:: state_type

Typ, który reprezentuje stan konwersji.

```cpp
typedef typename Codecvt::state_type state_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może reprezentować stan konwersji. Typ jest synonimem dla `Codecvt::state_type` .

## <a name="wstring_convertto_bytes"></a><a name="to_bytes"></a> wstring_convert:: to_bytes

Konwertuje szeroki ciąg na ciąg bajtowy.

```cpp
byte_string to_bytes(Elem Char);
byte_string to_bytes(const Elem* Wptr);
byte_string to_bytes(const wide_string& Wstr);
byte_string to_bytes(const Elem* first, const Elem* last);
```

### <a name="parameters"></a>Parametry

*Delikatn*\
Znak dwubajtowy do przekonwertowania.

*Wptr*\
Styl języka C, sekwencja zakończona zerem, rozpoczynająca się w `wptr` , który ma zostać przekonwertowany.

*Wstr*\
[Wide_string](#wide_string) do przekonwertowania.

*pierwszego*\
Pierwszy element w zakresie elementów do przekonwertowania.

*ostatniego*\
Ostatni element w zakresie elementów do przekonwertowania.

### <a name="remarks"></a>Uwagi

Jeśli obiekt [stanu konwersji](../standard-library/wstring-convert-class.md) *nie* został skonstruowany z wartością jawną, jest ustawiany na jego wartość domyślną (początkowy stan konwersji) przed rozpoczęciem konwersji. W przeciwnym razie pozostaje niezmieniona.

Liczba pomyślnie przekonwertowanych elementów wejściowych jest zapisywana w obiekcie licznika konwersji. Jeśli błąd konwersji nie wystąpi, funkcja członkowska zwraca przekonwertowany ciąg bajtowy. W przeciwnym razie, jeśli obiekt został skonstruowany przy użyciu inicjatora komunikatu o błędzie typu Byte, funkcja członkowska zwraca obiekt komunikatu o błędzie ciągu bajtowego. W przeciwnym razie funkcja członkowska zgłasza obiekt klasy [range_error](../standard-library/range-error-class.md).

## <a name="wstring_convertwide_string"></a><a name="wide_string"></a> wstring_convert:: wide_string

Typ, który reprezentuje ciąg szeroki.

```cpp
typedef std::basic_string<Elem> wide_string;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `std::basic_string<Elem>` .

## <a name="wstring_convertwstring_convert"></a><a name="wstring_convert"></a> wstring_convert:: wstring_convert

Konstruuje obiekt typu `wstring_convert` .

```cpp
wstring_convert(Codecvt *Pcvt = new Codecvt);
wstring_convert(Codecvt *Pcvt, state_type _State);
wstring_convert(const byte_string& _Berr, const wide_string& Werr = wide_string());
```

### <a name="parameters"></a>Parametry

*\*Pcvt*\
Obiekt typu `Codecvt` do przeprowadzenia konwersji.

*_State*\
Obiekt typu [state_type](#state_type) reprezentujący stan konwersji.

*_Berr*\
[Byte_string](#byte_string) , które mają być wyświetlane w przypadku błędów.

*Werr*\
[Wide_string](#wide_string) , które mają być wyświetlane w przypadku błędów.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor przechowuje *Pcvt_arg* w [obiekcie konwersji](../standard-library/wstring-convert-class.md)
