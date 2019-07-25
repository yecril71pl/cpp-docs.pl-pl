---
title: path — klasa
ms.date: 09/27/2018
f1_keywords:
- filesystem/std::experimental::filesystem::path
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
ms.openlocfilehash: 10c865aa2bc2431850c69e9dfedbef37414b2cb9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455101"
---
# <a name="path-class"></a>path — klasa

Klasa **Path** przechowuje obiekt typu `string_type`, który jest wywoływany `myname` w tym miejscu do celów specyfikacji, odpowiedni do użycia jako nazwa ścieżki. `string_type`jest synonimem dla `basic_string<value_type>`, gdzie `value_type` jest synonimem dla **wchar_t** w systemie Windows lub **char** na POSIX.

Aby uzyskać więcej informacji i przykłady kodu, zobacz [Nawigacja systemu plików (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Składnia

```cpp
class path;
```

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Ścieżka](#path)|Konstruuje `path`a.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[const_iterator](#const_iterator)|Synonim dla `iterator`.|
|[iterator](#iterator)|Jednokierunkowy iterator, który wyznacza `path` `myname`składniki.|
|[string_type](#string_type)|Typ jest synonimem dla `basic_string<value_type>`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[łączono](#append)|Dołącza określoną sekwencję do `mypath`, przekonwertowane i wstawia preferred_separator w razie potrzeby.|
|[ponownie](#assign)|Zastępuje `mypath` z określoną sekwencją przekonwertowaną zgodnie z wymaganiami.|
|[begin](#begin)|`path::iterator` Zwraca wyznaczanie pierwszego elementu Path w nazwie ścieżki, jeśli jest obecny.|
|[c_str](#c_str)|Zwraca wskaźnik do pierwszego znaku w `mypath`.|
|[Wyczyść](#clear)|Wykonuje `mypath.clear()`.|
|[porównaniu](#compare)|Zwraca wartości porównania.|
|[concat](#compare)|Dołącza określoną sekwencję do `mypath`, przekonwertowane (ale nie wstawia separatora) zgodnie z wymaganiami.|
|[empty](#empty)|Zwraca `mypath.empty()`wartość.|
|[punktów](#end)|Zwraca iterator końca sekwencji typu `iterator`.|
|[rozszerzenia](#extension)|Zwraca sufiks `filename()`.|
|[Nazwa pliku](#filename)|Zwraca składnik katalogu głównego ServiceName, w `empty() path() : *--end()`tym celu. Składnik może być pusty.|
|[generic_string](#generic_string)|Zwraca `this->string<Elem, Traits, Alloc>(al)` z (w obszarze systemu Windows) wszystkie ukośniki odwrotne konwertowane na ukośnik.|
|[generic_u16string](#generic_u16string)|Zwraca `u16string()` z (w obszarze systemu Windows) wszystkie ukośniki odwrotne konwertowane na ukośnik.|
|[generic_u32string](#generic_u32string)|Zwraca `u32string()` z (w obszarze systemu Windows) wszystkie ukośniki odwrotne konwertowane na ukośnik.|
|[generic_u8string](#generic_u8string)|Zwraca `u8string()` z (w obszarze systemu Windows) wszystkie ukośniki odwrotne konwertowane na ukośnik.|
|[generic_wstring](#generic_wstring)|Zwraca `wstring()` z (w obszarze systemu Windows) wszystkie ukośniki odwrotne konwertowane na ukośnik.|
|[has_extension](#has_extension)|Zwraca `!extension().empty()`wartość.|
|[has_filename](#has_filename)|Zwraca `!filename().empty()`wartość.|
|[has_parent_path](#has_parent_path)|Zwraca `!parent_path().empty()`wartość.|
|[has_relative_path](#has_relative_path)|Zwraca `!relative_path().empty()`wartość.|
|[has_root_directory](#has_root_directory)|Zwraca `!root_directory().empty()`wartość.|
|[has_root_name](#has_root_name)|Zwraca `!root_name().empty()`wartość.|
|[has_root_path](#has_root_path)|Zwraca `!root_path().empty()`wartość.|
|[has_stem](#has_stem)|Zwraca `!stem().empty()`wartość.|
|[is_absolute](#is_absolute)|Dla systemu Windows funkcja zwraca wartość `has_root_name() && has_root_directory()`. W przypadku POSIX funkcja zwraca wartość `has_root_directory()`.|
|[is_relative](#is_relative)|Zwraca `!is_absolute()`wartość.|
|[make_preferred](#make_preferred)|Konwertuje każdy separator na preferred_separator w razie potrzeby.|
|[trybu](#native)|Zwraca `myname`wartość.|
|[parent_path](#parent_path)|Zwraca składnik `myname`ścieżki nadrzędnej.|
|[preferred_separator](#preferred_separator)|Obiekt stała daje preferowany znak do oddzielania składników ścieżki, w zależności od systemu operacyjnego hosta. |
|[relative_path](#relative_path)|Zwraca składnik ścieżki względnej elementu `myname`. |
|[remove_filename](#remove_filename)|Usuwa nazwę pliku.|
|[replace_extension](#replace_extension)|Zastępuje rozszerzenie `myname`. |
|[replace_filename](#replace_filename)|RReplaces nazwę pliku.|
|[root_directory](#root_directory)|Zwraca składnik katalogu głównego programu `myname`. |
|[root_name](#root_name)|Zwraca składnik `myname`nazwy głównej. |
|[root_path](#root_path)|Zwraca składnik `myname`ścieżki głównej elementu.|
|[stem](#stem)|`stem` Zwraca`myname`składnik.|
|[string](#string)|Konwertuje sekwencję przechowywaną `mypath`w.|
|[swap](#swap)|Wykonuje `swap(mypath, right.mypath)`.|
|[u16string](#u16string)|Konwertuje sekwencję przechowywaną `mypath` w do UTF-16 i zwraca ją przechowywaną w obiekcie typu `u16string`.|
|[u32string](#u32string)|Konwertuje sekwencję przechowywaną `mypath` w do UTF-32 i zwraca ją przechowywaną w obiekcie typu `u32string`.|
|[u8string](#u8string)|Konwertuje sekwencję przechowywaną `mypath` w do UTF-8 i zwraca ją przechowywaną w obiekcie typu `u8string`.|
|[value_type](#value_type)|Typ opisuje elementy ścieżki preferowane przez system operacyjny hosta.|
|[wstring](#wstring)|Konwertuje sekwencję przechowywaną `mypath` w programie na kodowanie preferowaną przez system hosta `wchar_t` dla sekwencji i zwraca ją przechowywaną w obiekcie typu `wstring`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_as)|Zastępuje elementy ścieżki kopią innej ścieżki.|
|[operator+=](#op_add)|Różne `concat` wyrażenia.|
|[operator/=](#op_divide)|Różne `append` wyrażenia.|
|[string_type operatora](#op_string)|Zwraca `myname`wartość.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> systemu plików

**Przestrzeń nazw:** std:: eksperymentalne:: filesystem

## <a name="append"></a>Path:: Append

Dołącza określoną sekwencję do `mypath`, przekonwertowane i `preferred_separator` wstawia w razie potrzeby.

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

### <a name="parameters"></a>Parametry

*zewnętrz*\
Określona sekwencja.

*pierwszego*\
Początek określonej sekwencji.

*ostatniego*\
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

*zewnętrz*\
Określona sekwencja.

*pierwszego*\
Początek określonej sekwencji.

*ostatniego*\
Koniec określonej sekwencji.

## <a name="begin"></a>ścieżka:: BEGIN

`path::iterator` Zwraca wyznaczanie pierwszego elementu Path w nazwie ścieżki, jeśli jest obecny.

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

Pierwsza funkcja zwraca wartość `mypath.compare(pval.native())`. Druga funkcja zwraca `mypath.compare(str)`. Trzecia funkcja zwraca wartość `mypath.compare(ptr)`.

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

*PTR*\
Wskaźnik do porównania.

## <a name="concat"></a>ścieżka:: Concat

Dołącza określoną sekwencję do `mypath`, przekonwertowane (ale nie wstawia separatora) zgodnie z wymaganiami.

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

### <a name="parameters"></a>Parametry

*zewnętrz*\
Określona sekwencja.

*pierwszego*\
Początek określonej sekwencji.

*ostatniego*\
Koniec określonej sekwencji.

## <a name="const_iterator"></a>ścieżka:: const_iterator

Synonim dla `iterator`.

```cpp
typedef iterator const_iterator;
```

## <a name="empty"></a>Path:: Empty

Zwraca `mypath.empty()`wartość.

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

Zwraca sufiks `filename() X` takiego, że:

Jeśli `X == path(".") || X == path("..")` lub jeśli `X` nie zawiera kropki, sufiks jest pusty.

W przeciwnym razie sufiks zaczyna się od (i zawiera) z prawej kropką.

## <a name="filename"></a>Path:: filename

Zwraca składnik katalogu głównego ServiceName, w `empty() path() : *--end()`tym celu. Składnik może być pusty.

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

Zwraca `!extension().empty()`wartość.

```cpp
bool has_extension() const;
```

## <a name="has_filename"></a>ścieżka:: has_filename

Zwraca `!filename().empty()`wartość.

```cpp
bool has_filename() const;
```

## <a name="has_parent_path"></a>ścieżka:: has_parent_path

Zwraca `!parent_path().empty()`wartość.

```cpp
bool has_parent_path() const;
```

## <a name="has_relative_path"></a>ścieżka:: has_relative_path

Zwraca `!relative_path().empty()`wartość.

```cpp
bool has_relative_path() const;
```

## <a name="has_root_directory"></a>ścieżka:: has_root_directory

Zwraca `!root_directory().empty()`wartość.

```cpp
bool has_root_directory() const;
```

## <a name="has_root_name"></a>ścieżka:: has_root_name

Zwraca `!root_name().empty()`wartość.

```cpp
bool has_root_name() const;
```

## <a name="has_root_path"></a>ścieżka:: has_root_path

Zwraca `!root_path().empty()`wartość.

```cpp
bool has_root_path() const;
```

## <a name="has_stem"></a>ścieżka:: has_stem

Zwraca `!stem().empty()`wartość.

```cpp
bool has_stem() const;
```

## <a name="is_absolute"></a>ścieżka:: is_absolute

Dla systemu Windows funkcja zwraca wartość `has_root_name() && has_root_directory()`. W przypadku POSIX funkcja zwraca wartość `has_root_directory()`.

```cpp
bool is_absolute() const;
```

## <a name="is_relative"></a>ścieżka:: is_relative

Zwraca `!is_absolute()`wartość.

```cpp
bool is_relative() const;
```

## <a name="iterator"></a>Path:: iterator

Jednokierunkowy iterator, który wyznacza składniki `myname`ścieżki.

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

Klasa opisuje jednokierunkowy iterator, który wyznacza `path` `myname` składniki w sekwencji:

1. Nazwa główna, jeśli istnieje

1. Katalog główny, jeśli jest obecny

1. pozostałe elementy katalogu nadrzędnego `path`(jeśli istnieją) kończące się na nazwą pliku, jeśli jest obecny

Dla `pval` obiektu typu `path`:

1. `path::iterator X = pval.begin()`wyznacza pierwszy `path` element w nazwie ścieżki, jeśli jest obecny.

1. `X == pval.end()`jest prawdziwe, `X` gdy wskazuje koniec sekwencji składników.

3. `*X`Zwraca ciąg, który jest zgodny z bieżącym składnikiem

1. `++X`Określa Następny składnik w sekwencji, jeśli jest obecny.

1. `--X`Określa poprzedni składnik w sekwencji, jeśli jest obecny.

1. Zmiana unieważnia wszystkie Iteratory wyznaczające elementy w `myname`. `myname`

## <a name="make_preferred"></a>ścieżka:: make_preferred

Konwertuje każdy separator na wartość `preferred_separator` w razie potrzeby.

```cpp
path& make_preferred();
```

## <a name="native"></a>ścieżka:: Native

Zwraca `myname`wartość.

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

*Kliknij*\
[Ścieżka](../standard-library/path-class.md) jest kopiowana do `path`.

*zewnętrz*\
Ścieżka źródłowa.

### <a name="remarks"></a>Uwagi

Pierwszy operator członkowski jest `right.myname` kopiowany `myname`do. Drugi operator elementu członkowskiego `right.myname` przenosi `myname`do. Trzeci operator członkowski zachowuje się tak samo jak `*this = path(source)`.

## <a name="op_add"></a>Path:: operator + =

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

*Kliknij*\
Dodana ścieżka.

*str*\
Dodany ciąg.

*PTR*\
Dodany wskaźnik.

*elem*\
Dodano `value_type` lub .`Elem`

*zewnętrz*\
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

Różne `append` wyrażenia.

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Dodana ścieżka.

*zewnętrz*\
Dodane źródło.

### <a name="remarks"></a>Uwagi

Funkcje składowe zachowują się tak samo jak następujące odpowiednie wyrażenia:

1. `append(right);`

1. `append(source);`

## <a name="op_string"></a>Path:: operator string_type

Zwraca `myname`wartość.

```cpp
operator string_type() const;
```

## <a name="parent_path"></a>ścieżka::p arent_path

Zwraca składnik `myname`ścieżki nadrzędnej.

```cpp
path parent_path() const;
```

### <a name="remarks"></a>Uwagi

Zwraca składnik `myname`ścieżki nadrzędnej, w tym `myname` prefiks po usunięciu `filename().native()` i wszystkie bezpośrednio poprzedzające separatory katalogów. (Podobnie, jeśli `begin() != end()`jest to połączenie wszystkich elementów w zakresie `[begin(), --end())` przez ponowne zastosowanie `operator/=`). Składnik może być pusty.

## <a name="path"></a>ścieżka::p XPath

Konstrukcje a `path` na różne sposoby.

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

*Kliknij*\
Ścieżka, dla której skonstruowana ścieżka ma być kopią.

*zewnętrz*\
Źródło, którego skonstruowaną ścieżką jest kopia.

*Loc*\
Określone ustawienia regionalne.

*pierwszego*\
Pozycja pierwszego elementu, który ma zostać skopiowany.

*ostatniego*\
Pozycja ostatniego elementu, który ma zostać skopiowany.

### <a name="remarks"></a>Uwagi

Konstruktory wszystkie `myname` są na różne sposoby:

`path()` Jest`myname()`to.

Dla `path(const path& right`programu) jest `myname(right.myname)`.

`path(path&& right)` Jest`myname(right.myname)`to.

`template<class Source> path(const Source& source)` Jest`myname(source)`to.

W `template<class Source> path(const Source& source, const locale& loc)` `loc`tym celu należy uzyskać wszystkie potrzebne aspekty codecvt z. `myname(source)`

`template<class InIt> path(InIt first, InIt last)` Jest`myname(first, last)`to.

W `template<class InIt> path(InIt first, InIt last, const locale& loc)` `loc`tym celu należy uzyskać wszystkie potrzebne aspekty codecvt z. `myname(first, last)`

## <a name="preferred_separator"></a>ścieżka::p referred_separator

Obiekt stała daje preferowany znak do oddzielania składników ścieżki, w zależności od systemu operacyjnego hosta.

```cpp
#if _WIN32_C_LIB
static constexpr value_type preferred_separator == L'\\';
#else // assume Posix
static constexpr value_type preferred_separator == '/';
#endif // filesystem model now defined
```

### <a name="remarks"></a>Uwagi

Należy zauważyć, że jest to równie dozwolone w większości kontekstów w systemie Windows, aby użyć L "/" w tym miejscu.

## <a name="relative_path"></a>ścieżka:: RELATIVE_PATH

Zwraca składnik ścieżki względnej elementu `myname`.

```cpp
path relative_path() const;
```

### <a name="remarks"></a>Uwagi

Zwraca składnik `myname`ścieżki względnej, w odniesieniu do `myname` sufiksu `root_path().native()` po usunięciu i wszelkie bezpośrednio kolejne nadmiarowe separatory katalogów. Składnik może być pusty.

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

Najpierw usuwa sufiks `extension().native()` z `myname`. Następnie Jeśli `!newext.empty() && newext[0] != dot` (gdzie `dot` is `*path(".").c_str()`), `dot` jest dołączany do `myname`. Następnie *newext* jest dołączany `myname`do.

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

Zwraca składnik katalogu głównego programu `myname`.

```cpp
path root_directory() const;
```

### <a name="remarks"></a>Uwagi

Składnik może być pusty.

## <a name="root_name"></a>ścieżka:: root_name

Zwraca składnik `myname`nazwy głównej.

```cpp
path root_name() const;
```

### <a name="remarks"></a>Uwagi

Składnik może być pusty.

## <a name="root_path"></a>ścieżka:: root_path

Zwraca składnik `myname`ścieżki głównej elementu.

```cpp
path root_path() const;
```

### <a name="remarks"></a>Uwagi

Zwraca główny składnik `myname`ścieżki `root_name()`,wtym.  /  `root_directory` Składnik może być pusty.

## <a name="stem"></a>ścieżka:: trzon

`stem` Zwraca`myname`składnik.

```cpp
path stem() const;
```

### <a name="remarks"></a>Uwagi

Zwraca składnik programu, `myname` `extension().native()` w tym odnoszący się do wszystkich usuniętych końcowych elementów. `filename().native()` `stem` Składnik może być pusty.

## <a name="string"></a>Path:: String

Konwertuje sekwencję przechowywaną `mypath`w.

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska (szablon) konwertuje sekwencję przechowywaną `mypath` w taki sam sposób, jak:

1. `string()` Aby uzyskać `string<char, Traits, Alloc>()`

1. `wstring()` Aby uzyskać `string<wchar_t, Traits, Alloc>()`

1. `u16string()` Aby uzyskać `string<char16_t, Traits, Alloc>()`

1. `u32string()` Aby uzyskać `string<char32_t, Traits, Alloc>()`

Druga funkcja członkowska konwertuje sekwencję przechowywaną `mypath` w kodowaniu preferowaną przez system hosta dla sekwencji **znaków** i zwraca ją przechowywaną w obiekcie typu `string`.

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

Konwertuje sekwencję przechowywaną `mypath` w do UTF-16 i zwraca ją przechowywaną w obiekcie typu `u16string`.

```cpp
u16string u16string() const;
```

## <a name="u32string"></a>ścieżka:: u32string

Konwertuje sekwencję przechowywaną `mypath` w do UTF-32 i zwraca ją przechowywaną w obiekcie typu `u32string`.

```cpp
u32string u32string() const;
```

## <a name="u8string"></a>ścieżka:: u8string

Konwertuje sekwencję przechowywaną `mypath` w do UTF-8 i zwraca ją przechowywaną w obiekcie typu `u8string`.

```cpp
string u8string() const;
```

## <a name="value_type"></a>ścieżka:: value_type

Typ opisuje `path` elementy preferowane przez system operacyjny hosta.

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume Posix
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="wstring"></a>ścieżka:: wstring

Konwertuje sekwencję przechowywaną `mypath` w programie na kodowanie preferowaną przez system hosta dla sekwencji **wchar_t** i zwraca ją przechowywaną w obiekcie typu `wstring`.

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
