---
title: "basic_string — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xstring/std::basic_string
- xstring/std::basic_string::allocator_type
- xstring/std::basic_string::const_iterator
- xstring/std::basic_string::const_pointer
- xstring/std::basic_string::const_reference
- xstring/std::basic_string::const_reverse_iterator
- xstring/std::basic_string::difference_type
- xstring/std::basic_string::iterator
- xstring/std::basic_string::npos
- xstring/std::basic_string::pointer
- xstring/std::basic_string::reference
- xstring/std::basic_string::reverse_iterator
- xstring/std::basic_string::size_type
- xstring/std::basic_string::traits_type
- xstring/std::basic_string::value_type
- xstring/std::basic_string::append
- xstring/std::basic_string::assign
- xstring/std::basic_string::at
- xstring/std::basic_string::back
- xstring/std::basic_string::begin
- xstring/std::basic_string::c_str
- xstring/std::basic_string::capacity
- xstring/std::basic_string::cbegin
- xstring/std::basic_string::cend
- xstring/std::basic_string::clear
- xstring/std::basic_string::compare
- xstring/std::basic_string::copy
- xstring/std::basic_string::crbegin
- xstring/std::basic_string::crend
- xstring/std::basic_string::_Copy_s
- xstring/std::basic_string::data
- xstring/std::basic_string::empty
- xstring/std::basic_string::end
- xstring/std::basic_string::erase
- xstring/std::basic_string::find
- xstring/std::basic_string::find_first_not_of
- xstring/std::basic_string::find_first_of
- xstring/std::basic_string::find_last_not_of
- xstring/std::basic_string::find_last_of
- xstring/std::basic_string::front
- xstring/std::basic_string::get_allocator
- xstring/std::basic_string::insert
- xstring/std::basic_string::length
- xstring/std::basic_string::max_size
- xstring/std::basic_string::pop_back
- xstring/std::basic_string::push_back
- xstring/std::basic_string::rbegin
- xstring/std::basic_string::rend
- xstring/std::basic_string::replace
- xstring/std::basic_string::reserve
- xstring/std::basic_string::resize
- xstring/std::basic_string::rfind
- xstring/std::basic_string::shrink_to_fit
- xstring/std::basic_string::size
- xstring/std::basic_string::substr
- xstring/std::basic_string::swap
dev_langs:
- C++
helpviewer_keywords:
- std::basic_string [C++]
- std::basic_string [C++], allocator_type
- std::basic_string [C++], const_iterator
- std::basic_string [C++], const_pointer
- std::basic_string [C++], const_reference
- std::basic_string [C++], const_reverse_iterator
- std::basic_string [C++], difference_type
- std::basic_string [C++], iterator
- std::basic_string [C++], npos
- std::basic_string [C++], pointer
- std::basic_string [C++], reference
- std::basic_string [C++], reverse_iterator
- std::basic_string [C++], size_type
- std::basic_string [C++], traits_type
- std::basic_string [C++], value_type
- std::basic_string [C++], append
- std::basic_string [C++], assign
- std::basic_string [C++], at
- std::basic_string [C++], back
- std::basic_string [C++], begin
- std::basic_string [C++], c_str
- std::basic_string [C++], capacity
- std::basic_string [C++], cbegin
- std::basic_string [C++], cend
- std::basic_string [C++], clear
- std::basic_string [C++], compare
- std::basic_string [C++], copy
- std::basic_string [C++], crbegin
- std::basic_string [C++], crend
- std::basic_string [C++], _Copy_s
- std::basic_string [C++], data
- std::basic_string [C++], empty
- std::basic_string [C++], end
- std::basic_string [C++], erase
- std::basic_string [C++], find
- std::basic_string [C++], find_first_not_of
- std::basic_string [C++], find_first_of
- std::basic_string [C++], find_last_not_of
- std::basic_string [C++], find_last_of
- std::basic_string [C++], front
- std::basic_string [C++], get_allocator
- std::basic_string [C++], insert
- std::basic_string [C++], length
- std::basic_string [C++], max_size
- std::basic_string [C++], pop_back
- std::basic_string [C++], push_back
- std::basic_string [C++], rbegin
- std::basic_string [C++], rend
- std::basic_string [C++], replace
- std::basic_string [C++], reserve
- std::basic_string [C++], resize
- std::basic_string [C++], rfind
- std::basic_string [C++], shrink_to_fit
- std::basic_string [C++], size
- std::basic_string [C++], substr
- std::basic_string [C++], swap
ms.assetid: a9c3e0a2-39bf-4c8a-b093-9abe30839591
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 895b0921785e29a49bd367c2676995ba9af8e309
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="basicstring-class"></a>basic_string — Klasa
Sekwencje kontrolowane przez obiekt klasy szablonu `basic_string` są klasy string Standard C++ i są zwykle nazywane ciągów, ale ich nie należy mylić z stylu języka C zerem ciągów używanych w całym standardowa biblioteka C++. Ciąg Standard C++ jest kontenerem, który umożliwia korzystanie z ciągi jako normalne typów, takich jak operacje porównania i łączenia, Iteratory algorytmów standardowa biblioteka C++ i kopiowanie i przypisywanie za pomocą klasy przydzielania pamięci zarządzanej. Jeśli trzeba przekonwertować ciąg Standard C++ do ciągu zerem stylu języka C, użyj [basic_string::c_str](#c_str) elementu członkowskiego.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>  
class basic_string;  
```  
  
#### <a name="parameters"></a>Parametry  
 `CharType`  
 Typ danych mają być przechowywane w ciągu jednego znaku. Standardowa biblioteka C++ zapewnia specjalizacje tej klasy szablonu z definicji typu [ciąg](../standard-library/string-typedefs.md#string) dla elementów typu `char`, [wstring](../standard-library/string-typedefs.md#wstring), dla `wchar_t`, [u16string](../standard-library/string-typedefs.md#u16string) dla `char16_t`, i [u32string](../standard-library/string-typedefs.md#u32string) dla `char32_t`.  
  
 `Traits`  
 Różne właściwości ważne **CharType** opisano elementy w specjalizacji basic_string — klasa **cech**. Wartość domyślna to `char_traits` <  `CharType`>.  
  
 `Allocator`  
 Typ reprezentujący obiekt alokatora przechowywane, który hermetyzuje szczegółowe informacje dotyczące alokacji ciągu i cofania alokacji pamięci. Wartość domyślna to **alokatora**< `CharType`>.  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[basic_string](#basic_string)|Tworzy ciąg, który jest pusta lub zainicjowane przez określonych znaków lub jest kopii całości lub części innego obiektu ciągu lub ciągu C.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[allocator_type](#allocator_type)|Typ reprezentujący `allocator` klasy dla obiekt ciągu.|  
|[const_iterator](#const_iterator)|Typem udostępniający iteratora dostęp losowy i są dostępne do odczytu `const` elementu w ciągu.|  
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do `const` elementu w ciągu.|  
|[const_reference](#const_reference)|Typ, który zawiera odwołanie do `const` element przechowywane w ciągu do odczytu i wykonywania `const` operacji.|  
|[const_reverse_iterator](#const_reverse_iterator)|Typ, który udostępnia iteratora dostępie swobodnym, który może odczytać `const` elementu w ciągu.|  
|[difference_type](#difference_type)|Typ, który udostępnia różnica między dwa Iteratory, które odwołują się do elementów w tym samym ciągu.|  
|[iterator](#iterator)|Typ, który udostępnia iteratora dostępie swobodnym, które mogą odczytywać lub modyfikować dowolny element w ciągu.|  
|[npos](#npos)|Wartością całkowitą bez znaku ustawiana na wartość -1, która wskazuje "nie można odnaleźć" lub "wszystkie pozostałe znaki" Jeśli funkcja wyszukiwania nie powiodło się.|  
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do elementu znaku w ciągu lub znak tablicy.|  
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu przechowywane w ciągu.|  
|[reverse_iterator](#reverse_iterator)|Typ, który udostępnia iteratora dostępie swobodnym, które mogą odczytywać lub modyfikować elementu w ciągu odwróconej.|  
|[size_type](#size_type)|Typu bez znaku całkowitą liczbę elementów w ciągu.|  
|[traits_type](#traits_type)|Typ dla cech znaków elementy przechowywane w ciągu.|  
|[value_type](#value_type)|Typ, który reprezentuje typ przechowywane w ciągu znaków.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[Dołącz](#append)|Dodaje znaki do końca ciągu.|  
|[Przypisz](#assign)|Przypisuje nowy wartości znakowych zawartość ciągu.|  
|[at](#at)|Zwraca odwołanie do elementu w określonej lokalizacji w ciągu.|  
|[back](#back)||  
|[begin](#begin)|Zwraca iteratora adresowania pierwszym elementem w ciągu.|  
|[c_str](#c_str)|Konwertuje wartość ciągu jako ciąg znaków zakończony znakiem null stylu języka C.|  
|[capacity](#capacity)|Zwraca największą liczbę elementów, które może być przechowywany w ciągu bez zwiększania alokacji pamięci ciągu.|  
|[cbegin](#cbegin)|Zwraca const iteratora adresowania pierwszym elementem w ciągu.|  
|[cend](#cend)|Zwraca iteratora const, który dotyczy lokalizacji pomyślne ostatnim elementem w ciągu.|  
|[Wyczyść](#clear)|Usuwa wszystkie elementy ciągu.|  
|[Porównaj](#compare)|Porównanie ciągu z określonego ciągu do określenia, czy dwa ciągi są takie same i jeśli jest lexicographically mniej niż drugi.|  
|[copy](#copy)|Kopiuje co najwyżej określoną liczbę znaków z indeksowanego pozycji w ciągu źródłowej do docelowej tablicy znaków. Przestarzałe. Użyj [basic_string::_Copy_s](#copy_s) zamiast tego.|  
|[crbegin](#crbegin)|Zwraca iteratora const, którego dotyczy pierwszym elementem w ciągu odwróconej.|  
|[crend](#crend)|Zwraca iteratora const, którego dotyczy lokalizacji pomyślne ostatnim elementem w ciągu odwróconej.|  
|[_Copy_s](#copy_s)|Kopiuje co najwyżej określoną liczbę znaków z indeksowanego pozycji w ciągu źródłowej do docelowej tablicy znaków.|  
|[Dane](#data)|Konwertuje wartość ciągu do tablicy znaków.|  
|[empty](#empty)|Sprawdza, czy ciąg zawiera znaki.|  
|[Koniec](#end)|Zwraca iteratora, którego dotyczy lokalizacji pomyślne ostatnim elementem w ciągu.|  
|[wymazywanie](#erase)|Usuwa element lub zakres elementów w ciągu od określonej pozycji.|  
|[Znajdź](#find)|Wyszukuje ciąg w kierunku do przodu dla pierwszego wystąpienia podciągu, który odpowiada określonej sekwencji znaków.|  
|[find_first_not_of](#find_first_not_of)|Wyszukiwanie za pomocą ciągu pierwszego znaku, który nie jest żadnym elementem określonego ciągu.|  
|[find_first_of](#find_first_of)|Wyszukiwanie za pomocą ciągu pierwszego znaku, który dopasowuje dowolny element określonego ciągu.|  
|[find_last_not_of](#find_last_not_of)|Wyszukiwanie za pomocą ciągu ostatni znak, który nie jest dowolny element określony ciąg.|  
|[find_last_of](#find_last_of)|Wyszukiwanie za pomocą ciągu ostatni znak, który jest elementem określonego ciągu.|  
|[Front](#front)|Zwraca odwołanie do pierwszego elementu w ciągu.|  
|[get_allocator](#get_allocator)|Zwraca kopię `allocator` obiekt używany do utworzenia ciągu.|  
|[insert](#insert)|Wstawia element lub liczba elementów lub zakres elementów do ciągu na określonej pozycji.|  
|[length](#length)|Zwraca bieżącą liczbę elementów w ciągu.|  
|[max_size](#max_size)|Zwraca maksymalną liczbę znaków, które mogą zawierać ciąg.|  
|[pop_back](#pop_back)|Usuwa ostatnim elementem w ciągu.|  
|[push_back](#push_back)|Dodaje element do końca ciągu.|  
|[rbegin](#rbegin)|Zwraca iteratora do pierwszego elementu w ciągu odwróconej.|  
|[rend](#rend)|Zwraca iteratora tego punktów tuż za ostatnim elementem w ciągu odwróconej.|  
|[Zamień](#replace)|Zamienia elementów w ciągu na określonej pozycji określonych znaków lub kopiowane z innych zakresów lub ciągów lub C ciągów znaków.|  
|[reserve](#reserve)|Ustawia przynajmniej tak duże, jak określonej liczby pojemności ciągu na liczbę.|  
|[Zmiana rozmiaru](#resize)|Określa nowy rozmiar ciągu, dołączane lub wymazywanie elementów zgodnie z potrzebami.|  
|[rfind](#rfind)|Wyszukuje ciąg w kierunku do tyłu dla pierwszego wystąpienia podciągu, który odpowiada określonej sekwencji znaków.|  
|[shrink_to_fit](#shrink_to_fit)|Odrzuca nadmiarowej pojemności ciągu.|  
|[Rozmiar](#size)|Zwraca bieżącą liczbę elementów w ciągu.|  
|[substr](#substr)|Kopiuje podciąg co najwyżej pewną liczbę znaków od początku ciągu, od określonej pozycji.|  
|[swap](#swap)|Wymiany zawartości dwóch ciągów.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator+=](#op_add_eq)|Dołącza znaków do ciągu.|  
|[operator=](#op_eq)|Przypisuje nowy wartości znakowych zawartość ciągu.|  
|[operator&#91;&#93;](#op_at)|Zawiera odwołanie do znaku z indeksem określonym w ciągu.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli funkcja jest proszony o Generowanie sekwencję dłużej niż [max_size](#max_size) elementów, funkcja zgłasza błąd długość przez zgłaszanie typu obiektu [length_error —](../standard-library/length-error-class.md).  
  
 Odwołania, wskaźniki i Iteratory, które określają elementy kontrolowanej sekwencji może stać się nieprawidłowy po wywołaniu dowolnej funkcji, które zmienia kontrolowanej sekwencji lub po pierwszym wywołaniu niż **const** funkcję elementu członkowskiego.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<ciąg >  
  
 **Namespace:** Standard  
  
##  <a name="allocator_type"></a>  basic_string::allocator_type  
 Typ, który reprezentuje klasę alokatora dla obiekt ciągu.  
  
```  
typedef Allocator allocator_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem parametru szablonu **alokatora**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_allocator_type.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   // The following lines declare objects  
   // that use the default allocator.  
   string s1;  
   basic_string <char>::allocator_type xchar = s1.get_allocator( );  
   // You can now call functions on the allocator class xchar used by s1  
}  
```  
  
##  <a name="append"></a>  basic_string::append  
 Dodaje znaki do końca ciągu.  
  
```  
basic_string<CharType, Traits, Allocator>& append(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& append(
    const value_type* ptr,  
    size_type count);

basic_string<CharType, Traits, Allocator>& append(
    const basic_string<CharType, Traits, Allocator>& str,  
    size_type _Off,  
    size_type count);

basic_string<CharType, Traits, Allocator>& append(
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& append(
    size_type count,   
    value_type _Ch);

template <class InputIterator>  
basic_string<CharType, Traits, Allocator>& append(
    InputIterator first,   
    InputIterator last);

basic_string<CharType, Traits, Allocator>& append(
    const_pointer first,  
    const_pointer last);

basic_string<CharType, Traits, Allocator>& append(
    const_iterator first,  
    const_iterator last);
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 C — ciąg do dołączenia.  
  
 `str`  
 Ciąg, którego znaki mają być dołączane.  
  
 `_Off`  
 Indeks część ciągu źródła dostarczanie znaków, które mają być dołączane.  
  
 `count`  
 Liczba znaków, które mają być dołączane, co najwyżej z ciągu źródła.  
  
 `_Ch`  
 Wartość znaku do dołączenia.  
  
 `first`  
 Iteratora wejściowych adresowania pierwszym elementem w zakresie do dołączenia.  
  
 `last`  
 Wejściowy iteratora, const_pointer lub const_iterator adresowania pozycji jedna poza ostatniego elementu w zakresie do dołączenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do obiektu ciąg dołączany znaków przekazany przez funkcję elementu członkowskiego.  
  
### <a name="remarks"></a>Uwagi  
 Znaki może zostać dołączone do ciągu za pomocą [+= — operator](#op_add_eq) lub funkcje Członkowskie **Dołącz** lub [push_back](#push_back). `operator+=` dołącza wartości jednym argumentem podczas argument wielu **Dołącz** określoną część ciągu można określić dodawania dzięki funkcji Członkowskich.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_append.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   // The first member function  
   // appending a C-string to a string  
   string str1a ( "Hello " );  
   cout << "The original string str1 is: " << str1a << endl;  
   const char *cstr1a = "Out There ";  
   cout << "The C-string cstr1a is: " << cstr1a << endl;  
   str1a.append ( cstr1a );  
   cout << "Appending the C-string cstr1a to string str1 gives: "   
        << str1a << "." << endl << endl;  
  
   // The second member function  
   // appending part of a C-string to a string  
   string str1b ( "Hello " );  
   cout << "The string str1b is: " << str1b << endl;  
   const char *cstr1b = "Out There ";  
   cout << "The C-string cstr1b is: " << cstr1b << endl;  
   str1b.append ( cstr1b , 3 );  
   cout << "Appending the 1st part of the C-string cstr1b "  
        << "to string str1 gives: " << str1b << "."   
        << endl << endl;  
  
   // The third member function  
   // appending part of one string to another  
   string str1c ( "Hello " ), str2c ( "Wide World " );  
   cout << "The string str2c is: " << str2c << endl;  
   str1c.append ( str2c , 5 , 5 );  
   cout << "The appended string str1 is: "   
        << str1c << "." << endl << endl;  
  
   // The fourth member function  
   // appending one string to another in two ways,  
   // comparing append and operator [ ]  
   string str1d ( "Hello " ), str2d ( "Wide " ), str3d ( "World " );  
   cout << "The  string str2d is: " << str2d << endl;  
   str1d.append ( str2d );  
   cout << "The appended string str1d is: "   
        << str1d << "." << endl;  
   str1d += str3d;  
   cout << "The doubly appended strig str1 is: "   
        << str1d << "." << endl << endl;  
  
   // The fifth member function  
   // appending characters to a string  
   string str1e ( "Hello " );  
   str1e.append ( 4 , '!' );  
   cout << "The string str1 appended with exclamations is: "   
        << str1e << endl << endl;  
  
   // The sixth member function  
   // appending a range of one string to another  
   string str1f ( "Hello " ), str2f ( "Wide World " );  
   cout << "The string str2f is: " << str2f << endl;  
   str1f.append ( str2f.begin ( ) + 5 , str2f.end ( ) - 1 );  
   cout << "The appended string str1 is: "   
        << str1f << "." << endl << endl;  
}  
```  
  
```Output  
The original string str1 is: Hello   
The C-string cstr1a is: Out There   
Appending the C-string cstr1a to string str1 gives: Hello Out There .  
  
The string str1b is: Hello   
The C-string cstr1b is: Out There   
Appending the 1st part of the C-string cstr1b to string str1 gives: Hello Out.  
  
The string str2c is: Wide World   
The appended string str1 is: Hello World.  
  
The  string str2d is: Wide   
The appended string str1d is: Hello Wide .  
The doubly appended strig str1 is: Hello Wide World .  
  
The string str1 appended with exclamations is: Hello !!!!  
  
The string str2f is: Wide World   
The appended string str1 is: Hello World.  
```  
  
##  <a name="assign"></a>  basic_string::ASSIGN  
 Przypisuje nowy wartości znakowych zawartość ciągu.  
  
```  
basic_string<CharType, Traits, Allocator>& assign(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& assign(
    const value_type* ptr,  
    size_type count);

basic_string<CharType, Traits, Allocator>& assign(
    const basic_string<CharType, Traits, Allocator>& str,  
    size_type off,   
    size_type count);

basic_string<CharType, Traits, Allocator>& assign(
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& assign(
    size_type count,   
    value_type _Ch);

template <class InIt>  
basic_string<CharType, Traits, Allocator>& assign(
    InputIterator first,   
    InputIterator last);

basic_string<CharType, Traits, Allocator>& assign(
    const_pointer first,  
    const_pointer last);

basic_string<CharType, Traits, Allocator>& assign(
    const_iterator first,  
    const_iterator last);
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 Wskaźnik do znaków ciągu C do przypisania do ciągu docelowego.  
  
 `count`  
 Liczba znaków, które mają być dołączane, co najwyżej z ciągu źródła.  
  
 `str`  
 Ciąg źródła, którego znaki mają zostać przypisane do ciągu docelowego.  
  
 `_Ch`  
 Wartość znaku do przypisania.  
  
 `first`  
 Iteratora wejściowych, const_pointer lub const_iterator adresowania pierwszy znak w zakresie ciąg źródłowy ma być przypisany do zakresu docelowego.  
  
 `last`  
 Iterator wejściowych, const_pointer lub const_iterator adresowania spośród ciąg źródłowy poza ostatni znak w zakresie przypisuje się zakres docelowy.  
  
 `off`  
 Pozycja, jaką rozpocznie można przypisać nowe znaki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do obiektu ciąg, który jest przypisywany znaki nowego przez funkcję elementu członkowskiego.  
  
### <a name="remarks"></a>Uwagi  
 Ciągi można przypisać nowe wartości znakowych. Nowa wartość może być ciągiem i C ciąg albo pojedynczym znakiem. [Operatora =](#op_eq) mogą być używane, jeśli nowa wartość może być opisany przez pojedynczy parametr; w przeciwnym razie funkcji członkowskiej **przypisać**, który ma wiele parametrów może służyć do określenia, która część ciągu jest można przypisać do ciągu docelowego.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_assign.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   // The first member function assigning the  
   // characters of a C-string to a string  
   string str1a;  
   const char *cstr1a = "Out There";  
   cout << "The C-string cstr1a is: " << cstr1a <<  "." << endl;  
   str1a.assign ( cstr1a );  
   cout << "Assigning the C-string cstr1a to string str1 gives: "   
        << str1a << "." << endl << endl;  
  
   // The second member function assigning a specific  
   // number of the of characters a C-string to a string  
   string  str1b;  
   const char *cstr1b = "Out There";  
   cout << "The C-string cstr1b is: " << cstr1b << endl;  
   str1b.assign ( cstr1b , 3 );  
   cout << "Assigning the 1st part of the C-string cstr1b "  
        << "to string str1 gives: " << str1b << "."   
        << endl << endl;  
  
   // The third member function assigning a specific number  
   // of the characters from one string to another string   
   string str1c ( "Hello " ), str2c ( "Wide World " );  
   cout << "The string str2c is: " << str2c << endl;  
   str1c.assign ( str2c , 5 , 5 );  
   cout << "The newly assigned string str1 is: "   
        << str1c << "." << endl << endl;  
  
   // The fourth member function assigning the characters  
   // from one string to another string in two equivalent  
   // ways, comparing the assign and operator =  
   string str1d ( "Hello" ), str2d ( "Wide" ), str3d ( "World" );  
   cout << "The original string str1 is: " << str1d << "." << endl;  
   cout << "The string str2d is: " << str2d << endl;  
   str1d.assign ( str2d );  
   cout << "The string str1 newly assigned with string str2d is: "   
        << str1d << "." << endl;  
   cout << "The string str3d is: " << str3d << "." << endl;  
   str1d = str3d;  
   cout << "The string str1 reassigned with string str3d is: "   
        << str1d << "." << endl << endl;  
  
   // The fifth member function assigning a specific   
   // number of characters of a certain value to a string  
   string str1e ( "Hello " );  
   str1e.assign ( 4 , '!' );  
   cout << "The string str1 assigned with eclamations is: "   
        << str1e << endl << endl;  
  
   // The sixth member function assigning the value from  
   // the range of one string to another string  
   string str1f ( "Hello " ), str2f ( "Wide World " );  
   cout << "The string str2f is: " << str2f << endl;  
   str1f.assign ( str2f.begin ( ) + 5 , str2f.end ( ) - 1 );  
   cout << "The string str1 assigned a range of string str2f is: "   
        << str1f << "." << endl << endl;  
}  
```  
  
```Output  
The C-string cstr1a is: Out There.  
Assigning the C-string cstr1a to string str1 gives: Out There.  
  
The C-string cstr1b is: Out There  
Assigning the 1st part of the C-string cstr1b to string str1 gives: Out.  
  
The string str2c is: Wide World   
The newly assigned string str1 is: World.  
  
The original string str1 is: Hello.  
The string str2d is: Wide  
The string str1 newly assigned with string str2d is: Wide.  
The string str3d is: World.  
The string str1 reassigned with string str3d is: World.  
  
The string str1 assigned with eclamations is: !!!!  
  
The string str2f is: Wide World   
The string str1 assigned a range of string str2f is: World.  
```  
  
##  <a name="at"></a>  basic_string::AT  
 Zawiera odwołanie do znaku z indeksem określonym w ciągu.  
  
```  
const_reference at(size_type _Off) const;

 
reference at(size_type _Off);
```  
  
### <a name="parameters"></a>Parametry  
 `_Off`  
 Indeks położenie elementu powstanie odwołania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do znaku ciągu w miejscu określonym przez indeks parametru.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszym elementem w ciągu ma indeks równy zero i następujące elementy są indeksowane kolejno przez dodatnie liczby całkowite, dzięki czemu ciągu o długości  *n*  ma  *n* th Element indeksowane według numerów *n -* 1.  
  
 Element członkowski [operatora &#91; &#93;](#op_at) jest szybsza niż funkcja członkowska **na** zapewniające odczytu i zapisu do elementów ciąg.  
  
 Element członkowski `operator[]` nie sprawdza, czy wskaźnik przekazany jako parametr jest prawidłowy, ale funkcja członkowska **na** ma i dlatego należy używać, gdy ważność nie jest określone. Nieprawidłowy indeks, który jest indeks mniejsza od zera lub większa niż lub równe rozmiarowi ciągu przekazany do funkcji Członkowskich **w** zgłasza [out_of_range — klasa](../standard-library/out-of-range-class.md) wyjątku. Nieprawidłowy indeks przekazany do `operator[]` powoduje niezdefiniowane zachowanie, ale indeks równa długości ciągu jest prawidłowy indeks dla ciągów const i operator zwraca znak null, po upływie tego indeksu.  
  
 Odwołanie zwracane może unieważniona przez ponowne alokacje ciąg lub modyfikacji nienależących **const** ciągów.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_at.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   string str1 ( "Hello world" ), str2 ( "Goodbye world" );  
   const string  cstr1 ( "Hello there" ), cstr2 ( "Goodbye now" );  
   cout << "The original string str1 is: " << str1 << endl;  
   cout << "The original string str2 is: " << str2 << endl;  
  
   // Element access to the non const strings  
   basic_string <char>::reference refStr1 = str1 [6];  
   basic_string <char>::reference refStr2 = str2.at ( 3 );  
  
   cout << "The character with an index of 6 in string str1 is: "  
        << refStr1 << "." << endl;  
   cout << "The character with an index of 3 in string str2 is: "  
        << refStr2 << "." << endl;  
  
   // Element access to the const strings  
   basic_string <char>::const_reference crefStr1 = cstr1 [ cstr1.length ( ) ];  
   basic_string <char>::const_reference crefStr2 = cstr2.at ( 8 );  
  
   if ( crefStr1 == '\0' )  
      cout << "The null character is returned as a valid reference."  
           << endl;  
   else  
      cout << "The null character is not returned." << endl;  
   cout << "The character with index 8 in the const string cstr2 is: "  
        << crefStr2 << "." << endl;  
}  
```  
  
##  <a name="back"></a>  basic_string::back  
 Zwraca odwołanie do ostatniego elementu w ciągu.  
  
```  
const_reference back() const;

 
reference back();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do ostatniego elementu ciąg, który musi być niepusta.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="basic_string"></a>  basic_string::basic_string  
 Tworzy ciąg, który jest pusta, zainicjowane przez określone znaki lub jest kopii całości lub części inny obiekt string lub C styl (ciąg zakończony zerem).  
  
```  
basic_string();

explicit basic_string(
    const allocator_type& _Al);

basic_string(
    const basic_string& right);

basic_string(
    basic_string&& right);

basic_string(
    const basic_string& right,   
    size_type _Roff,  
    size_type count = npos);

basic_string(
    const basic_string& right,   
    size_type _Roff,  
    size_type count,   
    const allocator_type& _Al);

basic_string(
    const value_type* ptr,   
    size_type count);

basic_string(
    const value_type* ptr,   
    size_type count,  
    const allocator_type& _Al);

basic_string(
    const value_type* ptr);

basic_string(
    const value_type* ptr,  
    const allocator_type& _Al);

basic_string(
    size_type count,   
    value_type _Ch);

basic_string(
    size_type count,   
    value_type _Ch,  
    const allocator_type& _Al);

template <class InputIterator>  
basic_string(
 InputIterator first,   
    InputIterator last);

template <class InputIterator>  
basic_string(
 InputIterator first,   
    InputIterator last,   
    const allocator_type& _Al);

basic_string(
    const_pointer first,  
    const_pointer last);

basic_string(
    const_iterator first,  
    const_iterator last);
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 C — ciąg, którego znaki mają być używane do zainicjowania `string` tworzona. Ta wartość nie może być wskaźnika o wartości null.  
  
 `_Al`  
 Klasa przydzielania magazynu dla obiekt ciągu tworzona.  
  
 `count`  
 Liczba znaków, aby można było zainicjować.  
  
 `right`  
 Ciąg, który inicjuje ciąg tworzona.  
  
 `_Roff`  
 Indeks znaków w ciągu, który jest pierwszym ma być używany do inicjowania wartości znaków ciągu tworzona.  
  
 `_Ch`  
 Wartość znaku do skopiowania do ciągu tworzona.  
  
 `first`  
 Iterator wejściowych, const_pointer lub const_iterator adresowania pierwszym elementem w zakresie źródła do wstawienia.  
  
 `last`  
 Iterator wejściowych, const_pointer lub const_iterator adresowania pozycji jedna poza ostatniego elementu w zakresie źródła do wstawienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do obiektu ciąg, który jest generowana przez konstruktorów.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie konstruktory przechowywania [basic_string::allocator_type](#allocator_type) i zainicjuj kontrolowanej sekwencji. Obiekt alokatora jest argument `al`, jeśli jest obecny. Konstruktor kopiujący jest `right.` [basic_string::get_allocator](#get_allocator)`()`. W przeciwnym razie jest `Alloc()`.  
  
 Kontrolowanej sekwencji jest ustawiana na kopię sekwencji argument określony przez pozostałych argumentów. Konstruktor bez sekwencji operand Określa pusty początkowej kontrolowanej sekwencji. Jeśli `InputIterator` jest typu Liczba całkowita w Konstruktorze szablonu _F sekwencji operand `irst,  last` działa tak samo jak `(size_type) first, (value_type) last`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_ctor.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // The first member function initializing with a C-string  
   const char *cstr1a = "Hello Out There.";  
   basic_string <char> str1a ( cstr1a , 5);  
   cout << "The string initialized by C-string cstr1a is: "  
        << str1a << "." << endl;  
  
   // The second member function initializing with a string  
   string  str2a ( "How Do You Do" );  
   basic_string <char> str2b ( str2a , 7 , 7 );  
   cout << "The string initialized by part of the string cstr2a is: "  
        << str2b << "." << endl;  
  
   // The third member function initializing a string  
   // with a number of characters of a specific value  
   basic_string <char> str3a ( 5, '9' );  
   cout << "The string initialized by five number 9s is: "  
        << str3a << endl;  
  
   // The fourth member function creates an empty string  
   // and string with a specified allocator  
   basic_string <char> str4a;  
   string str4b;  
   basic_string <char> str4c ( str4b.get_allocator( ) );  
   if (str4c.empty ( ) )  
      cout << "The string str4c is empty." << endl;  
   else  
      cout << "The string str4c is not empty." << endl;  
  
   // The fifth member function initializes a string from  
   // another range of characters  
   string str5a ( "Hello World" );  
   basic_string <char> str5b ( str5a.begin ( ) + 5 , str5a.end ( ) );  
   cout << "The string initialized by another range is: "  
        << str5b << "." << endl;  
}  
```  
  
##  <a name="begin"></a>  basic_string::BEGIN  
 Zwraca iteratora adresowania pierwszym elementem w ciągu.  
  
```  
const_iterator begin() const;

 
iterator begin();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator dostępie swobodnym, którego dotyczy pierwszym elementem sekwencji lub bezpośrednio po zakończeniu pustej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_begin.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( ) {  
   using namespace std;  
   string str1 ( "No way out." ), str2;  
   basic_string <char>::iterator strp_Iter, str1_Iter, str2_Iter;  
   basic_string <char>::const_iterator str1_cIter;  
  
   str1_Iter = str1.begin ( );  
   cout << "The first character of the string str1 is: "   
        << *str1_Iter << endl;  
   cout << "The full original string str1 is: " << str1 << endl;  
  
   // The dereferenced iterator can be used to modify a character  
 *str1_Iter = 'G';  
   cout << "The first character of the modified str1 is now: "   
        << *str1_Iter << endl;  
   cout << "The full modified string str1 is now: " << str1 << endl;  
  
   // The following line would be an error because iterator is const  
   // *str1_cIter = 'g';  
  
   // For an empty string, begin is equivalent to end  
   if (  str2.begin ( ) == str2.end ( ) )  
      cout << "The string str2 is empty." << endl;  
   else  
      cout << "The string str2 is not empty." << endl;  
}  
```  
  
##  <a name="c_str"></a>  basic_string::c_str  
 Konwertuje zawartość ciąg jako stylu języka C, zerem ciągu.  
  
```  
const value_type *c_str() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do wersji stylu języka C wywoływanie ciągu.  Po wywołaniu funkcji wartością stałą, destruktor, w tym w basic_string — klasa obiektu nie jest prawidłową wartość wskaźnika.  
  
### <a name="remarks"></a>Uwagi  
 Obiekty typu String należących do basic_string C++ szablonu klasy —\<char > są zakończone nie zawsze jest wartość null. Znak null '\0' jest używany jako znak specjalny w ciągu C, aby oznaczyć końca ciągu, ale nie ma specjalnego znaczenia w obiekcie typu String i może być częścią ciągu, podobnie jak wszystkie inne znaki. Brak automatycznej konwersji z const **char\***  do ciągów, ale ciąg klasa nie zapewnia automatycznego konwersje z ciągów w stylu języka C do obiektów typu **basic_string —\< CHAR >**.  
  
 Zwracany ciąg w stylu języka C nie powinien być modyfikowany, to może unieważnić wskaźnikiem do ciągu lub usunięty, ponieważ ciąg ma ograniczony okres istnienia i jest własnością ciąg klasy.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_c_str.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   string  str1 ( "Hello world" );  
   cout << "The original string object str1 is: "   
        << str1 << endl;  
   cout << "The length of the string object str1 = "   
        << str1.length ( ) << endl << endl;  
  
   // Converting a string to an array of characters  
   const char *ptr1 = 0;  
   ptr1= str1.data ( );  
   cout << "The modified string object ptr1 is: " << ptr1   
        << endl;  
   cout << "The length of character array str1 = "   
        << strlen ( ptr1) << endl << endl;  
  
   // Converting a string to a C-style string  
   const char *c_str1 = str1.c_str ( );  
   cout << "The C-style string c_str1 is: " << c_str1   
        << endl;  
   cout << "The length of C-style string str1 = "   
        << strlen ( c_str1) << endl << endl;  
}  
```  
  
```Output  
The original string object str1 is: Hello world  
The length of the string object str1 = 11  
  
The modified string object ptr1 is: Hello world  
The length of character array str1 = 11  
  
The C-style string c_str1 is: Hello world  
The length of C-style string str1 = 11  
```  
  
##  <a name="capacity"></a>  basic_string::Capacity  
 Zwraca największą liczbę elementów, które może być przechowywany w ciągu bez zwiększania alokacji pamięci ciągu.  
  
```  
size_type capacity() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar magazynu przydzielone aktualnie w pamięci, aby pomieścić ciąg.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca magazynu przydzielonego do przechowywania kontrolowanej sekwencji przynajmniej tak duże jak wartość [rozmiar](#size).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_capacity.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   string  str1 ("Hello world");  
   cout << "The original string str1 is: " << str1 << endl;  
  
   // The size and length member functions differ in name only  
   basic_string <char>::size_type sizeStr1, lenStr1;  
   sizeStr1 = str1.size ( );  
   lenStr1 = str1.length ( );  
  
   basic_string <char>::size_type capStr1, max_sizeStr1;  
   capStr1 = str1.capacity ( );  
   max_sizeStr1 = str1.max_size ( );  
  
   // Compare size, length, capacity & max_size of a string  
   cout << "The current size of original string str1 is: "   
        << sizeStr1 << "." << endl;  
   cout << "The current length of original string str1 is: "   
        << lenStr1 << "." << endl;  
   cout << "The capacity of original string str1 is: "  
        << capStr1 << "." << endl;  
   cout << "The max_size of original string str1 is: "   
        << max_sizeStr1 << "." << endl << endl;  
  
   str1.erase ( 6, 5 );  
   cout << "The modified string str1 is: " << str1 << endl;  
  
   sizeStr1 = str1.size (  );  
   lenStr1 = str1.length (  );  
   capStr1 = str1.capacity (  );  
   max_sizeStr1 = str1.max_size (  );  
  
   // Compare size, length, capacity & max_size of a string  
   // after erasing part of the original string  
   cout << "The current size of modified string str1 is: "   
        << sizeStr1 << "." << endl;  
   cout << "The current length of modified string str1 is: "   
        << lenStr1 << "." << endl;  
   cout << "The capacity of modified string str1 is: "  
        << capStr1 << "." << endl;  
   cout << "The max_size of modified string str1 is: "   
        << max_sizeStr1 << "." << endl;  
}  
```  
  
##  <a name="cbegin"></a>  basic_string::cbegin  
 Zwraca `const` iteratora, którego dotyczy pierwszy element w zakresie.  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `const` iteratora dostępie swobodnym, który wskazuje na pierwszym elementem w zakresie lub lokalizacji bezpośrednio po zakończeniu pustego zakresu (dla pustego zakresu, `cbegin() == cend()`).  
  
### <a name="remarks"></a>Uwagi  
 Z wartością zwracaną z `cbegin`, elementy w zakresie nie może być modyfikowany.  
  
 Można użyć funkcji członkowskiej zamiast `begin()` funkcji członkowskiej, aby zagwarantować, że jest zwracana wartość `const_iterator`. Zazwyczaj jest używany w połączeniu z [automatycznie](../cpp/auto-cpp.md) wpisz słowo kluczowe wnioskowanie, jak pokazano w poniższym przykładzie. W tym przykładzie należy wziąć pod uwagę `Container` do można modyfikować (z systemem innym niż `const`) kontenera dowolnego rodzaju, który obsługuje `begin()` i `cbegin()`.  
  
```cpp  
auto i1 = Container.begin();
// i1 is Container<T>::iterator   
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator  
```  
  
##  <a name="cend"></a>  basic_string::cend  
 Zwraca `const` iteratora, którego dotyczy lokalizacji bezpośrednio po ostatnim elementem w zakresie.  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `const` iteratora dostępie swobodnym, który wskazuje poza koniec zakresu.  
  
### <a name="remarks"></a>Uwagi  
 `cend` Służy do sprawdzenia, czy iteratora osiągnęła koniec zakresu.  
  
 Można użyć funkcji członkowskiej zamiast `end()` funkcji członkowskiej, aby zagwarantować, że jest zwracana wartość `const_iterator`. Zazwyczaj jest używany w połączeniu z [automatycznie](../cpp/auto-cpp.md) wpisz słowo kluczowe wnioskowanie, jak pokazano w poniższym przykładzie. W tym przykładzie należy wziąć pod uwagę `Container` do można modyfikować (z systemem innym niż `const`) kontenera dowolnego rodzaju, który obsługuje `end()` i `cend()`.  
  
```cpp  
auto i1 = Container.end();
// i1 is Container<T>::iterator   
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator  
```  
  
 Wartość zwrócona przez `cend` nie powinny być wyłuskiwany.  
  
##  <a name="clear"></a>  basic_string::Clear  
 Usuwa wszystkie elementy ciągu.  
  
```  
void clear();
```  
  
### <a name="remarks"></a>Uwagi  
 Ciąg, na którym jest wywoływana funkcja członkowska jest pusta.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_clear.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   string  str1 ("Hello world"), str2;  
   basic_string <char>::iterator str_Iter;  
   cout << "The original string str1 is: ";  
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )  
      cout << *str_Iter;  
   cout << endl;  
  
   str1.clear ( );  
   cout << "The modified string str1 is: ";  
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )  
      cout << *str_Iter;  
   cout << endl;  
  
   //For an empty string, begin is equivalent to end  
   if ( str1.begin ( ) == str1.end ( ) )  
      cout << "Nothing printed above because "  
           << "the string str1 is empty." << endl;  
   else  
      cout << "The string str1 is not empty." << endl;  
}  
```  
  
```Output  
The original string str1 is: Hello world  
The modified string str1 is:   
Nothing printed above because the string str1 is empty.  
```  
  
##  <a name="compare"></a>  basic_string::COMPARE  
 Przeprowadza porównanie z uwzględnieniem wielkości liter z określonego ciągu do określenia, czy dwa ciągi są takie same i jeśli jest lexicographically mniej niż drugi.  
  
```  
int compare(
    const basic_string<CharType, Traits, Allocator>& str) const;

 
int compare(
    size_type _Pos1,   
    size_type _Num1,  
    const basic_string<CharType, Traits, Allocator>& str) const;

 
int compare(
    size_type _Pos1,  
    size_type _Num1,  
    const basic_string<CharType, Traits, Allocator>& str,   
    size_type _Off,   
    size_type count) const;

 
int compare(
    const value_type* ptr) const;

 
int compare(
    size_type _Pos1,  
    size_type _Num1,  
    const value_type* ptr) const;

 
int compare(
    size_type _Pos1,  
    size_type _Num1,  
    const value_type* ptr  
    size_type _Num2) const;
```  
  
### <a name="parameters"></a>Parametry  
 `str`  
 Ciąg, który ma zostać porównane na ciąg argumentu operacji.  
  
 `_Pos1`  
 Indeks ciągu operand, od której rozpoczyna się porównania.  
  
 `_Num1`  
 Maksymalna liczba znaków z ciągu argument operacji ma zostać porównane.  
  
 `_Num2`  
 Maksymalna liczba znaków z ciągu parametru do porównania.  
  
 `_Off`  
 Indeks ciąg parametru, od której rozpoczyna się porównania.  
  
 `count`  
 Maksymalna liczba znaków z ciągu parametru do porównania.  
  
 `ptr`  
 C — ciąg do porównania z argumentem ciągu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość ujemną, jeśli ciąg operand jest mniejsza niż ciąg parametru; zero, jeśli dwa ciągi są takie same; lub wartość dodatnią, jeśli argument ciągu jest większa niż ciąg parametru.  
  
### <a name="remarks"></a>Uwagi  
 **Porównania** porównanie funkcji Członkowskich całość lub część parametr i argument ciągów w zależności od tego, który używana.  
  
 Porównanie wykonywane jest rozróżniana wielkość liter.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_compare.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   // The first member function compares  
   // an operand string to a parameter string  
   int comp1;  
   string s1o ( "CAB" );  
   string s1p ( "CAB" );  
   cout << "The operand string is: " << s1o << endl;  
   cout << "The parameter string is: " << s1p << endl;  
   comp1 = s1o.compare ( s1p );  
   if ( comp1 < 0 )  
      cout << "The operand string is less than "  
           << "the parameter string." << endl;  
   else if ( comp1 == 0 )  
      cout << "The operand string is equal to "  
           << "the parameter string." << endl;  
   else  
      cout << "The operand string is greater than "  
           << "the parameter string." << endl;  
   cout << endl;  
  
   // The second member function compares part of  
   // an operand string to a parameter string  
   int comp2a, comp2b;  
   string s2o ( "AACAB" );  
   string s2p ( "CAB" );  
   cout << "The operand string is: " << s2o << endl;  
   cout << "The parameter string is: " << s2p << endl;  
   comp2a = s2o.compare (  2 , 3 , s2p );  
   if ( comp2a < 0 )  
      cout << "The last three characters of "  
           << "the operand string\n are less than "  
           << "the parameter string." << endl;  
   else if ( comp2a == 0 )  
      cout << "The last three characters of "  
           << "the operand string\n are equal to "  
           << "the parameter string." << endl;  
   else  
      cout << "The last three characters of "  
           << "the operand string\n is greater than "  
           << "the parameter string." << endl;  
  
   comp2b = s2o.compare (  0 , 3 , s2p );  
   if ( comp2b < 0 )  
      cout << "The first three characters of "  
           << "the operand string\n are less than "  
           << "the parameter string." << endl;  
   else if ( comp2b == 0 )  
      cout << "The first three characters of "  
           << "the operand string\n are equal to "  
           << "the parameter string." << endl;  
   else  
      cout << "The first three characters of "  
           << "the operand string\n is greater than "  
           << "the parameter string." << endl;  
   cout << endl;  
  
   // The third member function compares part of  
   // an operand string to part of a parameter string  
   int comp3a;  
   string s3o ( "AACAB" );  
   string s3p ( "DCABD" );  
   cout << "The operand string is: " << s3o << endl;  
   cout << "The parameter string is: " << s3p << endl;  
   comp3a = s3o.compare (  2 , 3 , s3p , 1 , 3 );  
   if ( comp3a < 0 )  
      cout << "The three characters from position 2 of "  
           << "the operand string are less than\n "  
           << "the 3 characters parameter string "   
           << "from position 1." << endl;  
   else if ( comp3a == 0 )  
      cout << "The three characters from position 2 of "  
           << "the operand string are equal to\n "  
           << "the 3 characters parameter string "   
           << "from position 1." << endl;  
   else  
      cout << "The three characters from position 2 of "  
           << "the operand string is greater than\n "  
           << "the 3 characters parameter string "   
           << "from position 1." << endl;  
   cout << endl;  
  
   // The fourth member function compares  
   // an operand string to a parameter C-string  
   int comp4a;  
   string s4o ( "ABC" );  
   const char* cs4p = "DEF";  
   cout << "The operand string is: " << s4o << endl;  
   cout << "The parameter C-string is: " << cs4p << endl;  
   comp4a = s4o.compare ( cs4p );  
   if ( comp4a < 0 )  
      cout << "The operand string is less than "  
           << "the parameter C-string." << endl;  
   else if ( comp4a == 0 )  
      cout << "The operand string is equal to "  
           << "the parameter C-string." << endl;  
   else  
      cout << "The operand string is greater than "  
           << "the parameter C-string." << endl;  
   cout << endl;  
  
   // The fifth member function compares part of  
   // an operand string to a parameter C-string  
   int comp5a;  
   string s5o ( "AACAB" );  
   const char* cs5p = "CAB";  
   cout << "The operand string is: " << s5o << endl;  
   cout << "The parameter string is: " << cs5p << endl;  
   comp5a = s5o.compare (  2 , 3 , s2p );  
   if ( comp5a < 0 )  
      cout << "The last three characters of "  
           << "the operand string\n are less than "  
           << "the parameter C-string." << endl;  
   else if ( comp5a == 0 )  
      cout << "The last three characters of "  
           << "the operand string\n are equal to "  
           << "the parameter C-string." << endl;  
   else  
      cout << "The last three characters of "  
           << "the operand string\n is greater than "  
           << "the parameter C-string." << endl;  
   cout << endl;  
  
   // The sixth member function compares part of  
   // an operand string to part of an equal length of  
   // a parameter C-string  
   int comp6a;  
   string s6o ( "AACAB" );  
   const char* cs6p = "ACAB";  
   cout << "The operand string is: " << s6o << endl;  
   cout << "The parameter C-string is: " << cs6p << endl;  
   comp6a = s6o.compare (  1 , 3 , cs6p , 3 );  
   if ( comp6a < 0 )  
      cout << "The 3 characters from position 1 of "  
           << "the operand string are less than\n "  
           << "the first 3 characters of the parameter C-string."   
           << endl;  
   else if ( comp6a == 0 )  
      cout << "The 3 characters from position 2 of "  
           << "the operand string are equal to\n "  
           << "the first 3 characters of the parameter C-string."   
           <<  endl;  
   else  
      cout << "The 3 characters from position 2 of "  
           << "the operand string is greater than\n "  
           << "the first 3 characters of the parameter C-string."   
           << endl;  
   cout << endl;  
}  
```  
  
```Output  
The operand string is: CAB  
The parameter string is: CAB  
The operand string is equal to the parameter string.  
  
The operand string is: AACAB  
The parameter string is: CAB  
The last three characters of the operand string  
 are equal to the parameter string.  
The first three characters of the operand string  
 are less than the parameter string.  
  
The operand string is: AACAB  
The parameter string is: DCABD  
The three characters from position 2 of the operand string are equal to  
 the 3 characters parameter string from position 1.  
  
The operand string is: ABC  
The parameter C-string is: DEF  
The operand string is less than the parameter C-string.  
  
The operand string is: AACAB  
The parameter string is: CAB  
The last three characters of the operand string  
 are equal to the parameter C-string.  
  
The operand string is: AACAB  
The parameter C-string is: ACAB  
The 3 characters from position 2 of the operand string are equal to  
 the first 3 characters of the parameter C-string.  
```  
  
##  <a name="const_iterator"></a>  basic_string::const_iterator  
 Typem udostępniający iteratora dostęp losowy i są dostępne do odczytu **const** elementu w ciągu.  
  
```  
typedef implementation-defined const_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `const_iterator` nie można zmodyfikować wartości znak i jest używany do iterowania po ciągu w kierunku do przodu.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rozpocząć](#begin) przykład sposobu deklarowanie i użycie `const_iterator`.  
  
##  <a name="const_pointer"></a>  basic_string::const_pointer  
 Typ, który dostarcza wskaźnik do **const** elementu w ciągu.  
  
```  
typedef typename allocator_type::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem **allocator_type::const_pointer**.  
  
 Dla typu **ciąg**, jest odpowiednikiem `char`*.  
  
 Wskaźniki, które są zadeklarowane const musi zostać zainicjowany, jeśli są deklarowane jako. Wskaźniki stałe zawsze punktu w tej samej lokalizacji pamięci i mogą wskazywać na stałe lub nieunikatowego danych.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_const_ptr.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   basic_string<char>::const_pointer pstr1a = "In Here";  
   const char *cstr1c = "Out There";  
  
   cout << "The string pstr1a is: " << pstr1a <<  "." << endl;  
   cout << "The C-string cstr1c is: " << cstr1c << "." << endl;  
}  
```  
  
```Output  
The string pstr1a is: In Here.  
The C-string cstr1c is: Out There.  
```  
  
##  <a name="const_reference"></a>  basic_string::const_reference  
 Typ, który zawiera odwołanie do **const** element przechowywane w ciągu do odczytu i wykonywania **const** operacji.  
  
```  
typedef typename allocator_type::const_reference const_reference;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `const_reference` nie może służyć do modyfikowania wartości elementu.  
  
 Typ jest synonimem **allocator_type::const_reference**. Dla ciągu **typu**, jest odpowiednikiem const **char &**.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [w](#at) przykład sposobu deklarowanie i użycie `const_reference`.  
  
##  <a name="const_reverse_iterator"></a>  basic_string::const_reverse_iterator  
 Typ, który udostępnia iteratora dostępie swobodnym, który może odczytać **const** elementu w ciągu.  
  
```  
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `const_reverse_iterator` nie można zmodyfikować wartości znaku i jest używany do iterowania po ciągu odwrotnie.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rbegin](#rbegin) przykład sposobu deklarowanie i użycie `const_reverse_iterator`.  
  
##  <a name="copy"></a>  basic_string::Copy  
 Kopiuje co najwyżej określoną liczbę znaków z indeksowanego pozycji w ciągu źródłowej do docelowej tablicy znaków.  
  
 Ta metoda jest potencjalnie niebezpieczne, ponieważ zależy od obiekt wywołujący, aby sprawdzić, czy przekazane wartości są poprawne. Należy rozważyć użycie [basic_string::_Copy_s](#copy_s) zamiast tego.  
  
```  
size_type copy(
    value_type* ptr,   
    size_type count,  
    size_type _Off = 0) const;
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 Tablica docelowa znak, do którego mają zostać skopiowane elementy.  
  
 _ `Count`  
 Liczba znaków, które zostaną skopiowane, co najwyżej z ciągu źródła.  
  
 `_Off`  
 Położenie początku w ciągu źródło, z którego mają zostać wprowadzone kopie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba znaków, które faktycznie skopiowane.  
  
### <a name="remarks"></a>Uwagi  
 Znak null nie jest dołączany na końcu kopii.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_copy.cpp  
// compile with: /EHsc /W3  
#include <string>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   string str1 ( "Hello World" );  
   basic_string <char>::iterator str_Iter;  
   char array1 [ 20 ] = { 0 };  
   char array2 [ 10 ] = { 0 };  
   basic_string <char>:: pointer array1Ptr = array1;  
   basic_string <char>:: value_type *array2Ptr = array2;  
  
   cout << "The original string str1 is: ";  
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )  
      cout << *str_Iter;  
   cout << endl;  
  
   basic_string <char>:: size_type nArray1;  
   // Note: string::copy is potentially unsafe, consider  
   // using string::_Copy_s instead.  
   nArray1 = str1.copy ( array1Ptr , 12 );  // C4996  
   cout << "The number of copied characters in array1 is: "  
        << nArray1 << endl;  
   cout << "The copied characters array1 is: " << array1 << endl;  
  
   basic_string <char>:: size_type nArray2;  
   // Note: string::copy is potentially unsafe, consider  
   // using string::_Copy_s instead.  
   nArray2 = str1.copy ( array2Ptr , 5 , 6  );  // C4996  
   cout << "The number of copied characters in array2 is: "  
           << nArray2 << endl;  
   cout << "The copied characters array2 is: " << array2Ptr << endl;  
}  
```  
  
```Output  
The original string str1 is: Hello World  
The number of copied characters in array1 is: 11  
The copied characters array1 is: Hello World  
The number of copied characters in array2 is: 5  
The copied characters array2 is: World  
```  
  
##  <a name="crbegin"></a>  basic_string::crbegin  
 Zwraca iteratora const, którego dotyczy pierwszym elementem w ciągu odwróconej.  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora wstecznego, który wskazuje poza koniec ciągu. Pozycja wskazuje na początku ciąg odwrotnej.  
  
##  <a name="crend"></a>  basic_string::crend  
 Zwraca iteratora const, którego dotyczy lokalizacji pomyślne ostatnim elementem w ciągu odwróconej.  
  
```  
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stała wstecznego iteratora, którego dotyczy lokalizacji pomyślne ostatnim elementem w ciągu odwróconej (lokalizacja miał przed pierwszym elementem w ciągu stałe).  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="copy_s"></a>  basic_string::_Copy_s  
 Kopiuje co najwyżej określoną liczbę znaków z indeksowanego pozycji w ciągu źródłowej do docelowej tablicy znaków.  
  
```  
size_type _Copy_s(
    value_type* dest,  
    size_type dest_size,  
    size_type count,  
    size_type _Off = 0) const;
```  
  
### <a name="parameters"></a>Parametry  
 `dest`  
 Tablica docelowa znak, do którego mają zostać skopiowane elementy.  
  
 `dest_size`  
 Rozmiar `dest`.  
  
 _ `Count`  
 Liczba znaków, które zostaną skopiowane, co najwyżej z ciągu źródła.  
  
 `_Off`  
 Położenie początku w ciągu źródło, z którego mają zostać wprowadzone kopie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba znaków, które faktycznie skopiowane.  
  
### <a name="remarks"></a>Uwagi  
 Znak null nie jest dołączany na końcu kopii.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string__Copy_s.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
    string str1("Hello World");  
    basic_string<char>::iterator str_Iter;  
    const int array1_size = 20;  
    char array1[array1_size] = { 0 };  
    const int array2_size = 10;  
    char array2[array2_size] = { 0 };  
    basic_string<char>:: pointer array1Ptr = array1;  
    basic_string<char>:: value_type *array2Ptr = array2;  
  
    cout << "The original string str1 is: ";  
    for (str_Iter = str1.begin(); str_Iter != str1.end(); str_Iter++)  
        cout << *str_Iter;  
    cout << endl;  
  
    basic_string<char>::size_type nArray1;  
    nArray1 = str1._Copy_s(array1Ptr, array1_size, 12);  
    cout << "The number of copied characters in array1 is: "  
         << nArray1 << endl;  
    cout << "The copied characters array1 is: " << array1 << endl;  
  
    basic_string<char>:: size_type nArray2;  
    nArray2 = str1._Copy_s(array2Ptr, array2_size, 5, 6);  
    cout << "The number of copied characters in array2 is: "  
         << nArray2 << endl;  
    cout << "The copied characters array2 is: " << array2Ptr << endl;  
}  
```  
  
```Output  
The original string str1 is: Hello World  
The number of copied characters in array1 is: 11  
The copied characters array1 is: Hello World  
The number of copied characters in array2 is: 5  
The copied characters array2 is: World  
```  
  
##  <a name="data"></a>  basic_string::Data  
 Konwertuje wartość ciągu do tablicy znaków.  
  
```  
const value_type *data() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do pierwszego elementu tablicy z zawartością ciągu lub, w przypadku pusta tablica, nie można usunąć odwołania wskaźnik inną niż null.  
  
### <a name="remarks"></a>Uwagi  
 Obiekty typu String należących do basic_string C++ szablonu klasy — \<char > są zakończone nie zawsze jest wartość null. Typ zwracany dla **danych** nie jest prawidłowym ciągiem C, ponieważ pobiera dołączane żadne znaki null. Znak null '\0' jest używany jako znak specjalny w ciągu C można oznaczyć końca ciągu, ale nie ma specjalnego znaczenia w obiekcie typu String i może być częścią z obiektem ciągu, podobnie jak wszystkie inne znaki.  
  
 Brak automatycznej konwersji z const **char\***  do ciągów, ale ciąg klasa nie zapewnia automatycznego konwersje z ciągów w stylu języka C do obiektów typu **basic_string — \< CHAR >**.  
  
 Zwracany ciąg nie powinien być modyfikowany, ponieważ to może unieważnić wskaźnikiem do ciągu lub usunięty, ponieważ ciąg ma ograniczony okres istnienia i jest własnością ciąg klasy.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_data.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   string str1 ( "Hello world" );  
   cout << "The original string object str1 is: "   
        << str1 << endl;  
   cout << "The length of the string object str1 = "   
        << str1.length ( ) << endl << endl;  
  
   // Converting a string to an array of characters  
   const char *ptr1 = 0;  
   ptr1= str1.data ( );  
   cout << "The modified string object ptr1 is: " << ptr1   
        << endl;  
   cout << "The length of character array str1 = "   
        << strlen ( ptr1) << endl << endl;  
  
   // Converting a string to a C-style string  
   const char *c_str1 = str1.c_str ( );  
   cout << "The C-style string c_str1 is: " << c_str1   
        << endl;  
   cout << "The length of C-style string str1 = "   
        << strlen ( c_str1) << endl << endl;  
}  
```  
  
```Output  
The original string object str1 is: Hello world  
The length of the string object str1 = 11  
  
The modified string object ptr1 is: Hello world  
The length of character array str1 = 11  
  
The C-style string c_str1 is: Hello world  
The length of C-style string str1 = 11  
```  
  
##  <a name="difference_type"></a>  basic_string::difference_type  
 Typ, który udostępnia różnica między dwa Iteratory, które odwołują się do elementów w tym samym ciągu.  
  
```  
typedef typename allocator_type::difference_type difference_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Wpisz liczbę całkowitą ze znakiem opisuje obiekt, który może reprezentować różnica między adresami dwóch elementów w kontrolowanej sekwencji.  
  
 Dla typu **ciąg**, jest odpowiednikiem **ptrdiff_t —**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_diff_type.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   string str1 ( "quintillion" );  
   cout << "The original string str1 is: " << str1 << endl;  
   basic_string <char>::size_type indexChFi, indexChLi;  
  
   indexChFi = str1.find_first_of ( "i" );  
   indexChLi = str1.find_last_of ( "i" );  
   basic_string<char>::difference_type diffi = indexChLi - indexChFi;  
  
   cout << "The first character i is at position: "  
        << indexChFi << "." << endl;  
   cout << "The last character i is at position: "  
        << indexChLi << "." << endl;  
   cout << "The difference is: " << diffi << "." << endl;  
}  
```  
  
```Output  
The original string str1 is: quintillion  
The first character i is at position: 2.  
The last character i is at position: 8.  
The difference is: 6.  
```  
  
##  <a name="empty"></a>  basic_string::Empty  
 Sprawdza, czy ciąg zawiera znaki, czy nie.  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli obiekt ciąg nie zawiera znaków; **false** jeśli ma ona co najmniej jeden znak.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska jest odpowiednikiem [rozmiar](#size) == 0.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_empty.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main() {  
   using namespace std;  
  
   bool b1, b2;  
  
   string str1 ("Hello world");  
   cout << "The original string object str1 is: " << str1 << endl;  
   b1 = str1.empty();  
   if (b1)  
      cout << "The string object str1 is empty." << endl;  
   else  
      cout << "The string object str1 is not empty." << endl;  
   cout << endl;  
  
   // An example of an empty string object  
   string str2;  
   b2 = str2.empty();  
   if (b2)  
      cout << "The string object str2 is empty." << endl;  
   else  
      cout << "The string object str2 is not empty." << endl;  
}  
```  
  
##  <a name="end"></a>  basic_string::end  
 Zwraca iteratora, którego dotyczy lokalizacji pomyślne ostatnim elementem w ciągu.  
  
```  
const_iterator end() const;

 
iterator end();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca iteratora dostępie swobodnym, który dotyczy lokalizacji pomyślne ostatnim elementem w ciągu.  
  
### <a name="remarks"></a>Uwagi  
 **końcowy** często używany do sprawdzania, czy iteratora osiągnął koniec parametrach. Wartość zwrócona przez **zakończenia** nie powinny być wyłuskiwany.  
  
 Jeśli wartość zwracana **zakończenia** jest przypisany do `const_iterator`, nie można zmodyfikować z obiektem ciągu. Jeśli wartość zwracana **zakończenia** jest przypisany do **iterator**, można zmodyfikować z obiektem ciągu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_end.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   string str1 ( "No way out." ), str2;  
   basic_string <char>::iterator str_Iter, str1_Iter, str2_Iter;  
   basic_string <char>::const_iterator str1_cIter;  
  
   str1_Iter = str1.end ( );  
   str1_Iter--;  
   str1_Iter--;  
   cout << "The last character-letter of the string str1 is: " << *str1_Iter << endl;  
   cout << "The full orginal string str1 is: " << str1 << endl;  
  
   // end used to test when an iterator has reached the end of its string  
   cout << "The string is now: ";  
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )  
      cout << *str_Iter;  
   cout << endl;  
  
   // The dereferenced iterator can be used to modify a character  
 *str1_Iter = 'T';  
   cout << "The last character-letter of the modified str1 is now: "  
        << *str1_Iter << endl;  
   cout << "The modified string str1 is now: " << str1 << endl;  
  
   // The following line would be an error because iterator is const  
   // *str1_cIter = 'T';  
  
   // For an empty string, end is equivalent to begin  
   if ( str2.begin( ) == str2.end ( ) )  
      cout << "The string str2 is empty." << endl;  
   else  
      cout << "The stringstr2  is not empty." << endl;  
}  
```  
  
```Output  
The last character-letter of the string str1 is: t  
The full orginal string str1 is: No way out.  
The string is now: No way out.  
The last character-letter of the modified str1 is now: T  
The modified string str1 is now: No way ouT.  
The string str2 is empty.  
```  
  
##  <a name="erase"></a>  basic_string::ERASE  
 Usuwa element lub zakres elementów w ciągu od określonej pozycji.  
  
```  
iterator erase(
    iterator first,   
    iterator last);

iterator erase(
    iterator _It);

basic_string<CharType, Traits, Allocator>& erase(
    size_type _Pos = 0,  
    size_type count = npos);
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Iteratora adresowania położenie pierwszego elementu w zakresie usunięcie.  
  
 `last`  
 Iteratora adresowania pozycji w jednym ostatniego elementu w zakresie usunięcie.  
  
 `_It`  
 Iteratora adresowania położenie elementu w ciągu usunięcie.  
  
 `_Pos`  
 Indeks pierwszego znaku w ciągu do usunięcia.  
  
 `count`  
 Liczba elementów, które zostaną usunięte, jeśli istnieją dowolną liczbę z zakresu od początku ciągu z *_Pos*.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dla funkcji Członkowskich dwóch pierwszych iteratora adresowania pierwszego znaku za ostatni znak usunięte przez funkcję elementu członkowskiego. Trzeci funkcji Członkowskich, odwołanie do obiektu ciąg, z której zostały usunięte elementy.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca trzecie funkcji członkowskiej  **\*to**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_erase.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   // The 1st member function using a range demarcated  
   // by iterators  
   string str1 ( "Hello world" );  
   basic_string <char>::iterator str1_Iter;  
   cout << "The original string object str1 is: "   
        << str1 << "." << endl;  
   str1_Iter = str1.erase ( str1.begin ( ) + 3 , str1.end ( ) - 1 );  
   cout << "The first element after those removed is: "  
        << *str1_Iter << "." << endl;  
   cout << "The modified string object str1 is: " << str1   
           << "." << endl << endl;  
  
   // The 2nd member function erasing a char pointed to   
   // by an iterator  
   string str2 ( "Hello World" );  
   basic_string <char>::iterator str2_Iter;  
   cout << "The original string object str2 is: " << str2  
        << "." << endl;  
   str2_Iter = str2.erase ( str2.begin ( ) + 5 );  
   cout << "The first element after those removed is: "  
        << *str2_Iter << "." << endl;  
   cout << "The modified string object str2 is: " << str2   
        << "." << endl << endl;  
  
   // The 3rd member function erasing a number of chars   
   // after a char  
   string str3 ( "Hello computer" ), str3m;  
   basic_string <char>::iterator str3_Iter;  
   cout << "The original string object str3 is: "   
        << str3 << "." << endl;  
   str3m = str3.erase ( 6 , 8 );  
   cout << "The modified string object str3m is: "   
        << str3m << "." << endl;  
}  
```  
  
```Output  
The original string object str1 is: Hello world.  
The first element after those removed is: d.  
The modified string object str1 is: Held.  
  
