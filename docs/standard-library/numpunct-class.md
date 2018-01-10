---
title: "numpunct — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
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
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7cd59fec5d8b5b2a6a05634242e0506688422f81
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="numpunct-class"></a>numpunct — Klasa
Szablon klasy, która opisuje obiekt, który może służyć jako lokalnego aspektu do opisywania sekwencji typu `CharType` używany do reprezentowania informacje dotyczące formatowania i znaków interpunkcyjnych wyrażeń liczbowych i logicznych.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class CharType>  
class numpunct : public locale::facet;  
```  
  
#### <a name="parameters"></a>Parametry  
 `CharType`  
 Typ używany w programie do kodowania znaków w ustawieniach regionalnych.  
  
## <a name="remarks"></a>Uwagi  
 Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba jej wartości przechowywanej dostępu są przechowywane w unikatową wartość dodatnią **identyfikator.**  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[numpunct —](#numpunct)|Konstruktor dla obiektów typu `numpunct`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#char_type)|Typ opisujący znak używany przez ustawienie regionalne.|  
|[STRING_TYPE](#string_type)|Typ, który opisuje ciąg zawierający znaki typu `CharType`.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[decimal_point](#decimal_point)|Zwraca element ustawień regionalnych używany jako separator dziesiętny.|  
|[do_decimal_point](#do_decimal_point)|Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana w celu zwrócenia elementu specyficznego dla ustawień regionalnych używanego jako separator dziesiętny.|  
|[do_falsename](#do_falsename)|A chronione wirtualnej funkcji członkowskiej wywoływaną w taki sposób, aby zwracało ciąg do użycia jako wartości reprezentacji tekstu `false`.|  
|[do_grouping](#do_grouping)|Chroniona funkcja wirtualna elementu członkowskiego, wywoływana w celu zwrócenia reguły specyficznej dla ustawień regionalnych, aby określić sposób grupowania cyfr na lewo od każdego znaku dziesiętnego.|  
|[do_thousands_sep](#do_thousands_sep)|Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana w celu zwrócenia elementu specyficznego dla ustawień regionalnych używanego jako separator tysięczny.|  
|[do_truename](#do_truename)|A chronione wirtualnej funkcji członkowskiej wywoływaną w taki sposób, aby zwracało ciąg do użycia jako wartości reprezentacji tekstu `true`.|  
|[falsename](#falsename)|Zwraca ciąg wykorzystywany jako wartości reprezentacji tekstu `false`.|  
|[Grupowanie](#grouping)|Zwraca regułę specyficzną dla ustawień regionalnych określającą sposób grupowania cyfr na lewo od każdego znaku dziesiętnego.|  
|[thousands_sep](#thousands_sep)|Zwraca element specyficzny dla ustawień regionalnych używany jako separator tysięczny.|  
|[truename](#truename)|Zwraca ciąg wykorzystywany jako wartości reprezentacji tekstu `true`.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<ustawień regionalnych >  
  
 **Namespace:** Standard  
  
##  <a name="char_type"></a>numpunct::char_type  
 Typ opisujący znak używany przez ustawienie regionalne.  
  
```  
typedef CharType char_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem parametru szablonu **CharType.**  
  
##  <a name="decimal_point"></a>numpunct::decimal_point  
 Zwraca element ustawień regionalnych używany jako separator dziesiętny.  
  
