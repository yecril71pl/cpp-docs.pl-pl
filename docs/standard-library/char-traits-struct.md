---
title: "char_traits — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- iosfwd/std::char_traits
- iosfwd/std::char_traits::char_type
- iosfwd/std::char_traits::int_type
- iosfwd/std::char_traits::off_type
- iosfwd/std::char_traits::pos_type
- iosfwd/std::char_traits::state_type
- iosfwd/std::char_traits::assign
- iosfwd/std::char_traits::compare
- iosfwd/std::char_traits::copy
- iosfwd/std::char_traits::_Copy_s
- iosfwd/std::char_traits::eof
- iosfwd/std::char_traits::eq
- iosfwd/std::char_traits::eq_int_type
- iosfwd/std::char_traits::find
- iosfwd/std::char_traits::length
- iosfwd/std::char_traits::lt
- iosfwd/std::char_traits::move
- iosfwd/std::char_traits::_Move_s
- iosfwd/std::char_traits::not_eof
- iosfwd/std::char_traits::to_char_type
- iosfwd/std::char_traits::to_int_type
dev_langs: C++
helpviewer_keywords:
- char_traits struct
- char_traits class
ms.assetid: 568e59f0-4521-4207-9223-9dcf6a16d620
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e0ad63f077bcc018681f852d1495e9f1abd7d4fd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="chartraits-struct"></a>char_traits — Struktura
Char_traits — struktura opisano atrybuty skojarzone ze znakiem.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class CharType>  
struct char_traits;  
```  
  
#### <a name="parameters"></a>Parametry  
 `CharType`  
 Typ elementu danych.  
  
## <a name="remarks"></a>Uwagi  
 Struktura szablonu w tym artykule opisano różne cech znaków dla typu **CharType**. Klasy szablonów [basic_string —](../standard-library/basic-string-class.md) oraz kilka klasy szablonu iostream, w tym [basic_ios —](../standard-library/basic-ios-class.md), te informacje służą do modyfikowania elementów typu **CharType** . Typ elementu nie może wymagać jawnego utworzenia lub zniszczenia. Podaj konstruktora domyślnego konstruktora kopiującego i operatora przypisania z oczekiwanym semantyki. Bitowe kopii musi mieć ten sam efekt co przypisania. Brak funkcji Członkowskich char_traits — struktura jest zgłaszają wyjątki.  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#char_type)|Typ znaku.|  
|[int_type](#int_type)|Typu integer, mogącej reprezentować znaku typu `char_type` lub znak zakończenia pliku (EOF).|  
|[off_type](#off_type)|Integer — typ reprezentujące przesunięcia od pozycji w strumieniu.|  
|[pos_type](#pos_type)|Integer — typ reprezentujące pozycji w strumieniu.|  
|[state_type](#state_type)|Typ, który reprezentuje stan konwersji w przypadku znaków wielobajtowych w strumieniu.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[Przypisz](#assign)|Przypisuje wartość jednego znaku do innego.|  
|[Porównaj](#compare)|Porównuje maksymalnie określoną liczbę znaków w dwóch ciągów.|  
|[Kopiuj](#copy)|Kopiuje określoną liczbę znaków z ciągu na inny. Przestarzałe. Użyj [char_traits::_Copy_s](#copy_s) zamiast tego.|  
|[_Copy_s](#copy_s)|Kopiuje określoną liczbę znaków z ciągu na inny.|  
|[EOF](#eof)|Zwraca znak końcowy pliku (EOF).|  
|[EQ](#eq)|Sprawdza, czy dwa `char_type` znaki są takie same.|  
|[eq_int_type](#eq_int_type)|Sprawdza, czy dwa znaki reprezentowane jako `int_type`s są takie same.|  
|[Znajdź](#find)|Wyszukuje pierwsze wystąpienie określonego znaku w zakresie znaków.|  
|[długość](#length)|Zwraca długość ciągu.|  
|[lt](#lt)|Sprawdza, czy znak jest mniejsza niż innym.|  
|[Przenieś](#move)|Kopiuje określoną liczbę znaków w sekwencji do innego, nakładających się to możliwe, sekwencji. Przestarzałe. Użyj [char_traits::_Move_s](#move_s) zamiast tego.|  
|[_Move_s](#move_s)|Kopiuje określoną liczbę znaków w sekwencji do innego, nakładających się to możliwe, sekwencji.|  
|[not_eof](#not_eof)|Sprawdza, czy znak jest znak końca pliku (EOF).|  
|[to_char_type](#to_char_type)|Konwertuje `int_type` znak do odpowiednich `char_type` znaku i zwraca wynik.|  
|[to_int_type](#to_int_type)|Konwertuje `char_type` znak do odpowiednich `int_type` znaku i zwraca wynik.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<ciąg >  
  
 **Namespace:** Standard  
  
##  <a name="assign"></a>char_traits::ASSIGN  
 Przypisuje wartość jednego znaku do innego lub zakres elementów w ciągu.  
  
```  
static void assign(char_type& _CharTo,
    const char_type& _CharFrom);

