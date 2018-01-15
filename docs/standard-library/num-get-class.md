---
title: "num_get — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xlocnum/std::num_get
- locale/std::num_get::char_type
- locale/std::num_get::iter_type
- locale/std::num_get::do_get
- locale/std::num_get::get
dev_langs: C++
helpviewer_keywords:
- std::num_get [C++]
- std::num_get [C++], char_type
- std::num_get [C++], iter_type
- std::num_get [C++], do_get
- std::num_get [C++], get
ms.assetid: 9933735d-3918-4b17-abad-5fca2adc62d7
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7437bfe26f95b57584f294a7280540014e4a1b85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="numget-class"></a>num_get — Klasa
Szablon klasy, która opisuje obiekt, który może służyć jako zestaw reguł ustawienia regionalne do sterowania konwersje sekwencji typu `CharType` do wartości liczbowych.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>  
class num_get : public locale::facet;
```  
  
#### <a name="parameters"></a>Parametry  
 `CharType`  
 Typ używany w programie do kodowania znaków w ustawieniach regionalnych.  
  
 `InputIterator`  
 Typ iteratora, z którego liczbowe funkcje get odczytują swoje dane wejściowe.  
  
## <a name="remarks"></a>Uwagi  
 Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba jej wartości przechowywanej dostępu są przechowywane w unikatową wartość dodatnią **identyfikator.**  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[num_get —](#num_get)|Konstruktor dla obiektów typu `num_get` służące do wyodrębniania wartości liczbowe sekwencji.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#char_type)|Typ opisujący znak używany przez ustawienie regionalne.|  
|[iter_type](#iter_type)|Typ, który opisuje iterator danych wejściowych.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[do_get](#do_get)|Funkcja wirtualna wywoływana w celu wyodrębniania wartości liczbowej lub logicznej z sekwencji znaków.|  
|[get](#get)|Wyodrębnia wartość liczbową lub logiczną z sekwencji znaków.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<ustawień regionalnych >  
  
 **Namespace:** Standard  
  
##  <a name="char_type"></a>num_get::char_type  
 Typ opisujący znak używany przez ustawienie regionalne.  
  
```
typedef CharType char_type;
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem parametru szablonu **CharType**.  
  
##  <a name="do_get"></a>num_get::do_get  
 Funkcja wirtualna wywoływana w celu wyodrębniania wartości liczbowej lub logicznej z sekwencji znaków.  
  
