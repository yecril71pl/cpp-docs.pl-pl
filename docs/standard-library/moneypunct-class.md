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
ms.openlocfilehash: 3a277b2f97fd53c52b705051c30eb18faf6364d0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366246"
---
# <a name="moneypunct-class"></a>moneypunct — Klasa

Szablon klasy opisuje obiekt, który może służyć jako aspekt ustawień regionalnych do opisania sekwencji typu *CharType* używane do reprezentowania pieniężnego pola wejściowego lub pieniężnego pola wyjściowego. Jeśli parametr szablonu *Intl* jest *prawdziwy,* przestrzegane są konwencje międzynarodowe.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType, bool Intl>
class moneypunct;
```

### <a name="parameters"></a>Parametry

*Chartype*\
Typ używany w programie do kodowania znaków.

*Intl*\
Flaga określająca, czy międzynarodowe konwencje mają być przestrzegane.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba uzyskania dostępu do przechowywanej wartości przechowuje unikatową wartość dodatnią w **identyfikatorze.**

Const obiekt statyczny intl przechowuje wartość parametru szablonu *Intl*.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[punkt pieniądz](#moneypunct)|Konstruktor obiektów `moneypunct`typu .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[Char_type](#char_type)|Typ opisujący znak używany przez ustawienie regionalne.|
|[string_type](#string_type)|Typ opisujący ciąg zawierający znaki `CharType`typu .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
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
|[Grupowanie](#grouping)|Zwraca regułę specyficzną dla ustawień regionalnych określającą sposób grupowania cyfr na lewo od każdego znaku dziesiętnego.|
|[neg_format](#neg_format)|Zwraca regułę specyficzną dla ustawień regionalnych przy formatowaniu danych wyjściowych z kwotami ujemnymi.|
|[negative_sign](#negative_sign)|Zwraca sekwencję elementów specyficzną dla danych ustawień regionalnych w celu wykorzystania jako symbol znaku ujemnego.|
|[pos_format](#pos_format)|Zwraca regułę specyficzną dla ustawień regionalnych przy formatowaniu danych wyjściowych z kwotami dodatnimi.|
|[positive_sign](#positive_sign)|Zwraca sekwencję elementów specyficzną dla danych ustawień regionalnych w celu wykorzystania jako symbol znaku dodatniego.|
|[thousands_sep](#thousands_sep)|Zwraca sekwencję elementów specyficzną dla danych ustawień regionalnych w celu wykorzystania jako symbol separatora tysięcznego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ustawień regionalnych

**Przestrzeń nazw:** std

## <a name="moneypunctchar_type"></a><a name="char_type"></a>moneypunct::char_type

Typ opisujący znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu **CharType**.

## <a name="moneypunctcurr_symbol"></a><a name="curr_symbol"></a>moneypunct::curr_symbol

Zwraca sekwencję elementów specyficzną dla danych ustawień regionalnych w celu wykorzystania jako symbol waluty.

```cpp
string_type curr_symbol() const;
```

### <a name="return-value"></a>Wartość zwracana

Ciąg zawierający symbol waluty.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_curr_symbol](#do_curr_symbol).

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

## <a name="moneypunctdecimal_point"></a><a name="decimal_point"></a>moneypunct::decimal_point

Zwraca sekwencję elementów specyficzną dla danych ustawień regionalnych w celu wykorzystania jako symbol separatora dziesiętnego.

```cpp
CharType decimal_point() const;
```

### <a name="return-value"></a>Wartość zwracana

Sekwencja elementów specyficznych dla ustawień regionalnych, które mają być używane jako symbol punktu dziesiętnego.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_decimal_point](#do_decimal_point).

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

## <a name="moneypunctdo_curr_symbol"></a><a name="do_curr_symbol"></a>moneypunct::do_curr_symbol

Chroniona funkcja wirtualna elementu członkowskiego, która zwraca sekwencję elementów specyficznych dla ustawień regionalnych, używanych jako symbol waluty.

```cpp
virtual string_type do_curr_symbol() const;
```

### <a name="return-value"></a>Wartość zwracana

Sekwencja elementów specyficznych dla ustawień regionalnych, które mają być używane jako symbol punktu dziesiętnego.

### <a name="example"></a>Przykład

Zobacz przykład [curr_symbol](#curr_symbol), gdzie funkcja wirtualnego elementu `curr_symbol`członkowskiego jest wywoływana przez .

## <a name="moneypunctdo_decimal_point"></a><a name="do_decimal_point"></a>moneypunct::do_decimal_point

Funkcja chronionego elementu członkowskiego wirtualnego, która zwraca sekwencję elementów specyficznych dla ustawień regionalnych, która ma być używana jako symbol przecinka dziesiętnego.

```cpp
virtual CharType do_decimal_point() const;
```

### <a name="return-value"></a>Wartość zwracana

Sekwencja elementów specyficznych dla ustawień regionalnych, które mają być używane jako symbol punktu dziesiętnego.

### <a name="example"></a>Przykład

Zobacz przykład [decimal_point](#decimal_point), gdzie funkcja wirtualnego elementu `decimal_point`członkowskiego jest wywoływana przez .

## <a name="moneypunctdo_frac_digits"></a><a name="do_frac_digits"></a>moneypunct::do_frac_digits

Chroniona funkcja wirtualnego elementu członkowskiego, która zwraca liczbę specyficznych dla ustawień regionalnych liczby cyfr do wyświetlenia po prawej stronie dowolnego przecinka dziesiętnego.

```cpp
virtual int do_frac_digits() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba cyfr charakterystycznych dla ustawień regionalnych, która ma być wyświetlana po prawej stronie dowolnego przecinka dziesiętnego.