The original string object str2 is: Hello World.  
The first element after those removed is: W.  
The modified string object str2 is: HelloWorld.  
  
The original string object str3 is: Hello computer.  
The modified string object str3m is: Hello .  
```  
  
##  <a name="find"></a>  basic_string::Find  
 Wyszukuje ciąg w kierunku do przodu dla pierwszego wystąpienia podciągu, który odpowiada określonej sekwencji znaków.  
  
```  
size_type find(
    value_type _Ch,   
    size_type _Off = 0) const;

 
size_type find(
    const value_type* ptr,  
    size_type _Off = 0) const;

 
size_type find(
    const value_type* ptr,   
    size_type _Off,  
    size_type count) const;

 
size_type find(
    const basic_string<CharType, Traits, Allocator>& str,  
    size_type _Off = 0) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Ch`  
 Wartość znak, dla którego funkcja członkowska jest do wyszukiwania.  
  
 `_Off`  
 Indeks pozycji, o której ma się rozpocząć wyszukiwanie.  
  
 `ptr`  
 C-ciąg dla którego funkcja członkowska jest do wyszukiwania.  
  
 `count`  
 Liczba znaków, do przodu licząc od pierwszego znaku w ciągu C dla którego funkcja członkowska jest do wyszukiwania.  
  
 `str`  
 Ciąg, którego funkcja członkowska jest do wyszukiwania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks pierwszego znaku podciągu wyszukiwane zakończone powodzeniem; w przeciwnym razie `npos`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_find.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // The first member function  
   // searches for a single character in a string  
   string str1 ( "Hello Everyone" );  
   cout << "The original string str1 is: " << str1 << endl;  
   basic_string <char>::size_type indexCh1a, indexCh1b;  
  
   indexCh1a = str1.find ( "e" , 3 );  
   if (indexCh1a != string::npos )  
      cout << "The index of the 1st 'e' found after the 3rd"  
           << " position in str1 is: " << indexCh1a << endl;  
   else  
      cout << "The character 'e' was not found in str1 ." << endl;  
  
   indexCh1b = str1.find ( "x" );  
   if (indexCh1b != string::npos )  
      cout << "The index of the 'x' found in str1 is: "  
           << indexCh1b << endl << endl;  
   else  
      cout << "The Character 'x' was not found in str1."  
           << endl << endl;  
  
   // The second member function searches a string  
   // for a substring as specified by a C-string  
   string str2 ( "Let me make this perfectly clear." );  
   cout << "The original string str2 is: " << str2 << endl;  
   basic_string <char>::size_type indexCh2a, indexCh2b;  
  
   const char *cstr2 = "perfect";  
   indexCh2a = str2.find ( cstr2 , 5 );  
   if ( indexCh2a != string::npos )  
      cout << "The index of the 1st element of 'perfect' "  
           << "after\n the 5th position in str2 is: "  
           << indexCh2a << endl;  
   else  
      cout << "The substring 'perfect' was not found in str2 ."  
           << endl;  
  
   const char *cstr2b = "imperfectly";  
   indexCh2b = str2.find ( cstr2b , 0 );  
   if (indexCh2b != string::npos )  
      cout << "The index of the 1st element of 'imperfect' "  
           << "after\n the 5th position in str3 is: "  
           << indexCh2b << endl;  
   else  
      cout << "The substring 'imperfect' was not found in str2 ."  
           << endl << endl;  
  
   // The third member function searches a string  
   // for a substring as specified by a C-string  
   string str3 ( "This is a sample string for this program" );  
   cout << "The original string str3 is: " << str3 << endl;  
   basic_string <char>::size_type indexCh3a, indexCh3b;  
  
   const char *cstr3a = "sample";  
   indexCh3a = str3.find ( cstr3a );  
   if ( indexCh3a != string::npos )  
      cout << "The index of the 1st element of sample "  
           << "in str3 is: " << indexCh3a << endl;  
   else  
      cout << "The substring 'perfect' was not found in str3 ."  
           << endl;  
  
   const char *cstr3b = "for";  
   indexCh3b = str3.find ( cstr3b , indexCh3a + 1 , 2 );  
   if (indexCh3b != string::npos )  
      cout << "The index of the next occurrence of 'for' is in "  
           << "str3 begins at: " << indexCh3b << endl << endl;  
   else  
      cout << "There is no next occurrence of 'for' in str3 ."  
           << endl << endl;  
  
   // The fourth member function searches a string  
   // for a substring as specified by a string  
   string str4 ( "clearly this perfectly unclear." );  
   cout << "The original string str4 is: " << str4 << endl;  
   basic_string <char>::size_type indexCh4a, indexCh4b;  
  
   string str4a ( "clear" );  
   indexCh4a = str4.find ( str4a , 5 );  
   if ( indexCh4a != string::npos )  
      cout << "The index of the 1st element of 'clear' "  
           << "after\n the 5th position in str4 is: "  
           << indexCh4a << endl;  
   else  
      cout << "The substring 'clear' was not found in str4 ."  
           << endl;  
  
   string str4b ( "clear" );  
   indexCh4b = str4.find ( str4b );  
   if (indexCh4b != string::npos )  
      cout << "The index of the 1st element of 'clear' "  
           << "in str4 is: "  
           << indexCh4b << endl;  
   else  
      cout << "The substring 'clear' was not found in str4 ."  
           << endl << endl;  
}  
```  
  