static char_type *assign(char_type* strTo,
    size_t _Num,
    char_type _CharFrom);
```  
  
### <a name="parameters"></a>Parametry  
 **_** *CharFrom*  
 Znak, którego wartość ma być przypisana.  
  
 *_CharTo*  
 Element, który ma być przypisana wartość znaku.  
  
 * strTo *  
 Ciąg lub znak tablica której początkowej elementy mają zostać przypisane wartości znakowych.  
  
 `_Num`  
 Liczba elementów, które mają być można przypisać wartości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Drugi funkcji członkowskiej zwraca wskaźnik do ciągu których pierwszy `_Num` elementy zostały przypisane wartości *_CharFrom*.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// char_traits_assign.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   // The first member function assigning   
   // one character value to another character  
   char ChTo = 't';  
   const char ChFrom = 'f';  
   cout << "The initial characters ( ChTo , ChFrom ) are: ( "  
        << ChTo << " , " << ChFrom << " )." << endl;  
   char_traits<char>::assign ( ChTo , ChFrom );  
   cout << "After assigning, the characters ( ChTo , ChFrom ) are: ( "  
        << ChTo << " , " << ChFrom << " )." << endl << endl;  
  
   // The second member function assigning   
   // character values to initial part of a string  
   char_traits<char>::char_type s1[] = "abcd-1234-abcd";  
   char_traits<char>::char_type* result1;  
   cout << "The target string s1 is: " << s1 << endl;  
   result1 = char_traits<char>::assign ( s1 , 4 , 'f' );  
   cout << "The result1 = assign ( s1 , 4 , 'f' ) is: "  
        << result1 << endl;  
}  
```  
  
```Output  
The initial characters ( ChTo , ChFrom ) are: ( t , f ).  
After assigning, the characters ( ChTo , ChFrom ) are: ( f , f ).  
  
The target string s1 is: abcd-1234-abcd  
The result1 = assign ( s1 , 4 , 'f' ) is: ffff-1234-abcd  
```  
  
##  <a name="char_type"></a>char_traits::char_type  
 Typ znaku.  
  
```  
typedef CharType char_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem parametru szablonu **CharType**.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [kopiowania](#copy) przykład sposobu deklarowanie i użycie `char_type`.  
  
##  <a name="compare"></a>char_traits::COMPARE  
 Porównuje maksymalnie określoną liczbę znaków w dwóch ciągów.  
  
```  
static int compare(const char_type* str1,
    const char_type* str2,
    size_t _Num);
```  
  
### <a name="parameters"></a>Parametry  
 * str1 *  
 Pierwsze dwa ciągi, które ma być porównywana ze sobą.  
  
 * str2 *  
 Drugi dwa ciągi, które ma być porównywana ze sobą.  
  
 `_Num`  
 Liczba elementów w ciągach do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Ujemna wartość, jeśli pierwszy ciąg jest mniejszy niż drugi ciąg znaków, 0, jeśli dwa ciągi są równe lub wartość dodatnią, jeśli pierwszy ciąg jest większy niż drugi ciąg.  
  
### <a name="remarks"></a>Uwagi  
 Porównanie ciągów jest dokonywane elementu przez element pierwszego testowania pod kątem równości, a następnie, jeśli dwa elementy w sekwencji testów nie równa, ich są sprawdzane pod kątem poniżej.  
  
 Jeśli dwa ciągi porównanie w zakresie, ale jeden jest dłuższy niż inne, a następnie krótszą dwóch jest mniejsza niż dłużej.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// char_traits_compare.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main() {  
   using namespace std;  
  
   char_traits<char>::char_type* s1 = "CAB";  
   char_traits<char>::char_type* s2 = "ABC";  
   char_traits<char>::char_type* s3 = "ABC";  
   char_traits<char>::char_type* s4 = "ABCD";  
  
   cout << "The string s1 is: " << s1 << endl;  
   cout << "The string s2 is: " << s2 << endl;  
   cout << "The string s3 is: " << s3 << endl;  
   cout << "The string s4 is: " << s4 << endl;  
  
   int comp1, comp2, comp3, comp4;  
   comp1 = char_traits<char>::compare ( s1 , s2 , 2 );  
   comp2 = char_traits<char>::compare ( s2 , s3 , 3 );  
   comp3 = char_traits<char>::compare ( s3 , s4 , 4 );  
   comp4 = char_traits<char>::compare ( s4 , s3 , 4 );  
   cout << "compare ( s1 , s2 , 2 ) = " << comp1 << endl;  
   cout << "compare ( s2 , s3 , 3 ) = " << comp2 << endl;  
   cout << "compare ( s3 , s4 , 4 ) = " << comp3 << endl;  
   cout << "compare ( s4 , s3 , 4 ) = " << comp4 << endl;  
}  
```  
  
