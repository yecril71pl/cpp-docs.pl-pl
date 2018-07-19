---
title: messages — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b7b604fd58c3f320b62c022e6b5d1749c1f3a87
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954893"
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

*CharType* typ używany w programie do kodowania znaków w ustawieniach regionalnych.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba dostępu do jego przechowywanej wartości przechowuje unikatową wartość dodatnią w **identyfikator.**

W zasadzie ten zestaw reguł otwiera katalog komunikatów zdefiniowany w klasie bazowej messages_base, pobiera wymagane informacje i zamyka katalog.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Komunikaty](#messages)|Funkcja konstruktora zestawu reguł komunikatów.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ znaku, który jest używany do wyświetlania komunikatów.|
|[string_type](#string_type)|Typ, który opisuje ciąg typu `basic_string` zawierający znaki typu `CharType`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[close](#close)|Zamyka katalog komunikatów.|
|[do_close —](#do_close)|Funkcja wirtualna wywoływana, aby zamknąć katalog komunikatów.|
|[do_get](#do_get)|Funkcja wirtualna wywoływana, aby pobrać katalog komunikatów.|
|[do_open —](#do_open)|Funkcja wirtualna wywoływana, aby otworzyć katalog komunikatów.|
|[get](#get)|Pobiera katalog komunikatów.|
|[open](#open)|Otwiera katalog komunikatów.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** standardowe

## <a name="char_type"></a>  messages::char_type

Typ znaku, który jest używany do wyświetlania komunikatów.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu **CharType**.

## <a name="close"></a>  messages::Close

Zamyka katalog komunikatów.

```cpp
void close(catalog _Catval) const;
```

### <a name="parameters"></a>Parametry

*_Catval* katalogu zostanie zamknięty.

### <a name="remarks"></a>Uwagi

Wywołania funkcji elementu członkowskiego [do_close —](#do_close)(_ *Catval*).

## <a name="do_close"></a>  messages::do_close

Funkcja wirtualna wywoływana, aby zamknąć katalog komunikatów.

```cpp
virtual void do_close(catalog _Catval) const;
```

### <a name="parameters"></a>Parametry

*_Catval* katalogu zostanie zamknięty.

### <a name="remarks"></a>Uwagi

Chroniona funkcja elementu członkowskiego Zamyka katalog komunikatów *_Catval*, który musi mieć otwarty przez wcześniejszego wywołania funkcji [do_open —](#do_open).

*_Catval* musi pochodzić z wcześniej otwartych katalogu, który nie jest zamknięty.

### <a name="example"></a>Przykład

Zobacz przykład [Zamknij](#close), która wywołuje metodę `do_close`.

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

*_Catval* identyfikacji określająca katalog komunikatów, który ma być przeszukiwany.

*_Ustaw* zidentyfikowany pierwszy używana do lokalizowania komunikat w katalog komunikatów.

*_Message* zidentyfikowane drugi używana do lokalizowania komunikat w katalog komunikatów.

*_Dfault* ciąg, który ma zostać zwrócona w przypadku niepowodzenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca kopię *_Dfault* w przypadku niepowodzenia. W przeciwnym razie zwraca kopię sekwencji określony komunikat.

### <a name="remarks"></a>Uwagi

Chroniona funkcja elementu członkowskiego próbuje uzyskać sekwencji komunikatów z katalog komunikatów *_Catval*. Rozsądne może okazać się użycie *_Ustaw*, *_Message*, i *_Dfault* w ten sposób.

### <a name="example"></a>Przykład

Zobacz przykład [uzyskać](#get), która wywołuje metodę `do_get`.

## <a name="do_open"></a>  messages::do_open

Funkcja wirtualna wywoływana, aby otworzyć katalog komunikatów.

```cpp
virtual catalog do_open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>Parametry

*_Catname* nazwę katalogu, który ma być przeszukiwany.

*_Loc* ustawienia regionalne są wyszukiwane w wykazie.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość, która porównuje mniejsza od zera na błąd. W przeciwnym wypadku zwracana wartość może służyć jako pierwszy argument w wywołaniu nowsze [uzyskać](#get).

### <a name="remarks"></a>Uwagi

Chroniona funkcja elementu członkowskiego próbuje otworzyć katalog komunikatów, którego nazwa jest *_Catname*. Rozsądne może okazać się użycie ustawień regionalnych *_Loc* w ten sposób

Zwracana wartość będzie używana jako argument w wywołaniu nowsze [Zamknij](#close).

### <a name="example"></a>Przykład

Zobacz przykład [Otwórz](#open), która wywołuje metodę `do_open`.

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

*_Catval* identyfikacji określająca katalog komunikatów, który ma być przeszukiwany.

*_Ustaw* zidentyfikowany pierwszy używana do lokalizowania komunikat w katalog komunikatów.

*_Message* zidentyfikowane drugi używana do lokalizowania komunikat w katalog komunikatów.

*_Dfault* ciąg, który ma zostać zwrócona w przypadku niepowodzenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca kopię *_Dfault* w przypadku niepowodzenia. W przeciwnym razie zwraca kopię sekwencji określony komunikat.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_get —](#do_get)( `_Catval`, `_Set`, `_Message`, `_Dfault`).

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

*_Refs* wartość całkowitą, można określić typ zarządzania pamięci dla obiektu.

*_Locname* nazwę ustawień regionalnych.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *_Refs* parametrów i ich znaczenie są:

- 0: okres istnienia obiektu jest zarządzany przez ustawienia regionalne, zawierających go.

- 1: okres istnienia obiektu musi być zarządzane ręcznie.

- \> 1: nie zdefiniowano tych wartości.

Żadnych przykładów bezpośrednie są to tylko możliwe, ponieważ destruktor jest chroniony.

Konstruktor inicjuje jego podstawowego obiektu z **locale::**[aspekt](../standard-library/locale-class.md#facet_class)( `_Refs`).

## <a name="open"></a>  messages::Open

Otwiera katalog komunikatów.

```cpp
catalog open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>Parametry

*_Catname* nazwę katalogu, który ma być przeszukiwany.

*_Loc* ustawienia regionalne są wyszukiwane w wykazie.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość, która porównuje mniejsza od zera na błąd. W przeciwnym wypadku zwracana wartość może służyć jako pierwszy argument w wywołaniu nowsze [uzyskać](#get).

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_open —](#do_open)( `_Catname`, `_Loc`).

## <a name="string_type"></a>  messages::STRING_TYPE

Typ, który opisuje ciąg typu `basic_string` zawierający znaki typu `CharType`.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizacji szablonu klasy [basic_string](../standard-library/basic-string-class.md) których obiekty można przechowywać kopie sekwencjami wiadomości.

## <a name="see-also"></a>Zobacz także

[\<Ustawienia regionalne >](../standard-library/locale.md)<br/>
[messages_base, klasa](../standard-library/messages-base-class.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