```Output  
The original string str1 is: Hello Everyone  
The index of the 1st 'e' found after the 3rd position in str1 is: 8  
The Character 'x' was not found in str1.  
  
The original string str2 is: Let me make this perfectly clear.  
The index of the 1st element of 'perfect' after  
 the 5th position in str2 is: 17  
The substring 'imperfect' was not found in str2 .  
  
The original string str3 is: This is a sample string for this program  
The index of the 1st element of sample in str3 is: 10  
The index of the next occurrence of 'for' is in str3 begins at: 24  
  
The original string str4 is: clearly this perfectly unclear.  
The index of the 1st element of 'clear' after  
 the 5th position in str4 is: 25  
The index of the 1st element of 'clear' in str4 is: 0  
```  
  
##  <a name="find_first_not_of"></a>  basic_string::find_first_not_of  
 Wyszukiwanie za pomocą ciągu pierwszego znaku, który nie jest elementem określonego ciągu.  
  
```  
size_type find_first_not_of(
    value_type _Ch,   
    size_type _Off = 0) const;

 
size_type find_first_not_of(
    const value_type* ptr,  
    size_type _Off = 0) const;

 
size_type find_first_not_of(
    const value_type* ptr,   
    size_type _Off,  
    size_type count) const;

 
size_type find_first_not_of(
    const basic_string<CharType, Traits, Allocator>& str,  
    size_type _Off = 0) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Ch`  
 Wartość znak, dla którego funkcja członkowska jest do wyszukiwania.  
  
 `_Off`  
 Indeks pozycji, o której ma się rozpocząć wyszukiwanie.  
  
 `ptr`  
 C-ciąg dla którego funkcja członkowska jest do wyszukiwania.  
  
 `count`  
 Liczba znaków, do przodu licząc od pierwszego znaku w ciągu C dla którego funkcja członkowska jest do wyszukiwania.  
  
 `str`  
 Ciąg, którego funkcja członkowska jest do wyszukiwania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks pierwszego znaku podciągu wyszukiwane zakończone powodzeniem; w przeciwnym razie `npos`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_find_first_not_of.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   // The first member function  
   // searches for a single character in a string  
   string str1 ( "xddd-1234-abcd" );  
   cout << "The original string str1 is: " << str1 << endl;  
   basic_string <char>::size_type indexCh1a, indexCh1b;  
   static const basic_string <char>::size_type npos = -1;  
  
   indexCh1a = str1.find_first_not_of ( "d" , 2 );  
   if ( indexCh1a != npos )  
      cout << "The index of the 1st 'd' found after the 3rd"  
           << " position in str1 is: " << indexCh1a << endl;  
   else  
      cout << "The character 'd' was not found in str1 ." << endl;  
  
   indexCh1b = str1.find_first_not_of  ( "x" );  
   if (indexCh1b != npos )  
      cout << "The index of the 'non x' found in str1 is: "   
           << indexCh1b << endl << endl;  
   else  
      cout << "The character 'non x' was not found in str1."  
           << endl << endl;  
  
   // The second member function searches a string  
   // for a substring as specified by a C-string  
   string str2 ( "BBB-1111" );  
   cout << "The original string str2 is: " << str2 << endl;  
   basic_string <char>::size_type indexCh2a, indexCh2b;  
  
   const char *cstr2 = "B1";  
   indexCh2a = str2.find_first_not_of ( cstr2 , 6 );  
   if ( indexCh2a != npos )  
      cout << "The index of the 1st occurrence of an "  
           << "element of 'B1' in str2 after\n the 6th "  
           << "position is: " << indexCh2a << endl;  
   else  
      cout << "Elements of the substring 'B1' were not"  
           << "\n found in str2 after the 6th position."  
           << endl;  
  
   const char *cstr2b = "B2";  
   indexCh2b = str2.find_first_not_of ( cstr2b );  
   if ( indexCh2b != npos )  
      cout << "The index of the 1st element of 'B2' "  
           << "after\n the 0th position in str2 is: "  
           << indexCh2b << endl << endl;  
   else  
      cout << "The substring 'B2' was not found in str2 ."   
           << endl << endl << endl;  
  
   // The third member function searches a string  
   // for a substring as specified by a C-string  
   string str3 ( "444-555-GGG" );  
   cout << "The original string str3 is: " << str3 << endl;  
   basic_string <char>::size_type indexCh3a, indexCh3b;  
  
   const char *cstr3a = "45G";  
   indexCh3a = str3.find_first_not_of ( cstr3a );  
   if ( indexCh3a != npos )  
      cout << "The index of the 1st occurrence of an "  
           << "element in str3\n other than one of the "  
           << "characters in '45G' is: " << indexCh3a   
           << endl;  
   else  
      cout << "Elements in str3 contain only characters "  
           << " in the string '45G'. "  
           << endl;  
  
   const char *cstr3b = "45G";  
   indexCh3b = str3.find_first_not_of ( cstr3b , indexCh3a + 1 , 2 );  
   if ( indexCh3b != npos )  
      cout << "The index of the second occurrence of an "  
           << "element of '45G' in str3\n after the 0th "  
           << "position is: " << indexCh3b << endl << endl;  
   else  
      cout << "Elements in str3 contain only characters "  
           << " in the string  '45G'. "  
           << endl  << endl;  
  
   // The fourth member function searches a string  
   // for a substring as specified by a string  
   string str4 ( "12-ab-12-ab" );  
   cout << "The original string str4 is: " << str4 << endl;  
   basic_string <char>::size_type indexCh4a, indexCh4b;  
  
   string str4a ( "ba3" );  
   indexCh4a = str4.find_first_not_of ( str4a , 5 );  
   if (indexCh4a != npos )  
      cout << "The index of the 1st non occurrence of an "  
           << "element of 'ba3' in str4 after\n the 5th "  
           << "position is: " << indexCh4a << endl;  
   else  
      cout << "Elements other than those in the substring"  
           << " 'ba3' were not found in the string str4."  
           << endl;  
  
   string str4b ( "12" );  
   indexCh4b = str4.find_first_not_of ( str4b  );  
   if (indexCh4b != npos )  
      cout << "The index of the 1st non occurrence of an "  
           << "element of '12' in str4 after\n the 0th "  
           << "position is: " << indexCh4b << endl;  
   else  
      cout << "Elements other than those in the substring"  
           << " '12' were not found in the string str4."  
           << endl;  
}  
```  
  
```Output  
The original string str1 is: xddd-1234-abcd  
The index of the 1st 'd' found after the 3rd position in str1 is: 4  
The index of the 'non x' found in str1 is: 1  
  