### <a name="example"></a>Przykład

Zobacz przykład [frac_digits](#frac_digits), gdzie funkcja wirtualnego elementu `frac_digits`członkowskiego jest wywoływana przez .

## <a name="moneypunctdo_grouping"></a><a name="do_grouping"></a>moneypunct::do_grouping

Funkcja chronionego elementu członkowskiego wirtualnego, która zwraca regułę specyficzne dla ustawień regionalnych do określania, jak cyfry są grupowane po lewej stronie dowolnego przecinka dziesiętnego.

```cpp
virtual string do_grouping() const;
```

### <a name="return-value"></a>Wartość zwracana

Reguła specyficzna dla ustawień regionalnych określająca sposób grupowania cyfr po lewej stronie dowolnego przecinka dziesiętnego.

### <a name="example"></a>Przykład

Zobacz przykład [grupowania,](#grouping)gdzie funkcja wirtualnego `grouping`elementu członkowskiego jest wywoływana przez .

## <a name="moneypunctdo_neg_format"></a><a name="do_neg_format"></a>moneypunct::do_neg_format

Chroniona funkcja wirtualna elementu członkowskiego, wywoływana w celu zwrócenia reguły specyficznej dla ustawień regionalnych przy formatowaniu danych wyjściowych z kwotami ujemnymi.

```cpp
virtual pattern do_neg_format() const;
```

### <a name="return-value"></a>Wartość zwracana

Funkcja chronionego elementu członkowskiego wirtualnego zwraca regułę specyficzne dla ustawień regionalnych do określania sposobu generowania pola wyjściowego dla kwoty ujemnej. Każdy z czterech `pattern::field` elementów może mieć wartości:

- `none`aby dopasować zero lub więcej spacji lub nic nie wygenerować.

- `sign`, aby dopasować lub wygenerować znak dodatni lub ujemny.

- `space`, aby dopasować zero lub więcej spacji lub wygenerować spację.

- `symbol`, aby dopasować lub wygenerować symbol waluty.

- `value`aby dopasować lub wygenerować wartość pieniężną.

Składniki pieniężnego pola wyjściowego są generowane, a składniki pola danych wejściowych pieniężnych są dopasowywały w kolejności, w jakiej te elementy pojawiają się w `pattern::field`programie . Każda z `sign`wartości `symbol` `value`, , `none` i `space` albo albo musi pojawić się dokładnie raz. Wartość `none` nie może pojawić się w pierwszej kolejności. Spacja wartości nie **może** być wyświetlana jako pierwsza ani ostatnia. Jeśli `Intl` jest prawdziwa, `symbol`kolejność `sign` `none`jest `value`, , , a następnie .

Wersja szablonu `moneypunct` \< **CharType**, **Intl** `{`> zwraca **money_base::symbol**, **money_base::sign**, **money_base::value**, **money_base::none**`}`.

### <a name="example"></a>Przykład

Zobacz przykład [neg_format](#neg_format), gdzie funkcja wirtualnego elementu `neg_format`członkowskiego jest wywoływana przez .

## <a name="moneypunctdo_negative_sign"></a><a name="do_negative_sign"></a>moneypunct::do_negative_sign

Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana w celu zwrócenia sekwencji elementów specyficznych dla ustawień regionalnych używanych jako symbol znaku ujemnego.

```cpp
virtual string_type do_negative_sign() const;
```

### <a name="return-value"></a>Wartość zwracana

Sekwencja elementów specyficznych dla ustawień regionalnych do użycia jako znak ujemny.

### <a name="example"></a>Przykład

Zobacz przykład [negative_sign](#negative_sign), gdzie funkcja wirtualnego elementu `negative_sign`członkowskiego jest wywoływana przez .

## <a name="moneypunctdo_pos_format"></a><a name="do_pos_format"></a>moneypunct::do_pos_format

Chroniona funkcja wirtualna elementu członkowskiego, wywoływana w celu zwrócenia reguły specyficznej dla ustawień regionalnych przy formatowaniu danych wyjściowych z kwotami dodatnimi.

```cpp
virtual pattern do_pos_format() const;
```

### <a name="return-value"></a>Wartość zwracana

Funkcja chronionego wirtualnego elementu członkowskiego zwraca regułę specyficzne dla ustawień regionalnych do określania sposobu generowania pola wyjściowego dla kwoty dodatniej. (Określa również, jak dopasować składniki pola danych wejściowych pieniężnych. Kodowanie jest takie samo jak w przypadku [do_neg_format](#do_neg_format).

Wersja\< szablonu moneypunct **CharType**, **Inputlterator** `{`> zwraca **money_base::symbol**, **money_base::sign**, **money_base::value**, **money_base::none**`}`.

### <a name="example"></a>Przykład

Zobacz przykład [pos_format](#pos_format), gdzie funkcja wirtualnego elementu `pos_format`członkowskiego jest wywoływana przez .

## <a name="moneypunctdo_positive_sign"></a><a name="do_positive_sign"></a>moneypunct::do_positive_sign

Funkcja chronionego wirtualnego elementu członkowskiego, która zwraca sekwencję elementów specyficznych dla ustawień regionalnych, która ma być używana jako znak dodatni.

```cpp
virtual string_type do_positive_sign() const;
```

### <a name="return-value"></a>Wartość zwracana

Sekwencja elementów specyficznych dla ustawień regionalnych do użycia jako znak dodatni.

### <a name="example"></a>Przykład

Zobacz przykład [positive_sign](#positive_sign), gdzie funkcja wirtualnego elementu `positive_sign`członkowskiego jest wywoływana przez .

## <a name="moneypunctdo_thousands_sep"></a><a name="do_thousands_sep"></a>moneypunct::do_thousands_sep

Funkcja chronionego elementu członkowskiego wirtualnego, która zwraca element specyficzny dla ustawień regionalnych do użycia jako separator grupy po lewej stronie dowolnego przecinka dziesiętnego.

```cpp
virtual CharType do_thousands_sep() const;
```

### <a name="return-value"></a>Wartość zwracana

Element specyficzny dla ustawień regionalnych, który ma być używany jako separator grupy po lewej stronie dowolnego przecinka dziesiętnego.

### <a name="example"></a>Przykład

Zobacz przykład [thousands_sep](#thousands_sep), gdzie funkcja wirtualnego elementu `thousands_sep`członkowskiego jest wywoływana przez .

## <a name="moneypunctfrac_digits"></a><a name="frac_digits"></a>moneypunct::frac_digits

Zwraca specyficzną dla ustawień regionalnych liczbę cyfr, które mają być wyświetlane z prawej strony każdego znaku dziesiętnego.

```cpp
int frac_digits() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba cyfr charakterystycznych dla ustawień regionalnych, która ma być wyświetlana po prawej stronie dowolnego przecinka dziesiętnego.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_frac_digits](#do_frac_digits).

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

## <a name="moneypunctgrouping"></a><a name="grouping"></a>moneypunct::grouping

Zwraca regułę specyficzną dla ustawień regionalnych określającą sposób grupowania cyfr na lewo od każdego znaku dziesiętnego.

```cpp
string grouping() const;
```

### <a name="return-value"></a>Wartość zwracana

Reguła specyficzna dla ustawień regionalnych określająca sposób grupowania cyfr po lewej stronie dowolnego przecinka dziesiętnego.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_grouping](#do_grouping).

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

## <a name="moneypunctmoneypunct"></a><a name="moneypunct"></a>moneypunct::moneypunct

Konstruktor obiektów `moneypunct`typu .

```cpp
explicit moneypunct(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_refs*\
Wartość całkowita używana do określania typu zarządzania pamięcią dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *_Refs* i ich znaczenie to:

- 0: Okres istnienia obiektu jest zarządzany przez ustawienia regionalne, które go zawierają.

- 1: Okres istnienia obiektu musi być zarządzany ręcznie.

- \>1: Te wartości nie są zdefiniowane.

Nie są możliwe żadne bezpośrednie przykłady, ponieważ destruktor jest chroniony.

Konstruktor inicjuje swój obiekt podstawowy z [ustawieniami ustawieniami regionalnymi::facet](../standard-library/locale-class.md#facet_class)(_ *Refs*).

## <a name="moneypunctneg_format"></a><a name="neg_format"></a>moneypunct::neg_format

Zwraca regułę specyficzną dla ustawień regionalnych przy formatowaniu danych wyjściowych z kwotami ujemnymi.

```cpp
pattern neg_format() const;
```

### <a name="return-value"></a>Wartość zwracana

Reguła specyficzne dla ustawień regionalnych do formatowania danych wyjściowych z kwotami ujemnymi.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_neg_format](#do_neg_format).

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

## <a name="moneypunctnegative_sign"></a><a name="negative_sign"></a>moneypunct::negative_sign

Zwraca sekwencję elementów specyficzną dla danych ustawień regionalnych w celu wykorzystania jako symbol znaku ujemnego.

```cpp
string_type negative_sign() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca sekwencję elementów specyficzną dla danych ustawień regionalnych w celu wykorzystania jako symbol znaku ujemnego.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_negative_sign](#do_negative_sign).

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

## <a name="moneypunctpos_format"></a><a name="pos_format"></a>moneypunct::pos_format

Zwraca regułę specyficzną dla ustawień regionalnych przy formatowaniu danych wyjściowych z kwotami dodatnimi.

```cpp
pattern pos_format() const;
```

### <a name="return-value"></a>Wartość zwracana

Reguła specyficzne dla ustawień regionalnych do formatowania danych wyjściowych z kwotami dodatnimi.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_pos_format](#do_pos_format).

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

## <a name="moneypunctpositive_sign"></a><a name="positive_sign"></a>moneypunct::positive_sign

Zwraca sekwencję elementów specyficzną dla danych ustawień regionalnych w celu wykorzystania jako symbol znaku dodatniego.

```cpp
string_type positive_sign() const;
```

### <a name="return-value"></a>Wartość zwracana

Sekwencja elementów specyficznych dla ustawień regionalnych do użycia jako symbol znaku dodatniego.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_positive_sign](#do_positive_sign).

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

## <a name="moneypunctstring_type"></a><a name="string_type"></a>moneypunct::string_type

Typ opisujący ciąg zawierający znaki typu **CharType**.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [basic_string](../standard-library/basic-string-class.md) których obiekty mogą przechowywać kopie sekwencji znaków interpunkcyjnych.

## <a name="moneypunctthousands_sep"></a><a name="thousands_sep"></a>moneypunct::thousands_sep

Zwraca sekwencję elementów specyficzną dla danych ustawień regionalnych w celu wykorzystania jako symbol separatora tysięcznego.

```cpp
CharType thousands_sep() const;
```

### <a name="return-value"></a>Wartość zwracana

Sekwencja elementów specyficznych dla ustawień regionalnych do użycia jako separator tysięcy

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_thousands_sep](#do_thousands_sep).

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

## <a name="see-also"></a>Zobacz też

[\<>ustawień regionalnych](../standard-library/locale.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
