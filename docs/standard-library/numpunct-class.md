---
title: numpunct — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::numpunct
- xlocnum/std::numpunct::char_type
- xlocnum/std::numpunct::string_type
- xlocnum/std::numpunct::decimal_point
- xlocnum/std::numpunct::do_decimal_point
- xlocnum/std::numpunct::do_falsename
- xlocnum/std::numpunct::do_grouping
- xlocnum/std::numpunct::do_thousands_sep
- xlocnum/std::numpunct::do_truename
- xlocnum/std::numpunct::falsename
- xlocnum/std::numpunct::grouping
- xlocnum/std::numpunct::thousands_sep
- xlocnum/std::numpunct::truename
helpviewer_keywords:
- std::numpunct [C++]
- std::numpunct [C++], char_type
- std::numpunct [C++], string_type
- std::numpunct [C++], decimal_point
- std::numpunct [C++], do_decimal_point
- std::numpunct [C++], do_falsename
- std::numpunct [C++], do_grouping
- std::numpunct [C++], do_thousands_sep
- std::numpunct [C++], do_truename
- std::numpunct [C++], falsename
- std::numpunct [C++], grouping
- std::numpunct [C++], thousands_sep
- std::numpunct [C++], truename
ms.assetid: 73fb93cc-ac11-4c98-987c-bfa6267df596
ms.openlocfilehash: 0bdd6556df892e5e231919dbc4ae95d14a6f95fe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373613"
---
# <a name="numpunct-class"></a>numpunct — Klasa