The original string str2 is: BBB-1111  
Elements of the substring 'B1' were not  
 found in str2 after the 6th position.  
The index of the 1st element of 'B2' after  
 the 0th position in str2 is: 3  
  
The original string str3 is: 444-555-GGG  
The index of the 1st occurrence of an element in str3  
 other than one of the characters in '45G' is: 3  
The index of the second occurrence of an element of '45G' in str3  
 after the 0th position is: 7  
  
The original string str4 is: 12-ab-12-ab  
The index of the 1st non occurrence of an element of 'ba3' in str4 after  
 the 5th position is: 5  
The index of the 1st non occurrence of an element of '12' in str4 after  
 the 0th position is: 2  
```  
  
##  <a name="find_first_of"></a>  basic_string::find_first_of  
 Wyszukiwanie za pomocą ciągu pierwszego znaku, który dopasowuje dowolny element określonego ciągu.  
  
```  
size_type find_first_of(
    value_type _Ch,   
    size_type _Off = 0) const;

 
size_type find_first_of(
    const value_type* ptr,  
    size_type _Off = 0) const;

 
size_type find_first_of(
    const value_type* ptr,   
    size_type _Off,  
    size_type count) const;

 
size_type find_first_of(
    const basic_string<CharType, Traits, Allocator>& str,  
    size_type _Off = 0) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Ch`  
 Wartość znak, dla którego funkcja członkowska jest do wyszukiwania.  
  
 `_Off`  
 Indeks pozycji, o której ma się rozpocząć wyszukiwanie.  
  
 `ptr`  
 C-ciąg dla którego funkcja członkowska jest do wyszukiwania.  
  
 `count`  
 Liczba znaków, do przodu licząc od pierwszego znaku w ciągu C dla którego funkcja członkowska jest do wyszukiwania.  
  
 `str`  
 Ciąg, którego funkcja członkowska jest do wyszukiwania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks pierwszego znaku podciągu wyszukiwane zakończone powodzeniem; w przeciwnym razie `npos`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_find_first_of.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   // The first member function  
   // searches for a single character in a string  
   string str1 ( "abcd-1234-abcd-1234" );  
   cout << "The original string str1 is: " << str1 << endl;  
   basic_string <char>::size_type indexCh1a, indexCh1b;  
   static const basic_string <char>::size_type npos = -1;  
  
   indexCh1a = str1.find_first_of ( "d" , 5 );  
   if ( indexCh1a != npos )  
      cout << "The index of the 1st 'd' found after the 5th"  
           << " position in str1 is: " << indexCh1a << endl;  
   else  
      cout << "The character 'd' was not found in str1 ." << endl;  
  
   indexCh1b = str1.find_first_of ( "x" );  
   if ( indexCh1b != npos )  
      cout << "The index of the 'x' found in str1 is: "   
           << indexCh1b << endl << endl;  
   else  
      cout << "The character 'x' was not found in str1."  
           << endl << endl;  
  
   // The second member function searches a string  
   // for any element of a substring as specified by a C-string  
   string str2 ( "ABCD-1234-ABCD-1234" );  
   cout << "The original string str2 is: " << str2 << endl;  
   basic_string <char>::size_type indexCh2a, indexCh2b;  
  
   const char *cstr2 = "B1";  
   indexCh2a = str2.find_first_of ( cstr2 , 6 );  
   if ( indexCh2a != npos )  
      cout << "The index of the 1st occurrence of an "  
           << "element of 'B1' in str2 after\n the 6th "  
           << "position is: " << indexCh2a << endl;  
   else  
      cout << "Elements of the substring 'B1' were not "  
           << "found in str2 after the 10th position."  
           << endl;  
  
   const char *cstr2b = "D2";  
   indexCh2b = str2.find_first_of ( cstr2b );  
   if ( indexCh2b != npos )  
      cout << "The index of the 1st element of 'D2' "  
           << "after\n the 0th position in str2 is: "  
           << indexCh2b << endl << endl;  
   else  
      cout << "The substring 'D2' was not found in str2 ."   
           << endl << endl << endl;  
  
   // The third member function searches a string  
   // for any element of a substring as specified by a C-string  
   string str3 ( "123-abc-123-abc-456-EFG-456-EFG" );  
   cout << "The original string str3 is: " << str3 << endl;  
   basic_string <char>::size_type indexCh3a, indexCh3b;  
  
   const char *cstr3a = "5G";  
   indexCh3a = str3.find_first_of ( cstr3a );  
   if ( indexCh3a != npos )  
      cout << "The index of the 1st occurrence of an "  
           << "element of '5G' in str3 after\n the 0th "  
           << "position is: " << indexCh3a << endl;  
   else  
      cout << "Elements of the substring '5G' were not "  
           << "found in str3\n after the 0th position."  
           << endl;  
  
   const char *cstr3b = "5GF";  
   indexCh3b = str3.find_first_of  ( cstr3b , indexCh3a + 1 , 2 );  
   if (indexCh3b != npos )  
      cout << "The index of the second occurrence of an "  
           << "element of '5G' in str3\n after the 0th "  
           << "position is: " << indexCh3b << endl << endl;  
   else  
      cout << "Elements of the substring '5G' were not "  
           << "found in str3\n after the first occurrrence."  
           << endl << endl;  
  
   // The fourth member function searches a string  
   // for any element of a substring as specified by a string  
   string str4 ( "12-ab-12-ab" );  
   cout << "The original string str4 is: " << str4 << endl;  
   basic_string <char>::size_type indexCh4a, indexCh4b;  
  
   string str4a ( "ba3" );  
   indexCh4a = str4.find_first_of ( str4a , 5 );  
   if ( indexCh4a != npos )  
      cout << "The index of the 1st occurrence of an "  
           << "element of 'ba3' in str4 after\n the 5th "  
           << "position is: " << indexCh4a << endl;  
   else  
      cout << "Elements of the substring 'ba3' were not "  
           << "found in str4\n after the 0th position."  
           << endl;  
  
   string str4b ( "a2" );  
   indexCh4b = str4.find_first_of ( str4b );  
   if ( indexCh4b != npos )  
      cout << "The index of the 1st occurrence of an "  
           << "element of 'a2' in str4 after\n the 0th "  
           << "position is: " << indexCh4b << endl;  
   else  
      cout << "Elements of the substring 'a2' were not "  
           << "found in str4\n after the 0th position."  
           << endl;  
}  
```  
  
