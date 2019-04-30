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
ms.openlocfilehash: df3b003289dcd86e8033521d8cb0cacdbb7dfbd8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410801"
---
# <a name="wstringconvert-class"></a>wstring_convert — Klasa

Klasa szablonu `wstring_convert` wykonuje konwersje między ciąg znaków dwubajtowych i ciąg bajtów.

## <a name="syntax"></a>Składnia

```cpp
template <class Codecvt, class Elem = wchar_t>
class wstring_convert
```

### <a name="parameters"></a>Parametry

*Codecvt*<br/>
[Ustawień regionalnych](../standard-library/locale-class.md) reguł, który reprezentuje obiekt konwersji.

*Elem*<br/>
Typ elementu znaków dwubajtowych.

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje obiekt, który kontroluje konwersje między obiektami szerokiego ciągu klasy `std::basic_string<Elem>` i obiektów w postaci ciągów bajt klasy `std::basic_string<char>` (znany także jako `std::string`). Klasa szablon definiuje typy `wide_string` i `byte_string` synonimami tych dwóch typów. Konwersji między sekwencjami `Elem` wartości (przechowywanych w `wide_string` obiekt) i wielobajtowych sekwencji (przechowywanej w `byte_string` obiektu) odbywa się przez obiekt klasy `Codecvt<Elem, char, std::mbstate_t>`, które spełnia wymagania normy zestaw reguł konwersji kodu `std::codecvt<Elem, char, std::mbstate_t>`.

Przechowuje obiekt tej klasy szablonu:

- Ciąg do wyświetlenia na błędy

- Ciąg znaków dwubajtowych do wyświetlania na błędy

- Wskaźnik do przydzielonego konwersji obiektu (zostanie zwolniony, kiedy niszczony jest obiekt wbuffer_convert —)

