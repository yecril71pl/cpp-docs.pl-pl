---
title: locale — Klasa
ms.date: 03/19/2019
f1_keywords:
- xlocale/std::locale
- xlocale/std::locale::category
- xlocale/std::locale::combine
- xlocale/std::locale::name
- xlocale/std::locale::classic
- xlocale/std::locale::global
- xlocale/std::locale::operator( )
- xlocale/std::locale::facet
- xlocale/std::locale::id
helpviewer_keywords:
- std::locale [C++]
- std::locale [C++], category
- std::locale [C++], combine
- std::locale [C++], name
- std::locale [C++], classic
- std::locale [C++], global
- std::locale [C++], facet
- std::locale [C++], id
ms.assetid: 7dd6d271-472d-4750-8fb5-ea8f55fbef62
ms.openlocfilehash: 2581c5cdacc9e542f5d911860128dcf5526621ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367317"
---
# <a name="locale-class"></a>locale — Klasa

Klasa opisująca obiekt ustawień regionalnych, który hermetyzuje informacje specyficzne dla kultury jako zbiór zestawu reguł, które wspólnie definiują specyficzne środowisko zlokalizowane.

## <a name="syntax"></a>Składnia

```cpp
class locale;
```

## <a name="remarks"></a>Uwagi

Aspekt jest wskaźnikiem do obiektu klasy pochodnej [aspektu](#facet_class) klasy, który ma publiczny obiekt formularza:

```cpp
static locale::id id;
```

Można zdefiniować nieograniczony zbiór tych zestawów reguł. Można także skonstruować obiekt ustawień regionalnych, który wyznacza dowolną liczbę zestawów reguł.

Wstępnie zdefiniowane grupy tych aspektów reprezentują [kategorie ustawień regionalnych](#category) tradycyjnie zarządzanych w `setlocale`bibliotece Standard C przez funkcję .

Kategoria `collate` (LC_COLLATE) obejmuje aspekty:

```cpp
collate<char>
collate<wchar_t>
```

Kategoria `ctype` (LC_CTYPE) obejmuje aspekty:

```cpp
ctype<char>
ctype<wchar_t>
codecvt<char, char, mbstate_t>
codecvt<wchar_t, char, mbstate_t>
codecvt<char16_t, char, mbstate_t>
codecvt<char32_t, char, mbstate_t>
```

Kategoria `monetary` (LC_MONETARY) obejmuje aspekty:

```cpp
moneypunct<char, false>
moneypunct<wchar_t, false>
moneypunct<char, true>
moneypunct<wchar_t, true>
money_get<char, istreambuf_iterator<char>>
money_get<wchar_t, istreambuf_iterator<wchar_t>>
money_put<char, ostreambuf_iterator<char>>
money_put<wchar_t, ostreambuf_iterator<wchar_t>>
```

Kategoria `numeric` (LC_NUMERIC) obejmuje aspekty:

```cpp
num_get<char, istreambuf_iterator<char>>
num_get<wchar_t, istreambuf_iterator<wchar_t>>
num_put<char, ostreambuf_iterator<char>>
num_put<wchar_t, ostreambuf_iterator<wchar_t>>
numpunct<char>
numpunct<wchar_t>
```

Kategoria `time` (LC_TIME) obejmuje aspekty:

```cpp
time_get<char, istreambuf_iterator<char>>
time_get<wchar_t, istreambuf_iterator<wchar_t>>
time_put<char, ostreambuf_iterator<char>>
time_put<wchar_t, ostreambuf_iterator<wchar_t>>
```

Kategoria `messages` (LC_MESSAGES) obejmuje aspekty:

```cpp
messages<char>
messages<wchar_t>
```

(Ostatnia kategoria jest wymagana przez POSIX, ale nie standard C).)

Niektóre z tych wstępnie zdefiniowanych aspektów `iostream` są używane przez klasy, aby kontrolować konwersję wartości liczbowych do i z sekwencji tekstowych.

Obiekt ustawień regionalnych klasy przechowuje również nazwę ustawień regionalnych jako obiekt [ciągu](../standard-library/string-typedefs.md#string)klasy . Przy użyciu nieprawidłowej nazwy ustawień regionalnych do konstruowania aspektu ustawień regionalnych lub obiektu ustawień regionalnych zgłasza obiekt klasy [runtime_error](../standard-library/runtime-error-class.md). Przechowywana nazwa ustawień `"*"` regionalnych jest, jeśli obiekt ustawień regionalnych nie może być pewien, że ustawienia regionalne w stylu C odpowiada dokładnie do tego reprezentowanego przez obiekt. W przeciwnym razie można ustanowić pasujące ustawienia regionalne w `locale_object`bibliotece `setlocale(LC_ALL , locale_object.`Standard C dla niektórych obiektów ustawień regionalnych , wywołując [nazwę](#name)`().c_str())`.

W tej implementacji można również wywołać funkcję statycznego elementu członkowskiego:

```cpp
static locale empty();
```

do konstruowania obiektu ustawień regionalnych, który ma nie zestawu reguł. Jest to również przezroczyste ustawienia regionalne. Jeśli funkcje szablonu [has_facet](../standard-library/locale-functions.md#has_facet) i [use_facet](../standard-library/locale-functions.md#use_facet) nie można znaleźć żądanego aspektu w przezroczystych ustawieniach regionalnych, najpierw skonsultują się z globalnymi ustawieniami regionalne, a następnie, jeśli jest przezroczysty, klasyczne ustawienia regionalne. Tak, można napisać:

```cpp
cout.imbue(locale::empty());
```

Kolejne wstawienia [`cout`](../standard-library/iostream.md#cout) są pośredniczy według bieżącego stanu ustawień regionalnych globalnego. Można nawet napisać:

```cpp
locale loc(locale::empty(),
    locale::classic(),
    locale::numeric);

cout.imbue(loc);
```

Reguły formatowania liczbowego dla `cout` kolejnych wstawień pozostają takie same jak w ustawieniach regionalnych C, nawet gdy globalne ustawienia regionalne dostarczają zmieniające reguły wstawiania dat i kwot pieniężnych.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Ustawień regionalnych](#locale)|Tworzy ustawienia regionalne lub kopię ustawień regionalnych, lub kopię ustawień regionalnych, w której zestaw reguł lub kategoria zostały zastąpione przez zestaw reguł lub kategorię z innych ustawień regionalnych.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[Kategorii](#category)|Typ całkowitoliczbowy, który zawiera wartości masek bitowych dla oznaczenia standardowych rodzin zestawów reguł.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[combine](#combine)|Wstawia zestaw reguł z określonych ustawień regionalnych do docelowych ustawień regionalnych.|
|[Nazwa](#name)|Zwraca przechowywaną nazwę ustawień regionalnych.|

### <a name="static-functions"></a>Funkcje statyczne

|||
|-|-|
|[Klasyczny](#classic)|Funkcja statycznej składowej zwraca obiekt ustawień regionalnych, który reprezentuje klasyczne ustawienia regionalne C.|
|[Globalne](#global)|Resetuje domyślne ustawienia lokalne dla programu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Przypisuje ustawienia regionalne.|
|[operator!=](#op_neq)|Testuje dwa ustawienia lokalne pod kątem nierówności.|
|[operator( )](#op_call)|Porównuje dwa `basic_string` obiekty.|
|[operator==](#op_eq_eq)|Testuje dwa ustawienia lokalne pod kątem równości.|

### <a name="classes"></a>Klasy

|Klasa|Opis|
|-|-|
|[facet](#facet_class)|Klasa, która służy jako klasa bazowa dla wszystkich zestawów reguł ustawień regionalnych.|
|[`id`](#id_class)|Klasa składowej zapewnia unikatową identyfikację zestawu reguł używaną jako indeks do wyszukiwania zestawów reguł w ustawieniach regionalnych.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ustawień regionalnych

**Przestrzeń nazw:** std

## <a name="localecategory"></a><a name="category"></a>ustawienia regionalne::kategoria

Typ całkowitoliczbowy, który zawiera wartości masek bitowych dla oznaczenia standardowych rodzin zestawów reguł.

```cpp
typedef int category;
static const int collate = LC_COLLATE;
static const int ctype = LC_CTYPE;
static const int monetary = LC_MONETARY;
static const int numeric = LC_NUMERIC;
static const int time = LC_TIME;
static const int messages = LC_MESSAGES;
static const int all = LC_ALL;
static const int none = 0;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem typu **int,** który może reprezentować grupę różnych elementów typu maski bitowej lokalnego do ustawień regionalnych klasy lub może służyć do reprezentowania dowolnej z odpowiednich kategorii ustawień regionalnych C. Elementy są następujące:

- `collate`, odpowiadającej kategorii C LC_COLLATE

- `ctype`, odpowiadającej kategorii C LC_CTYPE

- `monetary`, odpowiadającej kategorii C LC_MONETARY

- `numeric`, odpowiadającej kategorii C LC_NUMERIC

- `time`, odpowiadającej kategorii C LC_TIME

- `messages`, odpowiadającej kategorii POSIX LC_MESSAGES

Dwie kolejne użyteczne wartości to:

- `none`, co odpowiada żadnej z kategorii C

- `all`, odpowiadającej unii C wszystkich kategorii LC_ALL

Można reprezentować dowolną grupę kategorii `OR` przy użyciu tych stałych, jak `monetary` `time`w &#124; .

## <a name="localeclassic"></a><a name="classic"></a>ustawienia regionalne::klasyczny

Funkcja statycznej składowej zwraca obiekt ustawień regionalnych, który reprezentuje klasyczne ustawienia regionalne C.

```cpp
static const locale& classic();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do ustawień regionalnych C.

### <a name="remarks"></a>Uwagi

Klasyczne ustawienia regionalne C to amerykańskie angielskie ustawienia regionalne ASCII w bibliotece Standard C. Jest to ustawienia regionalne, które są używane niejawnie w programach, które nie są umięcjonizowane.

### <a name="example"></a>Przykład

```cpp
// locale_classic.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "german" );
   locale loc2 = locale::global( loc1 );
   cout << "The name of the previous locale is: " << loc2.name( )
        << "." << endl;
   cout << "The name of the current locale is: " << loc1.name( )
        << "." << endl;

   if (loc2 == locale::classic( ) )
      cout << "The previous locale was classic." << endl;
   else
      cout << "The previous locale was not classic." << endl;

   if (loc1 == locale::classic( ) )
      cout << "The current locale is classic." << endl;
   else
      cout << "The current locale is not classic." << endl;
}
```

```Output
The name of the previous locale is: C.
The name of the current locale is: German_Germany.1252.
The previous locale was classic.
The current locale is not classic.
```

## <a name="localecombine"></a><a name="combine"></a>ustawienia regionalne::kombajn

Wstawia zestaw reguł z określonych ustawień regionalnych do docelowych ustawień regionalnych.

```cpp
template <class Facet>
locale combine(const locale& source_locale) const;
```

### <a name="parameters"></a>Parametry

*source_locale*\
Ustawienia regionalne zawierające aspekt, który ma zostać wstawiony do ustawień regionalnych obiektu docelowego.

### <a name="return-value"></a>Wartość zwracana

Funkcja elementu członkowskiego zwraca obiekt ustawień regionalnych, który `Facet` zastępuje lub dodaje do ** \*tego** aspekt wymieniony w *source_locale*.

### <a name="example"></a>Przykład

```cpp
// locale_combine.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main() {
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s; it comes before z in the German alphabet
   _TCHAR * s2 = _T("Das ist weizzz.");
   int result1 = use_facet<collate<_TCHAR> > ( loc ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc ) << result1 << endl;

   locale loc2 ( "C" );
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc2 )  << result2 << endl;

   locale loc3 = loc2.combine<collate<_TCHAR> > (loc);
   int result3 = use_facet<collate<_TCHAR> > ( loc3 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc3 ) << result3 << endl;
}
```

## <a name="facet-class"></a><a name="facet_class"></a>klasa facet

Klasa, która służy jako klasa bazowa dla wszystkich zestawów reguł ustawień regionalnych.

```cpp
class facet {
protected:
    explicit facet(size_t references = 0);
    virtual ~facet();
private:
    facet(const facet&) // not defined
    void operator=(const facet&) // not defined
};
```

### <a name="remarks"></a>Uwagi

Nie można skopiować ani przypisać `facet`obiektu klasy . Można konstruować i niszczyć `locale::facet` obiekty pochodzące z klasy, ale nie obiekty klasy podstawowej właściwej. Zazwyczaj można skonstruować `_Myfac` obiekt pochodzący `facet` z podczas `locale`konstruowania , jak w`locale loc(locale::classic(), new _Myfac);`

W takich przypadkach konstruktor dla `facet` klasy podstawowej powinien mieć argument zero *odwołań.* Gdy obiekt nie jest już potrzebny, jest usuwany, więc podać argument *odwołania niezerowe* tylko w tych rzadkich przypadkach, w których bierzesz odpowiedzialność za okres istnienia obiektu.

## <a name="localeglobal"></a><a name="global"></a>ustawienia regionalne::global

Resetuje domyślne ustawienia regionalne programu. To wywołanie ma wpływ na globalne ustawienia regionalne dla języka C i C++.

```cpp
static locale global(const locale& new_default_locale);
```

### <a name="parameters"></a>Parametry

*new_default_locale*\
Ustawienia regionalne, które mają być używane jako domyślne ustawienia regionalne przez program.

### <a name="return-value"></a>Wartość zwracana

Poprzednie ustawienia regionalne przed zresetowaniem domyślnych ustawień regionalnych.

### <a name="remarks"></a>Uwagi

Przy uruchamianiu programu globalne ustawienia regionalne są takie same jak klasyczne ustawienia regionalne. Funkcja `global()` wywołuje `setlocale( LC_ALL, loc.name. c_str())` ustanowienie pasujących ustawień regionalnych w bibliotece Standard C.

### <a name="example"></a>Przykład

```cpp
// locale_global.cpp
// compile by using: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( )
{
   locale loc ( "German_germany" );
   locale loc1;
   cout << "The initial locale is: " << loc1.name( ) << endl;
   locale loc2 = locale::global ( loc );
   locale loc3;
   cout << "The current locale is: " << loc3.name( ) << endl;
   cout << "The previous locale was: " << loc2.name( ) << endl;
}
```

```Output
The initial locale is: C
The current locale is: German_Germany.1252
The previous locale was: C
```

## <a name="id-class"></a><a name="id_class"></a>klasa id

Klasa składowej zapewnia unikatową identyfikację zestawu reguł używaną jako indeks do wyszukiwania zestawów reguł w ustawieniach regionalnych.

```cpp
class id
{
   protected:    id();
   private:      id(const id&)
   void operator=(const id&)  // not defined
};
```

### <a name="remarks"></a>Uwagi

Klasa elementu członkowskiego opisuje statyczny obiekt członkowski wymagany przez każdy unikatowy aspekt ustawień regionalnych. Nie można skopiować ani przypisać `id`obiektu klasy .

## <a name="localelocale"></a><a name="locale"></a>ustawienia regionalne::ustawienia regionalne

Tworzy ustawienia regionalne lub kopię ustawień regionalnych, lub kopię ustawień regionalnych, w której zestaw reguł lub kategoria zostały zastąpione przez zestaw reguł lub kategorię z innych ustawień regionalnych. Zawiera również destruktor.

```cpp
locale();

explicit locale(const char* locale_name, category new_category = all);
explicit locale(const string& locale_name);
locale(const locale& from_locale);
locale(const locale& from_locale, const locale& Other, category new_category);
locale(const locale& from_locale, const char* locale_name, category new_category);

template <class Facet>
locale(const locale& from_locale, const Facet* new_facet);

~locale();
```

### <a name="parameters"></a>Parametry

*locale_name*\
Nazwa ustawień regionalnych.

*from_locale*\
Ustawienia regionalne, które mają zostać skopiowane podczas konstruowania nowych ustawień regionalnych.

*Innych*\
Ustawienia regionalne, z których można wybrać kategorię.

*new_category*\
Kategoria, która ma zostać zastąpiona w skonstruowanych ustawieniach regionalnych.

*new_facet*\
Aspekt, który ma zostać zastąpiony w skonstruowanych ustawieniach regionalnych.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor inicjuje obiekt, aby dopasować globalne ustawienia regionalne. Konstruktory drugiego i trzeciego inicjują wszystkie kategorie ustawień regionalnych, aby zachowania były zgodne z nazwą ustawień regionalnych *locale_name*. Pozostałe konstruktory kopiują *from_locale*, z odnotowanymi wyjątkami:

`locale(const locale& from_locale, const locale& Other, category new_category);`

zastępuje *inne* te aspekty odpowiadające kategorii C, dla których C & *new_category* jest niezerowy.

`locale(const locale& from_locale, const char* locale_name, category new_category);`

`locale(const locale& from_locale, const string& locale_name, category new_category);`

zastępuje z `locale(locale_name, all)` tych aspektów odpowiadających kategorii *replace_category* dla `replace_category & new_category` których jest niezerowa.

`template<class Facet> locale(const locale& from_locale, Facet* new_facet);`

zastępuje w (lub dodaje do) *from_locale* *new_facet*aspektu , jeśli *new_facet* nie jest wskaźnik zerowy.

Jeśli nazwa ustawień regionalnych *locale_name* jest wskaźnikiem zerowym lub w inny sposób nieprawidłowa, funkcja zgłasza [runtime_error](../standard-library/runtime-error-class.md).

### <a name="example"></a>Przykład

```cpp
// locale_locale.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( ) {

   // Second constructor
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s, it comes before z in the German alphabet
   _TCHAR * s2 = _T("Das ist weizzz.");
   int result1 = use_facet<collate<_TCHAR> > ( loc ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc ) << result1 << endl;

   // The first (default) constructor
   locale loc2;
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc2 )  << result2 << endl;

   // Third constructor
   locale loc3 (loc2,loc, _M_COLLATE );
   int result3 = use_facet<collate<_TCHAR> > ( loc3 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc3 ) << result3 << endl;

   // Fourth constructor
   locale loc4 (loc2, "German_Germany", _M_COLLATE );
   int result4 = use_facet<collate<_TCHAR> > ( loc4 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc4 ) << result4 << endl;
}
```

## <a name="localename"></a><a name="name"></a>ustawienia regionalne::nazwa

Zwraca przechowywaną nazwę ustawień regionalnych.

```cpp
string name() const;
```

### <a name="return-value"></a>Wartość zwracana

Ciąg podający nazwę ustawień regionalnych.

### <a name="example"></a>Przykład

```cpp
// locale_name.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "german" );
   locale loc2 = locale::global( loc1 );
   cout << "The name of the previous locale is: "
        << loc2.name( ) << "." << endl;
   cout << "The name of the current locale is: "
        << loc1.name( ) << "." << endl;
}
```

```Output
The name of the previous locale is: C.
The name of the current locale is: German_Germany.1252.
```

## <a name="localeoperator"></a><a name="op_eq"></a>ustawienia regionalne::operator=

Przypisuje ustawienia regionalne.

```cpp
const locale& operator=(const locale& other) noexcept;
```

## <a name="localeoperator"></a><a name="op_neq"></a>ustawienia regionalne::operator!=

Testuje dwa ustawienia lokalne pod kątem nierówności.

```cpp
bool operator!=(const locale& right) const;
```

### <a name="parameters"></a>Parametry

*Prawo*\
Jeden z ustawień regionalnych, które mają być testowane pod kątem nierówności.

### <a name="return-value"></a>Wartość zwracana

Wartość logiczna, która jest **true,** jeśli ustawienia regionalne nie są kopie tego samego ustawienia regionalne. Jest **false,** jeśli ustawienia regionalne są kopie tego samego ustawienia regionalne.

### <a name="remarks"></a>Uwagi

Dwa ustawienia regionalne są równe, jeśli są one takie same ustawienia regionalne, jeśli jeden jest kopią innych lub jeśli mają identyczne nazwy.

### <a name="example"></a>Przykład

```cpp
// locale_op_ne.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "German_Germany" );
   locale loc2( "German_Germany" );
   locale loc3( "English" );

   if ( loc1 != loc2 )
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc2 (" << loc2.name( ) << ") are not equal." << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc2 (" << loc2.name( ) << ") are equal." << endl;

   if ( loc1 != loc3 )
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc3 (" << loc3.name( ) << ") are not equal." << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc3 (" << loc3.name( ) << ") are equal." << endl;
}
```

```Output
locales loc1 (German_Germany.1252) and
loc2 (German_Germany.1252) are equal.
locales loc1 (German_Germany.1252) and
loc3 (English_United States.1252) are not equal.
```

## <a name="localeoperator"></a><a name="op_call"></a>ustawienia regionalne::operator()

Porównuje dwa `basic_string` obiekty.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator()(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right) const;
```

### <a name="parameters"></a>Parametry

*Lewej*\
Lewy ciąg.

*Prawo*\
Prawy ciąg.

### <a name="return-value"></a>Wartość zwracana

Funkcja elementu członkowskiego zwraca:

- -1, jeśli pierwsza sekwencja porównuje mniej niż druga sekwencja.

- +1, jeśli druga sekwencja porównuje mniej niż pierwsza sekwencja.

- 0, jeśli sekwencje są równoważne.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego skutecznie wykonuje:

```cpp
const collate<CharType>& fac = use_fac<collate<CharType>>(*this);

return (fac.compare(left.begin(), left.end(), right.begin(), right.end()) < 0);
```

Oznacza to, że można użyć obiektu ustawień regionalnych jako obiektu funkcyjnego.

### <a name="example"></a>Przykład

```cpp
// locale_op_compare.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

int main( )
{
   using namespace std;
   wchar_t *sa = L"ztesting";
   wchar_t *sb = L"\0x00DFtesting";
   basic_string<wchar_t> a( sa );
   basic_string<wchar_t> b( sb );

   locale loc( "German_Germany" );
   cout << loc( a,b ) << endl;

   const collate<wchar_t>& fac = use_facet<collate<wchar_t> >( loc );
   cout << ( fac.compare( sa, sa + a.length( ),
       sb, sb + b.length( ) ) < 0) << endl;
}
```

```Output
0
0
```

## <a name="localeoperator"></a><a name="op_eq_eq"></a>ustawienia regionalne::operator==

Testuje dwa ustawienia lokalne pod kątem równości.

```cpp
bool operator==(const locale& right) const;
```

### <a name="parameters"></a>Parametry

*Prawo*\
Jeden z ustawień regionalnych, które mają być testowane pod kątem równości.

### <a name="return-value"></a>Wartość zwracana

Wartość logiczna, która jest **true,** jeśli ustawienia regionalne są kopie tego samego ustawienia regionalne. Jest **false,** jeśli ustawienia regionalne nie są kopie tego samego ustawienia regionalne.

### <a name="remarks"></a>Uwagi

Dwa ustawienia regionalne są równe, jeśli są one takie same ustawienia regionalne, jeśli jeden jest kopią innych lub jeśli mają identyczne nazwy.

### <a name="example"></a>Przykład

```cpp
// locale_op_eq.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "German_Germany" );
   locale loc2( "German_Germany" );
   locale loc3( "English" );

   if ( loc1 == loc2 )
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc2 (" << loc2.name( ) << ") are equal."
      << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc2 (" << loc2.name( ) << ") are not equal."
      << endl;

   if ( loc1 == loc3 )
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc3 (" << loc3.name( ) << ") are equal."
      << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc3 (" << loc3.name( ) << ") are not equal."
      << endl;
}
```

```Output
locales loc1 (German_Germany.1252)
and loc2 (German_Germany.1252) are equal.
locales loc1 (German_Germany.1252)
and loc3 (English_United States.1252) are not equal.
```

## <a name="see-also"></a>Zobacz też

[\<>ustawień regionalnych](../standard-library/locale.md)\
[Strony kodowe](../c-runtime-library/code-pages.md)\
[Nazwy ustawień regionalnych, języki i ciągi kraju/regionu](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
