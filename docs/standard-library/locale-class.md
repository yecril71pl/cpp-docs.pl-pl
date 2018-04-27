---
title: Locale — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 28
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8599eabb4144a589206ae38ab3be29a1670f9f20
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="locale-class"></a>locale — Klasa

Klasa opisująca obiekt ustawień regionalnych, który hermetyzuje informacje specyficzne dla kultury jako zbiór zestawu reguł, które wspólnie definiują specyficzne środowisko zlokalizowane.

## <a name="syntax"></a>Składnia

```cpp
class locale;
```

## <a name="remarks"></a>Uwagi

Zestaw reguł jest wskaźnik do obiektu klasy pochodnej z klasy [aspektu](#facet_class) mający publicznego obiektu w postaci:

```cpp
static locale::id id;
```

Można zdefiniować nieograniczony zbiór tych zestawów reguł. Można także skonstruować obiekt ustawień regionalnych, który wyznacza dowolną liczbę zestawów reguł.

Wstępnie zdefiniowane grupy te aspekty reprezentują [kategorie regionalne](#category) tradycyjnie zarządzanej biblioteki standardowe C za pomocą funkcji `setlocale`.

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

Obiekt ustawień regionalnych klasy przechowuje także nazwa ustawień regionalnych jako obiekt klasy [ciąg](../standard-library/string-typedefs.md#string). Do utworzenia aspektu ustawień regionalnych lub obiekt ustawień regionalnych przy użyciu nazwy nieprawidłowe ustawienia regionalne zgłasza obiekt klasy [runtime_error —](../standard-library/runtime-error-class.md). Nazwa ustawień regionalnych przechowywanych jest `"*"` Jeśli obiekt ustawień regionalnych nie może być określone dokładnie do odpowiada ustawień regionalnych w stylu języka C który reprezentowanych przez obiekt. W przeciwnym razie można ustanowić dopasowania ustawień regionalnych biblioteki standardowe C dla obiekt ustawień regionalnych `Loc`, wywołując `setlocale`(lc_all — `,` `Loc`. [Nazwa](#name)`().c_str()`).

W tej implementacji można również wywołać funkcję statycznego elementu członkowskiego:

```cpp
static locale empty();
```

do konstruowania obiektu ustawień regionalnych, który ma nie zestawu reguł. Istnieje również przezroczyste ustawień regionalnych; Jeśli funkcje szablonu [has_facet](../standard-library/locale-functions.md#has_facet) i [use_facet](../standard-library/locale-functions.md#use_facet) nie można odnaleźć żądanego aspekt w przezroczysty ustawień regionalnych, ich zapoznaj się najpierw globalnych ustawień regionalnych, a następnie, czyli przezroczyste, klasycznym ustawień regionalnych. W ten sposób można napisać:

```cpp
cout.imbue(locale::empty());
```

Kolejne wstawiania do [cout](../standard-library/iostream.md#cout) są przenoszone przez przez bieżący stan globalnych ustawień regionalnych. Można nawet napisać:

```cpp
locale loc(locale::empty(),
    locale::classic(),
    locale::numeric);

cout.imbue(loc);
```

Reguły dla kolejnych wstawiania do formatowanie liczbowe `cout` pozostają takie same jak ustawienia regionalne C, nawet zmiana zasady Wstawianie dat i kwot pieniężnych dostarcza globalnych ustawień regionalnych.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Ustawienia regionalne](#locale)|Tworzy ustawienia regionalne lub kopię ustawień regionalnych, lub kopię ustawień regionalnych, w której zestaw reguł lub kategoria zostały zastąpione przez zestaw reguł lub kategorię z innych ustawień regionalnych.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[category](#category)|Typ całkowitoliczbowy, który zawiera wartości masek bitowych dla oznaczenia standardowych rodzin zestawów reguł.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[Łączenie](#combine)|Wstawia zestaw reguł z określonych ustawień regionalnych do docelowych ustawień regionalnych.|
|[Nazwa](#name)|Zwraca przechowywaną nazwę ustawień regionalnych.|

### <a name="static-functions"></a>Funkcje statyczne

|||
|-|-|
|[Classic](#classic)|Funkcja statycznej składowej zwraca obiekt ustawień regionalnych, który reprezentuje klasyczne ustawienia regionalne C.|
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

**Namespace:** Standard

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

Typ jest synonimem `int` typu, który może reprezentować grupy odrębnych elementach maską bitów wpisz lokalny dla ustawień regionalnych klasy lub może służyć do reprezentacji żadnych odpowiednich kategorie regionalne C. Dostępne są następujące elementy:

- **COLLATE —**, odpowiadające kategorii C lc_collate —

- **CType —**, odpowiadające kategorii C lc_ctype —

- **pieniężne**, odpowiadające kategorii lc_monetary — C

- **liczbowa**, odpowiadające kategorii C lc_numeric —

- **czas**, odpowiadające kategorii C lc_time —

- **komunikaty**, odpowiadające kategorii Posix LC_MESSAGES

Ponadto dwie wartości przydatne są:

- **Brak**, odpowiadające Brak kategorii C

- **wszystkie**, odpowiadające Unii C z wszystkich kategorii lc_all —

Użytkownik poświadcza dowolnego grupy kategorii, za pomocą `OR` za pomocą tych stałych jako w **pieniężnego** &#124; **czasu**.

## <a name="classic"></a>  Locale::Classic

Funkcja statycznej składowej zwraca obiekt ustawień regionalnych, który reprezentuje klasyczne ustawienia regionalne C.

```cpp
static const locale& classic();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do ustawienia regionalne C.

### <a name="remarks"></a>Uwagi

Klasycznym ustawień regionalnych C jest USA Ustawienia regionalne angielskiej wersji językowej ASCII w standardowej bibliotece C niejawnie używanego w programach, które nie są międzynarodowych.

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

`Loc` Ustawienia regionalne zawierający zestaw reguł ma zostać wstawiony do ustawień regionalnych docelowej.

### <a name="return-value"></a>Wartość zwracana

Funkcja członkowska zwraca obiekt ustawień regionalnych, który zastępuje w lub dodaje do  **\*to** aspekt `Facet` na liście `Loc`.

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

Należy pamiętać, nie można skopiować lub przypisać obiekt klasy zestawu reguł. Możesz utworzyć i zniszcz obiektów pochodzących od klasy `locale::facet` , ale nie obiekty prawidłowego klasy podstawowej. Zazwyczaj utworzenia obiektu `_Myfac` pochodną aspektu podczas tworzenia ustawień regionalnych, podobnie jak w **localeloc**( `locale::classic`(), **nowe**`_Myfac`);

W takich przypadkach konstruktora dla klasy podstawowej aspekt powinien mieć wartość zero `_Refs` argumentu. Obiekt nie jest już potrzebne, jest usuwane. W związku z tym podać niezerowe _ *Refs* argument tylko w tych rzadkich przypadkach, gdy użytkownik odpowiada za okres istnienia obiektu.

## <a name="global"></a>  Locale::Global

Przywraca domyślne ustawienia regionalne dla programu. Ma to wpływ na globalne ustawienia regionalne dla C i C++.

```cpp
static locale global(const locale& Loc);
```

### <a name="parameters"></a>Parametry

`Loc` Ustawienia regionalne ma być używany jako domyślnych ustawień regionalnych przez program.

### <a name="return-value"></a>Wartość zwracana

Poprzednie ustawienia regionalne, zanim resetowania domyślnych ustawień regionalnych.

### <a name="remarks"></a>Uwagi

W momencie uruchamiania programu globalnych ustawień regionalnych jest taka sama jak klasycznych ustawień regionalnych. `global()` Wywołania funkcji `setlocale( LC_ALL, loc.name. c_str())` ustanowienie dopasowania ustawień regionalnych biblioteki standardowe C.

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

Identyfikator klasy {chronione: id(); private: id(const id&) / / nie zdefiniowano void operator =(const id&) / / nie zdefiniowano};

### <a name="remarks"></a>Uwagi

Klasy członkowskiej opis obiektu statycznego elementu członkowskiego wymagane przez każdego aspektu unikatowy ustawień regionalnych. Należy pamiętać, że nie można skopiować lub przypisać obiekt klasy **identyfikator**.

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

`Locname` Nazwa ustawień regionalnych.

`Loc` Ustawienia regionalne, który ma zostać skopiowany przy tworzeniu nowych ustawień regionalnych.

`Other` Ustawienia regionalne z którego można wybrać kategorię.

`Cat` Kategoria mają zostać podstawione do skonstruowanego ustawień regionalnych.

`Fac` Aspekt mają zostać podstawione do skonstruowanego ustawień regionalnych.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje obiekt do dopasowania globalnych ustawień regionalnych. Kategorie regionalne mają zachowanie zgodne z Nazwa ustawień regionalnych zainicjować konstruktorów drugi i trzeci `Locname`. Kopiowanie konstruktorów pozostałych `Loc`, z wyjątkiem wymienionych:

`locale(const locale& Loc, const locale& Other, category Cat);`

zastępuje z `Other` tych aspektów odpowiadającego kategorii C, dla których C & `Cat` jest różna od zera.

`locale(const locale& Loc, const char* Locname, category Cat);`

`locale(const locale& Loc, const string& Locname, category Cat);`

zastępuje z `locale(Locname, _All)` tych aspektów odpowiadającego kategorii C, dla których C & `Cat` jest różna od zera.

`template<class Facet> locale(const locale& Loc, Facet* Fac);`

zastępuje w (lub dodaje do) `Loc` aspekt `Fac`, jeśli `Fac` nie jest wskaźnika o wartości null.

Jeśli nazwa ustawień regionalnych `Locname` jest wskaźnika o wartości null lub w inny sposób nieodpowiednich, funkcja zwraca [runtime_error —](../standard-library/runtime-error-class.md).

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

`right` Jedno z ustawień regionalnych, pod kątem nierówności.

### <a name="return-value"></a>Wartość zwracana

Wartość logiczna, która jest **true** Jeśli ustawienia regionalne nie są kopie tych samych ustawień regionalnych; **false** Jeśli ustawienia regionalne są kopie tych samych ustawień regionalnych.

### <a name="remarks"></a>Uwagi

Dwa ustawienia regionalne są takie same, jeśli są one tych samych ustawień regionalnych, jeśli jest kopię innych lub mają identyczne nazwy.

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

`left` Po lewej stronie ciągu.

`right` Ciąg prawo.

### <a name="return-value"></a>Wartość zwracana

Zwraca funkcję elementu członkowskiego:

- -1, jeśli pierwszy sekwencji porównuje mniej niż drugi sekwencji.

- + 1, jeśli drugi sekwencji porównuje mniej niż pierwszy sekwencji.

- 0, jeśli sekwencje są równoważne.

### <a name="remarks"></a>Uwagi

Funkcja członkowska skutecznie wykonuje:

```cpp
const collate<CharType>& fac = use_fac<collate<CharType>>(*this);

return (fac.compare(left.begin(), left.end(), right.begin(), right.end()) < 0);
```

W związku z tym można użyć obiektu ustawień regionalnych jako obiekt funkcji.

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

`right` Jedno z ustawień regionalnych, pod kątem równości.

### <a name="return-value"></a>Wartość zwracana

Wartość logiczna, która jest **true** Jeśli ustawienia regionalne są kopie tych samych ustawień regionalnych; **false** Jeśli ustawienia regionalne nie są kopie tych samych ustawień regionalnych.

### <a name="remarks"></a>Uwagi

Dwa ustawienia regionalne są takie same, jeśli są one tych samych ustawień regionalnych, jeśli jest kopię innych lub mają identyczne nazwy.

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

[\<Ustawienia regionalne >](../standard-library/locale.md)<br/>
[Strony kodowe](../c-runtime-library/code-pages.md)<br/>
[Nazwy lokalne, języki i ciągi Kraj/Region](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