##  <a name="copy"></a>char_traits::Copy  
 Kopiuje określoną liczbę znaków z ciągu na inny.  
  
 Ta metoda jest potencjalnie niebezpieczne, ponieważ zależy od obiekt wywołujący, aby sprawdzić, czy przekazane wartości są poprawne. Należy rozważyć użycie [char_traits::_Copy_s](#copy_s) zamiast tego.  
  
```  
static char_type *copy(char_type* _To,
    const char_type* _From,
    size_t _Num);
```  
  
### <a name="parameters"></a>Parametry  
 `_To`  
 Element na początku ciąg lub znak tablicy przeznaczone do odbierania skopiowanych sekwencji znaków.  
  
 `_From`  
 Element na początku tablicy źródłowej na ciąg lub znak do skopiowania.  
  
 `_Num`  
 Liczba elementów do skopiowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy element skopiować do tablicy ciąg lub znak przeznaczone do odbierania skopiowanych sekwencji znaków.  
  
### <a name="remarks"></a>Uwagi  
 Sekwencje znaków źródłowych i docelowych musi nie mogą się pokrywać.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// char_traits_copy.cpp  
// compile with: /EHsc /W3  
#include <string>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   char_traits<char>::char_type s1[] = "abcd-1234-abcd";  
   char_traits<char>::char_type s2[] = "ABCD-1234";  
   char_traits<char>::char_type* result1;  
   cout << "The source string is: " << s1 << endl;  
   cout << "The destination string is: " << s2 << endl;  
   // Note: char_traits::copy is potentially unsafe, consider  
   // using char_traits::_Copy_s instead.  
   result1 = char_traits<char>::copy ( s1 , s2 , 4 );  // C4996  
   cout << "The result1 = copy ( s1 , s2 , 4 ) is: "  
        << result1 << endl;  
}  
```  
  
```Output  
The source string is: abcd-1234-abcd  
The destination string is: ABCD-1234  
The result1 = copy ( s1 , s2 , 4 ) is: ABCD-1234-abcd  
```  
  
##  <a name="copy_s"></a>char_traits::_Copy_s  
 Kopiuje określoną liczbę znaków z ciągu na inny.  
  
```  
static char_type *_Copy_s(
    char_type* dest,  
    size_t dest_size,  
    const char_type* _From,  
    size_t count);
```  
  
### <a name="parameters"></a>Parametry  
 `dest`  
 Tablica ciąg lub znak przeznaczone do odbierania skopiowanych sekwencji znaków.  
  
 `dest_size`  
 Rozmiar `dest`. Jeśli `char_type` jest `char`, a następnie ten rozmiar jest w bajtach. Jeśli `char_type` jest `wchar_t`, to ten rozmiar jest słowami.  
  
 `_From`  
 Ciąg lub znak tablicy źródłowej do skopiowania.  
  
 `count`  
 Liczba elementów do skopiowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Tablica ciąg lub znak przeznaczone do odbierania skopiowanych sekwencji znaków.  
  
### <a name="remarks"></a>Uwagi  
 Sekwencje znaków źródłowych i docelowych musi nie mogą się pokrywać.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// char_traits__Copy_s.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
  
    char_traits<char>::char_type s1[] = "abcd-1234-abcd";  
    char_traits<char>::char_type s2[] = "ABCD-1234";  
    char_traits<char>::char_type* result1;  
    cout << "The source string is: " << s1 << endl;  
    cout << "The destination string is: " << s2 << endl;  
    result1 = char_traits<char>::_Copy_s(s1,  
        char_traits<char>::length(s1), s2, 4);  
    cout << "The result1 = _Copy_s(s1, "  
         << "char_traits<char>::length(s1), s2, 4) is: "  
         << result1 << endl;  
}  
```  
  
```Output  
The source string is: abcd-1234-abcd  
The destination string is: ABCD-1234  
The result1 = _Copy_s(s1, char_traits<char>::length(s1), s2, 4) is: ABCD-1234-abcd  
```  
  
##  <a name="eof"></a>char_traits::EOF  
 Zwraca znak końcowy pliku (EOF).  
  
```  
static int_type eof();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Znak EOF.  
  
### <a name="remarks"></a>Uwagi  
 Wartość reprezentującą koniec pliku (takich jak `EOF` lub `WEOF`).  
  
 Wartość ta nie musi odpowiadać na prawidłową stany standard C++ `char_type` wartość. Kompilator Visual C++ wymusza to ograniczenie dla typu `char`, ale nie dla typu `wchar_t`. Prezentuje to poniższy przykład.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// char_traits_eof.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
  
    char_traits<char>::char_type ch1 = 'x';  
    char_traits<char>::int_type int1;  
    int1 = char_traits<char>::to_int_type(ch1);  
    cout << "char_type ch1 is '" << ch1 << "' and corresponds to int_type "  
         << int1 << "." << endl << endl;  
  
    char_traits<char>::int_type int2 = char_traits<char>::eof();  
    cout << "The eof marker for char_traits<char> is: " << int2 << endl;  
  
    char_traits<wchar_t>::int_type int3 = char_traits<wchar_t>::eof();  
    cout << "The eof marker for char_traits<wchar_t> is: " << int3 << endl;  
}  
```  
  
