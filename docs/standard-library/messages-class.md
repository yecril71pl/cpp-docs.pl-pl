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
ms.openlocfilehash: deb9eaedba3c99bb2fcb8399ac412ccedb11545f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375923"
---
# <a name="messages-class"></a>messages — Klasa

Szablon klasy opisuje obiekt, który może służyć jako aspekt ustawień regionalnych do pobierania zlokalizowanych wiadomości z katalogu wiadomości międzynarodowych dla danego ustawienia regionalne.

Obecnie gdy klasa komunikatów jest implementowana, nie ma żadnych komunikatów.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType>
class messages : public messages_base;
```

### <a name="parameters"></a>Parametry

*Chartype*\
Typ używany w programie do kodowania znaków w ustawieniach regionalnych.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba uzyskania dostępu do przechowywanej wartości przechowuje unikatową wartość dodatnią w **identyfikatorze.**

W zasadzie ten zestaw reguł otwiera katalog komunikatów zdefiniowany w klasie bazowej messages_base, pobiera wymagane informacje i zamyka katalog.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[z chmury do urządzenia](#messages)|Funkcja konstruktora zestawu reguł komunikatów.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[Char_type](#char_type)|Typ znaku, który jest używany do wyświetlania komunikatów.|
|[string_type](#string_type)|Typ opisujący ciąg typu `basic_string` zawierający znaki `CharType`typu .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Zamknij](#close)|Zamyka katalog komunikatów.|
|[do_close](#do_close)|Funkcja wirtualna wywoływana, aby zamknąć katalog komunikatów.|
|[do_get](#do_get)|Funkcja wirtualna wywoływana, aby pobrać katalog komunikatów.|
|[do_open](#do_open)|Funkcja wirtualna wywoływana, aby otworzyć katalog komunikatów.|
|[get](#get)|Pobiera katalog komunikatów.|
|[Otwórz](#open)|Otwiera katalog komunikatów.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ustawień regionalnych

**Przestrzeń nazw:** std

## <a name="messageschar_type"></a><a name="char_type"></a>wiadomości::char_type

Typ znaku, który jest używany do wyświetlania komunikatów.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu **CharType**.

## <a name="messagesclose"></a><a name="close"></a>wiadomości::zamknij

Zamyka katalog komunikatów.

```cpp
void close(catalog _Catval) const;
```

### <a name="parameters"></a>Parametry

*_Catval*\
Katalog do zamknięcia.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wywołuje [do_close](#do_close)(_ *Catval*).

## <a name="messagesdo_close"></a><a name="do_close"></a>wiadomości::do_close

Funkcja wirtualna wywoływana, aby zamknąć katalog komunikatów.

```cpp
virtual void do_close(catalog _Catval) const;
```

### <a name="parameters"></a>Parametry

*_Catval*\
Katalog do zamknięcia.

### <a name="remarks"></a>Uwagi

Funkcja chronionego elementu członkowskiego zamyka katalog wiadomości *_Catval*, które muszą zostać otwarte przez wcześniejsze wywołanie [do_open](#do_open).

*_Catval* musi być uzyskany z wcześniej otwartego katalogu, który nie jest zamknięty.

### <a name="example"></a>Przykład

Zobacz przykład [zamknięcia](#close), `do_close`który wywołuje .

## <a name="messagesdo_get"></a><a name="do_get"></a>wiadomości::do_get

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
Wartość identyfikacji określająca katalog wiadomości, który ma być przeszukiwany.

*_ustaw*\
Pierwszy zidentyfikowany używany do zlokalizowania wiadomości w katalogu wiadomości.

*_Message*\
Drugi zidentyfikowany używany do lokalizowania wiadomości w katalogu wiadomości.

*_Dfault*\
Ciąg do zwracania w przypadku awarii.

### <a name="return-value"></a>Wartość zwracana

Zwraca kopię *_Dfault* na niepowodzenie. W przeciwnym razie zwraca kopię określonej sekwencji komunikatów.

### <a name="remarks"></a>Uwagi

Funkcja chronionego elementu członkowskiego próbuje uzyskać sekwencję wiadomości z katalogu wiadomości *_Catval*. Może korzystać z *_Set,* *_Message*i *_Dfault* w ten sposób.

### <a name="example"></a>Przykład

Zobacz [przykład, aby](#get)uzyskać `do_get`, który wywołuje .

## <a name="messagesdo_open"></a><a name="do_open"></a>wiadomości::do_open

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
Ustawienia regionalne wyszukiwane w katalogu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość, która porównuje mniej niż zero w przypadku awarii. W przeciwnym razie zwrócona wartość może służyć jako pierwszy argument na późniejszym wywołaniu, aby [uzyskać](#get).

### <a name="remarks"></a>Uwagi

Funkcja chronionego elementu członkowskiego próbuje otworzyć katalog wiadomości, którego nazwa jest *_Catname*. Może korzystać z _Loc *regionalnych* w ten sposób

Zwracana wartość powinna być używana jako argument na późniejszym wywołaniu, aby [zamknąć](#close).

### <a name="example"></a>Przykład

Zobacz przykład [otwórz](#open), `do_open`który wywołuje .

## <a name="messagesget"></a><a name="get"></a>wiadomości::get

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
Wartość identyfikacji określająca katalog wiadomości, który ma być przeszukiwany.

*_ustaw*\
Pierwszy zidentyfikowany używany do zlokalizowania wiadomości w katalogu wiadomości.

*_Message*\
Drugi zidentyfikowany używany do lokalizowania wiadomości w katalogu wiadomości.

*_Dfault*\
Ciąg do zwracania w przypadku awarii.

### <a name="return-value"></a>Wartość zwracana

Zwraca kopię *_Dfault* na niepowodzenie. W przeciwnym razie zwraca kopię określonej sekwencji komunikatów.

### <a name="remarks"></a>Uwagi

Funkcja elementu [do_get](#do_get)członkowskiego zwraca do_get `_Catval` `_Set`( `_Message` `_Dfault`, , , ).

## <a name="messagesmessages"></a><a name="messages"></a>wiadomości::wiadomości

Funkcja konstruktora zestawu reguł komunikatów.

```cpp
explicit messages(
    size_t _Refs = 0);