```  
CharType decimal_point() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Element ustawień regionalnych ma być używana jako separatorem dziesiętnym.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca [do_decimal_point](#do_decimal_point).  
  
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
  
##  <a name="do_decimal_point"></a>numpunct::do_decimal_point  
 Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana w celu zwrócenia elementu specyficznego dla ustawień regionalnych używanego jako separator dziesiętny.  
  
```  
virtual CharType do_decimal_point() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Element ustawień regionalnych ma być używana jako separatorem dziesiętnym.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [decimal_point](#decimal_point), w którym funkcja wirtualny element członkowski jest wywoływana przez `decimal_point`.  
  
##  <a name="do_falsename"></a>numpunct::do_falsename  
 Funkcja chroniony wirtualny element członkowski zwraca sekwencji można użyć jako wartości reprezentacji tekst **false**.  
  
```  
virtual string_type do_falsename() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ciąg zawierający sekwencji można użyć jako wartości reprezentacji tekst **false**.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca ciąg "false", do reprezentowania wartości **false** wszystkich ustawień regionalnych.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [falsename](#falsename), w którym funkcja wirtualny element członkowski jest wywoływana przez `falsename`.  
  
##  <a name="do_grouping"></a>numpunct::do_grouping  
 Chroniona funkcja wirtualna elementu członkowskiego, wywoływana w celu zwrócenia reguły specyficznej dla ustawień regionalnych, aby określić sposób grupowania cyfr na lewo od każdego znaku dziesiętnego.  
  
```  
virtual string do_grouping() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Reguła specyficzne dla ustawień regionalnych określające sposób grupowania cyfr na lewo od dowolnego punktu dziesiętnego.  
  
### <a name="remarks"></a>Uwagi  
 Chroniona funkcja wirtualna elementu członkowskiego zwraca regułę specyficzną dla ustawień regionalnych, aby określić sposób grupowania cyfr na lewo od każdego separatora dziesiętnego. Kodowanie jest taka sama, jak w przypadku **lconv::grouping**.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [grupowanie](#grouping), w którym funkcja wirtualny element członkowski jest wywoływana przez **grupowanie**.  
  
##  <a name="do_thousands_sep"></a>numpunct::do_thousands_sep  
 Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana w celu zwrócenia elementu specyficznego dla ustawień regionalnych używanego jako separator tysięczny.  
  
```  
virtual CharType do_thousands_sep() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca element specyficzny dla ustawień regionalnych używany jako separator tysięczny.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja chroniony wirtualny element członkowski zwraca element ustawień regionalnych typu **CharType** do użycia jako separator grupy na lewo od dowolnego punktu dziesiętnego.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [thousands_sep](#thousands_sep), w którym funkcja wirtualny element członkowski jest wywoływana przez `thousands_sep`.  
  
##  <a name="do_truename"></a>numpunct::do_truename  
 A chronione wirtualnej funkcji członkowskiej wywoływaną w taki sposób, aby zwracało ciąg do użycia jako wartości reprezentacji tekst **true**.  
  
```  
virtual string_type do_truename() const;
```  
  
### <a name="remarks"></a>Uwagi  
 Ciąg do użycia jako wartości reprezentacji tekst **true**.  
  
 Wszystkich ustawień regionalnych zwrócił ciągu "true", do reprezentowania wartości **true**.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [truename](#truename), w którym funkcja wirtualny element członkowski jest wywoływana przez `truename`.  
  
##  <a name="falsename"></a>numpunct::falsename  
 Zwraca ciąg wykorzystywany jako wartości reprezentacji tekst **false**.  
  
```  
string_type falsename() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ciąg zawierający sekwencji **CharType**s ma być używana jako reprezentacja tekstowa typu wartość **false**.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca ciąg "false", do reprezentowania wartości **false** wszystkich ustawień regionalnych.  
  
 Funkcja członkowska zwraca [do_falsename](#do_falsename).  
  
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
  
##  <a name="grouping"></a>numpunct::GROUPING  
 Zwraca regułę specyficzną dla ustawień regionalnych określającą sposób grupowania cyfr na lewo od każdego znaku dziesiętnego.  
  
```  
string grouping() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Reguła specyficzne dla ustawień regionalnych określające sposób grupowania cyfr na lewo od dowolnego punktu dziesiętnego.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca [do_grouping](#do_grouping).  
  
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
  
##  <a name="numpunct"></a>numpunct::numpunct  
 Konstruktor dla obiektów typu `numpunct`.  
  
```  
explicit numpunct(size_t _Refs = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `_Refs`  
 Wartość całkowita używany do określania typu zarządzania pamięci dla obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Możliwe wartości `_Refs` i ich znaczenie są:  
  
-   0: okres istnienia obiektu zarządza ustawieniami regionalnymi, które zawierałoby proces.  
  
-   1: okres istnienia obiektu musi być zarządzane ręcznie.  
  
-   \>1: te wartości są niezdefiniowane.  
  
 Nie bezpośredniego przykładów to możliwe, ponieważ destruktor jest chroniony.  
  
 Konstruktor inicjuje jego obiektu podstawowego z **locale::**[aspektu](../standard-library/locale-class.md#facet_class)( `_Refs`).  
  
##  <a name="string_type"></a>numpunct::STRING_TYPE  
 Typ, który opisuje ciąg zawierający znaki typu **CharType**.  
  
```  
typedef basic_string<CharType, Traits, Allocator> string_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano specjalizacji szablonu klasy [basic_string —](../standard-library/basic-string-class.md) obiektów, których można przechowywać kopie sekwencje znaków interpunkcyjnych.  
  
##  <a name="thousands_sep"></a>numpunct::thousands_sep  
 Zwraca element specyficzny dla ustawień regionalnych używany jako separator tysięczny.  
  
```  
CharType thousands_sep() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Element ustawień regionalnych ma być używana jako tysięcy separatora.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca [do_thousands_sep](#do_thousands_sep).  
  
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
  
##  <a name="truename"></a>numpunct::truename  
 Zwraca ciąg wykorzystywany jako wartości reprezentacji tekst **true**.  
  
```  
string_type falsename() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ciąg do użycia jako wartości reprezentacji tekst **true**.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca [do_truename](#do_truename).  
  
 Wszystkich ustawień regionalnych zwrócił ciągu "true", do reprezentowania wartości **true**.  
  
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
 [\<Ustawienia regionalne >](../standard-library/locale.md)   
 [facet — klasa](../standard-library/locale-class.md#facet_class)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