```Output  
char_type ch1 is 'x' and corresponds to int_type 120.  
  
The eof marker for char_traits<char> is: -1  
The eof marker for char_traits<wchar_t> is: 65535  
```  
  
##  <a name="eq"></a>char_traits::EQ  
 Sprawdza, czy dwa `char_type` znaki są takie same.  
  
```  
static bool eq(const char_type& _Ch1, const char_type& _Ch2);
```  
  
### <a name="parameters"></a>Parametry  
 `_Ch1`  
 Pierwsze dwa znaki pod kątem równości.  
  
 `_Ch2`  
 Drugi dwa znaki pod kątem równości.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** jeśli pierwszym znakiem jest równa drugim znaku; w przeciwnym razie **false**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// char_traits_eq.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   char_traits<char>::char_type ch1 =  'x';  
   char_traits<char>::char_type ch2 =  'y';  
   char_traits<char>::char_type ch3 =  'x';  
  
   // Testing for equality  
   bool b1 = char_traits<char>::eq ( ch1 , ch2 );  
   if ( b1 )  
      cout << "The character ch1 is equal "  
           << "to the character ch2." << endl;  
   else  
      cout << "The character ch1 is not equal "  
           << "to the character ch2." << endl;  
  
   // An equivalent and alternatively test procedure  
   if ( ch1 == ch3 )  
      cout << "The character ch1 is equal "  
           << "to the character ch3." << endl;  
   else  
      cout << "The character ch1 is not equal "  
           << "to the character ch3." << endl;  
}  
```  
  
```Output  
The character ch1 is not equal to the character ch2.  
The character ch1 is equal to the character ch3.  
```  
  
##  <a name="eq_int_type"></a>char_traits::eq_int_type  
 Sprawdza, czy dwa znaki reprezentowane jako `int_type`s są takie same lub nie.  
  
```  
static bool eq_int_type(const int_type& _Ch1, const int_type& _Ch2);
```  
  
### <a name="parameters"></a>Parametry  
 `_Ch1`  
 Pierwszy z dwóch znaków pod kątem równości **int_type**s.  
  
 `_Ch2`  
 Drugi dwa znaki pod kątem równości `int_type`s.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** jeśli pierwszym znakiem jest równa drugim znaku; w przeciwnym razie **false**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// char_traits_eq_int_type.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   char_traits<char>::char_type ch1 =  'x';  
   char_traits<char>::char_type ch2 =  'y';  
   char_traits<char>::char_type ch3 =  'x';  
  
   // Converting from char_type to int_type  
   char_traits<char>::int_type int1, int2 , int3;  
   int1 =char_traits<char>:: to_int_type ( ch1 );  
   int2 =char_traits<char>:: to_int_type ( ch2 );  
   int3 =char_traits<char>:: to_int_type ( ch3 );  
  
   cout << "The char_types and corresponding int_types are:"  
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "  
        << int1 << "."  
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "  
        << int2 << "."  
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "  
        << int3 << "." << endl << endl;  
  
   // Testing for equality of int_type representations  
   bool b1 = char_traits<char>::eq_int_type ( int1 , int2 );  
   if ( b1 )  
      cout << "The int_type representation of character ch1\n "  
           << "is equal to the int_type representation of ch2."  
           << endl;  
   else  
      cout << "The int_type representation of character ch1\n is "  
           << "not equal to the int_type representation of ch2."  
           << endl;  
  
   // An equivalent and alternatively test procedure  
   if ( int1 == int3 )  
      cout << "The int_type representation of character ch1\n "  
           << "is equal to the int_type representation of ch3."  
           << endl;  
   else  
      cout << "The int_type representation of character ch1\n is "  
           << "not equal to the int_type representation of ch3."  
           << endl;  
}  
```  
  
```Output  
The char_types and corresponding int_types are:  
    ch1 = x corresponding to int1 = 120.  
    ch2 = y corresponding to int1 = 121.  
    ch3 = x corresponding to int1 = 120.  
  
The int_type representation of character ch1  
 is not equal to the int_type representation of ch2.  
The int_type representation of character ch1  
 is equal to the int_type representation of ch3.  
```  
  
##  <a name="find"></a>char_traits::Find  
 Wyszukuje pierwsze wystąpienie określonego znaku w zakresie znaków.  
  
```  
static const char_type* find(const char_type* str,
    size_t _Num,
    const char_type& _Ch);
```  
  
