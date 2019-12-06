---
title: path — klasa
ms.date: 09/27/2018
f1_keywords:
- filesystem/std::experimental::filesystem::path
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
ms.openlocfilehash: 0bc26bb04464c52ed08d46e6a12c12cae6909d6f
ms.sourcegitcommit: 6ddfb8be5e5923a4d90a2c0f93f76a27ce7ac299
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/06/2019
ms.locfileid: "74898794"
---
# <a name="path-class"></a>path — klasa

Klasa **Path** przechowuje obiekt typu `string_type`, o nazwie `myname` w tym miejscu na potrzeby specyfikacji, odpowiednie do użycia jako nazwa ścieżki. `string_type` jest synonimem dla `basic_string<value_type>`, gdzie `value_type` jest synonimem dla **wchar_t** w systemie Windows lub **char** na POSIX.

Aby uzyskać więcej informacji i przykłady kodu, zobacz [Nawigacja systemu plików (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Składnia

```cpp
class path;
```

### <a name="constructors"></a>Konstruktorzy

|Konstruktor|Opis|
|-|-|
|[Ścieżka](#path)|Konstruuje `path`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[const_iterator](#const_iterator)|Synonim dla `iterator`.|
|[iterator](#iterator)|Iterator stałej dwukierunkowej, który wyznacza składniki `path` `myname`.|
|[string_type](#string_type)|Typ jest synonimem dla `basic_string<value_type>`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[łączono](#append)|Dołącza określoną sekwencję do `mypath`, przekonwertowane i wstawiania preferred_separator zgodnie z wymaganiami.|
|[ponownie](#assign)|Zastępuje `mypath` z określoną sekwencją przekonwertowaną zgodnie z wymaganiami.|
|[begin](#begin)|Zwraca `path::iterator` wyznaczania pierwszego elementu ścieżki w nazwie ścieżki, jeśli istnieje.|
|[c_str](#c_str)|Zwraca wskaźnik do pierwszego znaku w `mypath`.|
|[Wyczyść](#clear)|Wykonuje `mypath.clear()`.|
|[porównaniu](#compare)|Zwraca wartości porównania.|
|[concat](#compare)|Dołącza określoną sekwencję do `mypath`, przekonwertowane (ale nie wstawiając separatora) zgodnie z wymaganiami.|
|[empty](#empty)|Zwraca wartość `mypath.empty()`.|
|[punktów](#end)|Zwraca iterator końca sekwencji typu `iterator`.|
|[rozszerzenia](#extension)|Zwraca sufiks `filename()`.|
|[filename](#filename)|Zwraca składnik katalogu głównego elementu ServiceName, w `empty() path() : *--end()`. Składnik może być pusty.|
|[generic_string](#generic_string)|Zwraca `this->string<Elem, Traits, Alloc>(al)` z (w obszarze systemu Windows) wszystkie ukośniki odwrotne konwertowane na ukośnik.|
|[generic_u16string](#generic_u16string)|Zwraca `u16string()` z (w obszarze systemu Windows) wszystkie ukośniki odwrotne konwertowane na ukośnik.|
|[generic_u32string](#generic_u32string)|Zwraca `u32string()` z (w obszarze systemu Windows) wszystkie ukośniki odwrotne konwertowane na ukośnik.|
|[generic_u8string](#generic_u8string)|Zwraca `u8string()` z (w obszarze systemu Windows) wszystkie ukośniki odwrotne konwertowane na ukośnik.|
|[generic_wstring](#generic_wstring)|Zwraca `wstring()` z (w obszarze systemu Windows) wszystkie ukośniki odwrotne konwertowane na ukośnik.|
|[has_extension](#has_extension)|Zwraca wartość `!extension().empty()`.|
|[has_filename](#has_filename)|Zwraca wartość `!filename().empty()`.|
|[has_parent_path](#has_parent_path)|Zwraca wartość `!parent_path().empty()`.|
|[has_relative_path](#has_relative_path)|Zwraca wartość `!relative_path().empty()`.|
|[has_root_directory](#has_root_directory)|Zwraca wartość `!root_directory().empty()`.|
|[has_root_name](#has_root_name)|Zwraca wartość `!root_name().empty()`.|
|[has_root_path](#has_root_path)|Zwraca wartość `!root_path().empty()`.|
|[has_stem](#has_stem)|Zwraca wartość `!stem().empty()`.|
|[is_absolute](#is_absolute)|Dla systemu Windows funkcja zwraca `has_root_name() && has_root_directory()`. W przypadku POSIX funkcja zwraca `has_root_directory()`.|
|[is_relative](#is_relative)|Zwraca wartość `!is_absolute()`.|
|[make_preferred](#make_preferred)|Konwertuje każdy separator na preferred_separator w razie potrzeby.|
|[trybu](#native)|Zwraca wartość `myname`.|
|[parent_path](#parent_path)|Zwraca składnik ścieżki nadrzędnej `myname`.|
|[preferred_separator](#preferred_separator)|Obiekt stała daje preferowany znak do oddzielania składników ścieżki, w zależności od systemu operacyjnego hosta. |
|[relative_path](#relative_path)|Zwraca składnik ścieżki względnej `myname`. |
|[remove_filename](#remove_filename)|Usuwa nazwę pliku.|
|[replace_extension](#replace_extension)|Zastępuje rozszerzenie `myname`. |
|[replace_filename](#replace_filename)|RReplaces nazwę pliku.|
|[root_directory](#root_directory)|Zwraca składnik katalogu głównego `myname`. |
|[root_name](#root_name)|Zwraca składnik nazwy głównej `myname`. |
|[root_path](#root_path)|Zwraca składnik ścieżki głównej `myname`.|
|[stem](#stem)|Zwraca składnik `stem` `myname`.|
|[string](#string)|Konwertuje sekwencję przechowywaną w `mypath`.|
|[swap](#swap)|Wykonuje `swap(mypath, right.mypath)`.|
|[u16string](#u16string)|Konwertuje sekwencję przechowywaną w `mypath` do UTF-16 i zwraca ją przechowywaną w obiekcie typu `u16string`.|
|[u32string](#u32string)|Konwertuje sekwencję przechowywaną w `mypath` do UTF-32 i zwraca ją przechowywaną w obiekcie typu `u32string`.|
|[u8string](#u8string)|Konwertuje sekwencję przechowywaną w `mypath` na UTF-8 i zwraca ją przechowywaną w obiekcie typu `u8string`.|
|[value_type](#value_type)|Typ opisuje elementy ścieżki preferowane przez system operacyjny hosta.|
|[wstring](#wstring)|Konwertuje sekwencję przechowywaną w `mypath` na kodowanie preferowane przez system hosta dla sekwencji `wchar_t` i zwraca ją przechowywaną w obiekcie typu `wstring`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_as)|Zastępuje elementy ścieżki kopią innej ścieżki.|
|[operator+=](#op_add)|Różne wyrażenia `concat`.|
|[operator/=](#op_divide)|Różne wyrażenia `append`.|
|[string_type operatora](#op_string)|Zwraca wartość `myname`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> systemu plików

**Przestrzeń nazw:** std:: eksperymentalne:: filesystem

## <a name="append"></a>Path:: Append

Dołącza określoną sekwencję do `mypath`, przekonwertowane i wstawiania `preferred_separator` zgodnie z wymaganiami.

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

### <a name="parameters"></a>Parametry

\ *źródłowa*
Określona sekwencja.

*pierwszy*\
Początek określonej sekwencji.

*ostatni*\
Koniec określonej sekwencji.

## <a name="assign"></a>ścieżka:: Assign

Zastępuje `mypath` z określoną sekwencją przekonwertowaną zgodnie z wymaganiami.

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

### <a name="parameters"></a>Parametry

\ *źródłowa*
Określona sekwencja.

*pierwszy*\
Początek określonej sekwencji.

*ostatni*\
Koniec określonej sekwencji.

## <a name="begin"></a>ścieżka:: BEGIN

Zwraca `path::iterator` wyznaczania pierwszego elementu ścieżki w nazwie ścieżki, jeśli istnieje.

```cpp
iterator begin() const;
```

## <a name="c_str"></a>ścieżka:: c_str

Zwraca wskaźnik do pierwszego znaku w `mypath`.

```cpp
const value_type& *c_str() const noexcept;
```

## <a name="clear"></a>ścieżka:: Clear

Wykonuje `mypath.clear()`.

```cpp
void clear() noexcept;
```

## <a name="compare"></a>Path:: Compare

Pierwsza funkcja zwraca `mypath.compare(pval.native())`. Druga funkcja zwraca `mypath.compare(str)`. Trzecia funkcja zwraca `mypath.compare(ptr)`.

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>Parametry

*pval*\
Ścieżka do porównania.

*str*\
Ciąg do porównania.

\ *PTR*
Wskaźnik do porównania.

## <a name="concat"></a>ścieżka:: Concat

Dołącza określoną sekwencję do `mypath`, przekonwertowane (ale nie wstawiając separatora) zgodnie z wymaganiami.

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

### <a name="parameters"></a>Parametry

\ *źródłowa*
Określona sekwencja.

*pierwszy*\
Początek określonej sekwencji.

*ostatni*\
Koniec określonej sekwencji.

## <a name="const_iterator"></a>ścieżka:: const_iterator

Synonim dla `iterator`.

```cpp
typedef iterator const_iterator;
```

## <a name="empty"></a>Path:: Empty

Zwraca wartość `mypath.empty()`.

```cpp
bool empty() const noexcept;
```

## <a name="end"></a>Path:: end

Zwraca iterator końca sekwencji typu `iterator`.

```cpp
iterator end() const;
```

## <a name="extension"></a>Path:: Extension

Zwraca sufiks `filename()`.

```cpp
path extension() const;
```

### <a name="remarks"></a>Uwagi

Zwraca sufiks `filename() X` w taki sposób, że:

Jeśli `X == path(".") || X == path("..")` lub jeśli `X` nie zawiera kropki, sufiks jest pusty.

W przeciwnym razie sufiks zaczyna się od (i zawiera) z prawej kropką.

## <a name="filename"></a>Path:: filename

Zwraca składnik katalogu głównego elementu ServiceName, w `empty() path() : *--end()`. Składnik może być pusty.

```cpp
path filename() const;
```

## <a name="generic_string"></a>ścieżka:: generic_string

Zwraca `this->string<Elem, Traits, Alloc>(al)` z (w obszarze systemu Windows) wszystkie ukośniki odwrotne konwertowane na ukośnik.

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

## <a name="generic_u16string"></a>ścieżka:: generic_u16string

Zwraca `u16string()` z (w obszarze systemu Windows) wszystkie ukośniki odwrotne konwertowane na ukośnik.

```cpp
u16string generic_u16string() const;
```

## <a name="generic_u32string"></a>ścieżka:: generic_u32string

Zwraca `u32string()` z (w obszarze systemu Windows) wszystkie ukośniki odwrotne konwertowane na ukośnik.

```cpp
u32string generic_u32string() const;
```

## <a name="generic_u8string"></a>ścieżka:: generic_u8string

Zwraca `u8string()` z (w obszarze systemu Windows) wszystkie ukośniki odwrotne konwertowane na ukośnik.

```cpp
string generic_u8string() const;
```

## <a name="generic_wstring"></a>ścieżka:: generic_wstring

Zwraca `wstring()` z (w obszarze systemu Windows) wszystkie ukośniki odwrotne konwertowane na ukośnik.

```cpp
wstring generic_wstring() const;
```

## <a name="has_extension"></a>ścieżka:: has_extension

Zwraca wartość `!extension().empty()`.

```cpp
bool has_extension() const;
```

## <a name="has_filename"></a>ścieżka:: has_filename

Zwraca wartość `!filename().empty()`.

```cpp
bool has_filename() const;
```

## <a name="has_parent_path"></a>ścieżka:: has_parent_path

Zwraca wartość `!parent_path().empty()`.

```cpp
bool has_parent_path() const;
```

## <a name="has_relative_path"></a>ścieżka:: has_relative_path

Zwraca wartość `!relative_path().empty()`.

```cpp
bool has_relative_path() const;
```

## <a name="has_root_directory"></a>ścieżka:: has_root_directory

Zwraca wartość `!root_directory().empty()`.

```cpp
bool has_root_directory() const;
```

## <a name="has_root_name"></a>ścieżka:: has_root_name

Zwraca wartość `!root_name().empty()`.

```cpp
bool has_root_name() const;
```

## <a name="has_root_path"></a>ścieżka:: has_root_path

Zwraca wartość `!root_path().empty()`.

```cpp
bool has_root_path() const;
```

## <a name="has_stem"></a>ścieżka:: has_stem

Zwraca wartość `!stem().empty()`.

```cpp
bool has_stem() const;
```

## <a name="is_absolute"></a>ścieżka:: is_absolute

Dla systemu Windows funkcja zwraca `has_root_name() && has_root_directory()`. W przypadku POSIX funkcja zwraca `has_root_directory()`.

```cpp
bool is_absolute() const;
```

## <a name="is_relative"></a>ścieżka:: is_relative

Zwraca wartość `!is_absolute()`.

```cpp
bool is_relative() const;
```

## <a name="iterator"></a>Path:: iterator

Jednokierunkowy iterator, który wyznacza składniki ścieżki `myname`.

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

Klasa opisuje jednokierunkowy iterator, który wyznacza `path` składniki `myname` w sekwencji:

1. Nazwa główna, jeśli istnieje

1. Katalog główny, jeśli jest obecny

1. pozostałe elementy katalogu nadrzędnego `path`(jeśli istnieją) kończące się na nazwą pliku, jeśli jest obecny

Dla `pval` obiektu typu `path`:

1. `path::iterator X = pval.begin()` wyznacza pierwszy `path` elementu w nazwie ścieżki, jeśli jest obecny.

1. `X == pval.end()` ma wartość true, gdy `X` punkty po zakończeniu sekwencji składników.

3. `*X` zwraca ciąg, który pasuje do bieżącego składnika

1. `++X` wyznacza Następny składnik w sekwencji, jeśli jest obecny.

1. `--X` wyznacza poprzedni składnik w sekwencji, jeśli jest obecny.

1. Zmiana `myname` unieważnia wszystkie Iteratory wyznaczające elementy w `myname`.

## <a name="make_preferred"></a>ścieżka:: make_preferred

Konwertuje każdy separator na `preferred_separator` w razie potrzeby.

```cpp
path& make_preferred();
```

## <a name="native"></a>ścieżka:: Native

Zwraca wartość `myname`.

```cpp
const string_type& native() const noexcept;
```

## <a name="op_as"></a>Path:: operator =

Zastępuje elementy ścieżki kopią innej ścieżki.

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

### <a name="parameters"></a>Parametry

*prawa*\
[Ścieżka](../standard-library/path-class.md) jest kopiowana do `path`.

\ *źródłowa*
Ścieżka źródłowa.

### <a name="remarks"></a>Uwagi

Pierwszy operator członkowski kopiuje `right.myname` do `myname`. Drugi operator elementu członkowskiego przenosi `right.myname` do `myname`. Trzeci operator członkowski zachowuje się tak samo jak `*this = path(source)`.

## <a name="op_add"></a>Path:: operator + =

Różne wyrażenia `concat`.

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

*prawa*\
Dodana ścieżka.

*str*\
Dodany ciąg.

\ *PTR*
Dodany wskaźnik.

*elem*\
Dodano `value_type` lub `Elem`.

\ *źródłowa*
Dodane źródło.

### <a name="remarks"></a>Uwagi

Funkcje składowe zachowują się tak samo jak następujące odpowiednie wyrażenia:

1. `concat(right);`

1. `concat(path(str));`

1. `concat(ptr);`

1. `concat(string_type(1, elem));`

1. `concat(source);`

1. `concat(path(basic_string<Elem>(1, elem)));`

## <a name="op_divide"></a>Path:: operator/=

Różne wyrażenia `append`.

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

### <a name="parameters"></a>Parametry

*prawa*\
Dodana ścieżka.

\ *źródłowa*
Dodane źródło.

### <a name="remarks"></a>Uwagi

Funkcje składowe zachowują się tak samo jak następujące odpowiednie wyrażenia:

1. `append(right);`

1. `append(source);`

## <a name="op_string"></a>Path:: operator string_type

Zwraca wartość `myname`.

```cpp
operator string_type() const;
```

## <a name="parent_path"></a>ścieżka::p arent_path

Zwraca składnik ścieżki nadrzędnej `myname`.

```cpp
path parent_path() const;
```

### <a name="remarks"></a>Uwagi

Zwraca składnik ścieżki nadrzędnej `myname`, w tym prefiks `myname` po usunięciu `filename().native()` i wszelkich bezpośrednio poprzedzających separatory katalogów. (Podobnie, jeśli `begin() != end()`, jest to połączenie wszystkich elementów w zakresie `[begin(), --end())` przez ponowne zastosowanie `operator/=`). Składnik może być pusty.

## <a name="path"></a>ścieżka::p XPath

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

*prawa*\
Ścieżka, dla której skonstruowana ścieżka ma być kopią.

\ *źródłowa*
Źródło, którego skonstruowaną ścieżką jest kopia.

\. *Loc*
Określone ustawienia regionalne.

*pierwszy*\
Pozycja pierwszego elementu, który ma zostać skopiowany.

*ostatni*\
Pozycja ostatniego elementu, który ma zostać skopiowany.

### <a name="remarks"></a>Uwagi

Konstruktory wszystkie `myname` na różne sposoby:

Dla `path()` jest `myname()`.

Dla `path(const path& right`) jest `myname(right.myname)`.

Dla `path(path&& right)` jest `myname(right.myname)`.

Dla `template<class Source> path(const Source& source)` jest `myname(source)`.

Dla `template<class Source> path(const Source& source, const locale& loc)` jest `myname(source)`, uzyskanie wszelkich wymaganych aspektów codecvt z `loc`.

Dla `template<class InIt> path(InIt first, InIt last)` jest `myname(first, last)`.

Dla `template<class InIt> path(InIt first, InIt last, const locale& loc)` jest `myname(first, last)`, uzyskanie wszelkich wymaganych aspektów codecvt z `loc`.

## <a name="preferred_separator"></a>ścieżka::p referred_separator

Obiekt stała daje preferowany znak do oddzielania składników ścieżki, w zależności od systemu operacyjnego hosta.

```cpp
#if _WIN32_C_LIB
static constexpr value_type preferred_separator == L'\\';
#else // assume POSIX
static constexpr value_type preferred_separator == '/';
#endif // filesystem model now defined
```

### <a name="remarks"></a>Uwagi

Należy zauważyć, że jest to równie dozwolone w większości kontekstów w systemie Windows, aby użyć L "/" w tym miejscu.

## <a name="relative_path"></a>ścieżka:: relative_path

Zwraca składnik ścieżki względnej `myname`.

```cpp
path relative_path() const;
```

### <a name="remarks"></a>Uwagi

Zwraca składnik ścieżki względnej `myname`, w odniesieniu do sufiksu `myname` po usunięciu `root_path().native()` i wszelkie bezpośrednio kolejne nadmiarowe separatory katalogów. Składnik może być pusty.

## <a name="remove_filename"></a>ścieżka:: remove_filename

Usuwa nazwę pliku.

```cpp
path& remove_filename();
```

## <a name="replace_extension"></a>ścieżka:: replace_extension

Zastępuje rozszerzenie `myname`.

```cpp
path& replace_extension(const path& newext = path());
```

### <a name="parameters"></a>Parametry

*newext*\
Nowe rozszerzenie.

### <a name="remarks"></a>Uwagi

Najpierw usuwa sufiks `extension().native()` z `myname`. Następnie Jeśli `!newext.empty() && newext[0] != dot` (gdzie `dot` jest `*path(".").c_str()`), `dot` jest dołączany do `myname`. Następnie *newext* jest dołączany do `myname`.

## <a name="replace_filename"></a>ścieżka:: replace_filename

Zastępuje nazwę pliku.

```cpp
path& replace_filename(const path& pval);
```

### <a name="parameters"></a>Parametry

*pval*\
Ścieżka do nazwy pliku.

### <a name="remarks"></a>Uwagi

Funkcja członkowska wykonuje:

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="root_directory"></a>ścieżka:: root_directory

Zwraca składnik katalogu głównego `myname`.

```cpp
path root_directory() const;
```

### <a name="remarks"></a>Uwagi

Składnik może być pusty.

## <a name="root_name"></a>ścieżka:: root_name

Zwraca składnik nazwy głównej `myname`.

```cpp
path root_name() const;
```

### <a name="remarks"></a>Uwagi

Składnik może być pusty.

## <a name="root_path"></a>ścieżka:: root_path

Zwraca składnik ścieżki głównej `myname`.

```cpp
path root_path() const;
```

### <a name="remarks"></a>Uwagi

Zwraca składnik ścieżki głównej `myname`, w `root_name()` / `root_directory`. Składnik może być pusty.

## <a name="stem"></a>ścieżka:: trzon

Zwraca składnik `stem` `myname`.

```cpp
path stem() const;
```

### <a name="remarks"></a>Uwagi

Zwraca `stem` składnik `myname`, w `filename().native()` z usuniętymi `extension().native()` końcowymi. Składnik może być pusty.

## <a name="string"></a>Path:: String

Konwertuje sekwencję przechowywaną w `mypath`.

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska (szablon) konwertuje sekwencję przechowywaną w `mypath` tak samo jak:

1. `string()` Aby uzyskać `string<char, Traits, Alloc>()`

1. `wstring()` Aby uzyskać `string<wchar_t, Traits, Alloc>()`

1. `u16string()` Aby uzyskać `string<char16_t, Traits, Alloc>()`

1. `u32string()` Aby uzyskać `string<char32_t, Traits, Alloc>()`

Druga funkcja członkowska konwertuje sekwencję przechowywaną w `mypath` na kodowanie preferowane przez system hosta dla sekwencji **znaków** i zwraca ją przechowywaną w obiekcie typu `string`.

## <a name="string_type"></a>ścieżka:: string_type

Typ jest synonimem dla `basic_string<value_type>`.

```cpp
typedef basic_string<value_type> string_type;
```

## <a name="swap"></a>ścieżka:: swap

Wykonuje `swap(mypath, right.mypath)`.

```cpp
void swap(path& right) noexcept;
```

## <a name="u16string"></a>ścieżka:: u16string

Konwertuje sekwencję przechowywaną w `mypath` do UTF-16 i zwraca ją przechowywaną w obiekcie typu `u16string`.

```cpp
u16string u16string() const;
```

## <a name="u32string"></a>ścieżka:: u32string

Konwertuje sekwencję przechowywaną w `mypath` do UTF-32 i zwraca ją przechowywaną w obiekcie typu `u32string`.

```cpp
u32string u32string() const;
```

## <a name="u8string"></a>ścieżka:: u8string

Konwertuje sekwencję przechowywaną w `mypath` na UTF-8 i zwraca ją przechowywaną w obiekcie typu `u8string`.

```cpp
string u8string() const;
```

## <a name="value_type"></a>ścieżka:: value_type

Typ opisuje elementy `path` preferowane przez system operacyjny hosta.

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume POSIX
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="wstring"></a>ścieżka:: wstring

Konwertuje sekwencję przechowywaną w `mypath` na kodowanie preferowane przez system hosta dla sekwencji **wchar_t** i zwraca ją przechowywaną w obiekcie typu `wstring`.

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
