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
ms.openlocfilehash: f09f12d9100e9faad849de608a9124f457da23df
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366365"
---
# <a name="wstring_convert-class"></a>wstring_convert — Klasa

Szablon `wstring_convert` klasy wykonuje konwersje między ciągiem szerokim a ciągiem bajtowym.

## <a name="syntax"></a>Składnia

```cpp
template <class Codecvt, class Elem = wchar_t>
class wstring_convert
```

### <a name="parameters"></a>Parametry

*Kodekvt*\
Aspekt [ustawień regionalnych,](../standard-library/locale-class.md) który reprezentuje obiekt konwersji.

*Elem*\
Typ elementu o szerokim charakterze.

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje obiekt, który steruje konwersjami `std::basic_string<Elem>` między obiektami szerokiego ciągu klasy i obiektów ciągu bajtowego klasy `std::basic_string<char>` (znany również jako `std::string`). Szablon klasy definiuje `wide_string` typy `byte_string` i synonimy dla tych dwóch typów. Konwersja między `Elem` sekwencją wartości `wide_string` (przechowywanych w obiekcie) a `byte_string` sekwencjami wielobajtowymi `Codecvt<Elem, char, std::mbstate_t>`(przechowywanymi w obiekcie) jest wykonywana `std::codecvt<Elem, char, std::mbstate_t>`przez obiekt klasy, który spełnia wymagania standardowego aspektu konwersji kodu.

Obiekt tego szablonu klasy przechowuje:

- Ciąg bajtów wyświetlany w błędach

- Szeroki ciąg do wyświetlania na błędach

- Wskaźnik do przydzielonego obiektu konwersji (który jest zwalniany po zniszczeniu wbuffer_convert obiektu)

