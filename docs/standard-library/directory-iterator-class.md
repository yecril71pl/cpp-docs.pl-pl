---
title: directory_iterator, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/10/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- filesystem/std::experimental::filesystem::directory_iterator
- filesystem/std::experimental::filesystem::_Directory_iterator::_Directory_iterator
- filesystem/std::experimental::filesystem::directory_iterator::directory_iterator
- filesystem/std::experimental::filesystem::directory_iterator::increment
- filesystem/std::experimental::filesystem::directory_iterator::operator=
- filesystem/std::experimental::filesystem::directory_iterator::operator==
- filesystem/std::experimental::filesystem::directory_iterator::operator!=
- filesystem/std::experimental::filesystem::directory_iterator::operator*
- filesystem/std::experimental::filesystem::directory_iterator::operator-&gt;
- filesystem/std::experimental::filesystem::directory_iterator::operator++
dev_langs:
- C++
ms.assetid: dca2ecf8-3e69-4644-a83d-705061e10cc8
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::experimental::filesystem::directory_iterator
- std::experimental::filesystem::_Directory_iterator::_Directory_iterator
- std::experimental::filesystem::directory_iterator
- std::experimental::filesystem::directory_iterator::directory_iterator
- std::experimental::filesystem::directory_iterator::increment
- std::experimental::filesystem::directory_iterator::operator=
- std::experimental::filesystem::directory_iterator::operator==
- std::experimental::filesystem::directory_iterator::operator!=
- std::experimental::filesystem::directory_iterator::operator*
- std::experimental::filesystem::directory_iterator::operator-&gt;
- std::experimental::filesystem::directory_iterator::operator++
ms.workload:
- cplusplus
ms.openlocfilehash: 09970c0d3cf8771317c93670c0ec7f029e1ace2a
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44691591"
---
# <a name="directoryiterator-class"></a>directory_iterator — klasa

Opisuje iterator danych wejściowych, które sekwencji za pomocą nazwy plików w katalogu. Dla iteratora `X`, wyrażenie `*X` zwróci obiekt klasy `directory_entry` to wszystko na nazwę pliku i nic wiedzieć o jego stan.

Klasa przechowuje obiekt typu `path`, co jest nazywane `mydir` tutaj w celu specyfikacji, który reprezentuje nazwę katalogu, który ma zostać ustawione w kolejności, i obiektu typu `directory_entry` o nazwie `myentry` tutaj, który reprezentuje bieżący Nazwa pliku w katalogu sekwencji. Domyślne obiektu typu `directory_entry` ma pustą `mydir` pathname i reprezentuje iterator sekwencja kończenia.

Na przykład, biorąc pod uwagę katalogu `abc` z wpisy `def` i `ghi`, kod:

`for (directory_iterator next(path("abc")), end; next != end; ++next)     visit(next->path());`

wywoła `visit` z argumentami `path("abc/def")` i `path("abc/ghi")`.

Aby uzyskać więcej informacji i przykłady kodu, zobacz [nawigacji systemu plików (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Składnia

```cpp
class directory_iterator;
```

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[directory_iterator](#directory_iterator)|Tworzy iterator danych wejściowych, które sekwencji za pomocą nazwy plików w katalogu.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[Inkrementacja](#increment)|Próby, przejdź do następnego nazwy pliku w katalogu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator!=](#op_neq)|Zwraca `!(*this == right)`.|
|[operator=](#op_as)|Operatory przypisania domyślne elementów członkowskich zachowują się zgodnie z oczekiwaniami.|
|[operator==](#op_eq)|Zwraca **true** tylko wtedy, gdy oba `*this` i *prawo* są Iteratory sekwencja kończenia i / lub czy nie end z sekwencji Iteratory.|
|[operator *](#op_star)|Zwraca `myentry`.|
|[operator ->](#op_cast)|Zwraca `&**this`.|
|[operator++](#op_increment)|Wywołania `increment()`, następnie zwraca `*this`, lub kopię obiektu wywołania `increment()`, następnie zwraca kopię.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<eksperymentalne/filesystem >

**Namespace:** std::experimental::filesystem

## <a name="directory_iterator"></a> directory_iterator::directory_iterator

Pierwszy Konstruktor tworzy iterator sekwencja kończenia. Magazyn drugie i trzecie konstruktory *pval* w `mydir`, następnie spróbować otworzyć i przeczytać `mydir` jako katalog. Jeśli operacja się powiedzie, przechowują pierwszą nazwę pliku w katalogu w `myentry`; w przeciwnym razie produkują iterator sekwencja kończenia.

Domyślne construtors zachowują się zgodnie z oczekiwaniami.

```cpp
directory_iterator() noexcept;
explicit directory_iterator(const path& pval);

directory_iterator(const path& pval, error_code& ec) noexcept;
directory_iterator(const directory_iterator&) = default;
directory_iterator(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parametry

*pval*<br/>
Ścieżka Nazwa pliku przechowywanego.

*we*<br/>
Kod stanu błędu. 

*directory_iterator*<br/>
Przechowywany obiekt.

## <a name="increment"></a> directory_iterator::Increment

Funkcja polegające na Przejdź do następnego nazwy pliku w katalogu. Jeśli operacja się powiedzie, przechowuje nazwę tego pliku w `myentry`; w przeciwnym razie wywołuje iteratora sekwencja kończenia.

```cpp
directory_iterator& increment(error_code& ec) noexcept;
```

## <a name="op_neq"></a> directory_iterator::operator! =

Operator elementu członkowskiego zwraca `!(*this == right)`.

```cpp
bool operator!=(const directory_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*right*<br/>
[Directory_iterator](../standard-library/directory-iterator-class.md) którą jest porównywany `directory_iterator`.

## <a name="op_as"></a> directory_iterator::operator =

Operatory przypisania domyślne elementów członkowskich zachowują się zgodnie z oczekiwaniami.

```cpp
directory_iterator& operator=(const directory_iterator&) = default;
directory_iterator& operator=(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parametry

*right*<br/>
[Directory_iterator](../standard-library/directory-iterator-class.md) są kopiowane do `directory_iterator`.

## <a name="op_eq"></a> directory_iterator::operator ==

Operator elementu członkowskiego zwraca **true** tylko wtedy, gdy oba `*this` i *prawo* są Iteratory sekwencja kończenia i / lub czy nie end z sekwencji Iteratory.

```cpp
bool operator==(const directory_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*right*<br/>
[Directory_iterator](../standard-library/directory-iterator-class.md) którą jest porównywany `directory_iterator`.

## <a name="op_star"></a> directory_iterator::operator *

Operator elementu członkowskiego zwraca `myentry`.

```cpp
const directory_entry& operator*() const;
```

## <a name="op_cast"></a> directory_iterator::operator ->

Funkcja elementu członkowskiego zwraca `&**this`.

```cpp
const directory_entry * operator->() const;
```

## <a name="op_increment"></a> directory_iterator::operator ++

Pierwszego wywołania funkcji elementu członkowskiego `increment()`, następnie zwraca `*this`. Funkcja drugiego członka tworzy kopię obiektu wywołania `increment()`, następnie zwraca kopię.

```cpp
directory_iterator& operator++();
directory_iterator& operator++(int);
```

### <a name="parameters"></a>Parametry

*int*<br/>
Liczba przyrostem.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<FileSystem >](../standard-library/filesystem.md)<br/>
[Nawigacja w systemie plików (C++)](../standard-library/file-system-navigation.md)<br/>