### <a name="parameters"></a>Parametry  
 `str`  
 Pierwszy znak w ciągu do wyszukania.  
  
 `_Num`  
 Liczba pozycji, licząc od pierwszego, w zakresie do wyszukania.  
  
 `_Ch`  
 Znak, który ma zostać wyszukany w zakresie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do pierwszego wystąpienia określony znak z zakresu, jeśli znaleziono; w przeciwnym razie wartość wskaźnika o wartości null.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// char_traits_find.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   const char* s1 = "f2d-1234-abcd";  
   const char* result1;  
   cout << "The string to be searched is: " << s1 << endl;  
  
   // Searching for a 'd' in the first 6 positions of string s1  
   result1 = char_traits<char>::find ( s1 , 6 , 'd');  
   cout << "The character searched for in s1 is: "  
        << *result1 << endl;  
   cout << "The string beginning with the first occurrence\n "  
        << "of the character 'd' is: " << result1 << endl;  
  
   // When no match is found the NULL value is returned  
   const char* result2;  
   result2 = char_traits<char>::find ( s1 , 3 , 'a');  
   if ( result2 == NULL )  
      cout << "The result2 of the search is NULL." << endl;  
   else  
      cout << "The result2 of the search  is: " << result1  
           << endl;  
}  
```  
  
```Output  
The string to be searched is: f2d-1234-abcd  
The character searched for in s1 is: d  
The string beginning with the first occurrence  
 of the character 'd' is: d-1234-abcd  
The result2 of the search is NULL.  
```  
  
##  <a name="int_type"></a>char_traits::int_type  
 Typu integer, mogącej reprezentować znaku typu `char_type` lub znak zakończenia pliku (EOF).  
  
```  
typedef long int_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Musi być możliwe do typu rzutowania wartości typu **CharType** do `int_type` następnie wróć do **CharType** bez zmiany oryginalnej wartości.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [eq_int_type](#eq_int_type) przykład sposobu deklarowanie i użycie `int_type`.  
  
##  <a name="length"></a>char_traits::length  
 Zwraca długość ciągu.  
  
```  
static size_t length(const char_type* str);
```  
  
### <a name="parameters"></a>Parametry  
 `str`  
 C — ciąg, którego długość ma być mierzony.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w sekwencji mierzony nie włącznie z terminatorem null.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// char_traits_length.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   const char* str1= "Hello";  
   cout << "The C-string str1 is: " << str1 << endl;  
  
   size_t lenStr1;  
   lenStr1 = char_traits<char>::length ( str1 );  
   cout << "The length of C-string str1 is: "   
        << lenStr1 << "." << endl;  
}  
```  
  
```Output  
The C-string str1 is: Hello  
The length of C-string str1 is: 5.  
```  
  
##  <a name="lt"></a>char_traits::lt  
 Sprawdza, czy znak jest mniejsza niż innym.  
  
```  
static bool lt(const char_type& _Ch1, const char_type& _Ch2);
```  
  
### <a name="parameters"></a>Parametry  
 `_Ch1`  
 Pierwszy z dwóch znaków pod kątem poniżej.  
  
 `_Ch2`  
 Drugi dwa znaki pod kątem poniżej.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** jeśli pierwszym znakiem jest mniejsza od drugiego znaku; w przeciwnym razie **false**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// char_traits_lt.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   char_traits<char>::char_type ch1 =  'x';  
   char_traits<char>::char_type ch2 =  'y';  
   char_traits<char>::char_type ch3 =  'z';  
  
   // Testing for less than  
   bool b1 = char_traits<char>::lt ( ch1 , ch2 );  
   if ( b1 )  
      cout << "The character ch1 is less than "  
           << "the character ch2." << endl;  
   else  
      cout << "The character ch1 is not less "  
           << "than the character ch2." << endl;  
  
   // An equivalent and alternatively test procedure  
   if ( ch3 <  ch2 )  
      cout << "The character ch3 is less than "  
           << "the character ch2." << endl;  
   else  
      cout << "The character ch3 is not less "  
           << "than the character ch2." << endl;  
}  
```  
  
```Output  
The character ch1 is less than the character ch2.  
The character ch3 is not less than the character ch2.  
```  
  
##  <a name="move"></a>char_traits::MOVE  
 Kopiuje określoną liczbę znaków w sekwencji do innego, prawdopodobnie nakładających się sekwencji.  
  
 Ta metoda jest potencjalnie niebezpieczne, ponieważ zależy od obiekt wywołujący, aby sprawdzić, czy przekazane wartości są poprawne. Należy rozważyć użycie [char_traits::_Move_s](#move_s) zamiast tego.  
  
```  
static char_type *move(char_type* _To,
    const char_type* _From,
    size_t _Num);
```  
  
### <a name="parameters"></a>Parametry  
 `_To`  
 Element na początku ciąg lub znak tablicy przeznaczone do odbierania skopiowanych sekwencji znaków.  
  
 `_From`  
 Element na początku tablicy źródłowej na ciąg lub znak do skopiowania.  
  
 `_Num`  
 Liczba elementów do skopiowania z ciąg źródła.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy element `_To` skopiować do tablicy ciąg lub znak przeznaczone do odbierania skopiowanych sekwencji znaków.  
  
### <a name="remarks"></a>Uwagi  
 Źródłowy i docelowy mogą się nakładać.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// char_traits_move.cpp  
// compile with: /EHsc /W3  
#include <string>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   char_traits<char>::char_type sFrom1[] =  "abcd-1234-abcd";  
   char_traits<char>::char_type sTo1[] =  "ABCD-1234";  
   char_traits<char>::char_type* result1;  
   cout << "The source string sFrom1 is: " << sFrom1 << endl;  
   cout << "The destination stringsTo1 is: " << sTo1 << endl;  
   // Note: char_traits::move is potentially unsafe, consider  
   // using char_traits::_Move_s instead.  
   result1 = char_traits<char>::move ( sTo1 ,  sFrom1 , 4 );  // C4996  
   cout << "The result1 = move ( sTo1 , sFrom1 , 4 ) is: "  
        << result1 << endl << endl;  
  
   // When source and destination overlap  
   char_traits<char>::char_type sToFrom2[] = "abcd-1234-ABCD";  
   char_traits<char>::char_type* result2;  
   cout << "The source/destination string sToFrom2 is: "  
        << sToFrom2 << endl;  
   const char* findc = char_traits<char>::find ( sToFrom2 , 4 , 'c' );  
   // Note: char_traits::move is potentially unsafe, consider  
   // using char_traits::_Move_s instead.  
   result2 = char_traits<char>::move ( sToFrom2 , findc , 8 );  // C4996  
   cout << "The result2 = move ( sToFrom2 , findc , 8 ) is: "  
        << result2 << endl;  
}  
```  
  
```Output  
The source string sFrom1 is: abcd-1234-abcd  
The destination stringsTo1 is: ABCD-1234  
The result1 = move ( sTo1 , sFrom1 , 4 ) is: abcd-1234  
  