- Obiekt stanu konwersji typu [state_type](#state_type)

- Liczba konwersji

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[wstring_convert](#wstring_convert)|Konstruuje obiekt `wstring_convert`typu .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[byte_string](#byte_string)|Typ reprezentujący ciąg bajtowy.|
|[wide_string](#wide_string)|Typ, który reprezentuje szeroki ciąg.|
|[state_type](#state_type)|Typ reprezentujący stan konwersji.|
|[Int_type](#int_type)|Typ reprezentujący liczbę całkowitą.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[from_bytes](#from_bytes)|Konwertuje ciąg bajtów na szeroki ciąg.|
|[to_bytes](#to_bytes)|Konwertuje szeroki ciąg na ciąg bajtów.|
|[Przekształcić](#converted)|Zwraca liczbę udanych konwersji.|
|[Państwa](#state)|Zwraca obiekt reprezentujący stan konwersji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ustawień regionalnych

**Przestrzeń nazw:** std

## <a name="wstring_convertbyte_string"></a><a name="byte_string"></a>wstring_convert::byte_string

Typ reprezentujący ciąg bajtowy.

```cpp
typedef std::basic_string<char> byte_string;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `std::basic_string<char>`.

## <a name="wstring_convertconverted"></a><a name="converted"></a>wstring_convert::przekonwertowane

Zwraca liczbę udanych konwersji.

```cpp
size_t converted() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba udanych konwersji.

### <a name="remarks"></a>Uwagi

Liczba udanych konwersji jest przechowywana w obiekcie zliczania konwersji.

## <a name="wstring_convertfrom_bytes"></a><a name="from_bytes"></a>wstring_convert::from_bytes

Konwertuje ciąg bajtów na szeroki ciąg.

```cpp
wide_string from_bytes(char Byte);
wide_string from_bytes(const char* ptr);
wide_string from_bytes(const byte_string& Bstr);
wide_string from_bytes(const char* first, const char* last);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Byte*|Sekwencja bajtów jednoelementowych do konwersji.|
|*Ptr*|Sekwencja znaków w stylu C z zakończeniem zerowym do konwersji.|
|*Bstr*|[Byte_string](#byte_string) do konwersji.|
|*Pierwszym*|Pierwszy znak w zakresie znaków do konwersji.|
|*Ostatnio*|Ostatni znak w zakresie znaków do konwersji.|

### <a name="return-value"></a>Wartość zwracana

Szeroki obiekt ciągu wynikający z konwersji.

### <a name="remarks"></a>Uwagi

Jeśli obiekt [stanu konwersji](../standard-library/wstring-convert-class.md) *nie* został skonstruowany z jawną wartością, jest ustawiona na jego wartość domyślną (początkowy stan konwersji) przed rozpoczęciem konwersji. W przeciwnym razie pozostaje bez zmian.

Liczba pomyślnie przekonwertowanych elementów wejściowych jest przechowywana w obiekcie zliczania konwersji. Jeśli nie wystąpi żaden błąd konwersji, funkcja elementu członkowskiego zwraca przekonwertowany ciąg szeroki. W przeciwnym razie jeśli obiekt został skonstruowany za pomocą inicjatora dla komunikatu o błędzie szerokostrunowy, funkcja elementu członkowskiego zwraca obiekt komunikatu o błędzie szerokostrunowy. W przeciwnym razie funkcja elementu członkowskiego zgłasza obiekt klasy [range_error](../standard-library/range-error-class.md).

## <a name="wstring_convertint_type"></a><a name="int_type"></a>wstring_convert::int_type

Typ reprezentujący liczbę całkowitą.

```cpp
typedef typename wide_string::traits_type::int_type int_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `wide_string::traits_type::int_type`.

## <a name="wstring_convertstate"></a><a name="state"></a>wstring_convert::stan

Zwraca obiekt reprezentujący stan konwersji.

```cpp
state_type state() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt [stanu konwersji,](../standard-library/wstring-convert-class.md) który reprezentuje stan konwersji.

### <a name="remarks"></a>Uwagi

## <a name="wstring_convertstate_type"></a><a name="state_type"></a>wstring_convert::state_type

Typ reprezentujący stan konwersji.

```cpp
typedef typename Codecvt::state_type state_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może reprezentować stan konwersji. Typ jest synonimem `Codecvt::state_type`.

## <a name="wstring_convertto_bytes"></a><a name="to_bytes"></a>wstring_convert::to_bytes

Konwertuje szeroki ciąg na ciąg bajtów.

```cpp
byte_string to_bytes(Elem Char);
byte_string to_bytes(const Elem* Wptr);
byte_string to_bytes(const wide_string& Wstr);
byte_string to_bytes(const Elem* first, const Elem* last);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Char*|Szeroki znak do konwersji.|
|*Wertry*|Sekwencja w stylu C, zakończona `wptr`z wartością null, zaczynając od , która ma zostać przekonwertowana.|
|*Wstr (właśc.*|[Wide_string](#wide_string) do konwersji.|
|*Pierwszym*|Pierwszy element w zakresie elementów do konwersji.|
|*Ostatnio*|Ostatni element w zakresie elementów do konwersji.|

### <a name="remarks"></a>Uwagi

Jeśli obiekt [stanu konwersji](../standard-library/wstring-convert-class.md) *nie* został skonstruowany z jawną wartością, jest ustawiona na jego wartość domyślną (początkowy stan konwersji) przed rozpoczęciem konwersji. W przeciwnym razie pozostaje bez zmian.

Liczba pomyślnie przekonwertowanych elementów wejściowych jest przechowywana w obiekcie zliczania konwersji. Jeśli nie wystąpi żaden błąd konwersji, funkcja elementu członkowskiego zwraca przekonwertowany ciąg bajtów. W przeciwnym razie jeśli obiekt został skonstruowany za pomocą inicjatora dla komunikatu o błędzie ciągu bajtowego, funkcja elementu członkowskiego zwraca obiekt komunikatu o błędzie ciągu bajtowego. W przeciwnym razie funkcja elementu członkowskiego zgłasza obiekt klasy [range_error](../standard-library/range-error-class.md).

## <a name="wstring_convertwide_string"></a><a name="wide_string"></a>wstring_convert::wide_string

Typ, który reprezentuje szeroki ciąg.

```cpp
typedef std::basic_string<Elem> wide_string;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `std::basic_string<Elem>`.

## <a name="wstring_convertwstring_convert"></a><a name="wstring_convert"></a>wstring_convert::wstring_convert

Konstruuje obiekt `wstring_convert`typu .

```cpp
wstring_convert(Codecvt *Pcvt = new Codecvt);
wstring_convert(Codecvt *Pcvt, state_type _State);
wstring_convert(const byte_string& _Berr, const wide_string& Werr = wide_string());
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*\*Sztvt ( pcvt )*|Obiekt typu `Codecvt` do wykonania konwersji.|
|*_state*|Obiekt typu [state_type](#state_type) reprezentujący stan konwersji.|
|*_Berr*|[Byte_string](#byte_string) do wyświetlania na błędy.|
|*Werr ( Werr )*|[Wide_string](#wide_string) do wyświetlania na błędy.|

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor przechowuje *Pcvt_arg* w [obiekcie konwersji](../standard-library/wstring-convert-class.md)
