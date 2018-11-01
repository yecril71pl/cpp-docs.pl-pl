---
title: '&lt;System plików&gt; operatorów'
ms.date: 11/04/2016
f1_keywords:
- FILESYSTEM/std::experimental::filesystem::operator==
- FILESYSTEM/std::experimental::filesystem::operator!=
- FILESYSTEM/std::experimental::filesystem::operator<
- FILESYSTEM/std::experimental::filesystem::operator<=
- FILESYSTEM/std::experimental::filesystem::operator>
- FILESYSTEM/std::experimental::filesystem::operator>=
- FILESYSTEM/std::experimental::filesystem::operator/
- FILESYSTEM/std::experimental::filesystem::operator<<
- FILESYSTEM/std::experimental::filesystem::operator>>
ms.assetid: 102c4833-aa3b-41a8-8998-f5003c546bfd
ms.openlocfilehash: 378e5d7b8b36aa9b891a87662d432a451ac6bafe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631040"
---
# <a name="ltfilesystemgt-operators"></a>&lt;System plików&gt; operatorów

Operatory wykonać leksykalne porównanie dwóch ścieżek jako ciągi. Użyj `equivalent` funkcję, aby określić, czy dwie ścieżki (na przykład ścieżki względnej i ścieżką bezwzględną) odwoływać się do tego samego pliku lub katalogu na dysku.

Aby uzyskać więcej informacji, zobacz [nawigacji systemu plików (C++)](../standard-library/file-system-navigation.md).

## <a name="operator"></a>operator==

```cpp
bool operator==(const path& left, const path& right) noexcept;
```

Funkcja zwraca left.native() == right.native().

## <a name="operator"></a>operator!=

```cpp
bool operator!=(const path& left, const path& right) noexcept;
```

Funkcja zwraca! (== lewej po prawej stronie).

## <a name="operator"></a>operator<

```cpp
bool operator<(const path& left, const path& right) noexcept;
```

Funkcja zwraca left.native() < right.native().

## <a name="operator"></a>operator<=

```cpp
bool operator<=(const path& left, const path& right) noexcept;
```

Funkcja zwraca! (prawy \< po lewej stronie).

## <a name="operator"></a>operator>

```cpp
bool operator>(const path& left, const path& right) noexcept;
```

Funkcja zwraca bezpośrednio \< po lewej stronie.

## <a name="operator"></a>operator>=

```cpp
bool operator>=(const path& left, const path& right) noexcept;
```

Funkcja zwraca! (po lewej stronie < prawo).

## <a name="operator"></a>operator /

```cpp
path operator/(const path& left, const path& right);
```

Funkcja wykonuje:

```cpp
basic_string<Elem, Traits> str;
path ans = left;
return (ans /= right);
```

## <a name="operator"></a>Operator <<

```cpp
template <class Elem, class Traits>
basic_ostream<Elem, Traits>& operator<<(basic_ostream<Elem, Traits>& os, const path& pval);
```

Funkcja zwraca os << pval.string\<Elem, cechy > ().

## <a name="operator"></a>operator>>

```cpp
template <class Elem, class Traits>
basic_istream<Elem, Traits>& operator<<(basic_istream<Elem, Traits>& is, const path& pval);
```

Funkcja wykonuje:

```cpp
basic_string<Elem, Traits> str;
is>> str;
pval = str;
return (is);
```

## <a name="see-also"></a>Zobacz także

[PATH — klasa (standardowa biblioteka C++)](../standard-library/path-class.md)<br/>
[Nawigacja w systemie plików (C++)](../standard-library/file-system-navigation.md)<br/>
[\<FileSystem >](../standard-library/filesystem.md)<br/>
