---
title: "moneypunct — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8a9d1d621d9969d47976911bf52724c29888594d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="moneypunct-class"></a>moneypunct — Klasa
Klasa szablonu opisuje obiekt, który może służyć jako zestaw reguł ustawienia regionalne do opisywania sekwencji typu `CharType` używany do reprezentowania pieniężnego pole wejściowe lub pole pieniężne danych wyjściowych. Jeśli parametr szablonu `Intl` jest `true`, międzynarodowych konwencji są przestrzegane.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class CharType, bool Intl>  
class moneypunct;  
```  
  
#### <a name="parameters"></a>Parametry  
 `CharType`  
 Typ używany w programie do kodowania znaków.  
  
 `Intl`  
 Flaga określająca, czy międzynarodowe konwencje mają być przestrzegane.  
  
## <a name="remarks"></a>Uwagi  
 Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba jej wartości przechowywanej dostępu są przechowywane w unikatową wartość dodatnią **identyfikator.**  
  
 Stała wewnętrzna obiektu statycznego przechowuje wartość parametru szablonu **wewnętrzna**.  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[moneypunct](#moneypunct)|Konstruktor obiektów typu `moneypunct`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#char_type)|Typ opisujący znak używany przez ustawienie regionalne.|  
|[string_type](#string_type)|Typ, który opisuje ciąg zawierający znaki typu `CharType`.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
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
 **Nagłówek:** \<ustawień regionalnych >  
  
 **Namespace:** Standard  
  
##  <a name="char_type"></a>  moneypunct::char_type  
 Typ opisujący znak używany przez ustawienie regionalne.  
  
```  
typedef CharType char_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem parametru szablonu **CharType**.  
  
##  <a name="curr_symbol"></a>  moneypunct::curr_symbol  
 Zwraca sekwencję elementów specyficzną dla danych ustawień regionalnych w celu wykorzystania jako symbol waluty.  
  
```  
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
  
##  <a name="decimal_point"></a>  moneypunct::decimal_point  
 Zwraca sekwencję elementów specyficzną dla danych ustawień regionalnych w celu wykorzystania jako symbol separatora dziesiętnego.  
  
```  
CharType decimal_point() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Sekwencja specyficzne dla ustawień regionalnych elementy do użycia jako symbol punktu dziesiętnego.  
  
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
  
##  <a name="do_curr_symbol"></a>  moneypunct::do_curr_symbol  
 Chroniona funkcja wirtualna elementu członkowskiego, która zwraca sekwencję elementów specyficznych dla ustawień regionalnych, używanych jako symbol waluty.  
  
