---
title: moneypunct — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::moneypunct
- xlocmon/std::moneypunct::char_type
- xlocmon/std::moneypunct::string_type
- xlocmon/std::moneypunct::curr_symbol
- xlocmon/std::moneypunct::decimal_point
- xlocmon/std::moneypunct::do_curr_symbol
- xlocmon/std::moneypunct::do_decimal_point
- xlocmon/std::moneypunct::do_frac_digits
- xlocmon/std::moneypunct::do_grouping
- xlocmon/std::moneypunct::do_neg_format
- xlocmon/std::moneypunct::do_negative_sign
- xlocmon/std::moneypunct::do_pos_format
- xlocmon/std::moneypunct::do_positive_sign
- xlocmon/std::moneypunct::do_thousands_sep
- xlocmon/std::moneypunct::frac_digits
- xlocmon/std::moneypunct::grouping
- xlocmon/std::moneypunct::neg_format
- xlocmon/std::moneypunct::negative_sign
- xlocmon/std::moneypunct::pos_format
- xlocmon/std::moneypunct::positive_sign
- xlocmon/std::moneypunct::thousands_sep
helpviewer_keywords:
- std::moneypunct [C++]
- std::moneypunct [C++], char_type
- std::moneypunct [C++], string_type
- std::moneypunct [C++], curr_symbol
- std::moneypunct [C++], decimal_point
- std::moneypunct [C++], do_curr_symbol
- std::moneypunct [C++], do_decimal_point
- std::moneypunct [C++], do_frac_digits
- std::moneypunct [C++], do_grouping
- std::moneypunct [C++], do_neg_format
- std::moneypunct [C++], do_negative_sign
- std::moneypunct [C++], do_pos_format
- std::moneypunct [C++], do_positive_sign
- std::moneypunct [C++], do_thousands_sep
- std::moneypunct [C++], frac_digits
- std::moneypunct [C++], grouping
- std::moneypunct [C++], neg_format
- std::moneypunct [C++], negative_sign
- std::moneypunct [C++], pos_format
- std::moneypunct [C++], positive_sign
- std::moneypunct [C++], thousands_sep
ms.assetid: cf2650da-3e6f-491c-95d5-23e57f582ee6
ms.openlocfilehash: 8efed3cea9684c61f3bcac9eadb87b8a2b55ce09
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520943"
---
# <a name="moneypunct-class"></a>moneypunct — Klasa