The source/destination string sToFrom2 is: abcd-1234-ABCD  
The result2 = move ( sToFrom2 , findc , 8 ) is: cd-1234-4-ABCD  
```  
  
##  <a name="move_s"></a>char_traits::_Move_s  
 Kopiuje określoną liczbę znaków w sekwencji do innego, prawdopodobnie nakładających się sekwencji.  
  
```  
static char_type *_Move_s(
    char_type* dest,  
    size_t dest_size,  
    const char_type* _From,  
    size_t count);
```  
  
### <a name="parameters"></a>Parametry  
 `dest`  
 Element na początku ciąg lub znak tablicy przeznaczone do odbierania skopiowanych sekwencji znaków.  
  
 `dest_size`  
 Rozmiar `dest`. Jeśli `char_type` jest `char`, a następnie jest w bajtach. Jeśli `char_type` jest `wchar_t`, to znajduje się w wyrazy.  
  
 `_From`  
 Element na początku tablicy źródłowej na ciąg lub znak do skopiowania.  
  
 `count`  
 Liczba elementów do skopiowania z ciąg źródła.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy element `dest` skopiować do tablicy ciąg lub znak przeznaczone do odbierania skopiowanych sekwencji znaków.  
  
### <a name="remarks"></a>Uwagi  
 Źródłowy i docelowy mogą się nakładać.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// char_traits__Move_s.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
  
    char_traits<char>::char_type sFrom1[] =  "abcd-1234-abcd";  
    char_traits<char>::char_type sTo1[] =  "ABCD-1234";  
    char_traits<char>::char_type* result1;  
    cout << "The source string sFrom1 is: " << sFrom1 << endl;  
    cout << "The destination stringsTo1 is: " << sTo1 << endl;  
    result1 = char_traits<char>::_Move_s(sTo1,  
        char_traits<char>::length(sTo1), sFrom1, 4);  
    cout << "The result1 = _Move_s(sTo1, "  
         << "char_traits<char>::length(sTo1), sFrom1, 4) is: "  
         << result1 << endl << endl;  
  
    // When source and destination overlap  
    char_traits<char>::char_type sToFrom2[] = "abcd-1234-ABCD";  
    char_traits<char>::char_type* result2;  
    cout << "The source/destination string sToFrom2 is: "  
         << sToFrom2 << endl;  
    const char* findc = char_traits<char>::find(sToFrom2, 4, 'c');  
    result2 = char_traits<char>::_Move_s(sToFrom2,  
        char_traits<char>::length(sToFrom2), findc, 8);  
    cout << "The result2 = _Move_s(sToFrom2, "  
        << "char_traits<char>::length(sToFrom2), findc, 8) is: "  
         << result2 << endl;  
}  
```  
  
```Output  
The source string sFrom1 is: abcd-1234-abcd  
The destination stringsTo1 is: ABCD-1234  
The result1 = _Move_s(sTo1, char_traits<char>::length(sTo1), sFrom1, 4) is: abcd-1234  
  
The source/destination string sToFrom2 is: abcd-1234-ABCD  
The result2 = _Move_s(sToFrom2, char_traits<char>::length(sToFrom2), findc, 8) is: cd-1234-4-ABCD  
```  
  
##  <a name="not_eof"></a>char_traits::not_eof  
 Sprawdza, czy znak nie jest znak końca pliku (EOF) lub znacznik EOF.  
  
```  
static int_type not_eof(const int_type& _Ch);
```  
  
### <a name="parameters"></a>Parametry  
 `_Ch`  
 Znak przedstawiony jako `int_type` do sprawdzenia, czy jest on znak EOF lub nie.  
  
