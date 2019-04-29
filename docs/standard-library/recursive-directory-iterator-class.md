---
title: recursive_directory_iterator — klasa
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::tr2::sys::recursive_directory_iterator
ms.assetid: 79a061bd-5b64-404c-97e8-749c888c2ced
ms.openlocfilehash: 52e6f738aa226dba26bae0cf6e97cd18d107d677
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370134"
---
# <a name="recursivedirectoryiterator-class"></a>recursive_directory_iterator — klasa

Opisuje iterator danych wejściowych, sekwencji za pomocą nazwy plików w katalogu, prawdopodobnie malejącej w podkatalogach cyklicznie. Dla iteratora `X`, wyrażenie `*X` zwróci obiekt klasy `directory_entry` to wszystko na nazwę pliku i nic wiedzieć o jego stan.

Aby uzyskać więcej informacji i przykłady kodu, zobacz [nawigacji systemu plików (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Składnia

```cpp
class recursive_directory_iterator;
```

## <a name="remarks"></a>Uwagi

Magazyny klasy szablonu:

1. obiekt typu `stack<pair<directory_iterator, path>>`, co jest nazywane `mystack` w tym miejscu na potrzeby specyfikacji, która reprezentuje zagnieżdżonych katalogów do być sekwencjonowania

1. obiekt typu `directory_entry` o nazwie `myentry` tutaj, który reprezentuje bieżący nazwy pliku w sekwencji katalogu

1. obiekt typu **bool**, co jest nazywane `no_push` tutaj, który rejestruje, czy zejścia cyklicznego do podkatalogów jest wyłączona

1. obiekt typu `directory_options`, co jest nazywane `myoptions` tutaj, który rejestruje opcje ustalone w konstrukcji

Domyślne obiektu typu `recursive_directory_entry` ma iterator sekwencja kończenia w `mystack.top().first` i reprezentuje iterator sekwencja kończenia. Na przykład, biorąc pod uwagę katalogu `abc` z wpisy `def` (katalog) `def/ghi`, i `jkl`, kod:

```cpp
for (recursive_directory_iterator next(path("abc")), end; next != end; ++next)
    visit(next->path());
```

Wywołanie odwiedzi z argumentami `path("abc/def/ghi")` i `path("abc/jkl")`. Może kwalifikujesz się do sekwencjonowania za pośrednictwem podstrom na dwa sposoby:

1. Link symboliczny katalog ma zostać przeprowadzone skanowanie tylko wtedy, gdy konstruowania `recursive_directory_iterator` z `directory_options` argumentu, którego wartością jest `directory_options::follow_directory_symlink`.

1. Jeśli wywołasz `disable_recursion_pending` kolejnych katalogu podczas przyrostowa nie będzie cyklicznie skanowania.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[recursive_directory_iterator](#recursive_directory_iterator)|Konstruuje `recursive_directory_iterator`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[Głębokość](#depth)|Zwraca `mystack.size() - 1`, więc `pval` jest na poziomie od zera.|
|[disable_recursion_pending](#disable_recursion_pending)|Magazyny **true** w `no_push`.|
|[Inkrementacja](#increment)|Przechodzi do następnego nazwy pliku w sekwencji.|
|[Opcje](#options)|Zwraca `myoptions`.|
|[POP](#pop)|Zwraca następny obiekt.|
|[recursion_pending](#recursion_pending)|Zwraca `!no_push`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator!=](#op_neq)|Zwraca `!(*this == right)`.|
|[operator=](#op_as)|Operatory przypisania domyślne elementów członkowskich zachowują się zgodnie z oczekiwaniami.|
|[operator==](#op_eq)|Zwraca **true** tylko wtedy, gdy oba `*this` i *prawo* są Iteratory sekwencja kończenia i / lub czy nie end z sekwencji Iteratory.|
|[operator*](#op_multiply)|Zwraca `myentry`.|
|[operator->](#op_cast)|Zwraca `&**this`.|
|[operator++](#op_increment)|Zwiększa `recursive_directory_iterator`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<filesystem >

**Namespace:** STD::tr2:: sys

## <a name="depth"></a> recursive_directory_iterator::DEPTH

Zwraca `mystack.size() - 1`, więc `pval` jest na poziomie od zera.

```cpp
int depth() const;
```

## <a name="disable_recursion_pending"></a> recursive_directory_iterator::disable_recursion_pending

Magazyny **true** w `no_push`.

```cpp
void disable_recursion_pending();
```

## <a name="increment"></a> recursive_directory_iterator::Increment

Przechodzi do następnego nazwy pliku w sekwencji.

```cpp
recursive_directory_iterator& increment(error_code& ec) noexcept;
```

### <a name="parameters"></a>Parametry

*ec*<br/>
Określony kod błędu.

### <a name="remarks"></a>Uwagi

Funkcja polegające na Przejdź do następnego nazwy pliku w zagnieżdżonych sekwencji. Jeśli operacja się powiedzie, przechowuje nazwę tego pliku w `myentry`; w przeciwnym razie wywołuje iteratora sekwencja kończenia.

## <a name="op_neq"></a> recursive_directory_iterator::operator! =

Zwraca `!(*this == right)`.

```cpp
bool operator!=(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*right*<br/>
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) do porównania.

## <a name="op_as"></a> recursive_directory_iterator::operator =

Operatory przypisania domyślne elementów członkowskich zachowują się zgodnie z oczekiwaniami.

```cpp
recursive_directory_iterator& operator=(const recursive_directory_iterator&) = default;
recursive_directory_iterator& operator=(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parametry

*recursive_directory_iterator*<br/>
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) są kopiowane do `recursive_directory_iterator`.

## <a name="op_eq"></a> recursive_directory_iterator::operator ==

Zwraca **true** tylko wtedy, gdy oba `*this` i *prawo* są Iteratory sekwencja kończenia i / lub czy nie end z sekwencji Iteratory.

```cpp
bool operator==(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*right*<br/>
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) do porównania.

## <a name="op_multiply"></a> recursive_directory_iterator::operator *

Zwraca `myentry`.

```cpp
const directory_entry& operator*() const;
```

## <a name="op_cast"></a> recursive_directory_iterator::operator ->

Zwraca `&**this`.

```cpp
const directory_entry * operator->() const;
```

## <a name="op_increment"></a> recursive_directory_iterator::operator ++

Zwiększa `recursive_directory_iterator`.

```cpp
recursive_directory_iterator& operator++();

recursive_directory_iterator& operator++(int);
```

### <a name="parameters"></a>Parametry

*int*<br/>
Określonym przyrostem.

### <a name="remarks"></a>Uwagi

Pierwszego wywołania funkcji elementu członkowskiego `increment()`, następnie zwraca `*this`. Funkcja drugiego członka tworzy kopię obiektu wywołania `increment()`, następnie zwraca kopię.

## <a name="options"></a> recursive_directory_iterator::Options

Zwraca `myoptions`.

```cpp
directory_options options() const;
```

## <a name="pop"></a> recursive_directory_iterator::POP —

Zwraca następny obiekt.

```cpp
void pop();
```

### <a name="remarks"></a>Uwagi

Jeśli `depth() == 0` obiekt staje się iterator sekwencja kończenia. W przeciwnym razie funkcja elementu członkowskiego kończy się skanowanie bieżącego katalogu (najgłębiej zagnieżdżoną) i zostanie wznowiona na następny głębokość niższe.

## <a name="recursion_pending"></a> recursive_directory_iterator::recursion_pending

Zwraca `!no_push`.

```cpp
bool recursion_pending() const;
```

## <a name="recursive_directory_iterator"></a> recursive_directory_iterator::recursive_directory_iterator

Konstruuje `recursive_directory_iterator`.

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

*pval*<br/>
Określona ścieżka.

*error_code*<br/>
Określonego kodu błędu.

*zdecyduje*<br/>
Opcje określonego katalogu.

*recursive_directory_iterator*<br/>
`recursive_directory_iterator` Którego stworzonego elementu `recursive_directory_iterator` jest kopią.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor tworzy iterator sekwencja kończenia. Magazyn drugie i trzecie konstruktory **false** w `no_push` i `directory_options::none` w `myoptions`, następnie spróbować otworzyć i przeczytać *pval* jako katalog. Jeśli operacja się powiedzie, mogą zainicjować `mystack` i `myentry` do wyznaczenia pierwszy filename-directory zagnieżdżonych sekwencji; w przeciwnym razie produkują iterator sekwencja kończenia.

Czwarty i piąty Konstruktor działa tak samo jak drugi i trzeci, chyba że najpierw zapisać *zdecyduje* w `myoptions`. Domyślne construtors zachowują się zgodnie z oczekiwaniami.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[Nawigacja w systemie plików (C++)](../standard-library/file-system-navigation.md)<br/>
