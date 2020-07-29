---
title: path — klasa
ms.date: 09/27/2018
f1_keywords:
- filesystem/std::experimental::filesystem::path
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
ms.openlocfilehash: d7c8c739c3d235383ede0509cfa87b41200efeca
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233005"
---
# <a name="path-class"></a>path — klasa

Klasa **Path** przechowuje obiekt typu, który jest `string_type` wywoływany `myname` w tym miejscu do celów specyfikacji, odpowiedni do użycia jako nazwa ścieżki. `string_type`jest synonimem dla `basic_string<value_type>` , gdzie `value_type` jest synonimem dla **`wchar_t`** systemu Windows lub **`char`** na POSIX.

Aby uzyskać więcej informacji i przykłady kodu, zobacz [Nawigacja w systemie plików (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Składnia

```cpp
class path;
```

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[ścieżka](#path)|Konstruuje a `path` .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[const_iterator](#const_iterator)|Synonim dla `iterator` .|
|[Iterator](#iterator)|Jednokierunkowy iterator, który wyznacza `path` składniki `myname` .|
|[string_type](#string_type)|Typ jest synonimem dla `basic_string<value_type>` .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[łączono](#append)|Dołącza określoną sekwencję do `mypath` , przekonwertowane i wstawia preferred_separator w razie potrzeby.|
|[przypisać](#assign)|Zastępuje `mypath` z określoną sekwencją przekonwertowaną zgodnie z wymaganiami.|
|[zaczną](#begin)|Zwraca `path::iterator` wyznaczanie pierwszego elementu Path w nazwie ścieżki, jeśli jest obecny.|
|[c_str](#c_str)|Zwraca wskaźnik do pierwszego znaku w `mypath` .|
|[Wyczyść](#clear)|Wykonuje `mypath.clear()` .|
|[porównaniu](#compare)|Zwraca wartości porównania.|
|[Concat](#compare)|Dołącza określoną sekwencję do `mypath` , przekonwertowane (ale nie wstawia separatora) zgodnie z wymaganiami.|
|[puste](#empty)|Zwraca wartość `mypath.empty()`.|
|[punktów](#end)|Zwraca iterator końca sekwencji typu `iterator` .|
|[rozszerzenia](#extension)|Zwraca sufiks `filename()` .|
|[Nazwa pliku](#filename)|Zwraca składnik katalogu głównego ServiceName, w tym celu `empty() path() : *--end()` . Składnik może być pusty.|
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
|[is_absolute](#is_absolute)|Dla systemu Windows funkcja zwraca wartość `has_root_name() && has_root_directory()` . W przypadku POSIX funkcja zwraca wartość `has_root_directory()` .|
|[is_relative](#is_relative)|Zwraca wartość `!is_absolute()`.|
|[make_preferred](#make_preferred)|Konwertuje każdy separator na preferred_separator w razie potrzeby.|
|[natywne](#native)|Zwraca wartość `myname`.|
|[parent_path](#parent_path)|Zwraca składnik ścieżki nadrzędnej `myname` .|
|[preferred_separator](#preferred_separator)|Obiekt stała daje preferowany znak do oddzielania składników ścieżki, w zależności od systemu operacyjnego hosta. |
|[relative_path](#relative_path)|Zwraca składnik ścieżki względnej elementu `myname` . |
|[remove_filename](#remove_filename)|Usuwa nazwę pliku.|
|[replace_extension](#replace_extension)|Zastępuje rozszerzenie `myname` . |
|[replace_filename](#replace_filename)|RReplaces nazwę pliku.|
|[root_directory](#root_directory)|Zwraca składnik katalogu głównego programu `myname` . |
|[root_name](#root_name)|Zwraca składnik nazwy głównej `myname` . |
|[root_path](#root_path)|Zwraca składnik ścieżki głównej elementu `myname` .|
|[Spływ](#stem)|Zwraca `stem` składnik `myname` .|
|[parametry](#string)|Konwertuje sekwencję przechowywaną w `mypath` .|
|[wymiany](#swap)|Wykonuje `swap(mypath, right.mypath)` .|
|[u16string](#u16string)|Konwertuje sekwencję przechowywaną w `mypath` do UTF-16 i zwraca ją przechowywaną w obiekcie typu `u16string` .|
|[u32string](#u32string)|Konwertuje sekwencję przechowywaną w `mypath` do UTF-32 i zwraca ją przechowywaną w obiekcie typu `u32string` .|
|[u8string](#u8string)|Konwertuje sekwencję przechowywaną w `mypath` do UTF-8 i zwraca ją przechowywaną w obiekcie typu `u8string` .|
|[value_type](#value_type)|Typ opisuje elementy ścieżki preferowane przez system operacyjny hosta.|
|[wstring](#wstring)|Konwertuje sekwencję przechowywaną w programie `mypath` na kodowanie preferowaną przez system hosta dla **`wchar_t`** sekwencji i zwraca ją przechowywaną w obiekcie typu `wstring` .|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator =](#op_as)|Zastępuje elementy ścieżki kopią innej ścieżki.|
|[operator + =](#op_add)|Różne `concat` wyrażenia.|
|[operator/=](#op_divide)|Różne `append` wyrażenia.|
|[string_type operatora](#op_string)|Zwraca wartość `myname`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<filesystem>

**Przestrzeń nazw:** std:: eksperymentalne:: filesystem

## <a name="pathappend"></a><a name="append"></a>Path:: Append

Dołącza określoną sekwencję do `mypath` , przekonwertowane i wstawia `preferred_separator` w razie potrzeby.

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

## <a name="pathassign"></a><a name="assign"></a>ścieżka:: Assign

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

## <a name="pathbegin"></a><a name="begin"></a>ścieżka:: BEGIN

Zwraca `path::iterator` wyznaczanie pierwszego elementu Path w nazwie ścieżki, jeśli jest obecny.

```cpp
iterator begin() const;
```

## <a name="pathc_str"></a><a name="c_str"></a>ścieżka:: c_str

Zwraca wskaźnik do pierwszego znaku w `mypath` .

```cpp
const value_type& *c_str() const noexcept;
```

## <a name="pathclear"></a><a name="clear"></a>ścieżka:: Clear

Wykonuje `mypath.clear()` .

```cpp
void clear() noexcept;
```

## <a name="pathcompare"></a><a name="compare"></a>Path:: Compare

Pierwsza funkcja zwraca wartość `mypath.compare(pval.native())` . Druga funkcja zwraca `mypath.compare(str)` . Trzecia funkcja zwraca wartość `mypath.compare(ptr)` .

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

## <a name="pathconcat"></a><a name="concat"></a>ścieżka:: Concat

Dołącza określoną sekwencję do `mypath` , przekonwertowane (ale nie wstawia separatora) zgodnie z wymaganiami.

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

## <a name="pathconst_iterator"></a><a name="const_iterator"></a>ścieżka:: const_iterator

Synonim dla `iterator` .

```cpp
typedef iterator const_iterator;
```

## <a name="pathempty"></a><a name="empty"></a>Path:: Empty

Zwraca wartość `mypath.empty()`.

```cpp
bool empty() const noexcept;
```

## <a name="pathend"></a><a name="end"></a>Path:: end

Zwraca iterator końca sekwencji typu `iterator` .

```cpp
iterator end() const;
```

## <a name="pathextension"></a><a name="extension"></a>Path:: Extension

Zwraca sufiks `filename()` .

```cpp
path extension() const;
```

### <a name="remarks"></a>Uwagi

Zwraca sufiks `filename() X` takiego, że:

Jeśli `X == path(".") || X == path("..")` lub jeśli `X` nie zawiera kropki, sufiks jest pusty.

W przeciwnym razie sufiks zaczyna się od (i zawiera) z prawej kropką.

## <a name="pathfilename"></a><a name="filename"></a>Path:: filename

Zwraca składnik katalogu głównego ServiceName, w tym celu `empty() path() : *--end()` . Składnik może być pusty.

```cpp
path filename() const;
```

## <a name="pathgeneric_string"></a><a name="generic_string"></a>ścieżka:: generic_string

Zwraca `this->string<Elem, Traits, Alloc>(al)` z (w obszarze systemu Windows) wszystkie ukośniki odwrotne konwertowane na ukośnik.

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

## <a name="pathgeneric_u16string"></a><a name="generic_u16string"></a>ścieżka:: generic_u16string

Zwraca `u16string()` z (w obszarze systemu Windows) wszystkie ukośniki odwrotne konwertowane na ukośnik.

```cpp
u16string generic_u16string() const;
```

## <a name="pathgeneric_u32string"></a><a name="generic_u32string"></a>ścieżka:: generic_u32string

Zwraca `u32string()` z (w obszarze systemu Windows) wszystkie ukośniki odwrotne konwertowane na ukośnik.

```cpp
u32string generic_u32string() const;
```

## <a name="pathgeneric_u8string"></a><a name="generic_u8string"></a>ścieżka:: generic_u8string

Zwraca `u8string()` z (w obszarze systemu Windows) wszystkie ukośniki odwrotne konwertowane na ukośnik.

```cpp
string generic_u8string() const;
```

## <a name="pathgeneric_wstring"></a><a name="generic_wstring"></a>ścieżka:: generic_wstring

Zwraca `wstring()` z (w obszarze systemu Windows) wszystkie ukośniki odwrotne konwertowane na ukośnik.

```cpp
wstring generic_wstring() const;
```

## <a name="pathhas_extension"></a><a name="has_extension"></a>ścieżka:: has_extension

Zwraca wartość `!extension().empty()`.

```cpp
bool has_extension() const;
```

## <a name="pathhas_filename"></a><a name="has_filename"></a>ścieżka:: has_filename

Zwraca wartość `!filename().empty()`.

```cpp
bool has_filename() const;
```

## <a name="pathhas_parent_path"></a><a name="has_parent_path"></a>ścieżka:: has_parent_path

Zwraca wartość `!parent_path().empty()`.

```cpp
bool has_parent_path() const;
```

## <a name="pathhas_relative_path"></a><a name="has_relative_path"></a>ścieżka:: has_relative_path

Zwraca wartość `!relative_path().empty()`.

```cpp
bool has_relative_path() const;
```

## <a name="pathhas_root_directory"></a><a name="has_root_directory"></a>ścieżka:: has_root_directory

Zwraca wartość `!root_directory().empty()`.

```cpp
bool has_root_directory() const;
```

## <a name="pathhas_root_name"></a><a name="has_root_name"></a>ścieżka:: has_root_name

Zwraca wartość `!root_name().empty()`.

```cpp
bool has_root_name() const;
```

## <a name="pathhas_root_path"></a><a name="has_root_path"></a>ścieżka:: has_root_path

Zwraca wartość `!root_path().empty()`.

```cpp
bool has_root_path() const;
```

## <a name="pathhas_stem"></a><a name="has_stem"></a>ścieżka:: has_stem

Zwraca wartość `!stem().empty()`.

```cpp
bool has_stem() const;
```

## <a name="pathis_absolute"></a><a name="is_absolute"></a>ścieżka:: is_absolute

Dla systemu Windows funkcja zwraca wartość `has_root_name() && has_root_directory()` . W przypadku POSIX funkcja zwraca wartość `has_root_directory()` .

```cpp
bool is_absolute() const;
```

## <a name="pathis_relative"></a><a name="is_relative"></a>ścieżka:: is_relative

Zwraca wartość `!is_absolute()`.

```cpp
bool is_relative() const;
```

## <a name="pathiterator"></a><a name="iterator"></a>Path:: iterator

Jednokierunkowy iterator, który wyznacza składniki ścieżki `myname` .

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

1. pozostałe elementy katalogu nadrzędnego `path` (jeśli istnieją) kończące się na nazwą pliku, jeśli jest obecny

Dla `pval` obiektu typu `path` :

1. `path::iterator X = pval.begin()`wyznacza pierwszy `path` element w nazwie ścieżki, jeśli jest obecny.

1. `X == pval.end()`jest prawdziwe, gdy `X` wskazuje koniec sekwencji składników.

1. `*X`Zwraca ciąg, który jest zgodny z bieżącym składnikiem

1. `++X`Określa Następny składnik w sekwencji, jeśli jest obecny.

1. `--X`Określa poprzedni składnik w sekwencji, jeśli jest obecny.

1. Zmiana `myname` unieważnia wszystkie Iteratory wyznaczające elementy w `myname` .

## <a name="pathmake_preferred"></a><a name="make_preferred"></a>ścieżka:: make_preferred

Konwertuje każdy separator na wartość w `preferred_separator` razie potrzeby.

```cpp
path& make_preferred();
```

## <a name="pathnative"></a><a name="native"></a>ścieżka:: Native

Zwraca wartość `myname`.

```cpp
const string_type& native() const noexcept;
```

## <a name="pathoperator"></a><a name="op_as"></a>Path:: operator =

Zastępuje elementy ścieżki kopią innej ścieżki.

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
[Ścieżka](../standard-library/path-class.md) jest kopiowana do `path` .

*zewnętrz*\
Ścieżka źródłowa.

### <a name="remarks"></a>Uwagi

Pierwszy operator członkowski jest kopiowany `right.myname` do `myname` . Drugi operator elementu członkowskiego przenosi `right.myname` do `myname` . Trzeci operator członkowski zachowuje się tak samo jak `*this = path(source)` .

## <a name="pathoperator"></a><a name="op_add"></a>Path:: operator + =

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
Dodano `value_type` lub `Elem` .

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

## <a name="pathoperator"></a><a name="op_divide"></a>Path:: operator/=

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

## <a name="pathoperator-string_type"></a><a name="op_string"></a>Path:: operator string_type

Zwraca wartość `myname`.

```cpp
operator string_type() const;
```

## <a name="pathparent_path"></a><a name="parent_path"></a>ścieżka::p arent_path

Zwraca składnik ścieżki nadrzędnej `myname` .

```cpp
path parent_path() const;
```

### <a name="remarks"></a>Uwagi

Zwraca składnik ścieżki nadrzędnej `myname` , w tym prefiks `myname` po usunięciu `filename().native()` i wszystkie bezpośrednio poprzedzające separatory katalogów. (Podobnie, jeśli `begin() != end()` jest to połączenie wszystkich elementów w zakresie `[begin(), --end())` przez ponowne zastosowanie `operator/=` ). Składnik może być pusty.

## <a name="pathpath"></a><a name="path"></a>ścieżka::p XPath

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

Konstruktory wszystkie są `myname` na różne sposoby:

`path()`Jest to `myname()` .

Dla programu `path(const path& right` ) jest `myname(right.myname)` .

`path(path&& right)`Jest to `myname(right.myname)` .

`template<class Source> path(const Source& source)`Jest to `myname(source)` .

W `template<class Source> path(const Source& source, const locale& loc)` tym celu `myname(source)` należy uzyskać wszystkie potrzebne aspekty codecvt z `loc` .

`template<class InIt> path(InIt first, InIt last)`Jest to `myname(first, last)` .

W `template<class InIt> path(InIt first, InIt last, const locale& loc)` tym celu `myname(first, last)` należy uzyskać wszystkie potrzebne aspekty codecvt z `loc` .

## <a name="pathpreferred_separator"></a><a name="preferred_separator"></a>ścieżka::p referred_separator

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

## <a name="pathrelative_path"></a><a name="relative_path"></a>ścieżka:: relative_path

Zwraca składnik ścieżki względnej elementu `myname` .

```cpp
path relative_path() const;
```

### <a name="remarks"></a>Uwagi

Zwraca składnik ścieżki względnej, w odniesieniu `myname` do sufiksu `myname` po usunięciu `root_path().native()` i wszelkie bezpośrednio kolejne nadmiarowe separatory katalogów. Składnik może być pusty.

## <a name="pathremove_filename"></a><a name="remove_filename"></a>ścieżka:: remove_filename

Usuwa nazwę pliku.

```cpp
path& remove_filename();
```

## <a name="pathreplace_extension"></a><a name="replace_extension"></a>ścieżka:: replace_extension

Zastępuje rozszerzenie `myname` .

```cpp
path& replace_extension(const path& newext = path());
```

### <a name="parameters"></a>Parametry

*newext*\
Nowe rozszerzenie.

### <a name="remarks"></a>Uwagi

Najpierw usuwa sufiks `extension().native()` z `myname` . Następnie Jeśli `!newext.empty() && newext[0] != dot` (gdzie `dot` is `*path(".").c_str()` ), `dot` jest dołączany do `myname` . Następnie *newext* jest dołączany do `myname` .

## <a name="pathreplace_filename"></a><a name="replace_filename"></a>ścieżka:: replace_filename

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

## <a name="pathroot_directory"></a><a name="root_directory"></a>ścieżka:: root_directory

Zwraca składnik katalogu głównego programu `myname` .

```cpp
path root_directory() const;
```

### <a name="remarks"></a>Uwagi

Składnik może być pusty.

## <a name="pathroot_name"></a><a name="root_name"></a>ścieżka:: root_name

Zwraca składnik nazwy głównej `myname` .

```cpp
path root_name() const;
```

### <a name="remarks"></a>Uwagi

Składnik może być pusty.

## <a name="pathroot_path"></a><a name="root_path"></a>ścieżka:: root_path

Zwraca składnik ścieżki głównej elementu `myname` .

```cpp
path root_path() const;
```

### <a name="remarks"></a>Uwagi

Zwraca główny składnik ścieżki, w tym `myname` `root_name()`  /  `root_directory` . Składnik może być pusty.

## <a name="pathstem"></a><a name="stem"></a>ścieżka:: trzon

Zwraca `stem` składnik `myname` .

```cpp
path stem() const;
```

### <a name="remarks"></a>Uwagi

Zwraca `stem` składnik programu, w tym odnoszący `myname` `filename().native()` się do wszystkich usuniętych końcowych elementów `extension().native()` . Składnik może być pusty.

## <a name="pathstring"></a><a name="string"></a>Path:: String

Konwertuje sekwencję przechowywaną w `mypath` .

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska (szablon) konwertuje sekwencję przechowywaną w taki `mypath` sam sposób, jak:

1. `string()`dla`string<char, Traits, Alloc>()`

1. `wstring()`dla`string<wchar_t, Traits, Alloc>()`

1. `u16string()`dla`string<char16_t, Traits, Alloc>()`

1. `u32string()`dla`string<char32_t, Traits, Alloc>()`

Druga funkcja członkowska konwertuje sekwencję przechowywaną w `mypath` kodowaniu preferowaną przez system hosta dla **`char`** sekwencji i zwraca ją przechowywaną w obiekcie typu `string` .

## <a name="pathstring_type"></a><a name="string_type"></a>ścieżka:: string_type

Typ jest synonimem dla `basic_string<value_type>` .

```cpp
typedef basic_string<value_type> string_type;
```

## <a name="pathswap"></a><a name="swap"></a>ścieżka:: swap

Wykonuje `swap(mypath, right.mypath)` .

```cpp
void swap(path& right) noexcept;
```

## <a name="pathu16string"></a><a name="u16string"></a>ścieżka:: u16string

Konwertuje sekwencję przechowywaną w `mypath` do UTF-16 i zwraca ją przechowywaną w obiekcie typu `u16string` .

```cpp
u16string u16string() const;
```

## <a name="pathu32string"></a><a name="u32string"></a>ścieżka:: u32string

Konwertuje sekwencję przechowywaną w `mypath` do UTF-32 i zwraca ją przechowywaną w obiekcie typu `u32string` .

```cpp
u32string u32string() const;
```

## <a name="pathu8string"></a><a name="u8string"></a>ścieżka:: u8string

Konwertuje sekwencję przechowywaną w `mypath` do UTF-8 i zwraca ją przechowywaną w obiekcie typu `u8string` .

```cpp
string u8string() const;
```

## <a name="pathvalue_type"></a><a name="value_type"></a>ścieżka:: value_type

Typ opisuje `path` elementy preferowane przez system operacyjny hosta.

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume POSIX
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="pathwstring"></a><a name="wstring"></a>ścieżka:: wstring

Konwertuje sekwencję przechowywaną w programie `mypath` na kodowanie preferowaną przez system hosta dla **`wchar_t`** sekwencji i zwraca ją przechowywaną w obiekcie typu `wstring` .

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