### <a name="return-value"></a>Wartość zwracana  
 `int_type` Reprezentację znak przetestowane, jeśli **int_type** znaku nie jest równa znak EOF.  
  
 Jeśli znak `int_type` wartość jest równa znacznik EOF `int_type` wartość następnie **false**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// char_traits_not_eof.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( ) {  
   using namespace std;  
  
   char_traits<char>::char_type ch1 =  'x';  
   char_traits<char>::int_type int1;  
   int1 = char_traits<char>:: to_int_type ( ch1 );  
   cout << "The char_type ch1 is " << ch1  
        << " corresponding to int_type: "   
        << int1 << "." << endl;  
  
   // EOF member function  
   char_traits <char>::int_type int2 = char_traits<char>::eof ( );  
   cout << "The eofReturn is: " << int2 << endl;  
  
   // Testing for EOF or another character  
   char_traits <char>::int_type eofTest1, eofTest2;  
   eofTest1 = char_traits<char>::not_eof ( int1 );  
   if ( !eofTest1 )  
      cout << "The eofTest1 indicates ch1 is an EOF character."  
              << endl;  
   else  
      cout << "The eofTest1 returns: " << eofTest1   
           << ", which is the character: "   
           <<  char_traits<char>::to_char_type ( eofTest1 )  
           << "." << endl;  
  
   eofTest2 = char_traits<char>::not_eof ( int2 );  
   if ( !eofTest2 )  
      cout << "The eofTest2 indicates int2 is an EOF character."   
           << endl;  
   else  
      cout << "The eofTest1 returns: " << eofTest2   
           << ", which is the character: "   
           <<  char_traits<char>::to_char_type ( eofTest2 )   
           << "." << endl;  
}  
```  
  
```Output  
The char_type ch1 is x corresponding to int_type: 120.  
The eofReturn is: -1  
The eofTest1 returns: 120, which is the character: x.  
The eofTest2 indicates int2 is an EOF character.  
```  
  
##  <a name="off_type"></a>char_traits::off_type  
 Integer — typ reprezentujące przesunięcia od pozycji w strumieniu.  
  
```  
typedef streamoff off_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest całkowita opisujący obiekt, który może przechowywać Przesunięcie bajtów, zaangażowane w strumieniu różnych operacji rozmieszczania. Zazwyczaj jest synonimem [streamoff](../standard-library/ios-typedefs.md#streamoff), ale ma zasadniczo takie same właściwości jako typu.  
  
##  <a name="pos_type"></a>char_traits::pos_type  
 Integer — typ reprezentujące pozycji w strumieniu.  
  
```  
typedef streampos pos_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ zawiera opis obiektu, który może przechowywać wszystkie informacje niezbędne do przywrócenia wskaźnik dowolnego położenie pliku w strumieniu. Zazwyczaj jest synonimem [streampos](../standard-library/ios-typedefs.md#streampos), ale w każdym przypadku ma zasadniczo takie same właściwości jako typu.  
  
##  <a name="state_type"></a>char_traits::state_type  
 Typ, który reprezentuje stan konwersji znaków wielobajtowych w strumieniu.  
  
```  
typedef implementation-defined state_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ zawiera opis obiektu, który może reprezentować stan konwersji. Zazwyczaj jest synonimem `mbstate_t`, ale w każdym przypadku ma zasadniczo takie same właściwości jako typu.  
  
##  <a name="to_char_type"></a>char_traits::to_char_type  
 Konwertuje `int_type` znak do odpowiednich `char_type` znaku i zwraca wynik.  
  
```  
static char_type to_char_type(const int_type& _Ch);
```  
  
### <a name="parameters"></a>Parametry  
 `_Ch`  
 `int_type` Znak może być reprezentowana jako `char_type`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `char_type` Znak odpowiadający `int_type` znaków.  
  
 Wartość `_Ch` nie może być reprezentowany jako takie daje wynik nieokreślony.  
  
### <a name="remarks"></a>Uwagi  
 Operacje konwersji [to_int_type](#to_int_type) i `to_char_type` są odwrotność ze sobą, tak aby:  
  
 `to_int_type`( `to_char_type` ( *x* )) == *x*  
  
 dla każdego `int_type` *x* i  
  
 `to_char_type`( `to_int_type` ( *x* )) == *x*  
  
 dla każdego `char_type` *x*.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// char_traits_to_char_type.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   char_traits<char>::char_type ch1 =  'a';  
   char_traits<char>::char_type ch2 =  'b';  
   char_traits<char>::char_type ch3 =  'a';  
  
   // Converting from char_type to int_type  
   char_traits<char>::int_type int1, int2 , int3;  
   int1 =char_traits<char>:: to_int_type ( ch1 );  
   int2 =char_traits<char>:: to_int_type ( ch2 );  
   int3 =char_traits<char>:: to_int_type ( ch3 );  
  
   cout << "The char_types and corresponding int_types are:"  
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "   
        << int1 << "."  
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "   
        << int2 << "."  
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "   
        << int3 << "." << endl << endl;  
  
   // Converting from int_type back to char_type  
   char_traits<char>::char_type rec_ch1;  
   rec_ch1 = char_traits<char>:: to_char_type ( int1);  
   char_traits<char>::char_type rec_ch2;  
   rec_ch2 = char_traits<char>:: to_char_type ( int2);  
  
   cout << "The recovered char_types and corresponding int_types are:"  
        << "\n    recovered ch1 = " << rec_ch1 << " from int1 = "   
        << int1 << "."  
        << "\n    recovered ch2 = " << rec_ch2 << " from int2 = "   
        << int2 << "." << endl << endl;  
  
   // Testing that the conversions are inverse operations  
   bool b1 = char_traits<char>::eq ( rec_ch1 , ch1 );  
   if ( b1 )  
      cout << "The recovered char_type of ch1"  
           << " is equal to the original ch1." << endl;  
   else  
      cout << "The recovered char_type of ch1"  
           << " is not equal to the original ch1." << endl;  
  
   // An equivalent and alternatively test procedure  
   if ( rec_ch2 == ch2 )  
      cout << "The recovered char_type of ch2"  
           << " is equal to the original ch2." << endl;  
   else  
      cout << "The recovered char_type of ch2"  
           << " is not equal to the original ch2." << endl;  
}  
```  
  
```Output  
The char_types and corresponding int_types are:  
    ch1 = a corresponding to int1 = 97.  
    ch2 = b corresponding to int1 = 98.  
    ch3 = a corresponding to int1 = 97.  
  
The recovered char_types and corresponding int_types are:  
    recovered ch1 = a from int1 = 97.  
    recovered ch2 = b from int2 = 98.  
  
The recovered char_type of ch1 is equal to the original ch1.  
The recovered char_type of ch2 is equal to the original ch2.  
```  
  
##  <a name="to_int_type"></a>char_traits::to_int_type  
 Konwertuje `char_type` znak do odpowiednich `int_type` znaku i zwraca wynik.  
  
```  
static int_type to_int_type(const char_type& _Ch);
```  
  
### <a name="parameters"></a>Parametry  
 `_Ch`  
 `char_type` Znak może być reprezentowana jako `int_type`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `int_type` Znak odpowiadający `char_type` znaków.  
  
### <a name="remarks"></a>Uwagi  
 Operacje konwersji `to_int_type` i [to_char_type](#to_char_type) są odwrotność ze sobą, tak aby:  
  
 `to_int_type`( `to_char_type` ( *x* )) == *x*  
  
 dla każdego `int_type` *x*, i  
  
 `to_char_type`( `to_int_type` ( *x* )) == *x*  
  
 dla każdego `char_type` *x*.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// char_traits_to_int_type.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   char_traits<char>::char_type ch1 = 'a';  
   char_traits<char>::char_type ch2 = 'b';  
   char_traits<char>::char_type ch3 = 'a';  
  
   // Converting from char_type to int_type  
   char_traits<char>::int_type int1, int2 , int3;  
   int1 =char_traits<char>:: to_int_type ( ch1 );  
   int2 =char_traits<char>:: to_int_type ( ch2 );  
   int3 =char_traits<char>:: to_int_type ( ch3 );  
  
   cout << "The char_types and corresponding int_types are:"  
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "   
        << int1 << "."  
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "   
        << int2 << "."  
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "   
        << int3 << "." << endl << endl;  
  
   // Converting from int_type back to char_type  
   char_traits<char>::char_type rec_ch1;  
   rec_ch1 = char_traits<char>:: to_char_type ( int1);  
   char_traits<char>::char_type rec_ch2;  
   rec_ch2 = char_traits<char>:: to_char_type ( int2);  
  
   cout << "The recovered char_types and corresponding int_types are:"  
        << "\n    recovered ch1 = " << rec_ch1 << " from int1 = "   
        << int1 << "."  
        << "\n    recovered ch2 = " << rec_ch2 << " from int2 = "   
        << int2 << "." << endl << endl;  
  
   // Testing that the conversions are inverse operations  
   bool b1 = char_traits<char>::eq ( rec_ch1 , ch1 );  
   if ( b1 )  
      cout << "The recovered char_type of ch1"  
           << " is equal to the original ch1." << endl;  
   else  
      cout << "The recovered char_type of ch1"  
           << " is not equal to the original ch1." << endl;  
  
   // An equivalent and alternatively test procedure  
   if ( rec_ch2 == ch2 )  
      cout << "The recovered char_type of ch2"  
           << " is equal to the original ch2." << endl;  
   else  
      cout << "The recovered char_type of ch2"  
           << " is not equal to the original ch2." << endl;  
}  
```  
  
```Output  
The char_types and corresponding int_types are:  
    ch1 = a corresponding to int1 = 97.  
    ch2 = b corresponding to int1 = 98.  
    ch3 = a corresponding to int1 = 97.  
  
The recovered char_types and corresponding int_types are:  
    recovered ch1 = a from int1 = 97.  
    recovered ch2 = b from int2 = 98.  
  
The recovered char_type of ch1 is equal to the original ch1.  
The recovered char_type of ch2 is equal to the original ch2.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

