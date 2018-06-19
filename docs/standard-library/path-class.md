---
title: PATH — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 8ea20d43e2679addc10465cfc549a64fc210274f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861691"
---
# <a name="path-class"></a>path — klasa

**Ścieżki** klasy przechowuje obiekt typu String\_typu o nazwie mójużytkownik tutaj na potrzeby specyfikacji odpowiednie do użycia jako nazwa ścieżki. ciąg\_typu jest synonimem basic\_ciąg\<value_type >, gdzie wartość\_typu jest synonimem znak w systemie Windows lub wchar_t w obszarze Posix.

Aby uzyskać więcej informacji oraz przykłady kodu, zobacz [nawigacji systemu plików (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Składnia

```cpp
class path;
```

## <a name="pathappend"></a>path::append

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

Funkcje Członkowskie Dołącz określona sekwencja do mypath, przekonwertować i wstawianie preferred_separator zgodnie z potrzebami.

## <a name="pathassign"></a>path::ASSIGN

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

Funkcje Członkowskie Zamień mypath sekwencji określony, przekonwertować zgodnie z potrzebami.

## <a name="pathbegin"></a>path::begin

```cpp
iterator begin() const;
```

Zwraca path::iterator wyznaczenie pierwszy element ścieżki w nazwie ścieżki, jeśli jest obecny.

## <a name="pathcstr"></a>path::c_str

```cpp
const value_type& *c_str() const noexcept;
```

Zwraca wskaźnik do pierwszego znaku w mypath.

## <a name="pathclear"></a>path::Clear

```cpp
void clear() noexcept;
```

Funkcja członkowska wykonuje mypath.clear()

## <a name="pathcompare"></a>path::COMPARE

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

Pierwsza funkcja zwraca mypath.compare(pval.native()). Druga funkcja zwraca mypath.compare(str). Trzeci funkcja mypath.compare(ptr).

## <a name="pathconcat"></a>path::concat

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

Funkcje Członkowskie Dołącz określona sekwencja mypath przekonwertować (ale nie Wstawianie separator) zgodnie z potrzebami.

## <a name="pathconstiterator"></a>path::const_iterator

```cpp
typedef iterator const_iterator;
```

Typ jest synonimem iteratora.

## <a name="pathempty"></a>path::Empty

```cpp
bool empty() const noexcept;
```

Zwraca mypath.empty().

## <a name="pathend"></a>path::end

```cpp
iterator end() const;
```

Zwraca iterator sekwencja kończenia typ iteratora.

## <a name="pathextension"></a>path::Extension

```cpp
path extension() const;
```

Zwraca sufiks filename() X tak, aby:

Jeśli X == path(".") &#124; &#124; X == path("..") lub jeśli X zawiera nie kropki, sufiks jest pusty.

W przeciwnym razie sufiks rozpoczyna się od ciągu (i zawiera) po prawej stronie kropki (.).

## <a name="pathfilename"></a>path::filename

```cpp
path filename() const;
```

Zwraca składnik katalogu głównego mójużytkownik, w szczególności `empty()  path() : *--end()`. Składnik może być pusta.

## <a name="pathgenericstring"></a>path::generic_string

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

Zwraca `this->string<Elem, Traits, Alloc>(al)` z (w systemie Windows) wszelkie ukośnik odwrotny przekonwertować kreską ukośną.

## <a name="pathgenericu16string"></a>path::generic_u16string

```cpp
u16string generic_u16string() const;
```

Zwraca odwrotny żadnych u16string() z (w systemie Windows) przekonwertować kreską ukośną.

## <a name="pathgenericu32string"></a>path::generic_u32string

```cpp
u32string generic_u32string() const;
```

Zwraca odwrotny żadnych u32string() z (w systemie Windows) przekonwertować kreską ukośną.

## <a name="pathgenericu8string"></a>path::generic_u8string

```cpp
string generic_u8string() const;
```

Zwraca odwrotny żadnych u8string() z (w systemie Windows) przekonwertować kreską ukośną.

## <a name="pathgenericwstring"></a>path::generic_wstring

```cpp
wstring generic_wstring() const;
```

Zwraca odwrotny żadnych wstring() z (w systemie Windows) przekonwertować kreską ukośną.

## <a name="pathhasextension"></a>path::has_extension

```cpp
bool has_extension() const;
```

Zwraca! extension().empty().

## <a name="pathhasfilename"></a>path::has_filename

```cpp
bool has_filename() const;
```

Zwraca! filename().empty().

## <a name="pathhasparentpath"></a>path::has_parent_path

```cpp
bool has_parent_path() const;
```

Returns !parent_path().empty().

## <a name="pathhasrelativepath"></a>path::has_relative_path

```cpp
bool has_relative_path() const;
```

Returns !relative_path().empty().

## <a name="pathhasrootdirectory"></a>path::has_root_directory

```cpp
bool has_root_directory() const;
```

Zwraca! root_directory().empty().

## <a name="pathhasrootname"></a>path::has_root_name

```cpp
bool has_root_name() const;
```

Zwraca! root_name().empty().

## <a name="pathhasrootpath"></a>path::has_root_path

```cpp
bool has_root_path() const;
```

Zwraca! root_path().empty().

## <a name="pathhasstem"></a>path::has_stem

```cpp
bool has_stem() const;
```

Zwraca! stem().empty().

## <a name="pathisabsolute"></a>path::is_absolute

```cpp
bool is_absolute() const;
```

W systemie Windows, funkcja zwraca has_root_name() & & has_root_directory(). Dla Posix funkcja zwraca has_root_directory().

## <a name="pathisrelative"></a>path::is_relative

```cpp
bool is_relative() const;
```

Zwraca! is_absolute().

## <a name="pathiterator"></a>path::iterator

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

Klasa opisuje dwukierunkowego iteratora stałej, który wyznacza ścieżkę składników mójużytkownik w sekwencji:

1. Nazwa głównego, jeśli jest obecny

1. katalog główny, jeśli jest obecny

1. pozostałe elementy katalogu ścieżki nadrzędnej, jeśli jest obecny, kończąc nazwę pliku, jeśli jest obecny

Dla obiektu typu ścieżki pval:

1. path::iterator X = pval.begin() wyznacza pierwszy element ścieżki w nazwie ścieżki, jeśli jest obecny.

1. X == pval.end() ma wartość true, gdy X punktów tylko poza koniec sekwencja składników.

3. * X zwraca ciąg zgodny bieżącego składnika

1. ++ X wyznacza następny składnik w sekwencji, jeśli jest obecny.

1. --X wyznacza poprzedniego składnika w sekwencji, jeśli jest obecny.

1. Zmienianie mójużytkownik unieważnia Iteratory wszystkich elementów w mójużytkownik wyznaczenie.

## <a name="pathmakepreferred"></a>path::make_preferred

```cpp
path& make_preferred();
```

Funkcja członkowska konwertuje każdego separatora preferred_separator zgodnie z potrzebami.

## <a name="pathnative"></a>path::Native

```cpp
const string_type& native() const noexcept;
```

Zwraca mójużytkownik.

## <a name="pathoperator"></a>path::operator=

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

Pierwszy operator członkowski kopiuje right.myname mójużytkownik. Drugi operator członkowski przenosi right.myname mójużytkownik. Trzeci operator członkowski działa tak samo jak * to = path(source).

## <a name="pathoperator"></a>path::operator +=

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

Funkcje Członkowskie zachowują się taka sama jak następujących odpowiednich wyrażeń:

1. concat(right);

1. concat(path(str));

1. concat(ptr);

1. concat (string_type (element 1));

1. concat(source);

1. concat (ścieżka (basic_string —\<elementu >(1, elem)));

## <a name="pathoperator"></a>path::operator / =

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

Funkcje Członkowskie zachowują się taka sama jak następujących odpowiednich wyrażeń:

1. append(Right);

1. append(Source);

## <a name="pathoperator-stringtype"></a>path::operator string_type

```cpp
operator string_type() const;
```

Operator członkowski zwraca mójużytkownik.

## <a name="pathparentpath"></a>path::parent_path

```cpp
path parent_path() const;
```

Zwraca element nadrzędny składnika ścieżki mójużytkownik, w szczególności prefiks mójużytkownik po usunięciu filename().native() i wszystkie bezpośrednio poprzednie separatorów katalogu. (Jednakowo, jeśli begin()! = end(), jest łączenie wszystkich elementów z zakresu [begin(),--end()), stosując kolejno operator / =.) Składnik może być pusta.

## <a name="pathpath"></a>path::Path —

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

Wszystkie konstruktory utworzyć mójużytkownik na różne sposoby:

Path() jest myname().

Dla ścieżki (const Ścieżka & prawej) jest myname(right.myname).

Dla ścieżki (ścieżka & & prawo) jest myname(right.myname).

Dla szablonu\<klasy źródła > Ścieżka (const źródła & źródła) jest myname(source).

Dla szablonu\<klasy źródła > Ścieżka (const źródła i źródła, const ustawień regionalnych i lokalizacja) jest myname(source) uzyskiwanie wszystkie aspekty codecvt potrzebne w loc.

Dla szablonu\<klasy InIt > Ścieżka (InIt pierwszy, InIt ostatniego) jest mójużytkownik (imię, nazwisko).

Dla szablonu\<klasy InIt > Ścieżka (InIt InIt ostatnich, stałe ustawień regionalnych & Lokalizacja jest pierwszą) jest mójużytkownik (imię, nazwisko), uzyskiwanie wszelkie potrzebne aspekty codecvt z loc.

## <a name="pathpreferredseparator"></a>path::preferred_separator

```cpp
#if _WIN32_C_LIB
static constexpr value_type preferred_separator == L'\\';
#else // assume Posix
static constexpr value_type preferred_separator == '/';
#endif // filesystem model now defined
```

Stała obiektu daje preferowanych znak do oddzielania składników ścieżki, w zależności od systemu operacyjnego hosta. Należy pamiętać, że jednakowo dopuszczalna, w większości kontekstów w systemie Windows, aby użyć L '/' w tym miejscu.

## <a name="pathrelativepath"></a>path::relative_path

```cpp
path relative_path() const;
```

Zwraca składnik ścieżki względnej mójużytkownik, w szczególności sufiks mójużytkownik po usunięciu root_path().native() i żadnych separatorów natychmiast kolejnych nadmiarowe katalogu. Składnik może być pusta.

## <a name="pathremovefilename"></a>path::remove_filename

```cpp
path& remove_filename();
```

## <a name="pathreplaceextension"></a>path::replace_extension

```cpp
path& replace_extension(const path& newext = path());
```

Funkcja członkowska najpierw usuwa extension().native() sufiks mójużytkownik. Jeśli następnie! newext.empty() & & newext [0]! = kropka (gdzie jest kropka * path("."). c_str()), a następnie kropka jest dołączany do mójużytkownik. Następnie newext jest dołączany do mójużytkownik.

## <a name="pathreplacefilename"></a>path::replace_filename

```cpp
path& replace_filename(const path& pval);
```

Funkcja członkowska wykonuje:

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="pathrootdirectory"></a>path::root_directory

```cpp
path root_directory() const;
```

Zwraca składnik katalogu głównego mójużytkownik. Składnik może być pusta.

## <a name="pathrootname"></a>path::root_name

```cpp
path root_name() const;
```

Zwraca składnik nazwy głównej mójużytkownik. Składnik może być pusta.

## <a name="pathrootpath"></a>path::root_path

```cpp
path root_path() const;
```

Zwraca część ścieżki katalogu głównego mójużytkownik, w szczególności root_name() / root_directory. Składnik może być pusta.

## <a name="pathstem"></a>path::stem

```cpp
path stem() const;
```

Zwraca składnik stem mójużytkownik, w szczególności filename().native() z wszelkich końcowych extension().native() usunięte. Składnik może być pusta.

## <a name="pathstring"></a>path::String

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

Pierwszy funkcji członkowskiej (szablonu) konwertuje sekwencji przechowywane w mypath taki sam sposób jak:

1. String() ciągu\<char, cech, alokacji >)

1. wstring() ciągu\<wchar_t cech, alokacji >)