```Output  
The original string str1 is: abcd-1234-abcd-1234  
The index of the 1st 'd' found after the 5th position in str1 is: 13  
The character 'x' was not found in str1.  
  
The original string str2 is: ABCD-1234-ABCD-1234  
The index of the 1st occurrence of an element of 'B1' in str2 after  
 the 6th position is: 11  
The index of the 1st element of 'D2' after  
 the 0th position in str2 is: 3  
  
The original string str3 is: 123-abc-123-abc-456-EFG-456-EFG  
The index of the 1st occurrence of an element of '5G' in str3 after  
 the 0th position is: 17  
The index of the second occurrence of an element of '5G' in str3  
 after the 0th position is: 22  
  
The original string str4 is: 12-ab-12-ab  
The index of the 1st occurrence of an element of 'ba3' in str4 after  
 the 5th position is: 9  
The index of the 1st occurrence of an element of 'a2' in str4 after  
 the 0th position is: 1  
```  
  
##  <a name="find_last_not_of"></a>  basic_string::find_last_not_of  
 Wyszukiwanie za pomocą ciągu ostatni znak, który nie jest dowolny element określony ciąg.  
  
```  
size_type find_last_not_of(
    value_type _Ch,   
    size_type _Off = npos) const;

 
size_type find_last_not_of(
    const value_type* ptr,  
    size_type _Off = npos) const;

 
size_type find_last_not_of(
    const value_type* ptr,   
    size_type _Off,  
    size_type count) const;

 
size_type find_last_not_of(
    const basic_string<CharType, Traits, Allocator>& str,  
    size_type _Off = npos) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Ch`  
 Wartość znak, dla którego funkcja członkowska jest do wyszukiwania.  
  
 `_Off`  
 Indeks pozycji, jaką jest zakończenie wyszukiwania.  
  
 `ptr`  
 C-ciąg dla którego funkcja członkowska jest do wyszukiwania.  
  
 `count`  
 Liczba znaków, do przodu licząc od pierwszego znaku w ciągu C dla którego funkcja członkowska jest do wyszukiwania.  
  
 `str`  
 Ciąg, którego funkcja członkowska jest do wyszukiwania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks pierwszego znaku podciągu wyszukiwane zakończone powodzeniem; w przeciwnym razie `npos`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_find_last_not_of.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   // The first member function  
   // searches for a single character in a string  
   string str1 ( "dddd-1dd4-abdd" );  
   cout << "The original string str1 is: " << str1 << endl;  
   basic_string <char>::size_type indexCh1a, indexCh1b;  
   static const basic_string <char>::size_type npos = -1;  
  
   indexCh1a = str1.find_last_not_of ( "d" , 7 );  
   if ( indexCh1a != npos )  
      cout << "The index of the last non 'd'\n found before the "  
           << "7th position in str1 is: " << indexCh1a << endl;  
   else  
      cout << "The non 'd' character was not found ." << endl;  
  
   indexCh1b = str1.find_last_not_of  ( "d" );  
   if ( indexCh1b != npos )  
      cout << "The index of the non 'd' found in str1 is: "   
           << indexCh1b << endl << endl;  
   else  
      cout << "The Character 'non x' was not found in str1."  
           << endl << endl;  
  
   // The second member function searches a string  
   // for a substring as specified by a C-string  
   string str2 ( "BBB-1111" );  
   cout << "The original string str2 is: " << str2 << endl;  
   basic_string <char>::size_type indexCh2a, indexCh2b;  
  
   const char *cstr2 = "B1";  
   indexCh2a = str2.find_last_not_of  ( cstr2 , 6 );  
   if ( indexCh2a != npos )  
      cout << "The index of the last occurrence of a "  
           << "element\n not of 'B1' in str2 before the 6th "  
           << "position is: " << indexCh2a << endl;  
   else  
      cout << "Elements not of the substring 'B1' were not "  
           << "\n found in str2 before the 6th position."  
           << endl;  
  
   const char *cstr2b = "B-1";  
   indexCh2b = str2.find_last_not_of  ( cstr2b );  
   if ( indexCh2b != npos )  
      cout << "The index of the last element not "  
           << "in 'B-1'\n is: "  
           << indexCh2b << endl << endl;  
   else  
      cout << "The elements of the substring 'B-1' were "  
           << "not found in str2 ."   
           << endl << endl;  
  
   // The third member function searches a string  
   // for a substring as specified by a C-string  
   string str3 ( "444-555-GGG" );  
   cout << "The original string str3 is: " << str3 << endl;  
   basic_string <char>::size_type indexCh3a, indexCh3b;  
  
   const char *cstr3a = "45G";  
   indexCh3a = str3.find_last_not_of ( cstr3a );  
   if ( indexCh3a != npos )  
      cout << "The index of the last occurrence of an "  
           << "element in str3\n other than one of the "  
           << "characters in '45G' is: " << indexCh3a   
           << endl;  
   else  
      cout << "Elements in str3 contain only characters "  
           << " in the string  '45G'. "  
           << endl;  
  
   const char *cstr3b = "45G";  
   indexCh3b = str3.find_last_not_of ( cstr3b , 6 , indexCh3a - 1 );  
   if (indexCh3b != npos )  
      cout << "The index of the penultimate occurrence of an "  
           << "element\n not in '45G' in str3 is: "  
           << indexCh3b << endl << endl;  
   else  
      cout << "Elements in str3 contain only characters "  
           << " in the string '45G'. "  
           << endl  << endl;  
  
   // The fourth member function searches a string  
   // for a substring as specified by a string  
   string str4 ( "12-ab-12-ab" );  
   cout << "The original string str4 is: " << str4 << endl;  
   basic_string <char>::size_type indexCh4a, indexCh4b;  
  
   string str4a ( "b-a" );  
   indexCh4a = str4.find_last_not_of  ( str4a , 5 );  
   if ( indexCh4a != npos )  
      cout << "The index of the last occurrence of an "  
           << "element not\n in 'b-a' in str4 before the 5th "  
           << "position is: " << indexCh4a << endl;  
   else  
      cout << "Elements other than those in the substring"  
           << " 'b-a' were not found in the string str4."  
           << endl;  
  
   string str4b ( "12" );  
   indexCh4b = str4.find_last_not_of ( str4b  );  
   if ( indexCh4b != npos )  
      cout << "The index of the last occurrence of an "  
           << "element not in '12'\n in str4 before the end "  
           << "position is: " << indexCh4b << endl;  
   else  
      cout << "Elements other than those in the substring"  
           << " '12'\n were not found in the string str4."  
           << endl;  
}  
```  
  
```Output  
The original string str1 is: dddd-1dd4-abdd  
The index of the last non 'd'  
 found before the 7th position in str1 is: 5  
The index of the non 'd' found in str1 is: 11  
  
The original string str2 is: BBB-1111  
The index of the last occurrence of a element  
 not of 'B1' in str2 before the 6th position is: 3  
The elements of the substring 'B-1' were not found in str2 .  
  
The original string str3 is: 444-555-GGG  
The index of the last occurrence of an element in str3  
 other than one of the characters in '45G' is: 7  
The index of the penultimate occurrence of an element  
 not in '45G' in str3 is: 3  
  
The original string str4 is: 12-ab-12-ab  
The index of the last occurrence of an element not  
 in 'b-a' in str4 before the 5th position is: 1  
The index of the last occurrence of an element not in '12'  
 in str4 before the end position is: 10  
```  
  
##  <a name="find_last_of"></a>  basic_string::find_last_of  
 Wyszukiwanie za pomocą ciągu ostatni znak, który dopasowuje dowolny element określonego ciągu.  
  
```  
size_type find_last_of(
    value_type _Ch,   
    size_type _Off = npos) const;

 
 
size_type find_last_of(
    const value_type* ptr,  
    size_type _Off = npos) const;

 
 
size_type find_last_of(
    const value_type* ptr,   
    size_type _Off,  
    size_type count) const;

 
 
size_type find_last_of(
    const basic_string<CharType, Traits, Allocator>& str,  
    size_type _Off = npos) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Ch`  
 Wartość znak, dla którego funkcja członkowska jest do wyszukiwania.  
  
 `_Off`  
 Indeks pozycji, jaką jest zakończenie wyszukiwania.  
  
 `ptr`  
 C-ciąg dla którego funkcja członkowska jest do wyszukiwania.  
  
 `count`  
 Liczba znaków, do przodu licząc od pierwszego znaku w ciągu C dla którego funkcja członkowska jest do wyszukiwania.  
  
 `str`  
 Ciąg, którego funkcja członkowska jest do wyszukiwania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks ostatni znak podciągu wyszukiwane zakończone powodzeniem; w przeciwnym razie `npos`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_find_last_of.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // The first member function  
   // searches for a single character in a string  
   string str1 ( "abcd-1234-abcd-1234" );  
   cout << "The original string str1 is: " << str1 << endl;  
   basic_string <char>::size_type indexCh1a, indexCh1b;  
   static const basic_string <char>::size_type npos = -1;  
  
   indexCh1a = str1.find_last_of ( "d" , 14 );  
   if ( indexCh1a != npos )  
      cout << "The index of the last 'd' found before the 14th"  
           << " position in str1 is: " << indexCh1a << endl;  
   else  
      cout << "The character 'd' was not found in str1 ." << endl;  
  
   indexCh1b = str1.find_first_of ( "x" );  
   if ( indexCh1b != npos )  
      cout << "The index of the 'x' found in str1 is: "  
           << indexCh1b << endl << endl;  
   else  
      cout << "The character 'x' was not found in str1."  
           << endl << endl;  
  
   // The second member function searches a string  
   // for a substring as specified by a C-string  
   string str2 ( "ABCD-1234-ABCD-1234" );  
   cout << "The original string str2 is: " << str2 << endl;  
   basic_string <char>::size_type indexCh2a, indexCh2b;  
  
   const char *cstr2 = "B1";  
   indexCh2a = str2.find_last_of  ( cstr2 , 12 );  
   if (indexCh2a != npos )  
      cout << "The index of the last occurrence of an "  
           << "element of 'B1' in str2 before\n the 12th "  
           << "position is: " << indexCh2a << endl;  
   else  
      cout << "Elements of the substring 'B1' were not "  
           << "found in str2 before the 12th position."  
           << endl;  
  
   const char *cstr2b = "D2";  
   indexCh2b = str2.find_last_of  ( cstr2b );  
   if ( indexCh2b != npos )  
      cout << "The index of the last element of 'D2' "  
           << "after\n the 0th position in str2 is: "  
           << indexCh2b << endl << endl;  
   else  
      cout << "The substring 'D2' was not found in str2 ."  
           << endl << endl << endl;  
  
   // The third member function searches a string  
   // for a substring as specified by a C-string  
   string str3 ( "456-EFG-456-EFG" );  
   cout << "The original string str3 is: " << str3 << endl;  
   basic_string <char>::size_type indexCh3a;  
  
   const char *cstr3a = "5E";  
   indexCh3a = str3.find_last_of ( cstr3a , 8 , 8 );  
   if ( indexCh3a != npos )  
      cout << "The index of the last occurrence of an "  
           << "element of '5E' in str3 before\n the 8th "  
           << "position is: " << indexCh3a << endl << endl;  
   else  
      cout << "Elements of the substring '5G' were not "  
           << "found in str3\n before the 8th position."  
           << endl << endl;  
  
   // The fourth member function searches a string  
   // for a substring as specified by a string  
   string str4 ( "12-ab-12-ab" );  
   cout << "The original string str4 is: " << str4 << endl;  
   basic_string <char>::size_type indexCh4a, indexCh4b;  
  
   string str4a ( "ba3" );  
   indexCh4a = str4.find_last_of  ( str4a , 8 );  
   if ( indexCh4a != npos )  
      cout << "The index of the last occurrence of an "  
           << "element of 'ba3' in str4 before\n the 8th "  
           << "position is: " << indexCh4a << endl;  
   else  
      cout << "Elements of the substring 'ba3' were not "  
           << "found in str4\n after the 0th position."  
           << endl;  
  
   string str4b ( "a2" );  
   indexCh4b = str4.find_last_of ( str4b  );  
   if ( indexCh4b != npos )  
      cout << "The index of the last occurrence of an "  
           << "element of 'a2' in str4 before\n the 0th "  
           << "position is: " << indexCh4b << endl;  
   else  
      cout << "Elements of the substring 'a2' were not "  
           << "found in str4\n after the 0th position."  
           << endl;  
}  
```  
  
```Output  
The original string str1 is: abcd-1234-abcd-1234  
The index of the last 'd' found before the 14th position in str1 is: 13  
The character 'x' was not found in str1.  
  
The original string str2 is: ABCD-1234-ABCD-1234  
The index of the last occurrence of an element of 'B1' in str2 before  
 the 12th position is: 11  
The index of the last element of 'D2' after  
 the 0th position in str2 is: 16  
  
The original string str3 is: 456-EFG-456-EFG  
The index of the last occurrence of an element of '5E' in str3 before  
 the 8th position is: 4  
  
The original string str4 is: 12-ab-12-ab  
The index of the last occurrence of an element of 'ba3' in str4 before  
 the 8th position is: 4  
The index of the last occurrence of an element of 'a2' in str4 before  
 the 0th position is: 9  
```  
  