Szablon klasy opisujący obiekt, który może służyć jako aspekt lokalny `CharType` do opisywania sekwencji typu używanego do reprezentowania informacji o formatowaniu i interpunkcji wyrażeń liczbowych i logicznych.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType>
class numpunct : public locale::facet;
```

### <a name="parameters"></a>Parametry

*Chartype*\
Typ używany w programie do kodowania znaków w ustawieniach regionalnych.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba uzyskania dostępu do przechowywanej wartości przechowuje unikatową wartość dodatnią w **identyfikatorze.**

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[numpunct (numpunct)](#numpunct)|Konstruktor obiektów typu `numpunct`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[Char_type](#char_type)|Typ opisujący znak używany przez ustawienie regionalne.|
|[string_type](#string_type)|Typ opisujący ciąg zawierający znaki `CharType`typu .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[decimal_point](#decimal_point)|Zwraca element ustawień regionalnych używany jako separator dziesiętny.|
|[do_decimal_point](#do_decimal_point)|Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana w celu zwrócenia elementu specyficznego dla ustawień regionalnych używanego jako separator dziesiętny.|
|[do_falsename](#do_falsename)|Chroniona funkcja wirtualnego elementu członkowskiego, która jest wywoływana w celu zwrócenia ciągu do użycia jako tekstowej reprezentacji wartości **false**.|
|[do_grouping](#do_grouping)|Chroniona funkcja wirtualna elementu członkowskiego, wywoływana w celu zwrócenia reguły specyficznej dla ustawień regionalnych, aby określić sposób grupowania cyfr na lewo od każdego znaku dziesiętnego.|
|[do_thousands_sep](#do_thousands_sep)|Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana w celu zwrócenia elementu specyficznego dla ustawień regionalnych używanego jako separator tysięczny.|
|[do_truename](#do_truename)|Chroniona funkcja wirtualnego elementu członkowskiego, która jest wywoływana w celu zwrócenia ciągu do użycia jako tekstowej reprezentacji wartości **true**.|
|[nazwa falsename](#falsename)|Zwraca ciąg, który ma być używany jako tekstowa reprezentacja wartości **false**.|
|[Grupowanie](#grouping)|Zwraca regułę specyficzną dla ustawień regionalnych określającą sposób grupowania cyfr na lewo od każdego znaku dziesiętnego.|
|[thousands_sep](#thousands_sep)|Zwraca element specyficzny dla ustawień regionalnych używany jako separator tysięczny.|
|[nazwa truename](#truename)|Zwraca ciąg, który ma być używany jako tekstowa reprezentacja wartości **true**.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ustawień regionalnych

**Przestrzeń nazw:** std

## <a name="numpunctchar_type"></a><a name="char_type"></a>numpunct::char_type

Typ opisujący znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu **CharType.**

## <a name="numpunctdecimal_point"></a><a name="decimal_point"></a>numpunct::decimal_point

Zwraca element ustawień regionalnych używany jako separator dziesiętny.

```cpp
CharType decimal_point() const;
```

### <a name="return-value"></a>Wartość zwracana

Element specyficzny dla ustawień regionalnych do użycia jako przecinka dziesiętnego.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_decimal_point](#do_decimal_point).

### <a name="example"></a>Przykład

```cpp
// numpunct_decimal_point.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const numpunct <char> &npunct =
   use_facet <numpunct <char> >( loc);
   cout << loc.name( ) << " decimal point "<<
   npunct.decimal_point( ) << endl;
   cout << loc.name( ) << " thousands separator "
   << npunct.thousands_sep( ) << endl;
};
```

```Output
German_Germany.1252 decimal point ,
German_Germany.1252 thousands separator .
```

## <a name="numpunctdo_decimal_point"></a><a name="do_decimal_point"></a>numpunct::do_decimal_point

Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana w celu zwrócenia elementu specyficznego dla ustawień regionalnych używanego jako separator dziesiętny.

```cpp
virtual CharType do_decimal_point() const;
```

### <a name="return-value"></a>Wartość zwracana

Element specyficzny dla ustawień regionalnych do użycia jako przecinka dziesiętnego.

### <a name="example"></a>Przykład

Zobacz przykład [decimal_point](#decimal_point), gdzie funkcja wirtualnego elementu `decimal_point`członkowskiego jest wywoływana przez .

## <a name="numpunctdo_falsename"></a><a name="do_falsename"></a>numpunct::do_falsename

Funkcja chronionego wirtualnego elementu członkowskiego zwraca sekwencję, która ma być używana jako tekstowa reprezentacja wartości **false**.

```cpp
virtual string_type do_falsename() const;
```

### <a name="return-value"></a>Wartość zwracana

Ciąg zawierający sekwencję, która ma być używana jako tekstowa reprezentacja wartości **false**.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca ciąg "false", aby reprezentować wartość **false** we wszystkich ustawieniach regionalnych.

### <a name="example"></a>Przykład

Zobacz przykład [falsename](#falsename), gdzie funkcja wirtualnego `falsename`elementu członkowskiego jest wywoływana przez .

## <a name="numpunctdo_grouping"></a><a name="do_grouping"></a>numpunct::do_grouping

Chroniona funkcja wirtualna elementu członkowskiego, wywoływana w celu zwrócenia reguły specyficznej dla ustawień regionalnych, aby określić sposób grupowania cyfr na lewo od każdego znaku dziesiętnego.

```cpp
virtual string do_grouping() const;
```

### <a name="return-value"></a>Wartość zwracana

Reguła specyficzna dla ustawień regionalnych określająca sposób grupowania cyfr po lewej stronie dowolnego przecinka dziesiętnego.

### <a name="remarks"></a>Uwagi

Chroniona funkcja wirtualna elementu członkowskiego zwraca regułę specyficzną dla ustawień regionalnych, aby określić sposób grupowania cyfr na lewo od każdego separatora dziesiętnego. Kodowanie jest takie samo jak w przypadku **lconv::grouping**.

### <a name="example"></a>Przykład

Zobacz przykład [grupowania,](#grouping)gdzie funkcja wirtualnego `grouping`elementu członkowskiego jest wywoływana przez .

## <a name="numpunctdo_thousands_sep"></a><a name="do_thousands_sep"></a>numpunct::do_thousands_sep

Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana w celu zwrócenia elementu specyficznego dla ustawień regionalnych używanego jako separator tysięczny.

```cpp
virtual CharType do_thousands_sep() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca element specyficzny dla ustawień regionalnych używany jako separator tysięczny.

### <a name="remarks"></a>Uwagi

Funkcja chronionego elementu członkowskiego wirtualnego zwraca element `CharType` specyficzny dla ustawień regionalnych typu, który ma być używany jako separator grupy po lewej stronie dowolnego przecinka dziesiętnego.

### <a name="example"></a>Przykład

