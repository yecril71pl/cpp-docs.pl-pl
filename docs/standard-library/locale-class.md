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
ms.openlocfilehash: a11f5bf7e8c280da3ba2cae82cf355a3b28c0577
ms.sourcegitcommit: 4b0928a1a497648d0d327579c8262f25ed20d02e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72890160"
---
# <a name="locale-class"></a>locale — Klasa

Klasa opisująca obiekt ustawień regionalnych, który hermetyzuje informacje specyficzne dla kultury jako zbiór zestawu reguł, które wspólnie definiują specyficzne środowisko zlokalizowane.

## <a name="syntax"></a>Składnia

```cpp
class locale;
```

## <a name="remarks"></a>Uwagi

Zestaw reguł jest wskaźnikiem do obiektu klasy pochodzącej od [aspektu](#facet_class) klasy, który ma obiekt publiczny formularza:

```cpp
static locale::id id;
```

Można zdefiniować nieograniczony zbiór tych zestawów reguł. Można także skonstruować obiekt ustawień regionalnych, który wyznacza dowolną liczbę zestawów reguł.

Wstępnie zdefiniowane grupy tych aspektów reprezentują [Kategorie ustawień regionalnych](#category) tradycyjnie zarządzane w standardowej bibliotece C przez funkcję `setlocale`.

Kategoria `collate` (LC_COLLATE) obejmuje zestawy reguł:

```cpp
collate<char>
collate<wchar_t>
```

Kategoria `ctype` (LC_CTYPE) obejmuje zestawy reguł:

```cpp
ctype<char>
ctype<wchar_t>
codecvt<char, char, mbstate_t>
codecvt<wchar_t, char, mbstate_t>
codecvt<char16_t, char, mbstate_t>
codecvt<char32_t, char, mbstate_t>
```

Kategoria `monetary` (LC_MONETARY) obejmuje zestawy reguł:

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

Kategoria `numeric` (LC_NUMERIC) obejmuje zestawy reguł:

```cpp
num_get<char, istreambuf_iterator<char>>
num_get<wchar_t, istreambuf_iterator<wchar_t>>
num_put<char, ostreambuf_iterator<char>>
num_put<wchar_t, ostreambuf_iterator<wchar_t>>
numpunct<char>
numpunct<wchar_t>
```

Kategoria `time` (LC_TIME) obejmuje zestawy reguł:

```cpp
time_get<char, istreambuf_iterator<char>>
time_get<wchar_t, istreambuf_iterator<wchar_t>>
time_put<char, ostreambuf_iterator<char>>
time_put<wchar_t, ostreambuf_iterator<wchar_t>>
```

Kategoria `messages` (LC_MESSAGES) obejmuje zestawy reguł:

```cpp
messages<char>
messages<wchar_t>
```

(Ostatnia kategoria jest wymagana przez Posix, ale nie przez standard C).

Niektóre z tych wstępnie zdefiniowanych zestawów są używane przez klasy `iostream` do sterowania konwersją wartości numerycznych do i z sekwencji tekstu.

Obiekt ustawień regionalnych klasy również przechowuje nazwę ustawień regionalnych jako obiekt [ciągu](../standard-library/string-typedefs.md#string)klasy. Użycie nieprawidłowej nazwy ustawień regionalnych do skonstruowania zestawu reguł ustawień regionalnych lub obiektu ustawień regionalnych zgłasza obiekt klasy [runtime_error](../standard-library/runtime-error-class.md). Nazwa przechowywanych ustawień regionalnych jest `"*"`, jeśli obiekt locale nie może mieć pewności, że ustawienia regionalne w stylu języka C odpowiadają dokładnie na te reprezentowane przez obiekt. W przeciwnym razie można określić pasujące ustawienia regionalne w standardowej bibliotece C dla niektórych `locale_object`obiektów ustawień regionalnych, wywołując `setlocale(LC_ALL , locale_object.``().c_str())`[nazwy](#name) .

W tej implementacji można również wywołać funkcję statycznego elementu członkowskiego:

```cpp
static locale empty();
```

do konstruowania obiektu ustawień regionalnych, który ma nie zestawu reguł. Jest to również przejrzyste ustawienie regionalne. Jeśli funkcje szablonu [has_facet](../standard-library/locale-functions.md#has_facet) i [use_facet](../standard-library/locale-functions.md#use_facet) nie mogą znaleźć żądanego zestawu reguł w przezroczystych ustawieniach regionalnych, sprawdzają najpierw globalne ustawienia regionalne, a następnie, jeśli są przezroczyste, klasyczne ustawienia regionalne. Można więc napisać:

```cpp
cout.imbue(locale::empty());
```

Kolejne wstawienia do [`cout`](../standard-library/iostream.md#cout) są korygowane według bieżącego stanu globalnych ustawień regionalnych. Można nawet napisać:

```cpp
locale loc(locale::empty(),
    locale::classic(),
    locale::numeric);

cout.imbue(loc);
```

Reguły formatowania liczb dla kolejnych wstawek `cout` pozostają takie same jak w ustawieniach regionalnych języka C, nawet jeśli globalne ustawienia regionalne dostarczają zmiany reguł do wstawiania dat i kwot pieniężnych.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[ustawienie](#locale)|Tworzy ustawienia regionalne lub kopię ustawień regionalnych, lub kopię ustawień regionalnych, w której zestaw reguł lub kategoria zostały zastąpione przez zestaw reguł lub kategorię z innych ustawień regionalnych.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[kategorii](#category)|Typ całkowitoliczbowy, który zawiera wartości masek bitowych dla oznaczenia standardowych rodzin zestawów reguł.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[żądany](#combine)|Wstawia zestaw reguł z określonych ustawień regionalnych do docelowych ustawień regionalnych.|
|[Nazwij](#name)|Zwraca przechowywaną nazwę ustawień regionalnych.|

### <a name="static-functions"></a>Funkcje statyczne

|||
|-|-|
|[motyw](#classic)|Funkcja statycznej składowej zwraca obiekt ustawień regionalnych, który reprezentuje klasyczne ustawienia regionalne C.|
|[global](#global)|Resetuje domyślne ustawienia lokalne dla programu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator =](#op_eq)|Przypisuje ustawienia regionalne.|
|[operator!=](#op_neq)|Testuje dwa ustawienia lokalne pod kątem nierówności.|
|[operator ()](#op_call)|Porównuje dwa obiekty `basic_string`.|
|[operator = =](#op_eq_eq)|Testuje dwa ustawienia lokalne pod kątem równości.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[aspekt](#facet_class)|Klasa, która służy jako klasa bazowa dla wszystkich zestawów reguł ustawień regionalnych.|
|[`id`](#id_class)|Klasa składowej zapewnia unikatową identyfikację zestawu reguł używaną jako indeks do wyszukiwania zestawów reguł w ustawieniach regionalnych.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<locale >

**Przestrzeń nazw:** std

## <a name="category"></a>locale:: Category

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

Typ jest synonimem dla typu **int** , który może reprezentować grupę odrębnych elementów typu maski bitowej do ustawień regionalnych klasy lub może służyć do reprezentowania dowolnej z odpowiednich kategorii języka C. Elementy to:

- `collate`, odpowiadające kategorii C LC_COLLATE

- `ctype`, odpowiadające kategorii C LC_CTYPE

- `monetary`, odpowiadające kategorii C LC_MONETARY

- `numeric`, odpowiadające kategorii C LC_NUMERIC

- `time`, odpowiadające kategorii C LC_TIME

- `messages`, odpowiadające kategorii POSIX LC_MESSAGES

Dwie bardziej przydatne wartości to:

- `none`, odpowiadający żadnej kategorii C

- `all`, odpowiadające Unii C wszystkich kategorii LC_ALL

Można reprezentować dowolną grupę kategorii za pomocą `OR` z tymi stałymi, jak w `monetary` &#124;`time`.

## <a name="classic"></a>locale:: klasyczny

Funkcja statycznej składowej zwraca obiekt ustawień regionalnych, który reprezentuje klasyczne ustawienia regionalne C.

```cpp
static const locale& classic();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do ustawień regionalnych języka C.

### <a name="remarks"></a>Uwagi

Klasyczne ustawienia regionalne języka C to amerykańskie ustawienia regionalne ASCII w standardowej bibliotece C. Są to ustawienia regionalne używane niejawnie w programach, które nie są międzynarodowe.

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

## <a name="combine"></a>locale:: łączenie

Wstawia zestaw reguł z określonych ustawień regionalnych do docelowych ustawień regionalnych.

```cpp
template <class Facet>
locale combine(const locale& source_locale) const;
```

### <a name="parameters"></a>Parametry

*source_locale*\
Ustawienia regionalne zawierające zestaw reguł, który ma zostać wstawiony do docelowego ustawienia regionalnego.

### <a name="return-value"></a>Wartość zwracana

Funkcja członkowska zwraca obiekt ustawień regionalnych, który zastępuje lub dodaje do **\*ten** aspekt `Facet` wymieniony w *source_locale*.

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

## <a name="facet_class"></a>facet — Klasa

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

Nie można skopiować ani przypisać obiektu klasy `facet`. Można tworzyć i niszczyć obiekty pochodne od klasy `locale::facet` ale nie obiekty klasy podstawowej są odpowiednie. Zazwyczaj konstruowa się obiekt `_Myfac` pochodzący z `facet` podczas konstruowania `locale`, jak w `locale loc(locale::classic(), new _Myfac);`

W takich przypadkach Konstruktor dla klasy bazowej `facet` powinien mieć argument *odwołania* zerowe. Gdy obiekt nie jest już wymagany, jest usuwany, więc podajesz argument *odwołań* niezerowych tylko w tych rzadkich przypadkach, gdy ponosisz odpowiedzialność za okres istnienia obiektu.

## <a name="global"></a>locale:: Global

Resetuje domyślne ustawienia regionalne dla programu. To wywołanie ma wpływ na globalne ustawienia regionalne dla języków C++C i.

```cpp
static locale global(const locale& new_default_locale);
```

### <a name="parameters"></a>Parametry

*new_default_locale*\
Ustawienia regionalne, które mają być używane jako domyślne ustawienia regionalne programu.

### <a name="return-value"></a>Wartość zwracana

Poprzednie ustawienia regionalne przed zresetowaniem domyślnych ustawień regionalnych.

### <a name="remarks"></a>Uwagi

W trakcie uruchamiania programu globalne ustawienia regionalne są takie same jak klasyczne ustawienia regionalne. Funkcja `global()` wywołuje `setlocale( LC_ALL, loc.name. c_str())`, aby określić pasujące ustawienia regionalne w standardowej bibliotece C.

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

## <a name="id_class"></a>ID — Klasa

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

Klasa członkowska opisuje statyczny Obiekt członkowski wymagany przez każdy unikatowy zestaw reguł ustawień regionalnych. Nie można skopiować ani przypisać obiektu klasy `id`.

## <a name="locale"></a>locale:: locale

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

*Inne* \
Ustawienia regionalne, z których należy wybrać kategorię.

*new_category*\
Kategoria, która ma zostać zastąpiona przez skonstruowane ustawienia regionalne.

*new_facet*\
Zestaw reguł, który ma zostać zastąpiony przez skonstruowane ustawienia regionalne.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje obiekt, aby odpowiadał globalnym ustawieniom regionalnym. Drugi i trzeci konstruktorzy inicjują wszystkie kategorie ustawień regionalnych, aby mieć zachowanie spójne z nazwą ustawień regionalnych *locale_name*. Pozostałe konstruktory kopiują *from_locale*z wyjątkami:

`locale(const locale& from_locale, const locale& Other, category new_category);`

zastępuje z *innych* aspektów, które odpowiadają kategorii c, dla których & *new_category* jest różna od zera.

`locale(const locale& from_locale, const char* locale_name, category new_category);`

`locale(const locale& from_locale, const string& locale_name, category new_category);`

zastępuje `locale(locale_name, all)` tych aspektów odpowiadających kategorii *replace_category* , dla których `replace_category & new_category` jest różna od zera.

`template<class Facet> locale(const locale& from_locale, Facet* new_facet);`

zamienia w (lub dodaje do) *from_locale* aspekt *new_facet*, jeśli *new_facet* nie jest wskaźnikiem o wartości null.

Jeśli nazwa ustawień regionalnych *locale_name* jest wskaźnikiem typu null lub jest nieprawidłowa, funkcja zgłasza [runtime_error](../standard-library/runtime-error-class.md).

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

## <a name="name"></a>locale:: Name

Zwraca przechowywaną nazwę ustawień regionalnych.

```cpp
string name() const;
```

### <a name="return-value"></a>Wartość zwracana

Ciąg określający nazwę ustawień regionalnych.

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

## <a name="op_eq"></a>locale:: operator =

Przypisuje ustawienia regionalne.

```cpp
const locale& operator=(const locale& other) noexcept;
```

## <a name="op_neq"></a>locale:: operator! =

Testuje dwa ustawienia lokalne pod kątem nierówności.

```cpp
bool operator!=(const locale& right) const;
```

### <a name="parameters"></a>Parametry

*prawa* \
Jedno z wartości lokalnych do przetestowania pod kątem nierówności.

### <a name="return-value"></a>Wartość zwracana

Wartość logiczna **prawda** , jeśli ustawienia regionalne nie są kopiami tych samych ustawień regionalnych. Jest to **wartość FAŁSZ** , jeśli ustawienia regionalne są kopiami tych samych ustawień regionalnych.

### <a name="remarks"></a>Uwagi

Dwa ustawienia lokalne są równe, jeśli są one tymi samymi ustawieniami regionalnymi, jeśli jedna z nich jest kopią drugiego lub jeśli mają identyczne nazwy.

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

## <a name="op_call"></a>locale:: operator ()

Porównuje dwa obiekty `basic_string`.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator()(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right) const;
```

### <a name="parameters"></a>Parametry

\ *lewo*
Lewy ciąg.

*prawa* \
Prawidłowy ciąg.

### <a name="return-value"></a>Wartość zwracana

Funkcja członkowska zwraca:

- -1, jeśli pierwsza sekwencja porównuje mniej niż drugą sekwencję.

- \+ 1, jeśli druga sekwencja porównuje mniej niż pierwszą sekwencję.

- 0, jeśli sekwencje są równoważne.

### <a name="remarks"></a>Uwagi

Funkcja członkowska skutecznie wykonuje:

```cpp
const collate<CharType>& fac = use_fac<collate<CharType>>(*this);

return (fac.compare(left.begin(), left.end(), right.begin(), right.end()) < 0);
```

Oznacza to, że można użyć obiektu locale jako obiektu funkcji.

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

## <a name="op_eq_eq"></a>locale:: operator = =

Testuje dwa ustawienia lokalne pod kątem równości.

```cpp
bool operator==(const locale& right) const;
```

### <a name="parameters"></a>Parametry

*prawa* \
Jeden z ustawień regionalnych, które mają być testowane pod kątem równości.

### <a name="return-value"></a>Wartość zwracana

Wartość logiczna **prawda** , jeśli ustawienia regionalne są kopiami tych samych ustawień regionalnych. Ma **wartość FAŁSZ** , jeśli ustawienia regionalne nie są kopiami tych samych ustawień regionalnych.

### <a name="remarks"></a>Uwagi

Dwa ustawienia lokalne są równe, jeśli są one tymi samymi ustawieniami regionalnymi, jeśli jedna z nich jest kopią drugiego lub jeśli mają identyczne nazwy.

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

[\<locale >](../standard-library/locale.md) \
[Strony kodowe](../c-runtime-library/code-pages.md) \
[Nazwy lokalne, Języki i ciągi kraju/regionu](../c-runtime-library/locale-names-languages-and-country-region-strings.md) \
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