```
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;
    
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned short& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned int& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Początek zakresu znaków, z której mają być odczytywane numer.  
  
 `last`  
 Koniec zakresu znaków, z której mają być odczytywane numer.  
  
 `_Iosbase`  
 [Ios_base —](../standard-library/ios-base-class.md) których flagi są używane w procesie konwersji.  
  
 `_State`  
 Stan, do których failbit (zobacz [ios_base::iostate](../standard-library/ios-base-class.md#iostate)) jest dodawany w przypadku awarii.  
  
 `val`  
 Wartość, która została odczytana.  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator po przeczytaniu wartość.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszej funkcji wirtualnych chroniony element członkowski  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;
```  
  
 Dopasowuje elementy sekwencyjnych, zaczynając od `first` w sekwencji `[first, last)` dopóki nie został rozpoznany kompletna, niepustym całkowitą wejściowy pola. Jeśli się powiedzie, konwertuje to pole na równoważną wartość jako typ `long`i przechowuje wyniki w `val`. Zwraca iteratora wyznaczenie pierwszy element poza numeryczne pole wejściowe. W przeciwnym razie funkcja przechowuje postanowienia `val` i ustawia `ios_base::failbit` w `state`. Zwraca iteratora wyznaczenie pierwszy element poza żadnych prefiksów pola wejściowego prawidłową liczbą całkowitą. W obu przypadkach jest równa wartości zwracanej `last`, zestawy funkcji `ios_base::eofbit` w `state`.  
  
 Pole wprowadzania liczba całkowita jest konwertowany przez te same reguły używane przez funkcje skanowania do dopasowywania i konwertowanie szereg `char` elementy z pliku. (Każda taka `char` element przyjęto, że do mapowania na równoważny element typu `Elem` przez prosty, jeden do jednego, mapowania.) Specyfikacja konwersji równoważne skanowania jest określane w następujący sposób:  
  
 Jeśli `iosbase.` [ios_base::flags](../standard-library/ios-base-class.md#flags)`() & ios_base::basefield == ios_base::`[oct](../standard-library/ios-functions.md#oct), specyfikacja konwersji jest `lo`.  
  
 Jeśli `iosbase.flags() & ios_base::basefield == ios_base::` [szesnastkowych](../standard-library/ios-functions.md#hex), specyfikacja konwersji jest `lx`.  
  
 Jeśli `iosbase.flags() & ios_base::basefield == 0`, specyfikacja konwersji jest `li`.  
  
 W przeciwnym razie specyfikacja konwersji jest `ld`.  
  
 Format liczby całkowitej pola wejściowego dalsze jest określany przez [aspektu ustawień regionalnych](../standard-library/locale-class.md#facet_class) `fac` zwrócony przez wywołanie [use_facet](../standard-library/locale-functions.md#use_facet) `<` [numpunct —](../standard-library/numpunct-class.md) `<Elem>(iosbase.` [ios_base::getloc](../standard-library/ios-base-class.md#getloc)`())`. W szczególności:  
  
 `fac.`[numpunct::grouping](../standard-library/numpunct-class.md#grouping) `()` określa sposób grupowania cyfr na lewo od dowolnego punktu dziesiętnego  
  
 `fac.`[numpunct::thousands_sep](../standard-library/numpunct-class.md#thousands_sep) `()` określa sekwencji, która oddziela grup cyfr w lewą stronę dowolnego punktu dziesiętnego.  
  
 Jeśli nie wystąpienia `fac.thousands_sep()` występują w numeryczne pole wejściowe, jest nałożone nie ograniczenia grupowania. W przeciwnym razie żadnych ograniczeń grupowania powodowanego przez `fac.grouping()` są wymuszane, a separatorów są usuwane, zanim nastąpi konwersji skanowania.  
  
 Czwarty funkcji wirtualnych chroniony element członkowski:  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;
```  
  
 zachowuje się taka sama jak pierwsza strona, z wyjątkiem tego, że zastępuje specyfikację konwersji `ld` z `lu`. Jeśli pomyślnie konwertuje numeryczne pole wejściowe do wartości typu `unsigned long` i zapisuje tę wartość w `val`.  
  
 Piąty funkcji wirtualnych chroniony element członkowski:  
  
```
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;
```  
  
 zachowuje się taka sama jak pierwsza strona, z wyjątkiem tego, że zastępuje specyfikację konwersji `ld` z `lld`. Jeśli pomyślnie konwertuje numeryczne pole wejściowe do wartości typu `long long` i zapisuje tę wartość w `val`.  
  
 Szóstym funkcji wirtualnych chroniony element członkowski:  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;
```  

 zachowuje się taka sama jak pierwsza strona, z wyjątkiem tego, że zastępuje specyfikację konwersji `ld` z `llu`. Jeśli pomyślnie konwertuje numeryczne pole wejściowe do wartości typu `unsigned long long` i zapisuje tę wartość w `val`.  
  
 Siódmego funkcji wirtualnych chroniony element członkowski:  
  
```
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;
```  
  
 działa tak samo jak pierwsze, z tą różnicą, że usiłują odpowiada pełną, niepustym pola wprowadzania liczb zmiennoprzecinkowych. `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point) `()` określa sekwencji, która oddziela cyfr liczbą całkowitą od cyfr ułamek. Specyfikator konwersji w równoważnych skanowania jest `lf`.  
  
 Ósmego funkcji wirtualnych chroniony element członkowski:  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;
```  
  
 działa tak samo jak pierwsze, z tą różnicą, że usiłują odpowiada pełną, niepustym pola wprowadzania liczb zmiennoprzecinkowych. `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point) `()` określa sekwencji, która oddziela cyfr liczbą całkowitą od cyfr ułamek. Specyfikator konwersji w równoważnych skanowania jest `lf`.  
  
 Dziewiąty funkcji wirtualnych chroniony element członkowski:  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;
```  
  
 zachowuje się taka sama jak ósmego, z wyjątkiem tego, że specyfikatora konwersji równoważne skanowania `Lf`.  
  
 Dziesiątego funkcji wirtualnych chroniony element członkowski:  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```  
  
 działa tak samo, pierwsza strona, z wyjątkiem tego, że specyfikatora konwersji równoważne skanowania `p`.  
  
 Ostatniej funkcji wirtualnych (jedenasta) chroniony element członkowski:  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```  
  
 działa tak samo jak pierwszy, z tą różnicą, że usiłują odpowiada pełną, niepustym wejściowych polem. Jeśli pomyślnie konwertuje logiczna pola wejściowego na wartość typu `bool` i zapisuje tę wartość w `val`.  
  
 Wartość logiczna pole wejściowe przyjmuje jeden z dwóch formach. Jeśli `iosbase.flags() & ios_base::` [boolalpha](../standard-library/ios-functions.md#boolalpha) ma wartość false, jest taka sama jak liczba całkowita pola wejściowego, z wyjątkiem tego, że skonwertowana wartość musi być 0 (FAŁSZ) lub 1 (PRAWDA). W przeciwnym razie sekwencja musi odpowiadać albo `fac.` [numpunct::falsename](../standard-library/numpunct-class.md#falsename) `()` (na FAŁSZ) lub `fac.` [numpunct::truename](../standard-library/numpunct-class.md#truename) `()` (w przypadku wartości true).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [uzyskać](#get), w którym funkcja wirtualny element członkowski jest wywoływana przez `do_get`.  
  
##  <a name="get"></a>num_get::Get  
 Wyodrębnia wartość liczbową lub logiczną z sekwencji znaków.  
  
```
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned short& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned int& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Początek zakresu znaków, z której mają być odczytywane numer.  
  
 `last`  
 Koniec zakresu znaków, z której mają być odczytywane numer.  
  
 `_Iosbase`  
 [Ios_base —](../standard-library/ios-base-class.md) których flagi są używane w procesie konwersji.  
  
 `_State`  
 Stan, do których failbit (zobacz [ios_base::iostate](../standard-library/ios-base-class.md#iostate)) jest dodawany w przypadku awarii.  
  
 `val`  
 Wartość, która została odczytana.  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator po przeczytaniu wartość.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie funkcje Członkowskie zwracają [do_get](#do_get)( `first`, `last`, `_Iosbase`, `_State`, `val`).  
  
 Pierwszej funkcji wirtualnych chroniony element członkowski próbuje dopasować sekwencyjnych elementy, rozpoczynając od pierwszego w sekwencji [ `first`, `last`) dopóki nie został rozpoznany kompletna, niepustym całkowitą wejściowy pola. Jeśli się powiedzie, konwertuje to pole na równoważną wartość jako typ **długi** i przechowuje wyniki w `val`. Zwraca iteratora wyznaczenie pierwszy element poza numeryczne pole wejściowe. W przeciwnym razie funkcja przechowuje postanowienia `val` i ustawia `ios_base::failbit` w _ *stanu*. Zwraca iteratora wyznaczenie pierwszy element poza żadnych prefiksów pola wejściowego prawidłową liczbą całkowitą. W obu przypadkach jest równa wartości zwracanej **ostatniego**, zestawy funkcji `ios_base::eofbit` w `_State`.  
  
 Pole wprowadzania liczba całkowita jest konwertowany przez te same reguły używane przez funkcje skanowania do dopasowywania i konwertowanie szereg `char` elementy z pliku. Każdy taki `char` element przyjęto, że do mapowania na równoważny element typu **CharType** mapowanie proste i jeden do jednego. Specyfikacja konwersji równoważne skanowania jest określane w następujący sposób:  
  
-   Jeśli **iosbase**. [flagi](../standard-library/ios-base-class.md#flags) & `ios_base::basefield` == `ios_base::`[oct](../standard-library/ios-functions.md#oct), specyfikacja konwersji jest **lo**.  
  
-   Jeśli **iosbase.flags** & **ios_base::basefield** == `ios_base::`[szesnastkowych](../standard-library/ios-functions.md#hex), specyfikacja konwersji jest **lx** .  
  
-   Jeśli **iosbase.flags** & **ios_base::basefield** == 0, specyfikacja konwersji jest `li`.  
  
-   W przeciwnym razie specyfikacja konwersji jest **ld**.  
  
 Format liczby całkowitej pola wejściowego dalsze jest określany przez [aspektu ustawień regionalnych](../standard-library/locale-class.md#facet_class)**fac** zwrócony przez wywołanie [use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct — ](../standard-library/numpunct-class.md) \< **Elementu**> ( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)). W szczególności:  
  
- **FAC**. [Grupowanie](../standard-library/numpunct-class.md#grouping) określa sposób grupowania cyfr na lewo od dowolnego punktu dziesiętnego.  
  
- **FAC**. [thousands_sep](../standard-library/numpunct-class.md#thousands_sep) określa sekwencji, która oddziela grup cyfr w lewą stronę dowolnego punktu dziesiętnego.  
  
 Jeśli nie wystąpienia **fac**. `thousands_sep`występuje w numeryczne pole wejściowe, jest nałożone nie ograniczenia grupowania. W przeciwnym razie żadnych ograniczeń grupowania powodowanego przez **fac**. **Grupowanie** są wymuszane, a separatorów są usuwane, zanim nastąpi konwersji skanowania.  
  
 Drugi funkcji wirtualnych chroniony element członkowski:  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;
```  
  
 zachowuje się taka sama jak pierwsza strona, z wyjątkiem tego, że zastępuje specyfikację konwersji **ld** z **lu**. Jeśli się powiedzie, konwertuje numeryczne pole wejściowe do wartości typu `unsigned long` i zapisuje tę wartość w `val`.  
  
 Trzeci funkcji wirtualnych chroniony element członkowski:  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;
```  
  
 działa tak samo jak pierwsze, z tą różnicą, że jej próbuje dopasować pełną, niepustym pola wprowadzania liczb zmiennoprzecinkowych. **FAC**. [decimal_point](../standard-library/numpunct-class.md#decimal_point) określa sekwencji, która oddziela cyfr liczbą całkowitą od cyfr ułamek. Specyfikator konwersji w równoważnych skanowania jest **lf**.  
  
 Czwarty funkcji wirtualnych chroniony element członkowski:  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;
```  
  
 działa tak samo trzeci, z wyjątkiem tego, że specyfikatora konwersji równoważne skanowania **Lf**.  
  
 Piąty funkcji wirtualnych chroniony element członkowski:  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```  
  
 działa tak samo, pierwsza strona, z wyjątkiem tego, że specyfikatora konwersji równoważne skanowania **p**.  
  
 Szóstym funkcji wirtualnych chroniony element członkowski:  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```  
  
 zachowuje się taka sama jak pierwsza strona, z tą różnicą, że go próbuje dopasować pełną, niepustym wejściowych polem. Jeśli pomyślnie konwertuje logiczna pola wejściowego na wartość typu `bool` i zapisuje tę wartość w `val`.  
  
 Wartość logiczna pole wejściowe przyjmuje jeden z dwóch formach. Jeśli **iosbase**. **flagi** & `ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) jest **false**, jest taka sama jak liczba całkowita pola wejściowego, z wyjątkiem tego, że skonwertowana wartość musi być albo 0 (dla  **FALSE**) lub 1 (dla **true**). W przeciwnym razie sekwencja musi odpowiadać albo **fac**. [falsename](../standard-library/numpunct-class.md#falsename) (dla **false**), lub **fac**. [truename](../standard-library/numpunct-class.md#truename) (dla **true**).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// num_get_get.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany" );  
  
   basic_stringstream<char> psz, psz2;  
   psz << "-1000,56";  
  
   ios_base::iostate st = 0;  
   long double fVal;  
   cout << use_facet <numpunct <char> >(loc).thousands_sep( ) << endl;  
  
   psz.imbue( loc );  
   use_facet <num_get <char> >  
   (loc).get( basic_istream<char>::_Iter( psz.rdbuf( ) ),  
           basic_istream<char>::_Iter(0), psz, st, fVal );  
  
   if ( st & ios_base::failbit )  
      cout << "money_get( ) FAILED" << endl;  
   else  
      cout << "money_get( ) = " << fVal << endl;  
}  
```  
  
##  <a name="iter_type"></a>num_get::iter_type  
 Typ, który opisuje iterator danych wejściowych.  
  
```
typedef InputIterator iter_type;
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem parametru szablonu **InputIterator**.  
  
##  <a name="num_get"></a>num_get::num_get  
 Konstruktor dla obiektów typu `num_get` służące do wyodrębniania wartości liczbowe sekwencji.  
  
```
explicit num_get(size_t _Refs = 0);
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
  
## <a name="see-also"></a>Zobacz też  
 [\<Ustawienia regionalne >](../standard-library/locale.md)   
 [facet — klasa](../standard-library/locale-class.md#facet_class)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



