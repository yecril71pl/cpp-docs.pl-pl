---
title: PATH — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- filesystem/std::experimental::filesystem::path
dev_langs:
- C++
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7674f07c92f8a0c9d8a9070f3f99e00dfde39140
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235467"
---
# <a name="path-class"></a>path — klasa

**Ścieżki** klasa przechowuje obiekt typu `string_type`, co jest nazywane `myname` tutaj na potrzeby specyfikacji odpowiedni do użytku jako nazwa ścieżki. `string_type` jest synonimem dla `basic_string<value_type>`, gdzie `value_type` jest synonimem dla **wchar_t** na Windows lub **char** w modelu POSIX.

Aby uzyskać więcej informacji i przykłady kodu, zobacz [nawigacji systemu plików (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Składnia

```cpp
class path;
```

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Ścieżka](#path)|Konstruuje `path`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[const_iterator](#const_iterator)|Synonim dla `iterator`.|
|[iterator](#iterator)|Stałe iteratora dwukierunkowego, który wyznacza `path` składniki `myname`.|
|[string_type](#string_type)|Typ jest synonimem dla `basic_string<value_type>`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[Dołącz](#append)|Dołącza określony sekwencji w celu `mypath`, konwersji i wstawianie preferred_separator zgodnie z potrzebami.|
|[Przypisz](#assign)|Zastępuje `mypath` określonej sekwencji konwertowane odpowiednio do potrzeb.|
|[begin](#begin)|Zwraca `path::iterator` wyznaczanie pierwszego elementu w ścieżce w nazwie ścieżki, jeśli jest obecny.|
|[c_str](#c_str)|Zwraca wskaźnik do pierwszego znaku w `mypath`.|
|[Usuń zaznaczenie](#clear)|Wykonuje `mypath.clear()`.|
|[Porównanie](#compare)|Zwraca wartości do porównania.|
|[concat](#compare)|Dołącza określony sekwencji w celu `mypath`, przekonwertować (ale nie Wstawianie separatorem) zgodnie z potrzebami.|
|[pusty](#empty)|Zwraca `mypath.empty()`.|
|[koniec](#end)|Zwraca iterator sekwencja kończenia typu `iterator`.|
|[Rozszerzenie](#extension)|Zwraca sufiks `filename()`.|
|[Nazwa pliku](#filename)|Zwraca składnik katalogu głównego mojanazwa, w szczególności `empty() path() : *--end()`. Składnik może być pusta.|
|[generic_string —](#generic_string)|Zwraca `this->string<Elem, Traits, Alloc>(al)` z (w obszarze Windows) wszelkie ukośnik odwrotny jest konwertowany na ukośnik.|
|[generic_u16string](#generic_u16string)|Zwraca `u16string()` z (w obszarze Windows) wszelkie ukośnik odwrotny jest konwertowany na ukośnik.|
|[generic_u32string](#generic_u32string)|Zwraca `u32string()` z (w obszarze Windows) wszelkie ukośnik odwrotny jest konwertowany na ukośnik.|
|[generic_u8string](#generic_u8string)|Zwraca `u8string()` z (w obszarze Windows) wszelkie ukośnik odwrotny jest konwertowany na ukośnik.|
|[generic_wstring](#generic_wstring)|Zwraca `wstring()` z (w obszarze Windows) wszelkie ukośnik odwrotny jest konwertowany na ukośnik.|
|[has_extension](#has_extension)|Zwraca `!extension().empty()`.|
|[has_filename](#has_filename)|Zwraca `!filename().empty()`.|
|[has_parent_path](#has_parent_path)|Zwraca `!parent_path().empty()`.|
|[has_relative_path](#has_relative_path)|Zwraca `!relative_path().empty()`.|
|[has_root_directory](#has_root_directory)|Zwraca `!root_directory().empty()`.|
|[has_root_name](#has_root_name)|Zwraca `!root_name().empty()`.|
|[has_root_path](#has_root_path)|Zwraca `!root_path().empty()`.|
|[has_stem](#has_stem)|Zwraca `!stem().empty()`.|
|[is_absolute](#is_absolute)|Windows, funkcja zwraca `has_root_name() && has_root_directory()`. Posix, funkcja zwraca `has_root_directory()`.|
|[is_relative](#is_relative)|Zwraca `!is_absolute()`.|
|[make_preferred](#make_preferred)|Konwertuje każdego separatora preferred_separator zgodnie z potrzebami.|
|[Natywne](#native)|Zwraca `myname`.|
|[parent_path](#parent_path)|Zwraca element nadrzędny składnik path `myname`.|
|[preferred_separator](#preferred_separator)|Stały obiekt zawierają znaków preferowaną oddzielenie składników ścieżki, w zależności od systemu operacyjnego hosta. |
|[relative_path](#relative_path)|Zwraca składnik ścieżki względnej `myname`. |
|[remove_filename —](#remove_filename)|Usuwa nazwę pliku.|
|[replace_extension —](#replace_extension)|Zastępuje rozszerzenie `myname`. |
|[replace_filename](#replace_filename)|RReplaces nazwę pliku.|
|[root_directory](#root_directory)|Zwraca składnik katalogu głównego `myname`. |
|[root_name](#root_name)|Zwraca składnik nazwy głównej `myname`. |
|[root_path](#root_path)|Zwraca składnik ścieżki katalogu głównego `myname`.|
|[stem](#stem)|Zwraca `stem` składnika `myname`.|
|[string](#string)|Konwertuje sekwencję przechowywane w `mypath`.|
|[swap](#swap)|Wykonuje `swap(mypath, right.mypath)`.|
|[u16string](#u16string)|Konwertuje sekwencję przechowywane w `mypath` UTF-16 i zwraca ona przechowywana w obiekcie typu `u16string`.|
|[u32string](#u32string)|Konwertuje sekwencję przechowywane w `mypath` UTF-32 i zwraca ona przechowywana w obiekcie typu `u32string`.|
|[u8string](#u8string)|Konwertuje sekwencję przechowywane w `mypath` UTF-8 i zwraca ona przechowywana w obiekcie typu `u8string`.|
|[value_type](#value_type)|Typ opisuje elementów ścieżki faworytem przez system operacyjny hosta.|
|[wstring](#wstring)|Konwertuje sekwencję przechowywane w `mypath` faworytem przez system hosta do kodowania `wchar_t` sekwencji i zwraca ona przechowywana w obiekcie typu `wstring`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_as)|Zastępuje elementy ścieżki z kopią inną ścieżkę.|
|[operator+=](#op_add)|Różne `concat` wyrażenia.|
|[operator / =](#op_divide)|Różne `append` wyrażenia.|
|[string_type — operator](#op_string)|Zwraca `myname`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<filesystem >

**Namespace:** std::experimental::filesystem

## <a name="append"></a> path::append —

Dołącza określony sekwencji w celu `mypath`przekonwertowanego i wstawianie `preferred_separator` zgodnie z potrzebami.

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

### <a name="parameters"></a>Parametry

*source*<br/>
Określonej sekwencji.

*pierwszy*<br/>
Początek określonej sekwencji.

*ostatni*<br/>
Zakończenie określonej sekwencji.

## <a name="assign"></a> path::ASSIGN —

Zastępuje `mypath` określonej sekwencji konwertowane odpowiednio do potrzeb.

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

### <a name="parameters"></a>Parametry

*source*<br/>
Określonej sekwencji.

*pierwszy*<br/>
Początek określonej sekwencji.

*ostatni*<br/>
Zakończenie określonej sekwencji.

## <a name="begin"></a> path::BEGIN —

Zwraca `path::iterator` wyznaczanie pierwszego elementu w ścieżce w nazwie ścieżki, jeśli jest obecny.

```cpp
iterator begin() const;
```

## <a name="c_str"></a> path::c_str

Zwraca wskaźnik do pierwszego znaku w `mypath`.

```cpp
const value_type& *c_str() const noexcept;
```

## <a name="clear"></a> path::Clear —

Wykonuje `mypath.clear()`.

```cpp
void clear() noexcept;
```

## <a name="compare"></a> path::COMPARE —

Pierwsza funkcja zwraca `mypath.compare(pval.native())`. Druga funkcja zwraca `mypath.compare(str)`. Trzecia funkcja zwraca `mypath.compare(ptr)`.

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>Parametry

*pval*<br/>
Ścieżka do porównania.

*str*<br/>
Ciąg do porównania.

*ptr*<br/>
Wskaźnik do porównania.

## <a name="concat"></a> path::concat —

Dołącza określony sekwencji w celu `mypath`, przekonwertować (ale nie Wstawianie separatorem) zgodnie z potrzebami.

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

### <a name="parameters"></a>Parametry

*source*<br/>
Określonej sekwencji.

*pierwszy*<br/>
Początek określonej sekwencji.

*ostatni*<br/>
Zakończenie określonej sekwencji.

## <a name="const_iterator"></a> path::const_iterator

Synonim dla `iterator`.

```cpp
typedef iterator const_iterator;
```

## <a name="empty"></a> path::Empty —

Zwraca `mypath.empty()`.

```cpp
bool empty() const noexcept;
```

## <a name="end"></a> path::end —

Zwraca iterator sekwencja kończenia typu `iterator`.

```cpp
iterator end() const;
```

## <a name="extension"></a> path::Extension —

Zwraca sufiks `filename()`.

```cpp
path extension() const;
```

### <a name="remarks"></a>Uwagi

Zwraca sufiks `filename() X` tak, aby:

Jeśli `X == path(".") || X == path("..")` lub jeśli `X` zawiera nie kropka sufiks jest pusty.

W przeciwnym razie sufiks zaczyna się od (i zawiera) po prawej stronie kropki (.).

## <a name="filename"></a> path::filename —

Zwraca składnik katalogu głównego mojanazwa, w szczególności `empty() path() : *--end()`. Składnik może być pusta.

```cpp
path filename() const;
```

## <a name="generic_string"></a> path::generic_string

Zwraca `this->string<Elem, Traits, Alloc>(al)` z (w obszarze Windows) wszelkie ukośnik odwrotny jest konwertowany na ukośnik.

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

## <a name="generic_u16string"></a> path::generic_u16string

Zwraca `u16string()` z (w obszarze Windows) wszelkie ukośnik odwrotny jest konwertowany na ukośnik.

```cpp
u16string generic_u16string() const;
```

## <a name="generic_u32string"></a> path::generic_u32string

Zwraca `u32string()` z (w obszarze Windows) wszelkie ukośnik odwrotny jest konwertowany na ukośnik.

```cpp
u32string generic_u32string() const;
```

## <a name="generic_u8string"></a> path::generic_u8string

Zwraca `u8string()` z (w obszarze Windows) wszelkie ukośnik odwrotny jest konwertowany na ukośnik.

```cpp
string generic_u8string() const;
```

## <a name="generic_wstring"></a> path::generic_wstring

Zwraca `wstring()` z (w obszarze Windows) wszelkie ukośnik odwrotny jest konwertowany na ukośnik.

```cpp
wstring generic_wstring() const;
```

## <a name="has_extension"></a> path::has_extension

Zwraca `!extension().empty()`.

```cpp
bool has_extension() const;
```

## <a name="has_filename"></a> path::has_filename —

Zwraca `!filename().empty()`.

```cpp
bool has_filename() const;
```

## <a name="has_parent_path"></a> path::has_parent_path —

Zwraca `!parent_path().empty()`.

```cpp
bool has_parent_path() const;
```

## <a name="has_relative_path"></a> path::has_relative_path —

Zwraca `!relative_path().empty()`.

```cpp
bool has_relative_path() const;
```

## <a name="has_root_directory"></a> path::has_root_directory —

Zwraca `!root_directory().empty()`.

```cpp
bool has_root_directory() const;
```

## <a name="has_root_name"></a> path::has_root_name —

Zwraca `!root_name().empty()`.

```cpp
bool has_root_name() const;
```

## <a name="has_root_path"></a> path::has_root_path —

Zwraca `!root_path().empty()`.

```cpp
bool has_root_path() const;
```

## <a name="has_stem"></a> path::has_stem

Zwraca `!stem().empty()`.

```cpp
bool has_stem() const;
```

## <a name="is_absolute"></a> path::is_absolute —

Windows, funkcja zwraca `has_root_name() && has_root_directory()`. Posix, funkcja zwraca `has_root_directory()`.

```cpp
bool is_absolute() const;
```

## <a name="is_relative"></a> path::is_relative —

Zwraca `!is_absolute()`.

```cpp
bool is_relative() const;
```

## <a name="iterator"></a> path::iterator

Stałe iteratora dwukierunkowego, który wyznacza ścieżkę składniki `myname`.

```cpp
class iterator
   {
   // bidirectional iterator for path
   typedef bidirectional_iterator_tag iterator_category;
   typedef path_type value_type;
   typedef ptrdiff_t difference_type;
   typedef const value_type *pointer;
   typedef const value_type& reference;
   // ...
   };
```

### <a name="remarks"></a>Uwagi

Klasa opisuje stałej iteratora dwukierunkowego, który wyznacza `path` składniki `myname` w sekwencji:

1. główna nazwa, jeśli jest obecny

1. katalog główny, jeśli jest obecny

1. wszystkie pozostałe elementy katalogu nadrzędnego `path`, jeśli jest obecny, kończąc nazwy pliku, jeśli jest obecny

Aby uzyskać `pval` obiektu typu `path`:

1. `path::iterator X = pval.begin()` Określa pierwszy `path` elementu w nazwie ścieżki, jeśli jest obecny.

1. `X == pval.end()` jest istotne, kiedy `X` punktów tylko poza końcem sekwencji składników.

3. `*X` Zwraca ciąg, który pasuje do bieżącego składnika

1. `++X` wskazuje następny składnik w sekwencji, jeśli jest obecny.

1. `--X` wyznacza poprzedni składnik w sekwencji, jeśli jest obecny.

1. Zmienianie `myname` unieważnia wszystkie Iteratory, wyznaczanie elementów w `myname`.

## <a name="make_preferred"></a> path::make_preferred —

Konwertuje każdy separator, który `preferred_separator` zgodnie z potrzebami.

```cpp
path& make_preferred();
```

## <a name="native"></a> path::Native

Zwraca `myname`.

```cpp
const string_type& native() const noexcept;
```

## <a name="op_as"></a> path::operator =

Zastępuje elementy ścieżki z kopią inną ścieżkę.

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

### <a name="parameters"></a>Parametry

*right*<br/>
[Ścieżki](../standard-library/path-class.md) są kopiowane do `path`.

*source*<br/>
Ścieżka źródłowa.

### <a name="remarks"></a>Uwagi

Pierwszy kopie operator składowej `right.myname` do `myname`. Drugi operator członkowski przenosi `right.myname` do `myname`. Trzeci operator składowy zachowuje się taka sama jak `*this = path(source)`.

## <a name="op_add"></a> path::operator +=

Różne `concat` wyrażenia.

```cpp
path& operator+=(const path& right);
path& operator+=(const string_type& str);
path& operator+=(const value_type *ptr);
path& operator+=(value_type elem);

template <class Source>
path& operator+=(const Source& source);

template <class Elem>
path& operator+=(Elem elem);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Dodano ścieżka.

*str*<br/>
Dodano parametry.

*ptr*<br/>
Dodano wskaźnik.

*Elem*<br/>
Dodany `value_type` lub `Elem`.

*source*<br/>
Dodano źródło.

### <a name="remarks"></a>Uwagi

Funkcje elementów członkowskich zachowują się taka sama jak poniższy odpowiednich wyrażeń:

1. `concat(right);`

1. `concat(path(str));`

1. `concat(ptr);`

1. `concat(string_type(1, elem));`

1. `concat(source);`

1. `concat(path(basic_string<Elem>(1, elem)));`

## <a name="op_divide"></a> path::operator / =

Różne `append` wyrażenia.

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Dodano ścieżka.

*source*<br/>
Dodano źródło.

### <a name="remarks"></a>Uwagi

Funkcje elementów członkowskich zachowują się taka sama jak poniższy odpowiednich wyrażeń:

1. `append(right);`

1. `append(source);`

## <a name="op_string"></a> path::operator string_type

Zwraca `myname`.

```cpp
operator string_type() const;
```

## <a name="parent_path"></a> path::parent_path —

Zwraca element nadrzędny składnik path `myname`.

```cpp
path parent_path() const;
```

### <a name="remarks"></a>Uwagi

Zwraca element nadrzędny składnik path `myname`, w szczególności prefiks `myname` po usunięciu `filename().native()` i wszystkie bezpośrednio poprzedzającego separatora katalogów. (Tak samo, jeśli `begin() != end()`, jest łączenie wszystkich elementów w zakresie `[begin(), --end())` kolejno stosując `operator/=`.) Składnik może być pusta.

## <a name="path"></a> path::Path —

Konstruuje `path` na różne sposoby.

```cpp
path();

path(const path& right);
path(path&& right) noexcept;

template <class Source>
path(const Source& source);

template <class Source>
path(const Source& source, const locale& loc);

template <class InIt>
path(InIt first, InIt last);

template <class InIt>
path(InIt first, InIt last, const locale& loc);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Ścieżka, w której ścieżki konstruowanej jest kopią.

*source*<br/>
Źródło, w której ścieżki konstruowanej jest kopią.

*Lokalizacja*<br/>
Określonych ustawień regionalnych.

*pierwszy*<br/>
Pozycja pierwszego elementu, który ma być skopiowany.

*ostatni*<br/>
Pozycja ostatni element do skopiowania.

### <a name="remarks"></a>Uwagi

Konstruktory wszystkie konstruowania `myname` na różne sposoby:

Aby uzyskać `path()` jest `myname()`.

Aby uzyskać `path(const path& right`) jest `myname(right.myname)`.

Aby uzyskać `path(path&& right)` jest `myname(right.myname)`.

Aby uzyskać `template<class Source> path(const Source& source)` jest `myname(source)`.

Aby uzyskać `template<class Source> path(const Source& source, const locale& loc)` jest `myname(source)`, uzyskiwanie dowolne wymagane aspektami codecvt z `loc`.

Aby uzyskać `template<class InIt> path(InIt first, InIt last)` jest `myname(first, last)`.

Aby uzyskać `template<class InIt> path(InIt first, InIt last, const locale& loc)` jest `myname(first, last)`, uzyskiwanie dowolne wymagane aspektami codecvt z `loc`.

## <a name="preferred_separator"></a> path::preferred_separator

Stały obiekt zawierają znaków preferowaną oddzielenie składników ścieżki, w zależności od systemu operacyjnego hosta.

```cpp
#if _WIN32_C_LIB
static constexpr value_type preferred_separator == L'\\';
#else // assume Posix
static constexpr value_type preferred_separator == '/';
#endif // filesystem model now defined
```

### <a name="remarks"></a>Uwagi

Należy pamiętać, że równie dopuszczalna w większości konteksty w Windows do użycia L "/" w tym miejscu.

## <a name="relative_path"></a> path::relative_path —

Zwraca składnik ścieżki względnej `myname`.

```cpp
path relative_path() const;
```

### <a name="remarks"></a>Uwagi

Zwraca składnik ścieżki względnej `myname`, w szczególności sufiks `myname` po usunięciu `root_path().native()` i żadnych separatorów natychmiast kolejnych nadmiarowe katalogu. Składnik może być pusta.

## <a name="remove_filename"></a> path::remove_filename —

Usuwa nazwę pliku.

```cpp
path& remove_filename();
```

## <a name="replace_extension"></a> path::replace_extension —

Zastępuje rozszerzenie `myname`.

```cpp
path& replace_extension(const path& newext = path());
```

### <a name="parameters"></a>Parametry

*newext*<br/>
Nowe rozszerzenie.

### <a name="remarks"></a>Uwagi

Najpierw Usuwa sufiks `extension().native()` z `myname`. A w przypadku `!newext.empty() && newext[0] != dot` (gdzie `dot` jest `*path(".").c_str()`), następnie `dot` jest dołączany do `myname`. Następnie *newext* jest dołączany do `myname`.

## <a name="replace_filename"></a> path::replace_filename —

Zastępuje nazwę pliku.

```cpp
path& replace_filename(const path& pval);
```

### <a name="parameters"></a>Parametry

*pval*<br/>
Ścieżka do pliku.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wykonuje:

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="root_directory"></a> path::root_directory —

Zwraca składnik katalogu głównego `myname`.

```cpp
path root_directory() const;
```

### <a name="remarks"></a>Uwagi

Składnik może być pusta.

## <a name="root_name"></a> path::root_name —

Zwraca składnik nazwy głównej `myname`.

```cpp
path root_name() const;
```

### <a name="remarks"></a>Uwagi

Składnik może być pusta.

## <a name="root_path"></a> path::root_path —

Zwraca składnik ścieżki katalogu głównego `myname`.

```cpp
path root_path() const;
```

### <a name="remarks"></a>Uwagi

Zwraca składnik ścieżki katalogu głównego `myname`, konkretnie `root_name()`  /  `root_directory`. Składnik może być pusta.

## <a name="stem"></a> path::stem —

Zwraca `stem` składnika `myname`.

```cpp
path stem() const;
```

### <a name="remarks"></a>Uwagi

Zwraca `stem` składnika `myname`, konkretnie `filename().native()` wszelkie spacją `extension().native()` usunięte. Składnik może być pusta.

## <a name="string"></a> path::String

Konwertuje sekwencję przechowywane w `mypath`.

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego (szablon) konwertuje sekwencję przechowywane w `mypath` taki sam sposób jak:

1. `string()` Aby uzyskać `string<char, Traits, Alloc>()`

1. `wstring()` Aby uzyskać `string<wchar_t, Traits, Alloc>()`

1. `u16string()` Aby uzyskać `string<char16_t, Traits, Alloc>()`

1. `u32string()` Aby uzyskać `string<char32_t, Traits, Alloc>()`

Funkcja drugiego członka konwertuje sekwencję przechowywane w `mypath` faworytem przez system hosta do kodowania **char** sekwencji i zwraca ona przechowywana w obiekcie typu `string`.

## <a name="string_type"></a> path::STRING_TYPE

Typ jest synonimem dla `basic_string<value_type>`.

```cpp
typedef basic_string<value_type> string_type;
```

## <a name="swap"></a> path::swap —

Wykonuje `swap(mypath, right.mypath)`.

```cpp
void swap(path& right) noexcept;
```

## <a name="u16string"></a> path::u16string

Konwertuje sekwencję przechowywane w `mypath` UTF-16 i zwraca ona przechowywana w obiekcie typu `u16string`.

```cpp
u16string u16string() const;
```

## <a name="u32string"></a> path::u32string

Konwertuje sekwencję przechowywane w `mypath` UTF-32 i zwraca ona przechowywana w obiekcie typu `u32string`.

```cpp
u32string u32string() const;
```

## <a name="u8string"></a> path::u8string

Konwertuje sekwencję przechowywane w `mypath` UTF-8 i zwraca ona przechowywana w obiekcie typu `u8string`.

```cpp
string u8string() const;
```

## <a name="value_type"></a> path::value_type

Typ opisuje `path` elementy faworytem przez system operacyjny hosta.

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume Posix
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="wstring"></a> path::wstring

Konwertuje sekwencję przechowywane w `mypath` faworytem przez system hosta do kodowania **wchar_t** sekwencji i zwraca ona przechowywana w obiekcie typu `wstring`.

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