##  <a name="front"></a>  basic_string::front  
 Zwraca odwołanie do pierwszego elementu w ciągu.  
  
```  
const_reference front() const;

 
reference front();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do pierwszego elementu obiektu ciąg, który musi być niepusta.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="get_allocator"></a>  basic_string::get_allocator  
 Zwraca kopię obiektu alokatora użyta do skonstruowania ciągu.  
  
```  
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Allocator — używane przez ciąg.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca obiekt alokatora przechowywane.  
  
 Allocators — dla klasy ciągu Określ zarządzaniu klasę magazynu. Allocators — domyślna dostarczony wraz z klasy kontenerów są wystarczające dla większości potrzeb programowania. Pisanie i przy użyciu klasy alokatora jest temat zaawansowany C++.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_get_allocator.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   // The following lines declare objects  
   // that use the default allocator.  
   string s1;  
   basic_string <char> s2;  
   basic_string <char, char_traits< char >, allocator< char > > s3;  
  
   // s4 will use the same allocator class as s1  
   basic_string <char> s4( s1.get_allocator ( ) );  
  
   basic_string <char>::allocator_type xchar = s1.get_allocator( );  
   // You can now call functions on the allocator class xchar used by s1  
}  
```  
  
##  <a name="insert"></a>  basic_string::INSERT  
 Wstawia element lub liczba elementów lub zakres elementów do ciągu na określonej pozycji.  
  
```  
basic_string<CharType, Traits, Allocator>& insert(
    size_type _P0,   
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& insert(
    size_type _P0,   
    const value_type* ptr,  
    size_type count);

basic_string<CharType, Traits, Allocator>& insert(
    size_type _P0,  
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& insert(
    size_type _P0,  
    const basic_string<CharType, Traits, Allocator>& str,   
    size_type _Off,   
    size_type count);

basic_string<CharType, Traits, Allocator>& insert(
    size_type _P0,  
    size_type count,   
    value_type _Ch);

iterator insert(
    iterator _It);

iterator insert(
    iterator _It,  
    value_type _Ch)l  
template <class InputIterator>  
void insert(
    iterator _It,   
    InputIterator first,   
    InputIterator last);

void insert(
    iterator _It,   
    size_type count,   
    value_type _Ch);

void insert(
    iterator _It,  
    const_pointer first,  
    const_pointer last);

void insert(
    iterator _It,  
    const_iterator first,  
    const_iterator last);
```  
  
### <a name="parameters"></a>Parametry  
 *_P0*  
 Indeks pozycji za punkt wstawiania nowych znaków.  
  
 `ptr`  
 C — ciąg do całości lub częściowo umieszczona w ciągu.  
  
 `count`  
 Liczba znaków do wstawienia.  
  
 `str`  
 Ciąg, który ma zostać w całości lub częściowo wstawiony do ciągu docelowego.  
  
 `_Off`  
 Indeks część ciągu źródła dostarczanie znaków, które mają być dołączane.  
  
 `_Ch`  
 Wartość znaku elementów do wstawienia.  
  
 `_It`  
 Iteratora adresowania pozycji, za który znak jest do wstawienia.  
  
 `first`  
 Iterator wejściowych, const_pointer lub const_iterator adresowania pierwszym elementem w zakresie źródła do wstawienia.  
  
 `last`  
 Iterator wejściowych, const_pointer lub const_iterator adresowania pozycji jedna poza ostatniego elementu w zakresie źródła do wstawienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do obiektu ciąg, który jest przypisywany znaki nowego przez funkcję elementu członkowskiego lub, w przypadku wstawienia indywidualnym iteratora adresowania pozycji znaku wstawione lub Brak, w zależności od określonego elementu członkowskiego Funkcja.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_insert.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // The first member function inserting a C-string  
   // at a given position  
   basic_string <char> str1a ( "way" );  
   const char *cstr1a = "a";  
   str1a.insert ( 0, cstr1a );  
   cout << "The string with a C-string inserted at position 0 is: "  
        << str1a << "." << endl;  
  
   // The second member function inserting a C-string  
   // at a given position for a specified number of elements  
   basic_string <char> str2a ( "Good" );  
   const char *cstr2a = "Bye Bye Baby";  
   str2a.insert ( 4, cstr2a ,3 );  
   cout << "The string with a C-string inserted at the end is: "  
        << str2a << "." << endl;  
  
   // The third member function inserting a string  
   // at a given position  
   basic_string <char> str3a ( "Bye" );  
   string str3b ( "Good" );  
   str3a.insert ( 0, str3b );  
   cout << "The string with a string inserted at position 0 is: "  
        << str3a << "." << endl;  
  
   // The fourth member function inserting part of  
   // a string at a given position  
   basic_string <char> str4a ( "Good " );  
   string str4b ( "Bye Bye Baby" );  
   str4a.insert ( 5, str4b , 8 , 4 );  
   cout << "The string with part of a string inserted at position 4 is: "  
        << str4a << "." << endl;  
  
   // The fifth member function inserts a number of characters  
   // at a specified position in the string  
   string str5 ( "The number is: ." );  
   str5.insert ( 15 , 3 , '3' );  
   cout << "The string with characters inserted is: "  
        << str5 << endl;  
  
   // The sixth member function inserts a character  
   // at a specified position in the string  
   string str6 ( "ABCDFG" );  
   basic_string <char>::iterator str6_Iter = ( str6.begin ( ) + 4 );  
   str6.insert ( str6_Iter , 'e' );  
   cout << "The string with a character inserted is: "  
        << str6 << endl;  
  
   // The seventh member function inserts a range  
   // at a specified position in the string  
   string str7a ( "ABCDHIJ" );  
   string str7b ( "abcdefgh" );  
   basic_string <char>::iterator str7a_Iter = (str7a.begin ( ) + 4 );  
   str7a.insert ( str7a_Iter , str7b.begin ( ) + 4 , str7b.end ( ) -1 );  
   cout << "The string with a character inserted from a range is: "  
        << str7a << endl;  
  
   // The eigth member function inserts a number of  
   // characters at a specified position in the string  
   string str8 ( "ABCDHIJ" );  
   basic_string <char>::iterator str8_Iter = ( str8.begin ( ) + 4 );  
   str8.insert ( str8_Iter , 3 , 'e' );  
   cout << "The string with a character inserted from a range is: "  
        << str8 << endl;  
}  
```  
  
```Output  
The string with a C-string inserted at position 0 is: away.  
The string with a C-string inserted at the end is: GoodBye.  
The string with a string inserted at position 0 is: GoodBye.  
The string with part of a string inserted at position 4 is: Good Baby.  
The string with characters inserted is: The number is: 333.  
The string with a character inserted is: ABCDeFG  
The string with a character inserted from a range is: ABCDefgHIJ  
The string with a character inserted from a range is: ABCDeeeHIJ  
```  
  
##  <a name="iterator"></a>  basic_string::iterator  
 Typem udostępniający iteratora dostęp losowy i są dostępne do odczytu **const** elementu w ciągu.  
  
```  
typedef implementation-defined iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ **iterator** może służyć do modyfikowania wartości znaku i jest używany do iterowania po ciągu w kierunku do przodu.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rozpocząć](#begin) przykład sposobu deklarowanie i użycie **iterator**.  
  
##  <a name="length"></a>  basic_string::length  
 Zwraca bieżącą liczbę elementów w ciągu.  
  
```  
size_type length() const;
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska jest taka sama jak [rozmiar](#size).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_length.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   string str1 ("Hello world");  
   cout << "The original string str1 is: " << str1 << endl;  
  
   // The size and length member functions differ in name only  
   basic_string <char>::size_type sizeStr1, lenStr1;  
   sizeStr1 = str1.size ( );  
   lenStr1 = str1.length ( );  
  
   basic_string <char>::size_type capStr1, max_sizeStr1;  
   capStr1 = str1.capacity ( );  
   max_sizeStr1 = str1.max_size ( );  
  
   // Compare size, length, capacity & max_size of a string  
   cout << "The current size of original string str1 is: "   
        << sizeStr1 << "." << endl;  
   cout << "The current length of original string str1 is: "   
        << lenStr1 << "." << endl;  
   cout << "The capacity of original string str1 is: "  
        << capStr1 << "." << endl;  
   cout << "The max_size of original string str1 is: "   
        << max_sizeStr1 << "." << endl << endl;  
  
   str1.erase ( 6, 5 );  
   cout << "The modified string str1 is: " << str1 << endl;  
  
   sizeStr1 = str1.size ( );  
   lenStr1 = str1.length ( );  
   capStr1 = str1.capacity ( );  
   max_sizeStr1 = str1.max_size ( );  
  
   // Compare size, length, capacity & max_size of a string  
   // after erasing part of the original string  
   cout << "The current size of modified string str1 is: "   
        << sizeStr1 << "." << endl;  
   cout << "The current length of modified string str1 is: "   
        << lenStr1 << "." << endl;  
   cout << "The capacity of modified string str1 is: "  
        << capStr1 << "." << endl;  
   cout << "The max_size of modified string str1 is: "   
        << max_sizeStr1 << "." << endl;  
}  
```  
  
##  <a name="max_size"></a>  basic_string::max_size  
 Zwraca maksymalną liczbę znaków, które mogą zawierać ciąg.  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Maksymalna liczba znaków, które mogą zawierać ciąg.  
  
### <a name="remarks"></a>Uwagi  
 Wyjątek typu [length_error — klasa](../standard-library/length-error-class.md) jest generowany, gdy operacja powoduje ciąg o długości większej niż maksymalny rozmiar.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_max_size.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   string str1 ("Hello world");  
   cout << "The original string str1 is: " << str1 << endl;  
  
   // The size and length member functions differ in name only  
   basic_string <char>::size_type sizeStr1, lenStr1;  
   sizeStr1 = str1.size ( );  
   lenStr1 = str1.length ( );  
  
   basic_string <char>::size_type capStr1, max_sizeStr1;  
   capStr1 = str1.capacity ( );  
   max_sizeStr1 = str1.max_size ( );  
  
   // Compare size, length, capacity & max_size of a string  
   cout << "The current size of original string str1 is: "   
        << sizeStr1 << "." << endl;  
   cout << "The current length of original string str1 is: "   
        << lenStr1 << "." << endl;  
   cout << "The capacity of original string str1 is: "  
        << capStr1 << "." << endl;  
   cout << "The max_size of original string str1 is: "   
        << max_sizeStr1 << "." << endl << endl;  
  
   str1.erase ( 6, 5 );  
   cout << "The modified string str1 is: " << str1 << endl;  
  
   sizeStr1 = str1.size ( );  
   lenStr1 = str1.length ( );  
   capStr1 = str1.capacity ( );  
   max_sizeStr1 = str1.max_size ( );  
  
   // Compare size, length, capacity & max_size of a string  
   // after erasing part of the original string  
   cout << "The current size of modified string str1 is: "   
        << sizeStr1 << "." << endl;  
   cout << "The current length of modified string str1 is: "   
        << lenStr1 << "." << endl;  
   cout << "The capacity of modified string str1 is: "  
        << capStr1 << "." << endl;  
   cout << "The max_size of modified string str1 is: "   
        << max_sizeStr1 << "." << endl;  
}  
```  
  
##  <a name="npos"></a>  basic_string::npos  
 Wartością całkowitą bez znaku ustawiana na wartość -1, która wskazuje "nie można odnaleźć" lub "wszystkie pozostałe znaki" Jeśli funkcja wyszukiwania nie powiodło się.  
  
```  
static const size_type npos = -1;  
```  
  
### <a name="remarks"></a>Uwagi  
 Kiedy ma być sprawdzane pod kątem wartości zwracanej `npos` wartości, może nie działać, chyba że jest zwracana wartość typu [size_type](#size_type) i nie albo `int` lub `unsigned`.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [znaleźć](#find) przykład sposobu deklarowanie i użycie `npos`.  
  
##  <a name="op_add_eq"></a>  basic_string::operator +=  
 Dołącza znaków do ciągu.  
  
```  
basic_string<CharType, Traits, Allocator>& operator+=(
    value_type _Ch);

basic_string<CharType, Traits, Allocator>& operator+=(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& operator+=(
    const basic_string<CharType, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `_Ch`  
 Znak do dołączenia.  
  
 `ptr`  
 Znaki C ciąg do dołączenia.  
  
 `right`  
 Znaki ciąg do dołączenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do obiektu ciąg dołączany znaków przekazany przez funkcję elementu członkowskiego.  
  
### <a name="remarks"></a>Uwagi  
 Znaki może zostać dołączone do ciągu za pomocą `operator+=` lub funkcje Członkowskie [Dołącz](#append) lub [push_back](#push_back). `operator+=` Dołącza jednym argumentem wartości podczas wiele argumentów Dołącz funkcji członkowskiej umożliwia określoną część ciągu można określić dodawania.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_op_app.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   // The first member function  
   // appending a single character to a string  
   string str1a ( "Hello" );  
   cout << "The original string str1 is: " << str1a << endl;  
   str1a +=  '!' ;  
   cout << "The string str1 appended with an exclamation is: "   
        << str1a << endl << endl;  
  
   // The second member function  
   // appending a C-string to a string  
   string  str1b ( "Hello " );  
   const char *cstr1b = "Out There";  
   cout << "The C-string cstr1b is: " << cstr1b << endl;  
   str1b +=  cstr1b;  
   cout << "Appending the C-string cstr1b to string str1 gives: "   
        << str1b << "." << endl << endl;  
  
   // The third member function  
   // appending one string to another in two ways,  
   // comparing append and operator [ ]  
   string str1d ( "Hello " ), str2d ( "Wide " ), str3d ( "World" );  
   cout << "The string str2d is: " << str2d << endl;  
   str1d.append ( str2d );  
   cout << "The appended string str1d is: "   
        << str1d << "." << endl;  
   str1d += str3d;  
   cout << "The doubly appended strig str1 is: "   
        << str1d << "." << endl << endl;  
}  
```  
  
```Output  
The original string str1 is: Hello  
The string str1 appended with an exclamation is: Hello!  
  
The C-string cstr1b is: Out There  
Appending the C-string cstr1b to string str1 gives: Hello Out There.  
  
The string str2d is: Wide   
The appended string str1d is: Hello Wide .  
The doubly appended strig str1 is: Hello Wide World.  
```  
  
##  <a name="op_eq"></a>  basic_string::operator =  
 Przypisuje nowy wartości znakowych zawartość ciągu.  
  
```  
basic_string<CharType, Traits, Allocator>& operator=(
    value_type _Ch);

basic_string<CharType, Traits, Allocator>& operator=(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& operator=(
    const basic_string<CharType, Traits, Allocator>& right);

basic_string<CharType, Traits, Allocator>& operator=(
    const basic_string<CharType, Traits, Allocator>&& right);
```  
  
### <a name="parameters"></a>Parametry  
 `_Ch`  
 Wartość znaku do przypisania.  
  
 `ptr`  
 Wskaźnik do znaków ciągu C do przypisania do ciągu docelowego.  
  
 `right`  
 Ciąg źródła, którego znaki mają zostać przypisane do ciągu docelowego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do obiektu ciąg, który jest przypisywany znaki nowego przez funkcję elementu członkowskiego.  
  
### <a name="remarks"></a>Uwagi  
 Ciągi można przypisać nowe wartości znakowych. Nowa wartość może być ciągiem i C ciąg albo pojedynczym znakiem. `operator=` Mogą być używane, jeśli nowa wartość może być opisanego przez jeden parametr, w przeciwnym razie funkcja członkowska [przypisać](#assign), który ma wiele parametrów może służyć do określenia, która część ciągu ma być przypisana do elementu docelowego ciąg.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_op_assign.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   // The first member function assigning a  
   // character of a certain value to a string  
   string str1a ( "Hello " );  
   str1a = '0';  
   cout << "The string str1 assigned with the zero character is: "   
        << str1a << endl << endl;  
  
   // The second member function assigning the  
   // characters of a C-string to a string  
   string  str1b;  
   const char *cstr1b = "Out There";  
   cout << "The C-string cstr1b is: " << cstr1b <<  "." << endl;  
   str1b = cstr1b;  
   cout << "Assigning the C-string cstr1a to string str1 gives: "   
        << str1b << "." << endl << endl;  
  
   // The third member function assigning the characters  
   // from one string to another string in two equivalent  
   // ways, comparing the assign and operator =  
   string str1c ( "Hello" ), str2c ( "Wide" ), str3c ( "World" );  
   cout << "The original string str1 is: " << str1c << "." << endl;  
   cout << "The string str2c is: " << str2c << "." << endl;  
   str1c.assign ( str2c );  
   cout << "The string str1 newly assigned with string str2c is: "   
        << str1c << "." << endl;  
   cout << "The string str3c is: " << str3c << "." << endl;  
   str1c = str3c;  
   cout << "The string str1 reassigned with string str3c is: "   
        << str1c << "." << endl << endl;  
}  
```  
  
```Output  
The string str1 assigned with the zero character is: 0  
  
The C-string cstr1b is: Out There.  
Assigning the C-string cstr1a to string str1 gives: Out There.  
  
The original string str1 is: Hello.  
The string str2c is: Wide.  
The string str1 newly assigned with string str2c is: Wide.  
The string str3c is: World.  
The string str1 reassigned with string str3c is: World.  
```  
  
##  <a name="op_at"></a>  basic_string::operator]  
 Zawiera odwołanie do znaku z indeksem określonym w ciągu.  
  
```  
const_reference operator[](size_type _Off) const;  
reference operator[](size_type _Off);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Off`  
 Indeks położenie elementu powstanie odwołania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do znaku ciągu w miejscu określonym przez indeks parametru.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy element ciąg ma indeks równy zero i następujące elementy są indeksowane kolejno przez dodatnie liczby całkowite, dzięki czemu ciągu o długości  *n*  ma  *n*  TH element indeksowane według numerów  *n*  - 1.  
  
 `operator[]` jest szybsze niż funkcja członkowska [na](#at) zapewniające odczytu i zapisu do elementów ciąg.  
  
 `operator[]` nie sprawdza, czy wskaźnik przekazany jako parametr jest prawidłowy, ale funkcja członkowska **na** i dlatego powinny być używane w ważność nie jest określone. Nieprawidłowy indeks (indeks mniejsza od zera lub większa niż lub równe rozmiarowi ciągu) przekazany do funkcji Członkowskich **w** zgłasza [out_of_range — klasa](../standard-library/out-of-range-class.md) wyjątku. Nieprawidłowy indeks przekazany do `operator[]` powoduje niezdefiniowane zachowanie, ale indeks równa długości ciągu jest prawidłowy indeks dla ciągów const i operator zwraca znak null, po upływie tego indeksu.  
  
 Odwołanie zwracane może unieważniona przez ponowne alokacje ciąg lub modyfikacji nienależących **const** ciągów.  
  
 Podczas kompilowania za pomocą [ \_ITERATOR\_debugowania\_poziom](../standard-library/iterator-debug-level.md) ustawiono wartość 1 lub 2, błąd środowiska uruchomieniowego nastąpi próba uzyskania dostępu do elementu poza granicami ciągu. Aby uzyskać więcej informacji, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_op_ref.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   string str1 ( "Hello world" ), str2 ( "Goodbye world" );  
   const string cstr1 ( "Hello there" ), cstr2 ( "Goodbye now" );  
   cout << "The original string str1 is: " << str1 << endl;  
   cout << "The original string str2 is: " << str2 << endl;  
  
   // Element access to the non-const strings  
   basic_string <char>::reference refStr1 = str1 [6];  
   basic_string <char>::reference refStr2 = str2.at ( 3 );  
  
   cout << "The character with an index of 6 in string str1 is: "  
        << refStr1 << "." << endl;  
   cout << "The character with an index of 3 in string str2 is: "  
        << refStr2 << "." << endl;  
  
   // Element access to the const strings  
   basic_string <char>::const_reference crefStr1 = cstr1 [ cstr1.length ( ) ];  
   basic_string <char>::const_reference crefStr2 = cstr2.at ( 8 );  
  
   if ( crefStr1 == '\0' )  
      cout << "The null character is returned as a valid reference."  
           << endl;  
   else  
      cout << "The null character is not returned." << endl;  
   cout << "The character with index of 8 in the const string cstr2 is: "  
        << crefStr2 << "." << endl;  
}  
```  
  
##  <a name="pointer"></a>  basic_string::Pointer  
 Typ, który dostarcza wskaźnik do elementu znaku w ciągu lub znak tablicy.  
  
```  
typedef typename allocator_type::pointer pointer;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem **allocator_type::pointer**.  
  
 Dla typu **ciąg**, jest odpowiednikiem **char\***.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_pointer.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   basic_string<char>::pointer pstr1a = "In Here";  
   char *cstr1b = "Out There";  
   cout << "The string pstr1a is: " << pstr1a <<  "." << endl;  
   cout << "The C-string cstr1b is: " << cstr1b << "." << endl;  
}  
```  
  
```Output  
The string pstr1a is: In Here.  
The C-string cstr1b is: Out There.  
```  
  
##  <a name="pop_back"></a>  basic_string::pop_back  
 Usuwa ostatnim elementem w ciągu.  
  
```  
void pop_back();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska wywołuje `erase(size() - 1)` wymazania ostatnim elementem sekwencji, który musi być niepusta.  
  
##  <a name="push_back"></a>  basic_string::push_back  
 Dodaje element do końca ciągu.  
  
```  
void push_back(value_type _Ch);
```  
  
### <a name="parameters"></a>Parametry  
 `_Ch`  
 Znak, który ma zostać dodany do końca ciągu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje funkcję elementu członkowskiego [Wstaw](#insert)( [zakończenia](#end), _ *Ch* ).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_push_back.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   string str1 ( "abc" );  
   basic_string <char>::iterator str_Iter, str1_Iter;  
  
   cout << "The original string str1 is: ";  
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )  
      cout << *str_Iter;  
   cout << endl;  
  
   // str1.push_back ( 'd' );  
   str1_Iter = str1.end ( );  
   str1_Iter--;  
   cout << "The last character-letter of the modified str1 is now: "  
        << *str1_Iter << endl;  
  
   cout << "The modified string str1 is: ";  
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )  
      cout << *str_Iter;  
   cout << endl;  
}  
```  
  
```Output  
The original string str1 is: abc  
The last character-letter of the modified str1 is now: c  
The modified string str1 is: abc  
```  
  
##  <a name="rbegin"></a>  basic_string::rbegin  
 Zwraca iteratora do pierwszego elementu w ciągu odwróconej.  
  
```  
const_reverse_iterator rbegin() const;

 
reverse_iterator rbegin();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca iteratora dostępie swobodnym do pierwszego elementu w ciągu odwróconej adresowania, jakie byłyby ostatnim elementem w odpowiedni ciąg stałe.  
  
### <a name="remarks"></a>Uwagi  
 `rbegin` jest używany z ciągiem odwróconej podobnie jak [rozpocząć](#begin) jest używany z ciągiem.  
  
 Jeśli wartość zwracana `rbegin` jest przypisany do `const_reverse_iterator`, nie można zmodyfikować z obiektem ciągu. Jeśli wartość zwracana `rbegin` jest przypisany do `reverse_iterator`, można zmodyfikować z obiektem ciągu.  
  
 `rbegin` można zainicjować wstecz iteracji przez ciąg.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_rbegin.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   string str1 ( "Able was I ere I saw Elba" ), str2;  
   basic_string <char>::reverse_iterator str_rIter, str1_rIter, str2_rIter;  
   basic_string <char>::const_reverse_iterator str1_rcIter;  
  
   str1_rIter = str1.rbegin ( );  
   // str1_rIter--;  
   cout << "The first character-letter of the reversed string str1 is: "  
        << *str1_rIter << endl;  
   cout << "The full reversed string str1 is:\n ";  
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )  
      cout << *str_rIter;  
   cout << endl;  
  
   // The dereferenced iterator can be used to modify a character  
 *str1_rIter = 'A';  
   cout << "The first character-letter of the modified str1 is now: "  
        << *str1_rIter << endl;  
   cout << "The full modified reversed string str1 is now:\n ";  
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )  
      cout << *str_rIter;  
   cout << endl;  
  
   // The following line would be an error because iterator is const  
   // *str1_rcIter = 'A';  
  
   // For an empty string, begin is equivalent to end  
   if ( str2.rbegin( ) == str2.rend ( ) )  
      cout << "The string str2 is empty." << endl;  
   else  
      cout << "The stringstr2  is not empty." << endl;  
}  
```  
  
```Output  
The first character-letter of the reversed string str1 is: a  
The full reversed string str1 is:  
 ablE was I ere I saw elbA  
The first character-letter of the modified str1 is now: A  
The full modified reversed string str1 is now:  
 AblE was I ere I saw elbA  
The string str2 is empty.  
```  
  
##  <a name="reference"></a>  basic_string::Reference  
 Typ, który zawiera odwołanie do elementu przechowywane w ciągu.  
  
```  
typedef typename allocator_type::reference reference;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ **odwołania** może służyć do modyfikowania wartości elementu.  
  
 Typ jest synonimem **allocator_type::reference**.  
  
 Dla typu **ciąg**, jest odpowiednikiem **chr &**.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [w](#at) przykład sposobu deklarowanie i użycie **odwołania**.  
  
##  <a name="rend"></a>  basic_string::rend  
 Zwraca iteratora, którego dotyczy lokalizacji pomyślne ostatnim elementem w ciągu odwróconej.  
  
```  
const_reverse_iterator rend() const;

 
reverse_iterator rend();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwrotnej iteratora dostępie swobodnym, którego dotyczy lokalizacji pomyślne ostatnim elementem w ciągu odwróconej.  
  
### <a name="remarks"></a>Uwagi  
 `rend` jest używany z ciągiem odwróconej podobnie jak [zakończenia](#end) jest używany z ciągiem.  
  
 Jeśli wartość zwracana `rend` jest przypisany do `const_reverse_iterator`, nie można zmodyfikować z obiektem ciągu. Jeśli wartość zwracana `rend` jest przypisany do `reverse_iterator`, można zmodyfikować z obiektem ciągu.  
  
 `rend` może służyć do sprawdzenia, czy odwrotnej iteratora osiągnął koniec parametrach.  
  
 Wartość zwrócona przez `rend` nie powinny być wyłuskiwany.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_rend.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   string str1 ("Able was I ere I saw Elba"), str2;  
   basic_string <char>::reverse_iterator str_rIter, str1_rIter, str2_rIter;  
   basic_string <char>::const_reverse_iterator str1_rcIter;  
  
   str1_rIter = str1.rend ( );  
   str1_rIter--;  
   cout << "The last character-letter of the reversed string str1 is: "  
        << *str1_rIter << endl;  
   cout << "The full reversed string str1 is:\n ";  
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )  
      cout << *str_rIter;  
   cout << endl;  
  
   // The dereferenced iterator can be used to modify a character  
 *str1_rIter = 'o';  
   cout << "The last character-letter of the modified str1 is now: "  
        << *str1_rIter << endl;  
   cout << "The full modified reversed string str1 is now:\n ";  
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )  
      cout << *str_rIter;  
   cout << endl;  
  
   // The following line would be an error because iterator is const  
   // *str1_rcIter = 'T';  
  
   // For an empty string, end is equivalent to begin  
   if ( str2.rbegin( ) == str2.rend ( ) )  
      cout << "The string str2 is empty." << endl;  
   else  
      cout << "The stringstr2  is not empty." << endl;  
}  
```  
  
```Output  
The last character-letter of the reversed string str1 is: A  
The full reversed string str1 is:  
 ablE was I ere I saw elbA  
The last character-letter of the modified str1 is now: o  
The full modified reversed string str1 is now:  
 ablE was I ere I saw elbo  
The string str2 is empty.  
```  
  
##  <a name="replace"></a>  basic_string::replace  
 Zamienia elementów w ciągu na określonej pozycji określonych znaków lub kopiowane z innych zakresów lub ciągów lub C ciągów znaków.  
  
```  
basic_string<CharType, Traits, Allocator>& replace(
    size_type _Pos1,   
    size_type _Num1,  
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& replace(
    size_type _Pos1,   
    size_type _Num1,  
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& replace(
    size_type _Pos1,   
    size_type _Num1,  
    const value_type* ptr,   
    size_type _Num2);

basic_string<CharType, Traits, Allocator>& replace(
    size_type _Pos1,   
    size_type _Num1,  
    const basic_string<CharType, Traits, Allocator>& str,   
    size_type _Pos2,   
    size_type _Num2);

basic_string<CharType, Traits, Allocator>& replace(
    size_type _Pos1,   
    size_type _Num1,  
    size_type count,   
    value_type _Ch);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,   
    iterator last0,  
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,   
    iterator last0,  
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,  
    iterator last0,  
    const value_type* ptr,   
    size_type _Num2);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,   
    iterator last0,  
    size_type _Num2,   
    value_type _Ch);

template <class InputIterator>  
basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,   
    iterator last0,  
    InputIterator first,   
    InputIterator last);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,  
    iterator last0,  
    const_pointer first,  
    const_pointer last);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,  
    iterator last0,  
    const_iterator first,  
    const_iterator last);
