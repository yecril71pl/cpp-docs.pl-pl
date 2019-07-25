---
title: recursive_directory_iterator — klasa
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::tr2::sys::recursive_directory_iterator
ms.assetid: 79a061bd-5b64-404c-97e8-749c888c2ced
ms.openlocfilehash: 98eaf2494a3bc17c0f9d11683fc67fed433ba3a5
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451708"
---
# <a name="recursivedirectoryiterator-class"></a>recursive_directory_iterator — klasa

Opisuje iterator danych wejściowych, który umożliwia cykliczne przechodzenie sekwencji między nazwami plików w katalogu. W przypadku iteratora `X`wyrażenie `*X` szacuje obiekt klasy `directory_entry` , która otacza nazwę pliku i wszystkie znane informacje o stanie.

Aby uzyskać więcej informacji i przykładów kodu, zobacz [Nawigacja systemu plikówC++()](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Składnia

```cpp
class recursive_directory_iterator;
```

## <a name="remarks"></a>Uwagi

Klasy szablonu są przechowywane:

1. Obiekt typu `stack<pair<directory_iterator, path>>`, wywoływany `mystack` w tym miejscu do celów specyfikacji, który reprezentuje zagnieżdżenie katalogów do sekwencjonowania

1. Obiekt typu `directory_entry` o nazwie `myentry` w tym miejscu, który reprezentuje bieżącą nazwę pliku w sekwencji katalogu

1. Obiekt typu **bool**, wywoływany `no_push` w tym miejscu, który rejestruje, czy rekursywny w podkatalogach jest wyłączony

1. Obiekt typu `directory_options`o nazwie `myoptions` , który rejestruje opcje ustalone w konstrukcji

Domyślny skonstruowany obiekt typu `recursive_directory_entry` ma iterator End of Sequence w `mystack.top().first` i reprezentuje iterator końca sekwencji. Na przykład `abc` , mając katalog z wpisami `def` (katalog), `def/ghi`, i `jkl`, kod:

```cpp
for (recursive_directory_iterator next(path("abc")), end; next != end; ++next)
    visit(next->path());
```

wywoła odwiedzenie z `path("abc/def/ghi")` argumentami `path("abc/jkl")`i. Sekwencjonowanie można zakwalifikować za pomocą poddrzewa katalogów na dwa sposoby:

1. Link symboliczny katalogu zostanie przeskanowany tylko wtedy, gdy konstruujesz `recursive_directory_iterator` `directory_options` z argumentem, którego `directory_options::follow_directory_symlink`wartość to.

1. Jeśli zostanie wywołana `disable_recursion_pending` , kolejny katalog napotkany podczas przyrostu nie będzie przeskanowany cyklicznie.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[recursive_directory_iterator](#recursive_directory_iterator)|Konstruuje `recursive_directory_iterator`a.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[ścisł](#depth)|Zwraca `mystack.size() - 1`, więc `pval` ma głębokość zero.|
|[disable_recursion_pending](#disable_recursion_pending)|Przechowuje **wartość true** w `no_push`.|
|[pełny](#increment)|Przechodzi do kolejnej nazwy pliku w sekwencji.|
|[Opcje](#options)|Zwraca `myoptions`wartość.|
|[skakując](#pop)|Zwraca następny obiekt.|
|[recursion_pending](#recursion_pending)|Zwraca `!no_push`wartość.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator!=](#op_neq)|Zwraca `!(*this == right)`wartość.|
|[operator=](#op_as)|Operatory przypisywania domyślnego elementu członkowskiego zachowują się zgodnie z oczekiwaniami.|
|[operator==](#op_eq)|Zwraca **wartość true** tylko wtedy `*this` , gdy obie i *prawo* są iteratorami End-of-Sequence lub oba nie są kompletnymi iteratorami sekwencji.|
|[zakład](#op_multiply)|Zwraca `myentry`wartość.|
|[operator — >](#op_cast)|Zwraca `&**this`wartość.|
|[operator++](#op_increment)|`recursive_directory_iterator`Zwiększa.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> systemu plików

**Przestrzeń nazw:** std:: TR2:: sys

## <a name="depth"></a>recursive_directory_iterator::d epth

Zwraca `mystack.size() - 1`, więc `pval` ma głębokość zero.

```cpp
int depth() const;
```

## <a name="disable_recursion_pending"></a>recursive_directory_iterator::d isable_recursion_pending

Przechowuje **wartość true** w `no_push`.

```cpp
void disable_recursion_pending();
```

## <a name="increment"></a>recursive_directory_iterator:: Increment

Przechodzi do kolejnej nazwy pliku w sekwencji.

```cpp
recursive_directory_iterator& increment(error_code& ec) noexcept;
```

### <a name="parameters"></a>Parametry

*udziela*\
Określony kod błędu.

### <a name="remarks"></a>Uwagi

Funkcja próbuje przejść do kolejnej nazwy pliku w sekwencji zagnieżdżonej. Jeśli to się powiedzie, przechowuje tę `myentry`nazwę pliku w; w przeciwnym razie generuje iterator sekwencji końcowej.

## <a name="op_neq"></a>recursive_directory_iterator:: operator! =

Zwraca `!(*this == right)`wartość.

```cpp
bool operator!=(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) do porównania.

## <a name="op_as"></a>recursive_directory_iterator:: operator =

Operatory przypisywania domyślnego elementu członkowskiego zachowują się zgodnie z oczekiwaniami.

```cpp
recursive_directory_iterator& operator=(const recursive_directory_iterator&) = default;
recursive_directory_iterator& operator=(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parametry

*recursive_directory_iterator*\
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) kopiowany do `recursive_directory_iterator`.

## <a name="op_eq"></a>recursive_directory_iterator:: operator = =

Zwraca **wartość true** tylko wtedy `*this` , gdy obie i *prawo* są iteratorami End-of-Sequence lub oba nie są kompletnymi iteratorami sekwencji.

```cpp
bool operator==(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) do porównania.

## <a name="op_multiply"></a>recursive_directory_iterator:: operator *

Zwraca `myentry`wartość.

```cpp
const directory_entry& operator*() const;
```

## <a name="op_cast"></a>recursive_directory_iterator:: operator->

Zwraca `&**this`wartość.

```cpp
const directory_entry * operator->() const;
```

## <a name="op_increment"></a>recursive_directory_iterator:: operator + +

`recursive_directory_iterator`Zwiększa.

```cpp
recursive_directory_iterator& operator++();

recursive_directory_iterator& operator++(int);
```

### <a name="parameters"></a>Parametry

*ZAOKR*\
Określony przyrost.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego `increment()`wywołuje metodę, `*this`a następnie zwraca. Druga funkcja członkowska wykonuje kopię obiektu, wywołuje `increment()`, a następnie zwraca kopię.

## <a name="options"></a>recursive_directory_iterator:: Options

Zwraca `myoptions`wartość.

```cpp
directory_options options() const;
```

## <a name="pop"></a>recursive_directory_iterator::p op

Zwraca następny obiekt.

```cpp
void pop();
```

### <a name="remarks"></a>Uwagi

Jeśli `depth() == 0` obiekt jest iteratorem końca sekwencji. W przeciwnym razie funkcja członkowska kończy skanowanie bieżącego (najgłębszego) katalogu i wznawia się z następną niższą głębokością.

## <a name="recursion_pending"></a>recursive_directory_iterator::recursion_pending

Zwraca `!no_push`wartość.

```cpp
bool recursion_pending() const;
```

## <a name="recursive_directory_iterator"></a>recursive_directory_iterator::recursive_directory_iterator

Konstruuje `recursive_directory_iterator`a.

```cpp
recursive_directory_iterator() noexcept;
explicit recursive_directory_iterator(const path& pval);

recursive_directory_iterator(const path& pval,
    error_code& ec) noexcept;
recursive_directory_iterator(const path& pval,
    directory_options opts);

recursive_directory_iterator(const path& pval,
    directory_options opts,
    error_code& ec) noexcept;
recursive_directory_iterator(const recursive_directory_iterator&) = default;
recursive_directory_iterator(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parametry

*pval*\
Określona ścieżka.

*error_code*\
Określony kod błędu.

*Zasubskrybowanie*\
Określone opcje katalogu.

*recursive_directory_iterator*\
`recursive_directory_iterator` Którego konstrukcja`recursive_directory_iterator` ma być kopią.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor tworzy iterator końca sekwencji. Drugi i trzeci konstruktory przechowują **fałszywe** w `directory_options::none` `no_push` i `myoptions`w, a następnie próbują otworzyć i odczytać *Pval* jako katalog. Jeśli zakończyło się `mystack` pomyślnie `myentry` , zainicjują i wyznaczyli pierwszy plik spoza katalogu w sekwencji zagnieżdżonej; w przeciwnym razie tworzy iterator końca sekwencji.

Czwarte i piąte konstruktory zachowują się tak samo, jak drugi i trzeci, z  tą różnicą, że najpierw `myoptions`są załączane. Wartość domyślna construtors zachowuje się zgodnie z oczekiwaniami.

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)\
[Nawigacja w systemie plikówC++()](../standard-library/file-system-navigation.md)