```  
virtual string_type do_curr_symbol() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Sekwencja specyficzne dla ustawień regionalnych elementy do użycia jako symbol punktu dziesiętnego.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [curr_symbol](#curr_symbol), w którym funkcja wirtualny element członkowski jest wywoływana przez `curr_symbol`.  
  
##  <a name="do_decimal_point"></a>  moneypunct::do_decimal_point  
 Chronionych wirtualną funkcją członkowską zwracającą specyficzne dla ustawień regionalnych sekwencję elementów do użycia jako symbol punktu dziesiętnego.  
  
```  
virtual CharType do_decimal_point() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Sekwencja specyficzne dla ustawień regionalnych elementy do użycia jako symbol punktu dziesiętnego.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [decimal_point](#decimal_point), w którym funkcja wirtualny element członkowski jest wywoływana przez `decimal_point`.  
  
##  <a name="do_frac_digits"></a>  moneypunct::do_frac_digits  
 Funkcja chroniony element członkowski wirtualnego, która zwraca liczbę ustawień regionalnych liczbę miejsc po przecinku do wyświetlenia na prawo od dowolnego punktu dziesiętnego.  
  
```  
virtual int do_frac_digits() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Specyficzne dla ustawień regionalnych liczba liczbę miejsc po przecinku do wyświetlenia na prawo od dowolnego punktu dziesiętnego.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [frac_digits](#frac_digits), w którym funkcja wirtualny element członkowski jest wywoływana przez `frac_digits`.  
  
##  <a name="do_grouping"></a>  moneypunct::do_grouping  
 Chronione wirtualną funkcją członkowską zwracającą regułę specyficznych określające sposób grupowania cyfr na lewo od dowolnego punktu dziesiętnego.  
  
```  
virtual string do_grouping() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Reguła specyficzne dla ustawień regionalnych określające sposób grupowania cyfr na lewo od dowolnego punktu dziesiętnego.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [grupowanie](#grouping), w którym funkcja wirtualny element członkowski jest wywoływana przez **grupowanie**.  
  
##  <a name="do_neg_format"></a>  moneypunct::do_neg_format  
 Chroniona funkcja wirtualna elementu członkowskiego, wywoływana w celu zwrócenia reguły specyficznej dla ustawień regionalnych przy formatowaniu danych wyjściowych z kwotami ujemnymi.  
  
```  
virtual pattern do_neg_format() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Chroniony element członkowski wirtualnego funkcja regułę specyficznych określające sposób generowania pola pieniężne danych wyjściowych dla liczbą ujemną. Każdy z czterech elementy **pattern::field** może mieć wartości:  
  
- **Brak** odpowiada zero lub więcej spacji lub wygenerowanie nothing.  
  
- **znak** zgodny lub wygenerowanie znak dodatnią lub ujemną.  
  
- **miejsce** odpowiada zero lub więcej spacji lub wygenerowanie spacją.  
  
- **symbol** zgodny lub wygenerowanie symbol waluty.  
  
- **wartość** zgodny lub wygenerowanie wartość pieniężną.  
  
 Składniki pola pieniężne dane wyjściowe są generowane i składniki pieniężnego pole wejściowe są dopasowywane w kolejności, w którym te elementy są wyświetlane w **pattern::field**. Wartości **znak**, **symbol**, **wartość**oraz **Brak** lub **miejsca** musi występować dokładnie jeden raz. Wartość **Brak** nie musi występować jako pierwszy. Przestrzeni wartości **musi** nie są wyświetlane pierwszego lub ostatniego. Jeśli **wewnętrzna** ma wartość true, kolejność jest **symbol**, **znak**, **Brak**, następnie **wartość**.  
  
 Wersja szablonu `moneypunct` \< **CharType**, **wewnętrzna**> zwraca `{` **money_base::symbol**, **money_ Base::sign**, **money_base::value**, **money_base::none**`}`.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [neg_format](#neg_format), w którym funkcja wirtualny element członkowski jest wywoływana przez `neg_format`.  
  
##  <a name="do_negative_sign"></a>  moneypunct::do_negative_sign  
 Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana w celu zwrócenia sekwencji elementów specyficznych dla ustawień regionalnych używanych jako symbol znaku ujemnego.  
  
```  
virtual string_type do_negative_sign() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Sekwencja specyficzne dla ustawień regionalnych elementy do użycia jako symbolu wartości ujemnej.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [negative_sign](#negative_sign), w którym funkcja wirtualny element członkowski jest wywoływana przez `negative_sign`.  
  
##  <a name="do_pos_format"></a>  moneypunct::do_pos_format  
 Chroniona funkcja wirtualna elementu członkowskiego, wywoływana w celu zwrócenia reguły specyficznej dla ustawień regionalnych przy formatowaniu danych wyjściowych z kwotami dodatnimi.  
  
```  
virtual pattern do_pos_format() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Chroniony element członkowski wirtualnego funkcja regułę specyficznych określające sposób generowania pola pieniężne danych wyjściowych dla dodatnią wartość. (On również określa jak odpowiadające składniki pieniężnego pole wejściowe). Kodowanie jest taka sama, jak w przypadku [do_neg_format](#do_neg_format).  
  
 Wersja szablonu moneypunct —\< **CharType**, **Inputlterator**> zwraca `{` **money_base::symbol**, **pieniędzy _base::sign**, **money_base::value**, **money_base::none**`}`.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [pos_format](#pos_format), w którym funkcja wirtualny element członkowski jest wywoływana przez `pos_format`.  
  
##  <a name="do_positive_sign"></a>  moneypunct::do_positive_sign  
 Chronionych wirtualną funkcją członkowską zwracającą specyficzne dla ustawień regionalnych sekwencję elementów do użycia jako znak dodatni.  
  
```  
virtual string_type do_positive_sign() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Sekwencja specyficzne dla ustawień regionalnych elementy do użycia jako znak dodatni.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [positive_sign](#positive_sign), w którym funkcja wirtualny element członkowski jest wywoływana przez `positive_sign`.  
  
##  <a name="do_thousands_sep"></a>  moneypunct::do_thousands_sep  
 Chroniony element członkowski wirtualnego funkcja zwraca element ustawień regionalnych do użycia jako separator grupy na lewo od dowolnego punktu dziesiętnego.  
  
```  
virtual CharType do_thousands_sep() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Element ustawień regionalnych do użycia jako separator grupy na lewo od dowolnego punktu dziesiętnego.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [thousands_sep](#thousands_sep), w którym funkcja wirtualny element członkowski jest wywoływana przez `thousands_sep`.  
  
##  <a name="frac_digits"></a>  moneypunct::frac_digits  
 Zwraca specyficzną dla ustawień regionalnych liczbę cyfr, które mają być wyświetlane z prawej strony każdego znaku dziesiętnego.  
  
```  
int frac_digits() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Specyficzne dla ustawień regionalnych liczba liczbę miejsc po przecinku do wyświetlenia na prawo od dowolnego punktu dziesiętnego.  
  
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
  
##  <a name="grouping"></a>  moneypunct::GROUPING  
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
  
##  <a name="moneypunct"></a>  moneypunct::moneypunct  
 Konstruktor obiektów typu `moneypunct`.  
  
```  
explicit moneypunct(size_t _Refs = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `_Refs`  
 Wartość całkowita używany do określania typu zarządzania pamięci dla obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Możliwe wartości `_Refs` i ich znaczenie są:  
  
-   0: okres istnienia obiektu zarządza ustawieniami regionalnymi, które zawierałoby proces.  
  
-   1: okres istnienia obiektu musi być zarządzane ręcznie.  
  
-   \> 1: te wartości są niezdefiniowane.  
  
 Nie bezpośredniego przykładów to możliwe, ponieważ destruktor jest chroniony.  
  
 Konstruktor inicjuje jego obiektu podstawowego z [locale::facet](../standard-library/locale-class.md#facet_class)(_ *Refs*).  
  
##  <a name="neg_format"></a>  moneypunct::neg_format  
 Zwraca regułę specyficzną dla ustawień regionalnych przy formatowaniu danych wyjściowych z kwotami ujemnymi.  
  
```  
pattern neg_format() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Reguła specyficzne dla ustawień regionalnych formatowanie danych wyjściowych z wartości ujemnych.  
  
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
  
##  <a name="negative_sign"></a>  moneypunct::negative_sign  
 Zwraca sekwencję elementów specyficzną dla danych ustawień regionalnych w celu wykorzystania jako symbol znaku ujemnego.  
  
```  
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
  
##  <a name="pos_format"></a>  moneypunct::pos_format  
 Zwraca regułę specyficzną dla ustawień regionalnych przy formatowaniu danych wyjściowych z kwotami dodatnimi.  
  
```  
pattern pos_format() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Reguła specyficzne dla ustawień regionalnych formatowanie danych wyjściowych z kwoty dodatnie.  
  
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
  
##  <a name="positive_sign"></a>  moneypunct::positive_sign  
 Zwraca sekwencję elementów specyficzną dla danych ustawień regionalnych w celu wykorzystania jako symbol znaku dodatniego.  
  
```  
string_type positive_sign() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Sekwencja specyficzne dla ustawień regionalnych elementy do użycia jako symbol dodatnią logowania.  
  
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
  
##  <a name="string_type"></a>  moneypunct::STRING_TYPE  
 Typ, który opisuje ciąg zawierający znaki typu **CharType**.  
  
```  
typedef basic_string<CharType, Traits, Allocator> string_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano specjalizacji szablonu klasy [basic_string —](../standard-library/basic-string-class.md) obiektów, których można przechowywać kopie sekwencje znaków interpunkcyjnych.  
  
##  <a name="thousands_sep"></a>  moneypunct::thousands_sep  
 Zwraca sekwencję elementów specyficzną dla danych ustawień regionalnych w celu wykorzystania jako symbol separatora tysięcznego.  
  
```  
CharType thousands_sep() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Specyficzne dla ustawień regionalnych sekwencję elementów do użycia jako tysięcy separatora  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [\<locale>](../standard-library/locale.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

