---
title: messages — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a66da5bc1b1352f4506e6294447a0610a3e1be4e
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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

`CharType` Typ używany w programie do kodowania znaków w ustawieniach regionalnych.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba jej wartości przechowywanej dostępu są przechowywane w unikatową wartość dodatnią **identyfikator.**

W zasadzie ten zestaw reguł otwiera katalog komunikatów zdefiniowany w klasie bazowej messages_base, pobiera wymagane informacje i zamyka katalog.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Komunikaty](#messages)|Funkcja konstruktora zestawu reguł komunikatów.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ znaku, który jest używany do wyświetlania komunikatów.|
|[string_type](#string_type)|Typ, który opisuje ciąg typu `basic_string` zawierające znaki typu `CharType`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[close](#close)|Zamyka katalog komunikatów.|
|[do_close](#do_close)|Funkcja wirtualna wywoływana, aby zamknąć katalog komunikatów.|
|[do_get](#do_get)|Funkcja wirtualna wywoływana, aby pobrać katalog komunikatów.|
|[do_open](#do_open)|Funkcja wirtualna wywoływana, aby otworzyć katalog komunikatów.|
|[get](#get)|Pobiera katalog komunikatów.|
|[open](#open)|Otwiera katalog komunikatów.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** Standard

## <a name="char_type"></a>  messages::char_type

Typ znaku, który jest używany do wyświetlania komunikatów.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu **CharType**.

## <a name="close"></a>  messages::Close

Zamyka katalog komunikatów.

```cpp
void close(catalog _Catval) const;
```

### <a name="parameters"></a>Parametry

`_Catval` Katalog zostanie zamknięty.

### <a name="remarks"></a>Uwagi

Wywołania funkcji Członkowskich [do_close](#do_close)(_ *Catval*).

## <a name="do_close"></a>  messages::do_close

Funkcja wirtualna wywoływana, aby zamknąć katalog komunikatów.

```cpp
virtual void do_close(catalog _Catval) const;
```

### <a name="parameters"></a>Parametry

`_Catval` Katalog zostanie zamknięty.

### <a name="remarks"></a>Uwagi

Funkcja chroniony element członkowski Zamyka katalog komunikat `_Catval`, który musi został otwarty przez wywołanie wcześniejszych [do_open](#do_open).

*_Catval* musi pochodzić od wcześniej otwartych katalogu, który nie jest zamknięty.

### <a name="example"></a>Przykład

Zobacz przykład [zamknąć](#close), które wywołuje `do_close`.

## <a name="do_get"></a>  messages::do_get

Funkcja wirtualna wywoływana, aby pobrać katalog komunikatów.

```cpp
virtual string_type do_get(
    catalog _Catval,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```

### <a name="parameters"></a>Parametry

`_Catval` Wartość Identyfikacja określenie katalogu wiadomości do wyszukania.

`_Set` Zidentyfikowany pierwszy używana do lokalizowania komunikat w katalogu wiadomości.

`_Message` Drugi zidentyfikowane używana do lokalizowania komunikat w katalogu wiadomości.

`_Dfault` Ciąg, który ma zostać zwrócona w przypadku awarii.

### <a name="return-value"></a>Wartość zwracana

Zwraca kopię `_Dfault` w przypadku awarii. W przeciwnym wypadku zwraca kopię sekwencji określonego komunikatu.

### <a name="remarks"></a>Uwagi

Funkcja chroniony element członkowski próbuje uzyskać sekwencji komunikatów z katalogu komunikat `_Catval`. Rozsądne może korzystać z `_Set`, `_Message`, i `_Dfault` w ten sposób.

### <a name="example"></a>Przykład

Zobacz przykład [uzyskać](#get), które wywołuje `do_get`.

## <a name="do_open"></a>  messages::do_open

Funkcja wirtualna wywoływana, aby otworzyć katalog komunikatów.

```cpp
virtual catalog do_open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>Parametry

`_Catname` Nazwa katalogu, który ma zostać wyszukany.

`_Loc` Ustawienia regionalne są wyszukiwane w katalogu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość, która porównuje mniejsza od zera na błąd. W przeciwnym razie wartość zwracana wartość może służyć jako pierwszy argument w wywołaniu nowsze [uzyskać](#get).

### <a name="remarks"></a>Uwagi

Funkcja chroniony element członkowski spróbuje otworzyć wykazu komunikat, którego nazwa jest `_Catname`. Rozsądne może używać ustawień regionalnych `_Loc` w ten sposób

Zwracana wartość powinna być używana jako argument w wywołaniu nowsze [zamknąć](#close).

### <a name="example"></a>Przykład

Zobacz przykład [Otwórz](#open), które wywołuje `do_open`.

## <a name="get"></a>  messages::Get

Pobiera katalog komunikatów.

```cpp
string_type get(
    catalog _CatVal,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```

### <a name="parameters"></a>Parametry

`_Catval` Wartość Identyfikacja określenie katalogu wiadomości do wyszukania.

`_Set` Zidentyfikowany pierwszy używana do lokalizowania komunikat w katalogu wiadomości.

`_Message` Drugi zidentyfikowane używana do lokalizowania komunikat w katalogu wiadomości.

`_Dfault` Ciąg, który ma zostać zwrócona w przypadku awarii.

### <a name="return-value"></a>Wartość zwracana

Zwraca kopię `_Dfault` w przypadku awarii. W przeciwnym wypadku zwraca kopię sekwencji określonego komunikatu.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_get](#do_get)( `_Catval`, `_Set`, `_Message`, `_Dfault`).

## <a name="messages"></a>  messages::messages

Funkcja konstruktora zestawu reguł komunikatów.

```cpp
explicit messages(
    size_t _Refs = 0);

protected: messages(
    const char* _Locname,
    size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

`_Refs` Wartość całkowita używany do określania typu zarządzania pamięci dla obiektu.

`_Locname` Nazwa ustawień regionalnych.

### <a name="remarks"></a>Uwagi

Możliwe wartości `_Refs` i ich znaczenie są:

- 0: okres istnienia obiektu zarządza ustawieniami regionalnymi, które zawierałoby proces.

- 1: okres istnienia obiektu musi być zarządzane ręcznie.

- \> 1: te wartości są niezdefiniowane.

Nie bezpośredniego przykładów to możliwe, ponieważ destruktor jest chroniony.

Konstruktor inicjuje jego obiektu podstawowego z **locale::**[aspektu](../standard-library/locale-class.md#facet_class)( `_Refs`).

## <a name="open"></a>  messages::Open

Otwiera katalog komunikatów.

```cpp
catalog open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>Parametry

`_Catname` Nazwa katalogu, który ma zostać wyszukany.

`_Loc` Ustawienia regionalne są wyszukiwane w katalogu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość, która porównuje mniejsza od zera na błąd. W przeciwnym razie wartość zwracana wartość może służyć jako pierwszy argument w wywołaniu nowsze [uzyskać](#get).

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_open](#do_open)( `_Catname`, `_Loc`).

## <a name="string_type"></a>  messages::STRING_TYPE

Typ, który opisuje ciąg typu `basic_string` zawierające znaki typu **CharType**.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Uwagi

Typ w tym artykule opisano specjalizacji szablonu klasy [basic_string —](../standard-library/basic-string-class.md) których obiekty można przechowywać kopie sekwencji komunikatów.

## <a name="see-also"></a>Zobacz także

[\<Ustawienia regionalne >](../standard-library/locale.md)<br/>
[messages_base, klasa](../standard-library/messages-base-class.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
