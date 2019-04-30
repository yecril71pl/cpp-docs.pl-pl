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
ms.openlocfilehash: a1f5ace58af427645a0ad4eb8706506cc52ab08c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413180"
---
# <a name="locale-class"></a>locale — Klasa

Klasa opisująca obiekt ustawień regionalnych, który hermetyzuje informacje specyficzne dla kultury jako zbiór zestawu reguł, które wspólnie definiują specyficzne środowisko zlokalizowane.

## <a name="syntax"></a>Składnia

```cpp
class locale;
```

## <a name="remarks"></a>Uwagi

Zestaw reguł jest wskaźnikiem do obiektu klasy pochodzącej od klasy [aspekt](#facet_class) ma obiekt publiczny w postaci:

```cpp
static locale::id id;
```

Można zdefiniować nieograniczony zbiór tych zestawów reguł. Można także skonstruować obiekt ustawień regionalnych, który wyznacza dowolną liczbę zestawów reguł.

Wstępnie zdefiniowane grupy tych zestawów reguł reprezentują [kategorie ustawień regionalnych](#category) tradycyjnie zarządzanych w standardowej bibliotece C przez funkcję `setlocale`.

Kategoria collate (LC_COLLATE) obejmuje zestawy reguł:

```cpp
collate<char>
collate<wchar_t>
```

Kategoria ctype (LC_CTYPE) obejmuje zestawy reguł:

```cpp
ctype<char>
ctype<wchar_t>
codecvt<char, char, mbstate_t>
codecvt<wchar_t, char, mbstate_t>
codecvt<char16_t, char, mbstate_t>
codecvt<char32_t, char, mbstate_t>
```

Kategoria monetary (LC_MONETARY) obejmuje zestawy reguł:

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

Kategoria numeric (LC_NUMERIC) obejmuje zestawy reguł:

```cpp
num_get<char, istreambuf_iterator<char>>
num_get<wchar_t, istreambuf_iterator<wchar_t>>
num_put<char, ostreambuf_iterator<char>>
num_put<wchar_t, ostreambuf_iterator<wchar_t>>
numpunct<char>
numpunct<wchar_t>
```

Kategoria time (LC_TIME) obejmuje zestawy reguł:

```cpp
time_get<char, istreambuf_iterator<char>>
time_get<wchar_t, istreambuf_iterator<wchar_t>>
time_put<char, ostreambuf_iterator<char>>
time_put<wchar_t, ostreambuf_iterator<wchar_t>>
```

Kategoria messages (LC_MESSAGES) obejmuje zestawy reguł:

```cpp
messages<char>
messages<wchar_t>
```

(Ostatnia kategoria jest wymagana przez Posix, ale nie przez standard C).

Niektóre z tych wstępnie zdefiniowanych zestawów reguł są używane przez klasy iostreams w celu kontroli konwersji wartości numerycznych do i z sekwencji tekstowych.

Obiekt klasy Locale również przechowuje nazwy ustawień regionalnych jako obiekt klasy [ciąg](../standard-library/string-typedefs.md#string). Przy użyciu nieprawidłowej nazwy ustawień regionalnych do skonstruowania zestaw reguł ustawień regionalnych lub obiektu ustawień regionalnych zgłasza obiekt klasy [runtime_error](../standard-library/runtime-error-class.md). Jest przechowywana nazwa ustawień regionalnych `"*"` Jeśli obiekt ustawień regionalnych nie może mieć pewności, że ustawienia regionalne stylu C odpowiadają dokładnie, reprezentowane przez obiekt. W przeciwnym razie możesz ustanowić pasujące ustawienia regionalne w ramach standardowej biblioteki C dla obiektu ustawień regionalnych `Loc`, wywołując `setlocale`(LC_ALL `,` `Loc`. [Nazwa](#name)`().c_str()`).

W tej implementacji można również wywołać funkcję statycznego elementu członkowskiego:

```cpp
static locale empty();
```

do konstruowania obiektu ustawień regionalnych, który ma nie zestawu reguł. Warto również przezroczyste ustawienia regionalne; Jeśli funkcje szablonu [has_facet](../standard-library/locale-functions.md#has_facet) i [use_facet](../standard-library/locale-functions.md#use_facet) nie można odnaleźć żądanego zestawu reguł w przezroczystych ustawieniach regionalnych odwołują się do najpierw globalne ustawienia regionalne a następnie, jeśli są przezroczyste, klasyczne ustawienia regionalne. W ten sposób można napisać:

```cpp
cout.imbue(locale::empty());
```

Kolejne wstawienia do [cout](../standard-library/iostream.md#cout) są przenoszone przez przez bieżącego stanu globalnych ustawień regionalnych. Można nawet napisać:

```cpp
locale loc(locale::empty(),
    locale::classic(),
    locale::numeric);

cout.imbue(loc);
```

Reguły formatowania numerycznego dla kolejnych wstawień do `cout` pozostaje taki sam jak ustawienia regionalne C, nawet jeśli globalne ustawienia regionalne dostarczają zmieniających zasad wstawiania dat i kwot pieniężnych.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Ustawienia regionalne](#locale)|Tworzy ustawienia regionalne lub kopię ustawień regionalnych, lub kopię ustawień regionalnych, w której zestaw reguł lub kategoria zostały zastąpione przez zestaw reguł lub kategorię z innych ustawień regionalnych.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[category](#category)|Typ całkowitoliczbowy, który zawiera wartości masek bitowych dla oznaczenia standardowych rodzin zestawów reguł.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[combine](#combine)|Wstawia zestaw reguł z określonych ustawień regionalnych do docelowych ustawień regionalnych.|
|[Nazwa](#name)|Zwraca przechowywaną nazwę ustawień regionalnych.|

### <a name="static-functions"></a>Funkcje statyczne

|||
|-|-|
|[Model Klasyczny](#classic)|Funkcja statycznej składowej zwraca obiekt ustawień regionalnych, który reprezentuje klasyczne ustawienia regionalne C.|
|[global](#global)|Resetuje domyślne ustawienia lokalne dla programu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator!=](#op_neq)|Testuje dwa ustawienia lokalne pod kątem nierówności.|
|[operator( )](#op_call)|Porównuje dwa `basic_string` obiektów.|
|[operator==](#op_eq_eq)|Testuje dwa ustawienia lokalne pod kątem równości.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[aspekt](#facet_class)|Klasa, która służy jako klasa bazowa dla wszystkich zestawów reguł ustawień regionalnych.|
|[id](#id_class)|Klasa składowej zapewnia unikatową identyfikację zestawu reguł używaną jako indeks do wyszukiwania zestawów reguł w ustawieniach regionalnych.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** standardowe

## <a name="category"></a>  Locale::category

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

Typ jest synonimem dla **int** typ, który może reprezentować grupę odrębnych elementach maską bitów wpisz lokalny dla klasy locale lub może służyć do reprezentowania znajdujących się w odpowiedniej kategorii C w ustawieniach regionalnych. Dostępne są następujące elementy:

- `collate`, odpowiadające kategorii C LC_COLLATE

- `ctype`, odpowiadające kategorii C LC_CTYPE

- `monetary`, odpowiadające kategorii C LC_MONETARY

- `numeric`, odpowiadające kategorii C LC_NUMERIC

- `time`, odpowiadające kategorii C LC_TIME

- `messages`, odpowiadające kategorii Posix LC_MESSAGES

Ponadto dwa użyteczne wartości są następujące:

- `none`, odpowiadające na Brak kategorii C

- `all`, odpowiadający C sumę wszystkich kategorii LC_ALL

Dowolne grupy kategorii mogą być reprezentowane za pomocą `OR` za pomocą tych stałych, jak `monetary` &#124; `time`.

## <a name="classic"></a>  Locale::Classic

Funkcja statycznej składowej zwraca obiekt ustawień regionalnych, który reprezentuje klasyczne ustawienia regionalne C.

```cpp
static const locale& classic();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do ustawienia regionalne C.

### <a name="remarks"></a>Uwagi

Klasyczne ustawienia regionalne c. jest Stanów Zjednoczonych Ustawienia regionalne angielskiej ASCII w ramach standardowej biblioteki C, która niejawnie używane w programach, które nie są międzynarodowych.

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

## <a name="combine"></a>  Locale::Combine

Wstawia zestaw reguł z określonych ustawień regionalnych do docelowych ustawień regionalnych.

```cpp
template <class Facet>
locale combine(const locale& Loc) const;
```

### <a name="parameters"></a>Parametry

*Lokalizacja*<br/>
Ustawienia regionalne, zawierająca zestaw reguł do wstawienia do docelowych ustawień regionalnych.

### <a name="return-value"></a>Wartość zwracana

Funkcja elementu członkowskiego zwraca obiekt ustawień regionalnych, który zastępuje lub dodaje do  **\*to** aspekt `Facet` na liście *Loc*.

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

## <a name="facet_class"></a>  facet — klasa

Klasa, która służy jako klasa bazowa dla wszystkich zestawów reguł ustawień regionalnych.

```cpp
class facet {
protected:
    explicit facet(size_t _Refs = 0);
   virtual ~facet();
private:
   facet(const facet&)
   // not defined void operator=(const facet&)
     // not defined
};
```

### <a name="remarks"></a>Uwagi

Należy pamiętać, nie można kopiować ani przypisać obiekt klasy zestawu reguł. Można skonstruować i niszczy obiektów pochodzących od klasy `locale::facet` , ale nie obiekty odpowiednie klasy bazowej. Zazwyczaj utworzenia obiektu `_Myfac` pochodzące z zestawu reguł, podczas tworzenia ustawień regionalnych, podobnie jak w **localeloc**( `locale::classic`(), **nowe**`_Myfac`);

W takich przypadkach konstruktora dla klasy bazowej aspekt powinien mieć wartość zero `_Refs` argumentu. Gdy obiekt nie jest już potrzebny, został usunięty. W związku z tym, podaj wartość różną od zera _ *system plików Refs* argument tylko w tych rzadkich przypadkach, w którym użytkownik ponosi odpowiedzialność za okres istnienia obiektu.

## <a name="global"></a>  Locale::Global

Resetuje domyślne ustawienia regionalne dla programu. Dotyczy to globalnych ustawień regionalnych dla C i C++.

```cpp
static locale global(const locale& Loc);
```

### <a name="parameters"></a>Parametry

*Lokalizacja*<br/>
Ustawienia regionalne do użycia jako domyślnych ustawień regionalnych przez program.

### <a name="return-value"></a>Wartość zwracana

Poprzednie ustawienia regionalne, zanim został zresetowany domyślnych ustawień regionalnych.

### <a name="remarks"></a>Uwagi

W momencie uruchamiania programu globalnych ustawień regionalnych jest taka sama jak klasyczne ustawienia regionalne. `global()` Wywołaniach funkcji `setlocale( LC_ALL, loc.name. c_str())` nawiązać pasujące ustawienia regionalne biblioteki standardowej C.

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

## <a name="id_class"></a>  ID — klasa

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

Klasa elementu członkowskiego opisuje wymagany przez każdy reguł ustawień regionalnych unikatowy obiekt statyczny element członkowski. Należy pamiętać, że nie można kopiować ani przypisać obiekt klasy `id`.

## <a name="locale"></a>  Locale::Locale

Tworzy ustawienia regionalne lub kopię ustawień regionalnych, lub kopię ustawień regionalnych, w której zestaw reguł lub kategoria zostały zastąpione przez zestaw reguł lub kategorię z innych ustawień regionalnych.

```cpp
locale();

explicit locale(const char* Locname, category Cat = all);
explicit locale(const string& Locname);
locale( const locale& Loc);
locale(const locale& Loc, const locale& Other, category Cat);
locale(const locale& Loc, const char* Locname, category Cat);

template <class Facet>
locale(const locale& Loc, const Facet* Fac);
```

### <a name="parameters"></a>Parametry

*Locname*<br/>
Nazwa ustawień regionalnych.

*Lokalizacja*<br/>
Ustawienia regionalne, który ma zostać skopiowane do tworzenia nowych ustawień regionalnych.

*Inne*<br/>
Ustawienia regionalne, z którego można wybrać kategorię.

*CAT*<br/>
Kategoria do podstawienia do skonstruowanego ustawień regionalnych.

*FAC*<br/>
Zestaw reguł do podstawienia do skonstruowanego ustawień regionalnych.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje obiekt do dopasowania globalnych ustawień regionalnych. Drugie i trzecie konstruktory zainicjowania wszystkich kategorii ustawień regionalnych na zachowanie zgodne z nazwy ustawień regionalnych *Locname*. Pozostałe konstruktory kopiują *Loc*, z wyjątkiem wymienionych:

`locale(const locale& Loc, const locale& Other, category Cat);`

zastępuje z *innych* te aspekty odpowiadający kategorii C, dla których C & *Cat* jest różna od zera.

`locale(const locale& Loc, const char* Locname, category Cat);`

`locale(const locale& Loc, const string& Locname, category Cat);`

zastępuje z `locale(Locname, _All)` te aspekty odpowiadający kategorii C, dla których C & *Cat* jest różna od zera.

`template<class Facet> locale(const locale& Loc, Facet* Fac);`

zastępuje (lub dodaje do) *Loc* aspekt *Fac*, jeśli *Fac* nie jest wskaźnikiem typu null.

Jeśli nazwy ustawień regionalnych *Locname* jest wskaźnikiem typu null lub nieprawidłowa, funkcja zgłasza [runtime_error](../standard-library/runtime-error-class.md).

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

## <a name="name"></a>  Locale::Name

Zwraca przechowywaną nazwę ustawień regionalnych.

```cpp
string name() const;
```

### <a name="return-value"></a>Wartość zwracana

Ciąg, podając nazwę ustawień regionalnych.

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

## <a name="op_neq"></a>  Locale::operator! =

Testuje dwa ustawienia lokalne pod kątem nierówności.

```cpp
bool operator!=(const locale& right) const;
```

### <a name="parameters"></a>Parametry

*right*<br/>
Jedno z ustawień regionalnych, który ma zostać przetestowana pod kątem nierówności.

### <a name="return-value"></a>Wartość zwracana

Wartość logiczna, która jest **true** Jeśli ustawienia regionalne nie są kopie tych samych ustawień regionalnych; **false** Jeśli ustawienia regionalne są kopie tych samych ustawień regionalnych.

### <a name="remarks"></a>Uwagi

Dwa ustawienia lokalne są takie same, jeśli są one tych samych ustawień regionalnych, jeśli jeden jest kopią innego lub jeśli mają identyczne nazwy.

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

## <a name="op_call"></a>  Locale:: operator()

Porównuje dwa `basic_string` obiektów.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator()(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right) const;
```

### <a name="parameters"></a>Parametry

*left*<br/>
Ciąg, który po lewej stronie.

*right*<br/>
Ciąg, do prawej.

### <a name="return-value"></a>Wartość zwracana

Funkcja elementu członkowskiego zwraca:

- -1, jeśli pierwszej sekwencji porównuje mniejsza od drugiej sekwencji.

- + 1, jeśli drugiej sekwencji porównuje mniejszą od pierwszej sekwencji.

- 0, jeśli sekwencji, które są równoważne.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego skutecznie wykonuje:

```cpp
const collate<CharType>& fac = use_fac<collate<CharType>>(*this);

return (fac.compare(left.begin(), left.end(), right.begin(), right.end()) < 0);
```

W związku z tym można użyć obiektu ustawień regionalnych jako obiekt funkcyjny.

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

## <a name="op_eq_eq"></a>  Locale::operator ==

Testuje dwa ustawienia lokalne pod kątem równości.

```cpp
bool operator==(const locale& right) const;
```

### <a name="parameters"></a>Parametry

*right*<br/>
Jedno z ustawień regionalnych, który ma zostać przetestowana pod kątem równości.

### <a name="return-value"></a>Wartość zwracana

Wartość logiczna, która jest **true** Jeśli ustawienia regionalne są kopie tych samych ustawień regionalnych; **false** Jeśli ustawienia regionalne nie są kopie tych samych ustawień regionalnych.

### <a name="remarks"></a>Uwagi

Dwa ustawienia lokalne są takie same, jeśli są one tych samych ustawień regionalnych, jeśli jeden jest kopią innego lub jeśli mają identyczne nazwy.

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

## <a name="see-also"></a>Zobacz także

[\<locale>](../standard-library/locale.md)<br/>
[Strony kodowe](../c-runtime-library/code-pages.md)<br/>
[Nazwy lokalne, języki i ciągi Kraj/Region](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