```  
  
### <a name="parameters"></a>Parametry  
 `str`  
 Ciąg, który ma być źródłem znaków dla ciągu argumentu operacji.  
  
 `_Pos1`  
 Indeks ciągu operand, od której rozpoczyna się zastąpienia.  
  
 `_Num1`  
 Maksymalna liczba znaków, które mają zostać zastąpione w ciągu argumentu operacji.  
  
 *_Pos2*  
 Indeks ciąg parametru, od którego rozpoczyna się kopiowanie.  
  
 `_Num2`  
 Maksymalna liczba znaków do użycia w parametrze C-ciąg.  
  
 `ptr`  
 C — ciąg, który ma być źródłem znaków dla ciągu argumentu operacji.  
  
 `_Ch`  
 Znak, który ma zostać skopiowany na ciąg argumentu operacji.  
  
 * first0*  
 Iteratora adresowania pierwszego znaku do usunięcia w ciągu argumentu operacji.  
  
 * last0*  
 Iteratora adresowania ostatni znak do usunięcia w ciągu argumentu operacji.  
  
 `first`  
 Iterator, const_pointer lub const_iterator adresowania pierwszego znaku do skopiowania w ciągu parametru.  
  
 `last`  
 Iterator, const_pointer lub const_iterator adresowania ostatni znak do skopiowania w ciągu parametru.  
  
 `count`  
 Ile razy `_Ch` są kopiowane do ciągu argumentu operacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Ciąg argumentu z wprowadzone zastąpienia.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_replace.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   // The first two member functions replace  
   // part of the operand string with  
   // characters from a parameter string or C-string  
   string result1a, result1b;  
   string s1o ( "AAAAAAAA" );  
   string s1p ( "BBB" );  
   const char* cs1p = "CCC";  
   cout << "The operand string s1o is: " << s1o << endl;  
   cout << "The parameter string s1p is: " << s1p << endl;  
   cout << "The parameter C-string cs1p is: " << cs1p << endl;  
   result1a = s1o.replace ( 1 , 3 , s1p );  
   cout << "The result of s1o.replace ( 1 , 3 , s1p )\n is "   
        << "the string: " << result1a << "." << endl;  
   result1b = s1o.replace ( 5 , 3 , cs1p );  
   cout << "The result of s1o.replace ( 5 , 3 , cs1p )\n is "   
        << "the string: " << result1b << "." << endl;  
   cout << endl;  
  
   // The third & fourth member function replace  
   // part of the operand string with characters  
   // form part of a parameter string or C-string  
   string result2a, result2b;  
   string s2o ( "AAAAAAAA" );  
   string s2p ( "BBB" );  
   const char* cs2p = "CCC";  
   cout << "The operand string s2o is: " << s2o << endl;  
   cout << "The parameter string s1p is: " << s2p << endl;  
   cout << "The parameter C-string cs2p is: " << cs2p << endl;  
   result2a = s2o.replace ( 1 , 3 , s2p , 1 , 2 );  
   cout << "The result of s2o.replace (1, 3, s2p, 1, 2)\n is "   
        << "the string: " << result2a << "." << endl;  
   result2b = s2o.replace ( 4 , 3 , cs2p , 1 );  
   cout << "The result of s2o.replace (4 ,3 ,cs2p)\n is "   
        << "the string: " << result2b << "." << endl;  
   cout << endl;  
  
   // The fifth member function replaces  
   // part of the operand string with characters  
   string result3a;  
   string s3o ( "AAAAAAAA" );  
   char ch3p = 'C';  
   cout << "The operand string s3o is: " << s3o << endl;  
   cout << "The parameter character c1p is: " << ch3p << endl;  
   result3a = s3o.replace ( 1 , 3 , 4 , ch3p );  
   cout << "The result of s3o.replace(1, 3, 4, ch3p)\n is "   
        << "the string: " << result3a << "." << endl;  
   cout << endl;  
  
   // The sixth & seventh member functions replace  
   // part of the operand string, delineated with iterators,  
   // with a parameter string or C-string  
   string s4o ( "AAAAAAAA" );  
   string s4p ( "BBB" );  
   const char* cs4p = "CCC";  
   cout << "The operand string s4o is: " << s4o << endl;  
   cout << "The parameter string s4p is: " << s4p << endl;  
   cout << "The parameter C-string cs4p is: " << cs4p << endl;  
   basic_string<char>::iterator IterF0, IterL0;  
   IterF0 = s4o.begin ( );  
   IterL0 = s4o.begin ( ) + 3;  
   string result4a, result4b;  
   result4a = s4o.replace ( IterF0 , IterL0 , s4p );  
   cout << "The result of s1o.replace (IterF0, IterL0, s4p)\n is "   
        << "the string: " << result4a << "." << endl;  
   result4b = s4o.replace ( IterF0 , IterL0 , cs4p );  
   cout << "The result of s4o.replace (IterF0, IterL0, cs4p)\n is "   
        << "the string: " << result4b << "." << endl;  
   cout << endl;  
  
   // The 8th member function replaces  
   // part of the operand string delineated with iterators  
   // with a number of characters from a parameter C-string  
   string s5o ( "AAAAAAAF" );  
   const char* cs5p = "CCCBB";  
   cout << "The operand string s5o is: " << s5o << endl;  
   cout << "The parameter C-string cs5p is: " << cs5p << endl;  
   basic_string<char>::iterator IterF1, IterL1;  
   IterF1 = s5o.begin ( );  
   IterL1 = s5o.begin ( ) + 4;  
   string result5a;  
   result5a = s5o.replace ( IterF1 , IterL1 , cs5p , 4 );  
   cout << "The result of s5o.replace (IterF1, IterL1, cs4p ,4)\n is "   
        << "the string: " << result5a << "." << endl;  
   cout << endl;  
  
   // The 9th member function replaces  
   // part of the operand string delineated with iterators  
   // with specified characters  
   string s6o ( "AAAAAAAG" );  
   char ch6p = 'q';  
   cout << "The operand string s6o is: " << s6o << endl;  
   cout << "The parameter character ch6p is: " << ch6p << endl;  
   basic_string<char>::iterator IterF2, IterL2;  
   IterF2 = s6o.begin ( );  
   IterL2 = s6o.begin ( ) + 3;  
   string result6a;  
   result6a = s6o.replace ( IterF2 , IterL2 , 4 , ch6p );  
   cout << "The result of s6o.replace (IterF1, IterL1, 4, ch6p)\n is "   
        << "the string: " << result6a << "." << endl;  
   cout << endl;  
  
   // The 10th member function replaces  
   // part of the operand string delineated with iterators  
   // with part of a parameter string delineated with iterators  
   string s7o ( "OOOOOOO" );  
   string s7p ( "PPPP" );  
   cout << "The operand string s7o is: " << s7o << endl;  
   cout << "The parameter string s7p is: " << s7p << endl;  
   basic_string<char>::iterator IterF3, IterL3, IterF4, IterL4;  
   IterF3 = s7o.begin ( ) + 1;  
   IterL3 = s7o.begin ( ) + 3;  
   IterF4 = s7p.begin ( );  
   IterL4 = s7p.begin ( ) + 2;  
   string result7a;  
   result7a = s7o.replace ( IterF3 , IterL3 , IterF4 , IterL4 );  
   cout << "The result of s7o.replace (IterF3 ,IterL3 ,IterF4 ,IterL4)\n is "   
        << "the string: " << result7a << "." << endl;  
   cout << endl;  
}  
```  
  
```Output  
The operand string s1o is: AAAAAAAA  
The parameter string s1p is: BBB  
The parameter C-string cs1p is: CCC  
The result of s1o.replace ( 1 , 3 , s1p )  
 is the string: ABBBAAAA.  
The result of s1o.replace ( 5 , 3 , cs1p )  
 is the string: ABBBACCC.  
  
The operand string s2o is: AAAAAAAA  
The parameter string s1p is: BBB  
The parameter C-string cs2p is: CCC  
The result of s2o.replace (1, 3, s2p, 1, 2)  
 is the string: ABBAAAA.  
The result of s2o.replace (4 ,3 ,cs2p)  
 is the string: ABBAC.  
  
The operand string s3o is: AAAAAAAA  
The parameter character c1p is: C  
The result of s3o.replace(1, 3, 4, ch3p)  
 is the string: ACCCCAAAA.  
  
The operand string s4o is: AAAAAAAA  
The parameter string s4p is: BBB  
The parameter C-string cs4p is: CCC  
The result of s1o.replace (IterF0, IterL0, s4p)  
 is the string: BBBAAAAA.  
The result of s4o.replace (IterF0, IterL0, cs4p)  
 is the string: CCCAAAAA.  
  
The operand string s5o is: AAAAAAAF  
The parameter C-string cs5p is: CCCBB  
The result of s5o.replace (IterF1, IterL1, cs4p ,4)  
 is the string: CCCBAAAF.  
  
The operand string s6o is: AAAAAAAG  
The parameter character ch6p is: q  
The result of s6o.replace (IterF1, IterL1, 4, ch6p)  
 is the string: qqqqAAAAG.  
  
The operand string s7o is: OOOOOOO  
The parameter string s7p is: PPPP  
The result of s7o.replace (IterF3 ,IterL3 ,IterF4 ,IterL4)  
 is the string: OPPOOOO.  
```  
  
##  <a name="reserve"></a>  basic_string::Reserve  
 Ustawia przynajmniej tak duże, jak określonej liczby pojemności ciągu na liczbę.  
  