Szablon klasy opisuje obiekt, który może służyć jako zestaw reguł ustawień regionalnych do opisania sekwencji typu *CharType* używanego do reprezentowania pola walutowego lub pola danych wyjściowych pieniężnych. Jeśli parametr szablonu *Intl* ma *wartość true*, są przestrzegane międzynarodowe konwencje.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType, bool Intl>
class moneypunct;
```

### <a name="parameters"></a>Parametry

*CharType*\
Typ używany w programie do kodowania znaków.

*Intl*\
Flaga określająca, czy międzynarodowe konwencje mają być przestrzegane.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba uzyskania dostępu do przechowywanej wartości przechowuje unikatową wartość dodatnią w **identyfikatorze.**

Obiekt statyczny const Intl przechowuje wartość parametru szablonu *Intl*.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[moneypunct](#moneypunct)|Konstruktor obiektów typu `moneypunct` .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ opisujący znak używany przez ustawienie regionalne.|
|[string_type](#string_type)|Typ, który opisuje ciąg zawierający znaki typu `CharType` .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[curr_symbol](#curr_symbol)|Zwraca sekwencję elementów specyficzną dla danych ustawień regionalnych w celu wykorzystania jako symbol waluty.|
|[decimal_point](#decimal_point)|Zwraca sekwencję elementów specyficzną dla danych ustawień regionalnych w celu wykorzystania jako symbol separatora dziesiętnego.|
|[do_curr_symbol](#do_curr_symbol)|Chroniona funkcja wirtualna elementu członkowskiego, która zwraca sekwencję elementów specyficznych dla ustawień regionalnych, używanych jako symbol waluty.|
|[do_decimal_point](#do_decimal_point)|Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana w celu zwrócenia sekwencji elementów specyficznych dla ustawień regionalnych używanych jako symbol separatora dziesiętnego.|
|[do_frac_digits](#do_frac_digits)|Chroniona funkcja wirtualna elementu członkowskiego zwraca specyficzną dla ustawień regionalnych liczbę cyfr, które mają być wyświetlane z prawej strony każdego separatora dziesiętnego.|
|[do_grouping](#do_grouping)|Chroniona funkcja wirtualna elementu członkowskiego zwraca regułę specyficzną dla ustawień regionalnych, aby określić sposób grupowania cyfr na lewo od każdego separatora dziesiętnego.|
|[do_neg_format](#do_neg_format)|Chroniona funkcja wirtualna elementu członkowskiego, wywoływana w celu zwrócenia reguły specyficznej dla ustawień regionalnych przy formatowaniu danych wyjściowych z kwotami ujemnymi.|
|[do_negative_sign](#do_negative_sign)|Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana w celu zwrócenia sekwencji elementów specyficznych dla ustawień regionalnych używanych jako symbol znaku ujemnego.|
|[do_pos_format](#do_pos_format)|Chroniona funkcja wirtualna elementu członkowskiego, wywoływana w celu zwrócenia reguły specyficznej dla ustawień regionalnych przy formatowaniu danych wyjściowych z kwotami dodatnimi.|
|[do_positive_sign](#do_positive_sign)|Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana w celu zwrócenia sekwencji elementów specyficznych dla ustawień regionalnych używanych jako symbol znaku dodatniego.|
|[do_thousands_sep](#do_thousands_sep)|Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana w celu zwrócenia sekwencji elementów specyficznych dla ustawień regionalnych używanych jako symbol separatora tysięcznego.|
|[frac_digits](#frac_digits)|Zwraca specyficzną dla ustawień regionalnych liczbę cyfr, które mają być wyświetlane z prawej strony każdego znaku dziesiętnego.|
|[grupie](#grouping)|Zwraca regułę specyficzną dla ustawień regionalnych określającą sposób grupowania cyfr na lewo od każdego znaku dziesiętnego.|
|[neg_format](#neg_format)|Zwraca regułę specyficzną dla ustawień regionalnych przy formatowaniu danych wyjściowych z kwotami ujemnymi.|
|[negative_sign](#negative_sign)|Zwraca sekwencję elementów specyficzną dla danych ustawień regionalnych w celu wykorzystania jako symbol znaku ujemnego.|
|[pos_format](#pos_format)|Zwraca regułę specyficzną dla ustawień regionalnych przy formatowaniu danych wyjściowych z kwotami dodatnimi.|
|[positive_sign](#positive_sign)|Zwraca sekwencję elementów specyficzną dla danych ustawień regionalnych w celu wykorzystania jako symbol znaku dodatniego.|
|[thousands_sep](#thousands_sep)|Zwraca sekwencję elementów specyficzną dla danych ustawień regionalnych w celu wykorzystania jako symbol separatora tysięcznego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<locale>

**Przestrzeń nazw:** std

## <a name="moneypunctchar_type"></a><a name="char_type"></a>moneypunct:: char_type

Typ opisujący znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu **CharType**.

## <a name="moneypunctcurr_symbol"></a><a name="curr_symbol"></a>moneypunct:: curr_symbol

Zwraca sekwencję elementów specyficzną dla danych ustawień regionalnych w celu wykorzystania jako symbol waluty.

```cpp
string_type curr_symbol() const;
```

### <a name="return-value"></a>Wartość zwracana

Ciąg zawierający symbol waluty.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_curr_symbol](#do_curr_symbol).

### <a name="example"></a>Przykład

```cpp
// moneypunct_curr_symbol.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct < char, true > &mpunct = use_facet < moneypunct < char, true > >(loc);
   cout << loc.name( ) << " international currency symbol "<<  mpunct.curr_symbol( ) << endl;

   const moneypunct < char, false> &mpunct2 = use_facet < moneypunct < char, false> >(loc);
   cout << loc.name( ) << " domestic currency symbol "<<  mpunct2.curr_symbol( ) << endl;
};
```

## <a name="moneypunctdecimal_point"></a><a name="decimal_point"></a>moneypunct::d ecimal_point

Zwraca sekwencję elementów specyficzną dla danych ustawień regionalnych w celu wykorzystania jako symbol separatora dziesiętnego.

```cpp
CharType decimal_point() const;
```

### <a name="return-value"></a>Wartość zwracana

Sekwencja elementów specyficznych dla ustawień regionalnych do użycia jako symbol separatora dziesiętnego.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_decimal_point](#do_decimal_point).

### <a name="example"></a>Przykład

```cpp
// moneypunct_decimal_pt.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc("german_germany");

   const moneypunct < char, true > &mpunct = use_facet
      < moneypunct < char, true > >(loc);
   cout << loc.name( ) << " international decimal point "
        << mpunct.decimal_point( ) << endl;

   const moneypunct < char, false> &mpunct2 = use_facet
      < moneypunct < char, false> >(loc);
   cout << loc.name( ) << " domestic decimal point "
        << mpunct2.decimal_point( ) << endl;
}
```

```Output
German_Germany.1252 international decimal point ,
German_Germany.1252 domestic decimal point ,
```

## <a name="moneypunctdo_curr_symbol"></a><a name="do_curr_symbol"></a>moneypunct::d o_curr_symbol

Chroniona funkcja wirtualna elementu członkowskiego, która zwraca sekwencję elementów specyficznych dla ustawień regionalnych, używanych jako symbol waluty.

```cpp
virtual string_type do_curr_symbol() const;
```

### <a name="return-value"></a>Wartość zwracana

Sekwencja elementów specyficznych dla ustawień regionalnych do użycia jako symbol separatora dziesiętnego.

### <a name="example"></a>Przykład

Zobacz przykład dla [curr_symbol](#curr_symbol), gdzie wirtualna funkcja członkowska jest wywoływana przez `curr_symbol` .

## <a name="moneypunctdo_decimal_point"></a><a name="do_decimal_point"></a>moneypunct::d o_decimal_point

Chroniona funkcja wirtualna elementu członkowskiego zwracająca sekwencję elementów specyficznych dla ustawień regionalnych, która ma być używana jako symbol separatora dziesiętnego.

```cpp
virtual CharType do_decimal_point() const;
```

### <a name="return-value"></a>Wartość zwracana

Sekwencja elementów specyficznych dla ustawień regionalnych do użycia jako symbol separatora dziesiętnego.

### <a name="example"></a>Przykład

Zobacz przykład dla [decimal_point](#decimal_point), gdzie wirtualna funkcja członkowska jest wywoływana przez `decimal_point` .

## <a name="moneypunctdo_frac_digits"></a><a name="do_frac_digits"></a>moneypunct::d o_frac_digits

Chroniona funkcja wirtualna elementu członkowskiego zwracająca specyficzną dla ustawień regionalnych liczbę cyfr, które mają być wyświetlane z prawej strony dowolnego punktu dziesiętnego.

```cpp
virtual int do_frac_digits() const;
```

### <a name="return-value"></a>Wartość zwracana

Specyficzna dla ustawień regionalnych liczba cyfr do wyświetlenia po prawej stronie dowolnego punktu dziesiętnego.

### <a name="example"></a>Przykład

Zobacz przykład dla [frac_digits](#frac_digits), gdzie wirtualna funkcja członkowska jest wywoływana przez `frac_digits` .

## <a name="moneypunctdo_grouping"></a><a name="do_grouping"></a>moneypunct::d o_grouping

Chroniona funkcja wirtualna elementu członkowskiego zwracająca regułę specyficzną dla ustawień regionalnych służącą do określenia sposobu grupowania cyfr na lewo od dowolnego punktu dziesiętnego.

```cpp
virtual string do_grouping() const;
```

### <a name="return-value"></a>Wartość zwracana

Reguła specyficzna dla ustawień regionalnych określająca sposób grupowania cyfr na lewo od dowolnego miejsca dziesiętnego.

### <a name="example"></a>Przykład

Zobacz przykład [grupowania](#grouping), gdzie wirtualna funkcja członkowska jest wywoływana przez `grouping` .

## <a name="moneypunctdo_neg_format"></a><a name="do_neg_format"></a>moneypunct::d o_neg_format

Chroniona funkcja wirtualna elementu członkowskiego, wywoływana w celu zwrócenia reguły specyficznej dla ustawień regionalnych przy formatowaniu danych wyjściowych z kwotami ujemnymi.

```cpp
virtual pattern do_neg_format() const;
```

### <a name="return-value"></a>Wartość zwracana

Chroniona funkcja wirtualna elementu członkowskiego zwraca regułę specyficzną dla ustawień regionalnych służącą do określania sposobu generowania pola danych wyjściowych pieniężnych dla liczby ujemnej. Każdy z czterech elementów `pattern::field` może mieć wartości:

- `none`Aby dopasować zero lub więcej spacji lub wygenerować Nothing.

- `sign`Aby dopasować lub wygenerować znak dodatni lub ujemny.

- `space`Aby dopasować zero lub więcej spacji lub wygenerować spację.

- `symbol`Aby dopasować lub wygenerować symbol waluty.

- `value`Aby dopasować lub wygenerować wartość pieniężną.

Składniki pola danych wyjściowych pieniężnych są generowane, a składniki pola danych wejściowych pieniężnych są dopasowane w kolejności, w której te elementy są wyświetlane w `pattern::field` . Każda z wartości `sign` ,, `symbol` `value` i albo `none` `space` musi być wyświetlana dokładnie jeden raz. Wartość `none` nie może być wyświetlana jako pierwsza. Wartość `space` nie może być wyświetlana jako First ani Last. Jeśli `Intl` ma wartość true, Order jest `symbol` , `sign` , `none` , then `value` .

Wersja szablonu `moneypunct< CharType, Intl >` zwraca `{money_base::symbol, money_base::sign, money_base::value, money_base::none}` .

### <a name="example"></a>Przykład

Zobacz przykład dla [neg_format](#neg_format), gdzie wirtualna funkcja członkowska jest wywoływana przez `neg_format` .

## <a name="moneypunctdo_negative_sign"></a><a name="do_negative_sign"></a>moneypunct::d o_negative_sign

Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana w celu zwrócenia sekwencji elementów specyficznych dla ustawień regionalnych używanych jako symbol znaku ujemnego.

```cpp
virtual string_type do_negative_sign() const;
```

### <a name="return-value"></a>Wartość zwracana

Sekwencja elementów specyficznych dla ustawień regionalnych, która ma być używana jako znak ujemny.

### <a name="example"></a>Przykład

Zobacz przykład dla [negative_sign](#negative_sign), gdzie wirtualna funkcja członkowska jest wywoływana przez `negative_sign` .

## <a name="moneypunctdo_pos_format"></a><a name="do_pos_format"></a>moneypunct::d o_pos_format

Chroniona funkcja wirtualna elementu członkowskiego, wywoływana w celu zwrócenia reguły specyficznej dla ustawień regionalnych przy formatowaniu danych wyjściowych z kwotami dodatnimi.

```cpp
virtual pattern do_pos_format() const;
```

### <a name="return-value"></a>Wartość zwracana

Chroniona funkcja wirtualna elementu członkowskiego zwraca regułę specyficzną dla ustawień regionalnych służącą do określania sposobu generowania pola danych wyjściowych pieniężnych dla liczby dodatniej. (Określa również, jak dopasować składniki pola danych wejściowych pieniężnych). Kodowanie jest takie samo jak w przypadku [do_neg_format](#do_neg_format).

Wersja szablonu `moneypunct< CharType, Inputlterator >` zwraca `{ money_base::symbol, money_base::sign, money_base::value, money_base::none }` .

### <a name="example"></a>Przykład

Zobacz przykład dla [pos_format](#pos_format), gdzie wirtualna funkcja członkowska jest wywoływana przez `pos_format` .

## <a name="moneypunctdo_positive_sign"></a><a name="do_positive_sign"></a>moneypunct::d o_positive_sign

Chroniona funkcja wirtualna elementu członkowskiego zwracająca sekwencję elementów specyficznych dla ustawień regionalnych, która ma być używana jako znak dodatni.

```cpp
virtual string_type do_positive_sign() const;
```

### <a name="return-value"></a>Wartość zwracana

Sekwencja elementów specyficznych dla ustawień regionalnych, która ma być używana jako znak dodatni.

### <a name="example"></a>Przykład

Zobacz przykład dla [positive_sign](#positive_sign), gdzie wirtualna funkcja członkowska jest wywoływana przez `positive_sign` .

## <a name="moneypunctdo_thousands_sep"></a><a name="do_thousands_sep"></a>moneypunct::d o_thousands_sep

Chroniona funkcja wirtualna elementu członkowskiego zwracająca element specyficzny dla ustawień regionalnych, który ma być używany jako separator grupy z lewej strony dowolnego punktu dziesiętnego.

```cpp
virtual CharType do_thousands_sep() const;
```

### <a name="return-value"></a>Wartość zwracana

Element specyficzny dla ustawień regionalnych, który ma być używany jako separator grupy po lewej stronie dowolnego punktu dziesiętnego.

### <a name="example"></a>Przykład

Zobacz przykład dla [thousands_sep](#thousands_sep), gdzie wirtualna funkcja członkowska jest wywoływana przez `thousands_sep` .

## <a name="moneypunctfrac_digits"></a><a name="frac_digits"></a>moneypunct:: frac_digits

Zwraca specyficzną dla ustawień regionalnych liczbę cyfr, które mają być wyświetlane z prawej strony każdego znaku dziesiętnego.

```cpp
int frac_digits() const;
```

### <a name="return-value"></a>Wartość zwracana

Specyficzna dla ustawień regionalnych liczba cyfr do wyświetlenia po prawej stronie dowolnego punktu dziesiętnego.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_frac_digits](#do_frac_digits).

### <a name="example"></a>Przykład

```cpp
// moneypunct_frac_digits.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
       use_facet <moneypunct <char, true> >(loc);
   for (unsigned int i = 0; i <mpunct.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " international grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " international frac_digits\n to the right"
        << " of the radix character: "
        << mpunct.frac_digits ( ) << endl << endl;

   const moneypunct <char, false> &mpunct2 =
       use_facet <moneypunct <char, false> >(loc);
   for (unsigned int i = 0; i <mpunct2.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " domestic grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct2.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " domestic frac_digits\n to the right"
        << " of the radix character: "
        << mpunct2.frac_digits ( ) << endl << endl;
}
```

```Output
German_Germany.1252 international grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 international frac_digits
to the right of the radix character: 2

German_Germany.1252 domestic grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 domestic frac_digits
to the right of the radix character: 2
```

## <a name="moneypunctgrouping"></a><a name="grouping"></a>moneypunct:: Grouping

Zwraca regułę specyficzną dla ustawień regionalnych określającą sposób grupowania cyfr na lewo od każdego znaku dziesiętnego.

```cpp
string grouping() const;
```

### <a name="return-value"></a>Wartość zwracana

Reguła specyficzna dla ustawień regionalnych określająca sposób grupowania cyfr na lewo od dowolnego miejsca dziesiętnego.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_grouping](#do_grouping).

### <a name="example"></a>Przykład

```cpp
// moneypunct_grouping.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
       use_facet <moneypunct <char, true> >( loc );
   for (unsigned int i = 0; i <mpunct.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " international grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " international frac_digits\n to the right"
        << " of the radix character: "
        << mpunct.frac_digits ( ) << endl << endl;

   const moneypunct <char, false> &mpunct2 =
       use_facet <moneypunct <char, false> >( loc );
   for (unsigned int i = 0; i <mpunct2.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " domestic grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct2.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " domestic frac_digits\n to the right"
        << " of the radix character: "
        << mpunct2.frac_digits ( ) << endl << endl;
}
```

```Output
German_Germany.1252 international grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 international frac_digits
to the right of the radix character: 2

German_Germany.1252 domestic grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 domestic frac_digits
to the right of the radix character: 2
```

## <a name="moneypunctmoneypunct"></a><a name="moneypunct"></a>moneypunct:: moneypunct

Konstruktor obiektów typu `moneypunct` .

```cpp
explicit moneypunct(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs*\
Wartość całkowita służąca do określania typu zarządzania pamięcią dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *_Refs* i ich znaczenie są następujące:

- 0: okres istnienia obiektu jest zarządzany przez elementy lokalne, które go zawierają.

- 1: okres istnienia obiektu musi być zarządzany ręcznie.

- \>1: te wartości nie są zdefiniowane.

Nie są możliwe żadne bezpośrednie przykłady, ponieważ destruktor jest chroniony.

Konstruktor inicjuje swój obiekt podstawowy przy użyciu [ustawień regionalnych:: facet](../standard-library/locale-class.md#facet_class)(_ *ReFS*).

## <a name="moneypunctneg_format"></a><a name="neg_format"></a>moneypunct:: neg_format

Zwraca regułę specyficzną dla ustawień regionalnych przy formatowaniu danych wyjściowych z kwotami ujemnymi.

```cpp
pattern neg_format() const;
```

### <a name="return-value"></a>Wartość zwracana

Reguła specyficzna dla ustawień regionalnych służąca do formatowania danych wyjściowych z kwotami ujemnymi.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_neg_format](#do_neg_format).

### <a name="example"></a>Przykład

```cpp
// moneypunct_neg_format.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main( ) {
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true > >(loc);
   cout << loc.name( ) << " international negative number format: "
        << mpunct.neg_format( ).field[0]
        << mpunct.neg_format( ).field[1]
        << mpunct.neg_format( ).field[2]
        << mpunct.neg_format( ).field[3] << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic negative number format: "
        << mpunct2.neg_format( ).field[0]
        << mpunct2.neg_format( ).field[1]
        << mpunct2.neg_format( ).field[2]
        << mpunct2.neg_format( ).field[3] << endl;
}
```

## <a name="moneypunctnegative_sign"></a><a name="negative_sign"></a>moneypunct:: negative_sign

Zwraca sekwencję elementów specyficzną dla danych ustawień regionalnych w celu wykorzystania jako symbol znaku ujemnego.

```cpp
string_type negative_sign() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca sekwencję elementów specyficzną dla danych ustawień regionalnych w celu wykorzystania jako symbol znaku ujemnego.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_negative_sign](#do_negative_sign).

### <a name="example"></a>Przykład

```cpp
// moneypunct_neg_sign.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true> >(loc);
   cout << loc.name( ) << " international negative sign: "
        << mpunct.negative_sign( ) << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic negative sign: "
        << mpunct2.negative_sign( ) << endl;

   locale loc2( "French" );

   const moneypunct <char, true> &mpunct3 =
      use_facet <moneypunct <char, true> >(loc2);
   cout << loc2.name( ) << " international negative sign: "
        << mpunct3.negative_sign( ) << endl;

   const moneypunct <char, false> &mpunct4 =
      use_facet <moneypunct <char, false> >(loc2);
   cout << loc2.name( ) << " domestic negative sign: "
        << mpunct4.negative_sign( ) << endl;
};
```

```Output
German_Germany.1252 international negative sign: -
German_Germany.1252 domestic negative sign: -
French_France.1252 international negative sign: -
French_France.1252 domestic negative sign: -
```

## <a name="moneypunctpos_format"></a><a name="pos_format"></a>moneypunct::p os_format

Zwraca regułę specyficzną dla ustawień regionalnych przy formatowaniu danych wyjściowych z kwotami dodatnimi.

```cpp
pattern pos_format() const;
```

### <a name="return-value"></a>Wartość zwracana

Reguła specyficzna dla ustawień regionalnych służąca do formatowania danych wyjściowych z kwotami dodatnimi.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_pos_format](#do_pos_format).

### <a name="example"></a>Przykład

```cpp
// moneypunct_pos_format.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main() {
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true> >(loc);
   cout << loc.name( ) << " international positive number format: "
        << mpunct.pos_format( ).field[0]
        << mpunct.pos_format( ).field[1]
        << mpunct.pos_format( ).field[2]
        << mpunct.pos_format( ).field[3] << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic positive number format: "
        << mpunct2.pos_format( ).field[0]
        << mpunct2.pos_format( ).field[1]
        << mpunct2.pos_format( ).field[2]
        << mpunct2.pos_format( ).field[3] << endl;
}
```

## <a name="moneypunctpositive_sign"></a><a name="positive_sign"></a>moneypunct::p ositive_sign

Zwraca sekwencję elementów specyficzną dla danych ustawień regionalnych w celu wykorzystania jako symbol znaku dodatniego.

```cpp
string_type positive_sign() const;
```

### <a name="return-value"></a>Wartość zwracana

Sekwencja elementów specyficznych dla ustawień regionalnych do użycia jako symbol znaku dodatniego.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_positive_sign](#do_positive_sign).

### <a name="example"></a>Przykład

```cpp
// moneypunct_pos_sign.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true > >(loc);
   cout << loc.name( ) << " international positive sign:"
        << mpunct.positive_sign( ) << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic positive sign:"
        << mpunct2.positive_sign( ) << endl;

   locale loc2( "French" );

   const moneypunct <char, true> &mpunct3 =
      use_facet <moneypunct <char, true> >(loc2);
   cout << loc2.name( ) << " international positive sign:"
        << mpunct3.positive_sign( ) << endl;

   const moneypunct <char, false> &mpunct4 =
      use_facet <moneypunct <char, false> >(loc2);
   cout << loc2.name( ) << " domestic positive sign:"
        << mpunct4.positive_sign( ) << endl;
};
```

```Output
German_Germany.1252 international positive sign:
German_Germany.1252 domestic positive sign:
French_France.1252 international positive sign:
French_France.1252 domestic positive sign:
```

## <a name="moneypunctstring_type"></a><a name="string_type"></a>moneypunct:: string_type

Typ, który opisuje ciąg zawierający znaki typu **CharType**.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [basic_string](../standard-library/basic-string-class.md) którego obiekty mogą przechowywać kopie sekwencji interpunkcji.

## <a name="moneypunctthousands_sep"></a><a name="thousands_sep"></a>moneypunct:: thousands_sep

Zwraca sekwencję elementów specyficzną dla danych ustawień regionalnych w celu wykorzystania jako symbol separatora tysięcznego.

```cpp
CharType thousands_sep() const;
```

### <a name="return-value"></a>Wartość zwracana

Sekwencja elementów specyficznych dla ustawień regionalnych, które mają być używane jako separator tysięcy

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_thousands_sep](#do_thousands_sep).

### <a name="example"></a>Przykład

```cpp
// moneypunct_thou_sep.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
       use_facet <moneypunct <char, true > >(loc);
   cout << loc.name( ) << " international thousands separator: "
        << mpunct.thousands_sep( ) << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic thousands separator: "
        << mpunct2.thousands_sep( ) << endl << endl;

   locale loc2( "english_canada" );

   const moneypunct <char, true> &mpunct3 =
       use_facet <moneypunct <char, true> >(loc2);
   cout << loc2.name( ) << " international thousands separator: "
        << mpunct3.thousands_sep( ) << endl;

   const moneypunct <char, false> &mpunct4 =
      use_facet <moneypunct <char, false> >(loc2);
   cout << loc2.name( ) << " domestic thousands separator: "
        << mpunct4.thousands_sep( ) << endl;
}
```

```Output
German_Germany.1252 international thousands separator: .
German_Germany.1252 domestic thousands separator: .

English_Canada.1252 international thousands separator: ,
English_Canada.1252 domestic thousands separator: ,
```

## <a name="see-also"></a>Zobacz także

[\<locale>](../standard-library/locale.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
