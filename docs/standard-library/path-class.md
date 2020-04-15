---
title: path — klasa
ms.date: 09/27/2018
f1_keywords:
- filesystem/std::experimental::filesystem::path
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
ms.openlocfilehash: 669dfd2c8cd8576ebfb6684bab7cf63cdd51babc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372109"
---
# <a name="path-class"></a>path — klasa

Klasa **path** przechowuje obiekt `string_type`typu `myname` , wywoływany tutaj na potrzeby ekspozycji, nadaje się do użycia jako nazwa ścieżki. `string_type`jest synonimem `basic_string<value_type>`, `value_type` gdzie jest synonimem **wchar_t** w systemie Windows lub **char** na POSIX.

Aby uzyskać więcej informacji i przykłady kodu, zobacz [Nawigacja po systemie plików (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Składnia

```cpp
class path;
```

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Ścieżka](#path)|Konstruuje `path`plik .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[const_iterator](#const_iterator)|Synonimem . `iterator`|
|[Sterująca](#iterator)|Dwukierunkowy stały iterator, który `path` wyznacza `myname`składniki .|
|[string_type](#string_type)|Typ jest synonimem `basic_string<value_type>`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Dołączyć](#append)|Dołącza określoną sekwencję `mypath`do , konwertowane i wstawianie preferred_separator w razie potrzeby.|
|[Przypisać](#assign)|Zastępuje `mypath` określoną sekwencją, konwertowana w razie potrzeby.|
|[Rozpocząć](#begin)|Zwraca `path::iterator` wyznaczający pierwszy element ścieżki w nazwach ścieżki, jeśli jest obecny.|
|[c_str](#c_str)|Zwraca wskaźnik do pierwszego `mypath`znaku w pliku .|
|[Wyczyść](#clear)|Wykonuje `mypath.clear()`.|
|[Porównać](#compare)|Zwraca wartości porównania.|
|[Concat](#compare)|Dołącza określoną sekwencję `mypath`do , konwertowane (ale nie wstawianie separatora) w razie potrzeby.|
|[Pusty](#empty)|Zwraca wartość `mypath.empty()`.|
|[Końcu](#end)|Zwraca iterator końca sekwencji typu `iterator`.|
|[Rozszerzenie](#extension)|Zwraca sufiks `filename()`.|
|[Pod nazwą](#filename)|Zwraca składnik katalogu głównego myname, `empty() path() : *--end()`w szczególności . Komponent może być pusty.|
|[generic_string](#generic_string)|Zwraca `this->string<Elem, Traits, Alloc>(al)` z (w systemie Windows) dowolnym ukośnikiem odwrotnym przekonwertowanym na ukośnik do przodu.|
|[generic_u16string](#generic_u16string)|Zwraca `u16string()` z (w systemie Windows) dowolnym ukośnikiem odwrotnym przekonwertowanym na ukośnik do przodu.|
|[generic_u32string](#generic_u32string)|Zwraca `u32string()` z (w systemie Windows) dowolnym ukośnikiem odwrotnym przekonwertowanym na ukośnik do przodu.|
|[generic_u8string](#generic_u8string)|Zwraca `u8string()` z (w systemie Windows) dowolnym ukośnikiem odwrotnym przekonwertowanym na ukośnik do przodu.|
|[generic_wstring](#generic_wstring)|Zwraca `wstring()` z (w systemie Windows) dowolnym ukośnikiem odwrotnym przekonwertowanym na ukośnik do przodu.|
|[has_extension](#has_extension)|Zwraca wartość `!extension().empty()`.|
|[has_filename](#has_filename)|Zwraca wartość `!filename().empty()`.|
|[has_parent_path](#has_parent_path)|Zwraca wartość `!parent_path().empty()`.|
|[has_relative_path](#has_relative_path)|Zwraca wartość `!relative_path().empty()`.|
|[has_root_directory](#has_root_directory)|Zwraca wartość `!root_directory().empty()`.|
|[has_root_name](#has_root_name)|Zwraca wartość `!root_name().empty()`.|
|[has_root_path](#has_root_path)|Zwraca wartość `!root_path().empty()`.|
|[has_stem](#has_stem)|Zwraca wartość `!stem().empty()`.|
|[is_absolute](#is_absolute)|W systemie Windows `has_root_name() && has_root_directory()`funkcja zwraca . W przypadku POSIX `has_root_directory()`funkcja zwraca wartość .|
|[is_relative](#is_relative)|Zwraca wartość `!is_absolute()`.|
|[make_preferred](#make_preferred)|Konwertuje każdy separator na preferred_separator w razie potrzeby.|
|[Macierzystego](#native)|Zwraca wartość `myname`.|
|[parent_path](#parent_path)|Zwraca składnik ścieżki `myname`nadrzędnej .|
|[preferred_separator](#preferred_separator)|Obiekt stały daje preferowany znak do oddzielania składników ścieżki, w zależności od systemu operacyjnego hosta. |
|[relative_path](#relative_path)|Zwraca składnik ścieżki `myname`względnej . |
|[remove_filename](#remove_filename)|Usuwa nazwę pliku.|
|[replace_extension](#replace_extension)|Zastępuje rozszerzenie programu `myname`. |
|[replace_filename](#replace_filename)|RZamie nazwę pliku.|
|[root_directory](#root_directory)|Zwraca składnik katalogu głównego `myname`programu . |
|[root_name](#root_name)|Zwraca składnik nazwy `myname`głównej programu . |
|[root_path](#root_path)|Zwraca składnik ścieżki `myname`głównej programu .|
|[Macierzystych](#stem)|Zwraca `stem` składnik `myname`.|
|[Ciąg](#string)|Konwertuje sekwencję `mypath`przechowywaną w pliku .|
|[Wymiany](#swap)|Wykonuje `swap(mypath, right.mypath)`.|
|[u16string](#u16string)|Konwertuje sekwencję `mypath` przechowywaną na UTF-16 i zwraca `u16string`ją przechowywaną w obiekcie typu .|
|[u32string](#u32string)|Konwertuje sekwencję `mypath` przechowywaną na UTF-32 i zwraca `u32string`ją przechowywaną w obiekcie typu .|
|[u8string](#u8string)|Konwertuje sekwencję `mypath` przechowywaną na UTF-8 i zwraca `u8string`ją przechowywaną w obiekcie typu .|
|[value_type](#value_type)|Typ opisuje elementy ścieżki preferowane przez system operacyjny hosta.|
|[wstręt](#wstring)|Konwertuje sekwencję `mypath` przechowywaną w kodowaniu preferowanym `wchar_t` przez system hosta dla sekwencji i zwraca ją przechowywaną w obiekcie typu `wstring`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_as)|Zastępuje elementy ścieżki kopią innej ścieżki.|
|[operator+=](#op_add)|Różne `concat` wyrażenia.|
|[operator/=](#op_divide)|Różne `append` wyrażenia.|
|[string_type operatora](#op_string)|Zwraca wartość `myname`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> systemu plików

**Obszar nazw:** std::experimental::system plików

## <a name="pathappend"></a><a name="append"></a>ścieżka::dołącz

Dołącza określoną sekwencję `mypath`do , konwertowane i wstawianie w `preferred_separator` razie potrzeby.

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

### <a name="parameters"></a>Parametry

*Źródła*\
Określona sekwencja.

*Pierwszym*\
Początek określonej sekwencji.

*Ostatnio*\
Koniec określonej sekwencji.

## <a name="pathassign"></a><a name="assign"></a>ścieżka::przypisywanie

Zastępuje `mypath` określoną sekwencją, konwertowana w razie potrzeby.

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

### <a name="parameters"></a>Parametry

*Źródła*\
Określona sekwencja.

*Pierwszym*\
Początek określonej sekwencji.

*Ostatnio*\
Koniec określonej sekwencji.

## <a name="pathbegin"></a><a name="begin"></a>ścieżka::begin

Zwraca `path::iterator` wyznaczający pierwszy element ścieżki w nazwach ścieżki, jeśli jest obecny.

```cpp
iterator begin() const;
```

## <a name="pathc_str"></a><a name="c_str"></a>ścieżka::c_str

Zwraca wskaźnik do pierwszego `mypath`znaku w pliku .

```cpp
const value_type& *c_str() const noexcept;
```

## <a name="pathclear"></a><a name="clear"></a>ścieżka::wyczyść

Wykonuje `mypath.clear()`.

```cpp
void clear() noexcept;
```

## <a name="pathcompare"></a><a name="compare"></a>ścieżka::porównaj

Zwraca pierwszą `mypath.compare(pval.native())`funkcję . Druga funkcja `mypath.compare(str)`zwraca . Trzecia funkcja `mypath.compare(ptr)`zwraca .

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>Parametry

*Pval*\
Ścieżka do porównania.

*Str*\
Ciąg do porównania.

*Ptr*\
Wskaźnik do porównania.

## <a name="pathconcat"></a><a name="concat"></a>ścieżka::concat

Dołącza określoną sekwencję `mypath`do , konwertowane (ale nie wstawianie separatora) w razie potrzeby.

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

### <a name="parameters"></a>Parametry

*Źródła*\
Określona sekwencja.

*Pierwszym*\
Początek określonej sekwencji.

*Ostatnio*\
Koniec określonej sekwencji.

## <a name="pathconst_iterator"></a><a name="const_iterator"></a>ścieżka::const_iterator

Synonimem . `iterator`

```cpp
typedef iterator const_iterator;
```

## <a name="pathempty"></a><a name="empty"></a>ścieżka::empty

Zwraca wartość `mypath.empty()`.

```cpp
bool empty() const noexcept;
```

## <a name="pathend"></a><a name="end"></a>ścieżka::end

Zwraca iterator końca sekwencji typu `iterator`.

```cpp
iterator end() const;
```

## <a name="pathextension"></a><a name="extension"></a>ścieżka::rozszerzenie

Zwraca sufiks `filename()`.

```cpp
path extension() const;
```

### <a name="remarks"></a>Uwagi

Zwraca sufiks `filename() X` w taki sposób, że:

Jeśli `X == path(".") || X == path("..")` lub `X` jeśli nie zawiera kropki, sufiks jest pusty.

W przeciwnym razie sufiks zaczyna się od (i zawiera) kropkę po prawej stronie.

## <a name="pathfilename"></a><a name="filename"></a>ścieżka::nazwa pliku

Zwraca składnik katalogu głównego myname, `empty() path() : *--end()`w szczególności . Komponent może być pusty.

```cpp
path filename() const;
```

## <a name="pathgeneric_string"></a><a name="generic_string"></a>ścieżka::generic_string

Zwraca `this->string<Elem, Traits, Alloc>(al)` z (w systemie Windows) dowolnym ukośnikiem odwrotnym przekonwertowanym na ukośnik do przodu.

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

## <a name="pathgeneric_u16string"></a><a name="generic_u16string"></a>ścieżka::generic_u16string

Zwraca `u16string()` z (w systemie Windows) dowolnym ukośnikiem odwrotnym przekonwertowanym na ukośnik do przodu.

```cpp
u16string generic_u16string() const;
```

## <a name="pathgeneric_u32string"></a><a name="generic_u32string"></a>ścieżka::generic_u32string

Zwraca `u32string()` z (w systemie Windows) dowolnym ukośnikiem odwrotnym przekonwertowanym na ukośnik do przodu.

```cpp
u32string generic_u32string() const;
```

## <a name="pathgeneric_u8string"></a><a name="generic_u8string"></a>ścieżka::generic_u8string

Zwraca `u8string()` z (w systemie Windows) dowolnym ukośnikiem odwrotnym przekonwertowanym na ukośnik do przodu.

```cpp
string generic_u8string() const;
```

## <a name="pathgeneric_wstring"></a><a name="generic_wstring"></a>ścieżka::generic_wstring

Zwraca `wstring()` z (w systemie Windows) dowolnym ukośnikiem odwrotnym przekonwertowanym na ukośnik do przodu.

```cpp
wstring generic_wstring() const;
```

## <a name="pathhas_extension"></a><a name="has_extension"></a>ścieżka::has_extension

Zwraca wartość `!extension().empty()`.

```cpp
bool has_extension() const;
```

## <a name="pathhas_filename"></a><a name="has_filename"></a>ścieżka::has_filename

Zwraca wartość `!filename().empty()`.

```cpp
bool has_filename() const;
```

## <a name="pathhas_parent_path"></a><a name="has_parent_path"></a>ścieżka::has_parent_path

Zwraca wartość `!parent_path().empty()`.

```cpp
bool has_parent_path() const;
```

## <a name="pathhas_relative_path"></a><a name="has_relative_path"></a>ścieżka::has_relative_path

Zwraca wartość `!relative_path().empty()`.

```cpp
bool has_relative_path() const;
```

## <a name="pathhas_root_directory"></a><a name="has_root_directory"></a>ścieżka::has_root_directory

Zwraca wartość `!root_directory().empty()`.

```cpp
bool has_root_directory() const;
```

## <a name="pathhas_root_name"></a><a name="has_root_name"></a>ścieżka::has_root_name

Zwraca wartość `!root_name().empty()`.

```cpp
bool has_root_name() const;
```

## <a name="pathhas_root_path"></a><a name="has_root_path"></a>ścieżka::has_root_path

Zwraca wartość `!root_path().empty()`.

```cpp
bool has_root_path() const;
```

## <a name="pathhas_stem"></a><a name="has_stem"></a>ścieżka::has_stem

Zwraca wartość `!stem().empty()`.

```cpp
bool has_stem() const;
```

## <a name="pathis_absolute"></a><a name="is_absolute"></a>ścieżka::is_absolute

W systemie Windows `has_root_name() && has_root_directory()`funkcja zwraca . W przypadku POSIX `has_root_directory()`funkcja zwraca wartość .

```cpp
bool is_absolute() const;
```

## <a name="pathis_relative"></a><a name="is_relative"></a>ścieżka::is_relative

Zwraca wartość `!is_absolute()`.

```cpp
bool is_relative() const;
```

## <a name="pathiterator"></a><a name="iterator"></a>ścieżka::iterator

Dwukierunkowy stały iterator, który wyznacza składniki `myname`ścieżki .

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

Klasa opisuje dwukierunkowy iterator stałej, `path` `myname` który wyznacza składniki w sekwencji:

1. nazwę główną, jeśli jest obecna

1. katalogu głównego, jeśli jest obecny

1. pozostałe elementy katalogu nadrzędnego `path`, jeśli są obecne, kończące się na nazwę pliku, jeśli są obecne

Dla `pval` obiektu typu: `path`

1. `path::iterator X = pval.begin()`wyznacza pierwszy `path` element w nazwach ścieżki, jeśli jest obecny.

1. `X == pval.end()`jest prawdą, gdy `X` punkty tuż za końcem sekwencji składników.

1. `*X`zwraca ciąg odpowiadający bieżącemu składnikowi

1. `++X`wyznacza następny komponent w sekwencji, jeśli jest obecny.

1. `--X`wyznacza poprzedni komponent w sekwencji, jeśli jest obecny.

1. Zmiana `myname` unieważnia wszystkie iteratory wyznaczające `myname`elementy w programie .

## <a name="pathmake_preferred"></a><a name="make_preferred"></a>ścieżka::make_preferred

Konwertuje każdy separator na w `preferred_separator` razie potrzeby.

```cpp
path& make_preferred();
```

## <a name="pathnative"></a><a name="native"></a>ścieżka::natywna

Zwraca wartość `myname`.

```cpp
const string_type& native() const noexcept;
```

## <a name="pathoperator"></a><a name="op_as"></a>ścieżka::operator=

Zastępuje elementy ścieżki kopią innej ścieżki.

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

### <a name="parameters"></a>Parametry

*Prawo*\
[Ścieżka](../standard-library/path-class.md) kopiowana do `path`pliku .

*Źródła*\
Ścieżka źródłowsza.

### <a name="remarks"></a>Uwagi

Pierwszy operator elementu `right.myname` członkowskiego `myname`kopiuje do . Drugi operator elementu `right.myname` `myname`członkowskiego przechodzi do . Trzeci operator elementu członkowskiego zachowuje `*this = path(source)`się tak samo jak .

## <a name="pathoperator"></a><a name="op_add"></a>ścieżka::operator+=

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

*Prawo*\
Dodana ścieżka.

*Str*\
Dodany ciąg.

*Ptr*\
Dodany wskaźnik.

*Elem*\
Dodane `value_type` lub `Elem`.

*Źródła*\
Dodane źródło.

### <a name="remarks"></a>Uwagi

Funkcje elementu członkowskiego zachowują się tak samo jak następujące odpowiednie wyrażenia:

1. `concat(right);`

1. `concat(path(str));`

1. `concat(ptr);`

1. `concat(string_type(1, elem));`

1. `concat(source);`

1. `concat(path(basic_string<Elem>(1, elem)));`

## <a name="pathoperator"></a><a name="op_divide"></a>ścieżka::operator/=

Różne `append` wyrażenia.

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Dodana ścieżka.

*Źródła*\
Dodane źródło.

### <a name="remarks"></a>Uwagi

Funkcje elementu członkowskiego zachowują się tak samo jak następujące odpowiednie wyrażenia:

1. `append(right);`

1. `append(source);`

## <a name="pathoperator-string_type"></a><a name="op_string"></a>ścieżka::operator string_type

Zwraca wartość `myname`.

```cpp
operator string_type() const;
```

## <a name="pathparent_path"></a><a name="parent_path"></a>ścieżka::parent_path

Zwraca składnik ścieżki `myname`nadrzędnej .

```cpp
path parent_path() const;
```

### <a name="remarks"></a>Uwagi

Zwraca składnik ścieżki `myname`nadrzędnej , w `myname` szczególności prefiks po usunięciu `filename().native()` i wszelkie bezpośrednio poprzedzające separatory katalogów. (Podobnie, jeśli `begin() != end()`jest to łączenie wszystkich elementów `[begin(), --end())` w zakresie przez `operator/=`kolejne zastosowanie .) Komponent może być pusty.

## <a name="pathpath"></a><a name="path"></a>ścieżka::path

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

*Prawo*\
Ścieżka, której skonstruowana ścieżka ma być kopią.

*Źródła*\
Źródłem którego zbudowana ścieżka ma być kopią.

*Loc*\
Określone ustawienia regionalne.

*Pierwszym*\
Położenie pierwszego elementu do skopiowania.

*Ostatnio*\
Położenie ostatniego elementu do skopiowania.

### <a name="remarks"></a>Uwagi

Konstruktory `myname` wszystkie zbudowane na różne sposoby:

Dla `path()` niego `myname()`jest .

Dla `path(const path& right`) `myname(right.myname)`jest .

Dla `path(path&& right)` niego `myname(right.myname)`jest .

Dla `template<class Source> path(const Source& source)` niego `myname(source)`jest .

Dla `template<class Source> path(const Source& source, const locale& loc)` niego `myname(source)`jest, uzyskanie wszelkich potrzebnych aspektów `loc`codecvt z .

Dla `template<class InIt> path(InIt first, InIt last)` niego `myname(first, last)`jest .

Dla `template<class InIt> path(InIt first, InIt last, const locale& loc)` niego `myname(first, last)`jest, uzyskanie wszelkich potrzebnych aspektów `loc`codecvt z .

## <a name="pathpreferred_separator"></a><a name="preferred_separator"></a>ścieżka::preferred_separator

Obiekt stały daje preferowany znak do oddzielania składników ścieżki, w zależności od systemu operacyjnego hosta.

```cpp
#if _WIN32_C_LIB
static constexpr value_type preferred_separator == L'\\';
#else // assume POSIX
static constexpr value_type preferred_separator == '/';
#endif // filesystem model now defined
```

### <a name="remarks"></a>Uwagi

Należy zauważyć, że w większości kontekstów systemu Windows używanie L'/' w jego miejsce jest równie dopuszczalne w większości kontekstów systemu Windows.

## <a name="pathrelative_path"></a><a name="relative_path"></a>ścieżka::relative_path

Zwraca składnik ścieżki `myname`względnej .

```cpp
path relative_path() const;
```

### <a name="remarks"></a>Uwagi

Zwraca względny składnik `myname`ścieżki , w szczególności `myname` sufiks po usunięciu `root_path().native()` i wszelkie bezpośrednio kolejne nadmiarowe separatory katalogów. Komponent może być pusty.

## <a name="pathremove_filename"></a><a name="remove_filename"></a>ścieżka::remove_filename

Usuwa nazwę pliku.

```cpp
path& remove_filename();
```

## <a name="pathreplace_extension"></a><a name="replace_extension"></a>ścieżka::replace_extension

Zastępuje rozszerzenie programu `myname`.

```cpp
path& replace_extension(const path& newext = path());
```

### <a name="parameters"></a>Parametry

*newext*\
Nowe rozszerzenie.

### <a name="remarks"></a>Uwagi

Najpierw usuwa `extension().native()` sufiks `myname`z . Następnie, `!newext.empty() && newext[0] != dot` jeśli `dot` `*path(".").c_str()`(gdzie `dot` jest), a `myname`następnie jest dołączany do . Następnie *newext* jest dołączany do `myname`pliku .

## <a name="pathreplace_filename"></a><a name="replace_filename"></a>ścieżka::replace_filename

Zastępuje nazwę pliku.

```cpp
path& replace_filename(const path& pval);
```

### <a name="parameters"></a>Parametry

*Pval*\
Ścieżka nazwy pliku.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wykonuje:

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="pathroot_directory"></a><a name="root_directory"></a>ścieżka::root_directory

Zwraca składnik katalogu głównego `myname`programu .

```cpp
path root_directory() const;
```

### <a name="remarks"></a>Uwagi

Komponent może być pusty.

## <a name="pathroot_name"></a><a name="root_name"></a>ścieżka::root_name

Zwraca składnik nazwy `myname`głównej programu .

```cpp
path root_name() const;
```

### <a name="remarks"></a>Uwagi

Komponent może być pusty.

## <a name="pathroot_path"></a><a name="root_path"></a>ścieżka::root_path

Zwraca składnik ścieżki `myname`głównej programu .

```cpp
path root_path() const;
```

### <a name="remarks"></a>Uwagi

Zwraca składnik ścieżki `myname`głównej , `root_name()`  /  `root_directory`w szczególności . Komponent może być pusty.

## <a name="pathstem"></a><a name="stem"></a>ścieżka::łodyga

Zwraca `stem` składnik `myname`.

```cpp
path stem() const;
```

### <a name="remarks"></a>Uwagi

Zwraca `stem` składnik `myname`, w `filename().native()` szczególności z `extension().native()` usuniętymi końcami. Komponent może być pusty.

## <a name="pathstring"></a><a name="string"></a>ścieżka::ciąg

Konwertuje sekwencję `mypath`przechowywaną w pliku .

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego (szablon) konwertuje sekwencję przechowywaną w `mypath` taki sam sposób, jak:

1. `string()`For`string<char, Traits, Alloc>()`

1. `wstring()`For`string<wchar_t, Traits, Alloc>()`

1. `u16string()`For`string<char16_t, Traits, Alloc>()`

1. `u32string()`For`string<char32_t, Traits, Alloc>()`

Funkcja drugiego elementu członkowskiego konwertuje sekwencję przechowywaną w `mypath` kodowaniu preferowanym przez system hosta dla sekwencji **znaków** i zwraca ją przechowywaną w obiekcie typu `string`.

## <a name="pathstring_type"></a><a name="string_type"></a>ścieżka::string_type

Typ jest synonimem `basic_string<value_type>`.

```cpp
typedef basic_string<value_type> string_type;
```

## <a name="pathswap"></a><a name="swap"></a>ścieżka::swap

Wykonuje `swap(mypath, right.mypath)`.

```cpp
void swap(path& right) noexcept;
```

## <a name="pathu16string"></a><a name="u16string"></a>ścieżka::u16string

Konwertuje sekwencję `mypath` przechowywaną na UTF-16 i zwraca `u16string`ją przechowywaną w obiekcie typu .

```cpp
u16string u16string() const;
```

## <a name="pathu32string"></a><a name="u32string"></a>ścieżka::u32string

Konwertuje sekwencję `mypath` przechowywaną na UTF-32 i zwraca `u32string`ją przechowywaną w obiekcie typu .

```cpp
u32string u32string() const;
```

## <a name="pathu8string"></a><a name="u8string"></a>ścieżka::u8string

Konwertuje sekwencję `mypath` przechowywaną na UTF-8 i zwraca `u8string`ją przechowywaną w obiekcie typu .

```cpp
string u8string() const;
```

## <a name="pathvalue_type"></a><a name="value_type"></a>ścieżka::value_type

Typ opisuje `path` elementy preferowane przez system operacyjny hosta.

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume POSIX
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="pathwstring"></a><a name="wstring"></a>ścieżka::wstring

Konwertuje sekwencję `mypath` przechowywaną w kodowaniu preferowanym przez system hosta dla sekwencji **wchar_t** `wstring`i zwraca ją przechowywaną w obiekcie typu .

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>Zobacz też

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