Zobacz przykład [thousands_sep](#thousands_sep), gdzie funkcja wirtualnego elementu `thousands_sep`członkowskiego jest wywoływana przez .

## <a name="numpunctdo_truename"></a><a name="do_truename"></a>numpunct::do_truename

Chroniona funkcja wirtualnego elementu członkowskiego, która jest wywoływana w celu zwrócenia ciągu do użycia jako tekstowej reprezentacji wartości **true**.

```cpp
virtual string_type do_truename() const;
```

### <a name="remarks"></a>Uwagi

Ciąg używany jako tekstowa reprezentacja wartości **true**.

Wszystkie ustawienia regionalne zwracają ciąg "true", aby reprezentować wartość **true**.

### <a name="example"></a>Przykład

Zobacz przykład [truename](#truename), gdzie funkcja wirtualnego `truename`elementu członkowskiego jest wywoływana przez .

## <a name="numpunctfalsename"></a><a name="falsename"></a>numpunct::falsename

Zwraca ciąg, który ma być używany jako tekstowa reprezentacja wartości **false**.

```cpp
string_type falsename() const;
```

### <a name="return-value"></a>Wartość zwracana

Ciąg zawierający sekwencję `CharType`s do użycia jako tekstowa reprezentacja wartości **false**.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca ciąg "false", aby reprezentować wartość **false** we wszystkich ustawieniach regionalnych.

Funkcja elementu członkowskiego zwraca [do_falsename](#do_falsename).

### <a name="example"></a>Przykład

```cpp
// numpunct_falsename.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "English" );

   const numpunct <char> &npunct = use_facet <numpunct <char> >( loc );
   cout << loc.name( ) << " truename "<< npunct.truename( ) << endl;
   cout << loc.name( ) << " falsename "<< npunct.falsename( ) << endl;

   locale loc2( "French" );
   const numpunct <char> &npunct2 = use_facet <numpunct <char> >(loc2);
   cout << loc2.name( ) << " truename "<< npunct2.truename( ) << endl;
   cout << loc2.name( ) << " falsename "<< npunct2.falsename( ) << endl;
}
```

```Output
English_United States.1252 truename true
English_United States.1252 falsename false
French_France.1252 truename true
French_France.1252 falsename false
```

## <a name="numpunctgrouping"></a><a name="grouping"></a>numpunct::grupowanie

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
// numpunct_grouping.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany");

   const numpunct <char> &npunct =
       use_facet < numpunct <char> >( loc );
   for (unsigned int i = 0; i < npunct.grouping( ).length( ); i++)
   {
      cout << loc.name( ) << " international grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(npunct.grouping ( )[i])
           << endl;
   }
}
```

```Output
German_Germany.1252 international grouping:
the 0th group to the left of the radix character is of size 3
```

## <a name="numpunctnumpunct"></a><a name="numpunct"></a>numpunct::numpunct

Konstruktor obiektów typu `numpunct`.

```cpp
explicit numpunct(size_t _Refs = 0);
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

Konstruktor inicjuje swój obiekt bazowy`_Refs`za pomocą **ustawień regionalnych::**[aspekt](../standard-library/locale-class.md#facet_class)( ).

## <a name="numpunctstring_type"></a><a name="string_type"></a>numpunct::string_type

Typ opisujący ciąg zawierający znaki typu **CharType**.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [basic_string](../standard-library/basic-string-class.md) których obiekty mogą przechowywać kopie sekwencji znaków interpunkcyjnych.

## <a name="numpunctthousands_sep"></a><a name="thousands_sep"></a>numpunct::thousands_sep

Zwraca element specyficzny dla ustawień regionalnych używany jako separator tysięczny.

```cpp
CharType thousands_sep() const;
```

### <a name="return-value"></a>Wartość zwracana

Element specyficzny dla ustawień regionalnych do użycia jako separator tysięcy.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_thousands_sep](#do_thousands_sep).

### <a name="example"></a>Przykład

```cpp
// numpunct_thou_sep.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const numpunct <char> &npunct =
   use_facet < numpunct < char > >( loc );
   cout << loc.name( ) << " decimal point "<<
   npunct.decimal_point( ) << endl;
   cout << loc.name( ) << " thousands separator "
   << npunct.thousands_sep( ) << endl;
};
```

```Output
German_Germany.1252 decimal point ,
German_Germany.1252 thousands separator .
```

## <a name="numpuncttruename"></a><a name="truename"></a>numpunct::truename

Zwraca ciąg, który ma być używany jako tekstowa reprezentacja wartości **true**.

```cpp
string_type falsename() const;
```

### <a name="return-value"></a>Wartość zwracana

Ciąg używany jako tekstowa reprezentacja wartości **true**.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_truename](#do_truename).

Wszystkie ustawienia regionalne zwracają ciąg "true", aby reprezentować wartość **true**.

### <a name="example"></a>Przykład

```cpp
// numpunct_truename.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "English" );

   const numpunct < char> &npunct = use_facet <numpunct <char> >( loc );
   cout << loc.name( ) << " truename "<< npunct.truename( ) << endl;
   cout << loc.name( ) << " falsename "<< npunct.falsename( ) << endl;

   locale loc2("French");
   const numpunct <char> &npunct2 = use_facet <numpunct <char> >( loc2 );
   cout << loc2.name( ) << " truename "<< npunct2.truename( ) << endl;
   cout << loc2.name( ) << " falsename "<< npunct2.falsename( ) << endl;
}
```

```Output
English_United States.1252 truename true
English_United States.1252 falsename false
French_France.1252 truename true
French_France.1252 falsename false
```

## <a name="see-also"></a>Zobacz też

[\<>ustawień regionalnych](../standard-library/locale.md)\
[klasa facet](../standard-library/locale-class.md#facet_class)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
