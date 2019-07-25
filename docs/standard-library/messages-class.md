---
title: messages — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages
- xlocmes/std::messages::char_type
- xlocmes/std::messages::string_type
- xlocmes/std::messages::close
- xlocmes/std::messages::do_close
- xlocmes/std::messages::do_get
- xlocmes/std::messages::do_open
- xlocmes/std::messages::get
- xlocmes/std::messages::open
helpviewer_keywords:
- std::messages [C++]
- std::messages [C++], char_type
- std::messages [C++], string_type
- std::messages [C++], close
- std::messages [C++], do_close
- std::messages [C++], do_get
- std::messages [C++], do_open
- std::messages [C++], get
- std::messages [C++], open
ms.assetid: c4c71f40-4f24-48ab-9f7c-daccd8d5bd83
ms.openlocfilehash: f417c33d5502f8e5bd247936c8a0f93007239924
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449938"
---
# <a name="messages-class"></a>messages — Klasa

Klasa szablonu opisuje obiekt, który może służyć jako zestaw reguł ustawień regionalnych w celu pobrania zlokalizowanych komunikatów z katalogu międzynarodowych wiadomości dla danego ustawienia regionalnego.

Obecnie gdy klasa komunikatów jest implementowana, nie ma żadnych komunikatów.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType>
class messages : public messages_base;
```

### <a name="parameters"></a>Parametry

*CharType*\
Typ używany w programie do kodowania znaków w ustawieniach regionalnych.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba uzyskania dostępu do przechowywanej wartości przechowuje unikatową wartość dodatnią w **identyfikatorze.**

W zasadzie ten zestaw reguł otwiera katalog komunikatów zdefiniowany w klasie bazowej messages_base, pobiera wymagane informacje i zamyka katalog.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[komunikaty](#messages)|Funkcja konstruktora zestawu reguł komunikatów.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ znaku, który jest używany do wyświetlania komunikatów.|
|[string_type](#string_type)|Typ, który opisuje ciąg `basic_string` zawierający znaki typu. `CharType`|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[close](#close)|Zamyka katalog komunikatów.|
|[do_close](#do_close)|Funkcja wirtualna wywoływana, aby zamknąć katalog komunikatów.|
|[do_get](#do_get)|Funkcja wirtualna wywoływana, aby pobrać katalog komunikatów.|
|[do_open](#do_open)|Funkcja wirtualna wywoływana, aby otworzyć katalog komunikatów.|
|[get](#get)|Pobiera katalog komunikatów.|
|[open](#open)|Otwiera katalog komunikatów.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ustawień regionalnych

**Przestrzeń nazw:** std

## <a name="char_type"></a>messages:: char_type

Typ znaku, który jest używany do wyświetlania komunikatów.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu CharType .

## <a name="close"></a>messages:: Close

Zamyka katalog komunikatów.

```cpp
void close(catalog _Catval) const;
```

### <a name="parameters"></a>Parametry

*_Catval*\
Wykaz, który ma zostać zamknięty.

### <a name="remarks"></a>Uwagi

Funkcja członkowska wywołuje [do_close](#do_close)(_ *Catval*).

## <a name="do_close"></a>komunikaty::d o_close

Funkcja wirtualna wywoływana, aby zamknąć katalog komunikatów.

```cpp
virtual void do_close(catalog _Catval) const;
```

### <a name="parameters"></a>Parametry

*_Catval*\
Wykaz, który ma zostać zamknięty.

### <a name="remarks"></a>Uwagi

Funkcja chronionego elementu członkowskiego zamyka katalog komunikatów *_Catval*, który musi zostać otwarty przez wcześniejsze wywołanie do [do_open](#do_open).

*_Catval* należy uzyskać z wcześniej otwartego wykazu, który nie jest zamknięty.

### <a name="example"></a>Przykład

Zobacz przykład [zamykania](#close), który wywołuje `do_close`.

## <a name="do_get"></a>komunikaty::d o_get

Funkcja wirtualna wywoływana, aby pobrać katalog komunikatów.

```cpp
virtual string_type do_get(
    catalog _Catval,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```

### <a name="parameters"></a>Parametry

*_Catval*\
Wartość identyfikacyjna określająca wykaz komunikatów do przeszukania.

*_Ustaw*\
Pierwszy zidentyfikowany, używany do lokalizowania komunikatu w wykazie komunikatów.

*_Message*\
Drugi zidentyfikowany, używany do lokalizowania komunikatu w wykazie komunikatów.

*_Dfault*\
Ciąg, który ma zostać zwrócony w przypadku niepowodzenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca kopię *_Dfault* w przypadku niepowodzenia. W przeciwnym razie zwraca kopię określonej sekwencji komunikatów.

### <a name="remarks"></a>Uwagi

Funkcja chronionego elementu członkowskiego próbuje uzyskać sekwencję komunikatów z *_Catval*wykazu komunikatów. Może to spowodować użycie *_Ustaw*, *_Message*i *_Dfault* .

### <a name="example"></a>Przykład

Zobacz przykład dla [Get](#get), który wywołuje `do_get`.

## <a name="do_open"></a>komunikaty::d o_open

Funkcja wirtualna wywoływana, aby otworzyć katalog komunikatów.

```cpp
virtual catalog do_open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>Parametry

*_Catname*\
Nazwa katalogu, który ma być przeszukiwany.

*_Loc*\
Ustawienia regionalne, które są wyszukiwane w katalogu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość, która porównuje mniej niż zero w przypadku niepowodzenia. W przeciwnym razie zwracana wartość może być używana jako pierwszy argument w późniejszej wywołaniu metody [Get](#get).

### <a name="remarks"></a>Uwagi

Funkcja chronionego elementu członkowskiego próbuje otworzyć katalog komunikatów o nazwie *_Catname*. W takim przypadku może być używane *_Loc* ustawień regionalnych

Wartość zwracana powinna być używana jako argument dla późniejszego wywołania do [zamknięcia](#close).

### <a name="example"></a>Przykład

Zobacz przykład [otwierania](#open), które wywołuje `do_open`.

## <a name="get"></a>messages:: Get

Pobiera katalog komunikatów.

```cpp
string_type get(
    catalog _CatVal,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```

### <a name="parameters"></a>Parametry

*_Catval*\
Wartość identyfikacyjna określająca wykaz komunikatów do przeszukania.

*_Ustaw*\
Pierwszy zidentyfikowany, używany do lokalizowania komunikatu w wykazie komunikatów.

*_Message*\
Drugi zidentyfikowany, używany do lokalizowania komunikatu w wykazie komunikatów.

*_Dfault*\
Ciąg, który ma zostać zwrócony w przypadku niepowodzenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca kopię *_Dfault* w przypadku niepowodzenia. W przeciwnym razie zwraca kopię określonej sekwencji komunikatów.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_get](#do_get)( `_Catval`, `_Set`, `_Message` `_Dfault`,).

## <a name="messages"></a>messages:: messages

Funkcja konstruktora zestawu reguł komunikatów.

```cpp
explicit messages(
    size_t _Refs = 0);

protected: messages(
    const char* _Locname,
    size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs*\
Wartość całkowita służąca do określania typu zarządzania pamięcią dla obiektu.

*_Locname*\
Nazwa ustawień regionalnych.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *_Refs* i ich znaczenie są następujące:

- 0: Okres istnienia obiektu jest zarządzany przez elementy lokalne, które go zawierają.

- 1: Okres istnienia obiektu musi być zarządzany ręcznie.

- \> 1: Te wartości nie są zdefiniowane.

Nie są możliwe żadne bezpośrednie przykłady, ponieważ destruktor jest chroniony.

Konstruktor inicjuje swój obiekt podstawowy przy użyciu **ustawień regionalnych::** [facet](../standard-library/locale-class.md#facet_class)( `_Refs`).

## <a name="open"></a>messages:: Open

Otwiera katalog komunikatów.

```cpp
catalog open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>Parametry

*_Catname*\
Nazwa katalogu, który ma być przeszukiwany.

*_Loc*\
Ustawienia regionalne, które są wyszukiwane w katalogu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość, która porównuje mniej niż zero w przypadku niepowodzenia. W przeciwnym razie zwracana wartość może być używana jako pierwszy argument w późniejszej wywołaniu metody [Get](#get).

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_open](#do_open)( `_Catname`, `_Loc`).

## <a name="string_type"></a>messages:: string_type

Typ, który opisuje ciąg `basic_string` zawierający znaki typu. `CharType`

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację klasy szablonu [basic_string](../standard-library/basic-string-class.md) , której obiekty mogą przechowywać kopie sekwencji komunikatów.

## <a name="see-also"></a>Zobacz także

[\<locale>](../standard-library/locale.md)\
[Klasa messages_base](../standard-library/messages-base-class.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