- Obiekt stanu konwersji typu [state_type](#state_type)

- Liczba konwersji

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[wstring_convert](#wstring_convert)|Tworzy obiekt typu `wstring_convert`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[byte_string](#byte_string)|Typ, który reprezentuje ciąg bajtów.|
|[wide_string](#wide_string)|Typ, który reprezentuje ciąg znaków dwubajtowych.|
|[state_type](#state_type)|Typ, który reprezentuje stan konwersji.|
|[int_type](#int_type)|Typ, który reprezentuje liczbę całkowitą.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[from_bytes](#from_bytes)|Konwertuje ciąg bajtów na ciąg znaków dwubajtowych.|
|[to_bytes](#to_bytes)|Konwertuje ciąg znaków dwubajtowych ciąg bajtów.|
|[przekonwertowany](#converted)|Zwraca liczbę pomyślnych konwersji.|
|[state](#state)|Zwraca obiekt reprezentujący stan konwersji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** standardowe

## <a name="byte_string"></a>  wstring_convert::byte_string

Typ, który reprezentuje ciąg bajtów.

```cpp
typedef std::basic_string<char> byte_string;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `std::basic_string<char>`.

## <a name="converted"></a>  wstring_convert::Converted

Zwraca liczbę pomyślnych konwersji.

```cpp
size_t converted() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba pomyślnych konwersji.

### <a name="remarks"></a>Uwagi

Liczba pomyślnych konwersji jest przechowywana w obiekcie Liczba konwersji.

## <a name="from_bytes"></a>  wstring_convert::from_bytes

Konwertuje ciąg bajtów na ciąg znaków dwubajtowych.

```cpp
wide_string from_bytes(char Byte);
wide_string from_bytes(const char* ptr);
wide_string from_bytes(const byte_string& Bstr);
wide_string from_bytes(const char* first, const char* last);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Byte*|Sekwencja bajtów Jednoelementowy, który ma zostać przekonwertowany.|
|*ptr*|Stylu C zakończony znakiem null sekwencji znaków, które ma zostać przekonwertowany.|
|*BSTR*|[Byte_string](#byte_string) ma zostać przekonwertowany.|
|*pierwszy*|Pierwszy znak w zakresie znaków, które mają zostać przekonwertowane.|
|*last*|Ostatni znak zakresu znaków, które mają zostać przekonwertowane.|

### <a name="return-value"></a>Wartość zwracana

Obiekt szerokich, wynikające z konwersji.

### <a name="remarks"></a>Uwagi

Jeśli [stan konwersji](../standard-library/wstring-convert-class.md) obiekt był *nie* skonstruowany z jawną wartością, ustawiono wartość domyślną (stan konwersji początkowej) przed rozpoczęciem konwersji. W przeciwnym razie zostanie pozostawiony bez zmian.

Liczba elementów wejściowych pomyślnie przekonwertowany są przechowywane w obiekcie Liczba konwersji. Jeśli wystąpi błąd nie konwersji, funkcja elementu członkowskiego zwraca przekonwertowany ciąg dwubajtowy. W przeciwnym razie jeśli obiekt został skonstruowany przy użyciu inicjatora komunikatu o błędzie ciąg znaków dwubajtowych, funkcja elementu członkowskiego zwraca obiekt komunikat błędu szerokiego ciągu. W przeciwnym razie funkcja elementu członkowskiego zgłasza obiekt klasy [range_error —](../standard-library/range-error-class.md).

## <a name="int_type"></a>  wstring_convert::int_type

Typ, który reprezentuje liczbę całkowitą.

```cpp
typedef typename wide_string::traits_type::int_type int_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `wide_string::traits_type::int_type`.

## <a name="state"></a>  wstring_convert::State

Zwraca obiekt reprezentujący stan konwersji.

```cpp
state_type state() const;
```

### <a name="return-value"></a>Wartość zwracana

[Stan konwersji](../standard-library/wstring-convert-class.md) obiekt, który reprezentuje stan konwersji.

### <a name="remarks"></a>Uwagi

## <a name="state_type"></a>  wstring_convert::state_type

Typ, który reprezentuje stan konwersji.

```cpp
typedef typename Codecvt::state_type state_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może reprezentować stan konwersji. Typ jest synonimem dla `Codecvt::state_type`.

## <a name="to_bytes"></a>  wstring_convert::to_bytes

Konwertuje ciąg znaków dwubajtowych ciąg bajtów.

```cpp
byte_string to_bytes(Elem Char);
byte_string to_bytes(const Elem* Wptr);
byte_string to_bytes(const wide_string& Wstr);
byte_string to_bytes(const Elem* first, const Elem* last);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Char*|Znak dwubajtowy, który ma zostać przekonwertowany.|
|*Wptr*|Stylu C zakończony znakiem null sekwencji, rozpoczynając od `wptr`, ma zostać przekonwertowany.|
|*WSTR*|[Wide_string](#wide_string) ma zostać przekonwertowany.|
|*pierwszy*|Pierwszy element w zakresie elementów, które ma zostać przekonwertowany.|
|*last*|Ostatniego elementu w zakresie elementów, które ma zostać przekonwertowany.|

### <a name="remarks"></a>Uwagi

Jeśli [stan konwersji](../standard-library/wstring-convert-class.md) obiekt był *nie* skonstruowany z jawną wartością, ustawiono wartość domyślną (stan konwersji początkowej) przed rozpoczęciem konwersji. W przeciwnym razie zostanie pozostawiony bez zmian.

Liczba elementów wejściowych pomyślnie przekonwertowany są przechowywane w obiekcie Liczba konwersji. Jeśli wystąpi błąd nie konwersji, funkcja elementu członkowskiego zwraca ciąg przekonwertowany bajt. W przeciwnym razie jeśli obiekt został skonstruowany przy użyciu inicjatora bajtów ciąg komunikatu o błędzie, funkcja elementu członkowskiego zwraca obiekt bajtów ciąg wiadomości błędu. W przeciwnym razie funkcja elementu członkowskiego zgłasza obiekt klasy [range_error —](../standard-library/range-error-class.md).

## <a name="wide_string"></a>  wstring_convert::wide_string

Typ, który reprezentuje ciąg znaków dwubajtowych.

```cpp
typedef std::basic_string<Elem> wide_string;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `std::basic_string<Elem>`.

## <a name="wstring_convert"></a>  wstring_convert::wstring_convert

Tworzy obiekt typu `wstring_convert`.

```cpp
wstring_convert(Codecvt *Pcvt = new Codecvt);
wstring_convert(Codecvt *Pcvt, state_type _State);
wstring_convert(const byte_string& _Berr, const wide_string& Werr = wide_string());
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*\*Pcvt*|Obiekt typu `Codecvt` dokonać konwersji.|
|*_Stanu*|Obiekt typu [state_type](#state_type) reprezentujący stan konwersji.|
|*_Berr*|[Byte_string](#byte_string) do wyświetlania na błędy.|
|*Werr*|[Wide_string](#wide_string) do wyświetlania na błędy.|

### <a name="remarks"></a>Uwagi

Pierwszy magazynów Konstruktor *Pcvt_arg* w [konwersji obiektu](../standard-library/wstring-convert-class.md)