protected: messages(
    const char* _Locname,
    size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_refs*\
Wartość całkowita używana do określania typu zarządzania pamięcią dla obiektu.

*_Locname*\
Nazwa ustawień regionalnych.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *_Refs* i ich znaczenie to:

- 0: Okres istnienia obiektu jest zarządzany przez ustawienia regionalne, które go zawierają.

- 1: Okres istnienia obiektu musi być zarządzany ręcznie.

- \>1: Te wartości nie są zdefiniowane.

Nie są możliwe żadne bezpośrednie przykłady, ponieważ destruktor jest chroniony.

Konstruktor inicjuje swój obiekt bazowy `_Refs`za pomocą **ustawień regionalnych::**[aspekt](../standard-library/locale-class.md#facet_class)( ).

## <a name="messagesopen"></a><a name="open"></a>wiadomości::otwórz

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
Ustawienia regionalne wyszukiwane w katalogu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość, która porównuje mniej niż zero w przypadku awarii. W przeciwnym razie zwrócona wartość może służyć jako pierwszy argument na późniejszym wywołaniu, aby [uzyskać](#get).

### <a name="remarks"></a>Uwagi

Funkcja elementu [do_open](#do_open)członkowskiego zwraca do_open `_Catname` `_Loc`( , ).

## <a name="messagesstring_type"></a><a name="string_type"></a>wiadomości::string_type

Typ opisujący ciąg typu `basic_string` zawierający znaki `CharType`typu .

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [basic_string](../standard-library/basic-string-class.md) których obiekty mogą przechowywać kopie sekwencji wiadomości.

## <a name="see-also"></a>Zobacz też

[\<>ustawień regionalnych](../standard-library/locale.md)\
[Klasa messages_base](../standard-library/messages-base-class.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