```  
void reserve(size_type count = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `count`  
 Liczba znaków, dla których pamięć jest zarezerwowany.  
  
### <a name="remarks"></a>Uwagi  
 Posiadanie wystarczającą pojemność jest ważne, ponieważ ponowne alokacje jest czasochłonne i unieważnienie wszystkich odwołań, wskaźniki i Iteratory, które odwołują się do znaków w ciągu.  
  
 Koncepcja pojemności dla obiektów typu ciągów jest taka sama jak w przypadku obiektów typu wektora. W odróżnieniu od wektora, funkcja członkowska **zarezerwować** można wywołać w celu zmniejszenia pojemności obiektu. Żądanie jest nonbinding i może lub nie może mieć miejsce. Domyślnie wartość parametru wynosi zero, wywołanie **zarezerwować** jest żądanie bez możliwości wiązania w celu zmniejszenia pojemności ciąg do aktualnie rozmiaru liczbę znaków w ciągu. Pojemność nigdy nie zostanie zmniejszona poniżej bieżącą liczbę znaków.  
  
 Wywoływanie `reserve` jest jedynym sposobem zmniejszenia pojemności ciąg. Jak wspomniano powyżej, to żądanie jest jednak nonbinding i nie może mieć miejsce.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_reserve.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   string str1 ("Hello world");  
   cout << "The original string str1 is: " << str1 << endl;  
  
   basic_string <char>::size_type sizeStr1, sizerStr1;  
   sizeStr1 = str1.size ( );  
   basic_string <char>::size_type capStr1, caprStr1;  
   capStr1 = str1.capacity ( );  
  
   // Compare size & capacity of the original string  
   cout << "The current size of original string str1 is: "   
        << sizeStr1 << "." << endl;  
   cout << "The capacity of original string str1 is: "  
        << capStr1 << "." << endl << endl;  
  
   // Compare size & capacity of the string  
   // with added capacity  
   str1.reserve ( 40 );  
   sizerStr1 = str1.size ( );  
   caprStr1 = str1.capacity ( );  
  
   cout << "The string str1with augmented capacity is: "  
        << str1 << endl;  
   cout << "The current size of string str1 is: "   
        << sizerStr1 << "." << endl;  
   cout << "The new capacity of string str1 is: "  
        << caprStr1 << "." << endl << endl;  
  
   // Compare size & capacity of the string  
   // with downsized capacity  
   str1.reserve ( );  
   basic_string <char>::size_type sizedStr1;  
   basic_string <char>::size_type capdStr1;  
   sizedStr1 = str1.size ( );  
   capdStr1 = str1.capacity ( );  
  
   cout << "The string str1 with downsized capacity is: "  
        << str1 << endl;  
   cout << "The current size of string str1 is: "   
        << sizedStr1 << "." << endl;  
   cout << "The reduced capacity of string str1 is: "  
        << capdStr1 << "." << endl << endl;  
}  
```  
  
```Output  
The original string str1 is: Hello world  
The current size of original string str1 is: 11.  
The capacity of original string str1 is: 15.  
  
The string str1with augmented capacity is: Hello world  
The current size of string str1 is: 11.  
The new capacity of string str1 is: 47.  
  
The string str1 with downsized capacity is: Hello world  
The current size of string str1 is: 11.  
The reduced capacity of string str1 is: 47.  
```  
  
##  <a name="resize"></a>  basic_string::Resize  
 Określa nowy rozmiar ciągu, dołączane lub wymazywanie elementów zgodnie z potrzebami.  
  
```  
void resize(
    size_type count,);

void resize(
    size_type count,  
    _Elem _Ch);
```  
  
### <a name="parameters"></a>Parametry  
 `count`  
 Nowy rozmiar ciągu.  
  
 `_Ch`  
 Wartość, która dołączany znaków są inicjowane z, jeśli wymagane są dodatkowe elementy.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli rozmiar wynikowego przekracza maksymalną liczbę znaków, formularz zgłasza `length_error`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_resize.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   string  str1 ( "Hello world" );  
   cout << "The original string str1 is: " << str1 << endl;  
  
   basic_string <char>::size_type sizeStr1;  
   sizeStr1 = str1.size ( );  
   basic_string <char>::size_type capStr1;  
   capStr1 = str1.capacity ( );  
  
   // Compare size & capacity of the original string  
   cout << "The current size of original string str1 is: "   
        << sizeStr1 << "." << endl;  
   cout << "The capacity of original string str1 is: "  
        << capStr1 << "." << endl << endl;  
  
   // Use resize to increase size by 2 elements: exclamations  
   str1.resize ( str1.size ( ) + 2 , '!' );  
   cout << "The resized string str1 is: " << str1 << endl;  
  
   sizeStr1 = str1.size ( );  
   capStr1 = str1.capacity ( );  
  
   // Compare size & capacity of a string after resizing  
   cout << "The current size of resized string str1 is: "   
        << sizeStr1 << "." << endl;  
   cout << "The capacity of resized string str1 is: "  
        << capStr1 << "." << endl << endl;  
  
   // Use resize to increase size by 20 elements:  
   str1.resize ( str1.size ( ) + 20 );  
   cout << "The resized string str1 is: " << str1 << endl;  
  
   sizeStr1 = str1.size ( );  
   capStr1 = str1.capacity ( );  
  
   // Compare size & capacity of a string after resizing  
   // note capacity increases automatically as required  
   cout << "The current size of modified string str1 is: "   
        << sizeStr1 << "." << endl;  
   cout << "The capacity of modified string str1 is: "  
        << capStr1 << "." << endl << endl;  
  
   // Use resize to downsize by 28 elements:  
   str1.resize ( str1.size ( ) - 28 );  
   cout << "The downsized string str1 is: " << str1 << endl;  
  
   sizeStr1 = str1.size (  );  
   capStr1 = str1.capacity (  );  
  
   // Compare size & capacity of a string after downsizing  
   cout << "The current size of downsized string str1 is: "   
        << sizeStr1 << "." << endl;  
   cout << "The capacity of downsized string str1 is: "  
        << capStr1 << "." << endl;  
}  
```  
  
```Output  
The original string str1 is: Hello world  
The current size of original string str1 is: 11.  
The capacity of original string str1 is: 15.  
  
The resized string str1 is: Hello world!!  
The current size of resized string str1 is: 13.  
The capacity of resized string str1 is: 15.  
  
The resized string str1 is: Hello world!!                      
The current size of modified string str1 is: 33.  
The capacity of modified string str1 is: 47.  
  
The downsized string str1 is: Hello  
The current size of downsized string str1 is: 5.  
The capacity of downsized string str1 is: 47.  
```  
  
##  <a name="reverse_iterator"></a>  basic_string::reverse_iterator  
 Typ, który zawiera odwołanie do elementu przechowywane w ciągu.  
  
```  
typedef std::reverse_iterator<iterator> reverse_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `reverse_iterator` może służyć do modyfikowania wartości znaku i jest używany do iterowania po ciągu odwrotnie.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rbegin](#rbegin) przykład sposobu deklarowanie i użycie `reverse_iterator`.  
  
##  <a name="rfind"></a>  basic_string::rfind  
 Wyszukuje ciąg w kierunku do tyłu dla pierwszego wystąpienia podciągu, który odpowiada określonej sekwencji znaków.  
  
```  
size_type rfind(
    value_type _Ch,   
    size_type _Off = npos) const;

 
size_type rfind(
    const value_type* ptr,  
    size_type _Off = npos) const;

 
size_type rfind(
    const value_type* ptr,   
    size_type _Off,  
    size_type count) const;

 
size_type rfind(
    const basic_string<CharType, Traits, Allocator>& str,  
    size_type _Off = npos) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Ch`  
 Wartość znak, dla którego funkcja członkowska jest do wyszukiwania.  
  
 `_Off`  
 Indeks pozycji, o której ma się rozpocząć wyszukiwanie.  
  
 `ptr`  
 C-ciąg dla którego funkcja członkowska jest do wyszukiwania.  
  
 `count`  
 Liczba znaków, do przodu licząc od pierwszego znaku w ciągu C dla którego funkcja członkowska jest do wyszukiwania.  
  
 `str`  
 Ciąg, którego funkcja członkowska jest do wyszukiwania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks ostatniego wystąpienia, gdy Wstecz, przeszukiwane pierwszego znaku podciągu zakończone powodzeniem; w przeciwnym razie `npos`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_rfind.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // The first member function  
   // searches for a single character in a string  
   string str1 ( "Hello Everyone" );  
   cout << "The original string str1 is: " << str1 << endl;  
   basic_string <char>::size_type indexCh1a, indexCh1b;  
   static const basic_string <char>::size_type npos = -1;  
  
   indexCh1a = str1.rfind ( "e" , 9 );  
   if ( indexCh1a != npos )  
      cout << "The index of the 1st 'e' found before the 9th"  
           << " position in str1 is: " << indexCh1a << endl;  
   else  
      cout << "The character 'e' was not found in str1 ." << endl;  
  
   indexCh1b = str1.rfind ( "x" );  
   if ( indexCh1b != npos )  
      cout << "The index of the 'x' found in str1 is: "  
           << indexCh1b << endl << endl;  
   else  
      cout << "The character 'x' was not found in str1."  
           << endl << endl;  
  
   // The second member function searches a string  
   // for a substring as specified by a C-string  
   string str2 ( "Let me make this perfectly clear." );  
   cout << "The original string str2 is: " << str2 << endl;  
   basic_string <char>::size_type indexCh2a, indexCh2b;  
  
   const char *cstr2 = "perfect";  
   indexCh2a = str2.rfind ( cstr2 , 30 );  
   if ( indexCh2a != npos )  
      cout << "The index of the 1st element of 'perfect' "  
           << "before\n the 30th position in str2 is: "  
           << indexCh2a << endl;  
   else  
      cout << "The substring 'perfect' was not found in str2 ."  
           << endl;  
  
   const char *cstr2b = "imperfectly";  
   indexCh2b = str2.rfind ( cstr2b , 30 );  
   if ( indexCh2b != npos )  
      cout << "The index of the 1st element of 'imperfect' "  
           << "before\n the 5th position in str3 is: "  
           << indexCh2b << endl;  
   else  
      cout << "The substring 'imperfect' was not found in str2 ."  
           << endl << endl;  
  
   // The third member function searches a string  
   // for a substring as specified by a C-string  
   string str3 ( "It is a nice day. I am happy." );  
   cout << "The original string str3 is: " << str3 << endl;  
   basic_string <char>::size_type indexCh3a, indexCh3b;  
  
   const char *cstr3a = "nice";  
   indexCh3a = str3.rfind ( cstr3a );  
   if ( indexCh3a != npos )  
      cout << "The index of the 1st element of 'nice' "  
           << "in str3 is: " << indexCh3a << endl;  
   else  
      cout << "The substring 'nice' was not found in str3 ."  
           << endl;  
  
   const char *cstr3b = "am";  
   indexCh3b = str3.rfind ( cstr3b , indexCh3a + 25 , 2 );  
   if ( indexCh3b != npos )  
      cout << "The index of the next occurrance of 'am' in "  
           << "str3 begins at: " << indexCh3b << endl << endl;  
   else  
      cout << "There is no next occurrence of 'am' in str3 ."  
           << endl << endl;  
  
   // The fourth member function searches a string  
   // for a substring as specified by a string  
   string str4 ( "This perfectly unclear." );  
   cout << "The original string str4 is: " << str4 << endl;  
   basic_string <char>::size_type indexCh4a, indexCh4b;  
  
   string str4a ( "clear" );  
   indexCh4a = str4.rfind ( str4a , 15 );  
   if (indexCh4a != npos )  
      cout << "The index of the 1st element of 'clear' "  
           << "before\n the 15th position in str4 is: "  
           << indexCh4a << endl;  
   else  
      cout << "The substring 'clear' was not found in str4 "  
           << "before the 15th position." << endl;  
  
   string str4b ( "clear" );  
   indexCh4b = str4.rfind ( str4b );  
   if ( indexCh4b != npos )  
      cout << "The index of the 1st element of 'clear' "  
           << "in str4 is: "  
           << indexCh4b << endl;  
   else  
      cout << "The substring 'clear' was not found in str4 ."  
           << endl << endl;  
}  
```  
  
```Output  
The original string str1 is: Hello Everyone  
The index of the 1st 'e' found before the 9th position in str1 is: 8  
The character 'x' was not found in str1.  
  
The original string str2 is: Let me make this perfectly clear.  
The index of the 1st element of 'perfect' before  
 the 30th position in str2 is: 17  
The substring 'imperfect' was not found in str2 .  
  
The original string str3 is: It is a nice day. I am happy.  
The index of the 1st element of 'nice' in str3 is: 8  
The index of the next occurrance of 'am' in str3 begins at: 20  
  
The original string str4 is: This perfectly unclear.  
The substring 'clear' was not found in str4 before the 15th position.  
The index of the 1st element of 'clear' in str4 is: 17  
```  
  
##  <a name="shrink_to_fit"></a>  basic_string::shrink_to_fit  
 Odrzuca nadmiarowej pojemności ciągu.  
  
```  
void shrink_to_fit();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska eliminuje wszelkie niepotrzebne magazynu w kontenerze.  
  
##  <a name="size"></a>  basic_string::size  
 Zwraca bieżącą liczbę elementów w ciągu.  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Długość ciągu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_size.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   string str1 ("Hello world");  
   cout << "The original string str1 is: " << str1 << endl;  
  
   // The size and length member functions differ in name only  
   basic_string <char>::size_type sizeStr1, lenStr1;  
   sizeStr1 = str1.size (  );  
   lenStr1 = str1.length (  );  
  
   basic_string <char>::size_type capStr1, max_sizeStr1;  
   capStr1 = str1.capacity (  );  
   max_sizeStr1 = str1.max_size (  );  
  
   // Compare size, length, capacity & max_size of a string  
   cout << "The current size of original string str1 is: "   
        << sizeStr1 << "." << endl;  
   cout << "The current length of original string str1 is: "   
        << lenStr1 << "." << endl;  
   cout << "The capacity of original string str1 is: "  
        << capStr1 << "." << endl;  
   cout << "The max_size of original string str1 is: "   
        << max_sizeStr1 << "." << endl << endl;  
  
   str1.erase ( 6, 5 );  
   cout << "The modified string str1 is: " << str1 << endl;  
  
   sizeStr1 = str1.size ( );  
   lenStr1 = str1.length ( );  
   capStr1 = str1.capacity ( );  
   max_sizeStr1 = str1.max_size ( );  
  
   // Compare size, length, capacity & max_size of a string  
   // after erasing part of the original string  
   cout << "The current size of modified string str1 is: "   
        << sizeStr1 << "." << endl;  
   cout << "The current length of modified string str1 is: "   
        << lenStr1 << "." << endl;  
   cout << "The capacity of modified string str1 is: "  
        << capStr1 << "." << endl;  
   cout << "The max_size of modified string str1 is: "   
        << max_sizeStr1 << "." << endl;  
}  
```  
  
##  <a name="size_type"></a>  basic_string::size_type  
 Typ liczby całkowitej bez znaku, który może reprezentować liczbę elementów i indeksów w ciągu.  
  
```  
typedef typename allocator_type::size_type size_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jest to równoważne **allocator_type::size_type**.  
  
 Dla typu **ciąg**, jest odpowiednikiem **size_t**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_size_type.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   string str1 ( "Hello world" );  
  
   basic_string <char>::size_type sizeStr1, capStr1;  
   sizeStr1 = str1.size (  );  
   capStr1 = str1.capacity (  );  
  
   cout << "The current size of string str1 is: "   
        << sizeStr1 << "." << endl;  
   cout << "The capacity of string str1 is: " << capStr1   
         << "." << endl;  
}  
```  
  
```Output  
The current size of string str1 is: 11.  
The capacity of string str1 is: 15.  
```  
  
##  <a name="substr"></a>  basic_string::substr  
 Kopiuje podciąg co najwyżej pewną liczbę znaków od początku ciągu, od określonej pozycji.  
  
```  
basic_string<CharType, Traits, Allocator> substr(
    size_type _Off = 0,  
    size_type count = npos) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Off`  
 Indeks lokalizowania elementu w miejscu, z którego ma zostać kopię ciąg, wartość domyślna 0.  
  
 `count`  
 Liczba znaków, które mają być kopiowane, jeśli są obecne.  
  
### <a name="return-value"></a>Wartość zwracana  
 Obiekt podciąg, który jest kopią elementy argument ciągu rozpoczynający się od określonej w pierwszym argumencie pozycji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_substr.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   string  str1 ("Heterological paradoxes are persistent.");  
   cout << "The original string str1 is: \n " << str1  
        << endl << endl;  
  
   basic_string <char> str2 = str1.substr ( 6 , 7 );  
   cout << "The substring str1 copied is: " << str2  
        << endl << endl;  
  
   basic_string <char> str3 = str1.substr (  );  
   cout << "The default substring str3 is: \n " << str3  
        <<  "\n which is the entire original string." << endl;  
}  
```  
  
```Output  
The original string str1 is:   
 Heterological paradoxes are persistent.  
  
The substring str1 copied is: logical  
  
The default substring str3 is:   
 Heterological paradoxes are persistent.  
 which is the entire original string.  
```  
  
##  <a name="swap"></a>  basic_string::swap  
 Wymiany zawartości dwóch ciągów.  
  
```  
void swap(
    basic_string<CharType, Traits, Allocator>& str);
```  
  
### <a name="parameters"></a>Parametry  
 `str`  
 Ciąg źródłowy, której elementy są wymienianych z aliasami w ciągu docelowego.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ciągi są wymieniane mają ten sam obiekt alokatora `swap` funkcji członkowskiej:  
  
-   Występuje w czasie stałej.  
  
-   Zgłasza wyjątek bez wyjątków.  
  
-   Unieważnia nie odwołań, wskaźniki lub Iteratory, które określają elementów w dwóch ciągów.  
  
 W przeciwnym razie wykonuje szereg element zadania i wywołania konstruktora proporcjonalny do liczby elementów w dwóch kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_swap.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   // Declaring an objects of type basic_string<char>  
   string s1 ( "Tweedledee" );  
   string s2 ( "Tweedledum" );  
   cout << "Before swapping string s1 and s2:" << endl;  
   cout << " The basic_string s1 = " << s1 << "." << endl;  
   cout << " The basic_string s2 = " << s2 << "." << endl;  
  
   s1.swap ( s2 );  
   cout << "After swapping string s1 and s2:" << endl;  
   cout << " The basic_string s1 = " << s1 << "." << endl;  
   cout << " The basic_string s2 = " << s2 << "." << endl;  
}  
```  
  
```Output  
Before swapping string s1 and s2:  
 The basic_string s1 = Tweedledee.  
 The basic_string s2 = Tweedledum.  
After swapping string s1 and s2:  
 The basic_string s1 = Tweedledum.  
 The basic_string s2 = Tweedledee.  
```  
  
##  <a name="traits_type"></a>  basic_string::traits_type  
 Typ dla cech znaków elementy przechowywane w ciągu.  
  
```  
typedef Traits traits_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem dla drugiego parametru szablonu **cech**.  
  
 Dla typu **ciąg**, jest odpowiednikiem **char_traits\<char >**.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [kopiowania](../standard-library/char-traits-struct.md#copy) przykład sposobu deklarowanie i użycie `traits_type`.  
  
##  <a name="value_type"></a>  basic_string::value_type  
 Typ, który reprezentuje typ przechowywane w ciągu znaków.  
  
```  
typedef typename allocator_type::value_type value_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jest to równoważne **traits_type::char_type** i stanowi odpowiednik `char` dla obiektów typu **ciąg**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_string_value_type.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   basic_string<char>::value_type ch1 = 'G';  
  
   char ch2 = 'H';  
  
   cout << "The character ch1 is: " << ch1 << "." << endl;  
   cout << "The character ch2 is: " << ch2 << "." << endl;  
}  
```  
  
```Output  
The character ch1 is: G.  
The character ch2 is: H.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<string>](../standard-library/string.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