1. u16string() ciągu\<char16_t, cech, alokacji >)

1. u32string() ciągu\<char32_t, cech, alokacji >)

Drugi funkcji członkowskiej konwertuje sekwencji przechowywane w mypath kodowanie ich drużyna jest faworytem systemu hosta sekwencji znaku i zwraca wartość ona przechowywana w obiekcie typu String.

## <a name="pathstringtype"></a>path::STRING_TYPE

```cpp
typedef basic_string<value_type> string_type;
```

Typ jest synonimem basic_string — < value_type >.

## <a name="pathswap"></a>path::swap

```cpp
void swap(path& right) noexcept;
```

Wykonuje swap (mypath, right.mypath).

## <a name="pathu16string"></a>path::u16string

```cpp
u16string u16string() const;
```

Funkcja członkowska konwertuje sekwencji przechowywane w mypath UTF-16 i zwróci ona przechowywana w obiekcie u16string typu.

## <a name="pathu32string"></a>path::u32string

```cpp
u32string u32string() const;
```

Funkcja członkowska konwertuje sekwencji przechowywane w mypath UTF-32 i zwróci ona przechowywana w obiekcie u32string typu.

## <a name="pathu8string"></a>path::u8string

```cpp
string u8string() const;
```

Funkcja członkowska konwertuje przechowywanych w mypath UTF-8 kolejność i zwraca wartość ona przechowywana w obiekcie u8string typu.

## <a name="pathvaluetype"></a>path::value_type

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume Posix
typedef char value_type;
#endif // filesystem model now defined
```

Typ w tym artykule opisano elementy ścieżki ich drużyna jest faworytem systemu operacyjnego hosta.

## <a name="pathwstring"></a>path::wstring

```cpp
wstring wstring() const;
```

Konwertuje sekwencji przechowywane w mypath kodowanie ich drużyna jest faworytem systemu hosta sekwencji wchar_t i zwróci ona przechowywana w obiekcie wstring typu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<filesystem >

**Namespace:** std::experimental::filesystem

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
