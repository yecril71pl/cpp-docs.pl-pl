---
title: "Dane wejściowe Stream Member — funkcje | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- input stream objects
- input streams, member functions
ms.assetid: b4b9465d-0da9-4ccf-859d-72a68418982e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f9fb195bfb5e6e35d035ba5a3660bb91644a04ab
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="input-stream-member-functions"></a>Input Stream Member — Funkcje
Funkcje elementów członkowskich strumienia wejściowego służą do wprowadzania dysku. Funkcje Członkowskie obejmują:  
  
- [Otwórz funkcji dla strumieni danych wejściowych](#vclrftheopenfunctionforinputstreamsanchor11)  
  
- [Get](#vclrfthegetfunctionanchor12)  
  
- [Getline](#vclrfthegetlinefunctionanchor13)  
  
- [Odczyt](#vclrfthereadfunctionanchor14)  
  
- [Funkcje seekg i tellg](#vclrftheseekgandtellgfunctionsanchor7)  
  
- [Zamknij funkcji dla strumieni danych wejściowych](#vclrftheclosefunctionforinputstreamsanchor15)  
  
##  <a name="vclrftheopenfunctionforinputstreamsanchor11"></a>Otwórz funkcji dla strumieni danych wejściowych  
 Jeśli używasz strumienia wejściowego (ifstream) należy skojarzyć strumieniu z określonego pliku. Można to zrobić w konstruktorze lub użyć **Otwórz** funkcji. W obu przypadkach argumenty są takie same.  
  
 Zazwyczaj określić [ios_base::openmode](../standard-library/ios-base-class.md#openmode) Flaga podczas otwierania pliku skojarzone z strumień wejściowy (jest to domyślny tryb **ios::in**). Aby uzyskać listę **open_mode** flagi, zobacz [Otwórz](#vclrftheopenfunctionforinputstreamsanchor11). Flagi można łączyć z bitowego OR (&#124;) — operator.  
  
 Aby odczytać plik, należy najpierw użyć **niepowodzenie** funkcji członkowskiej, aby określić, czy istnieje:  
  
```  
istream ifile("FILENAME");

if (ifile.fail())  
// The file does not exist ...  
```  
  
##  <a name="vclrfthegetfunctionanchor12"></a>Get
 Niesformatowany **uzyskać** funkcji członkowskiej działa jak  **>>**  operatora z dwoma wyjątkami. Najpierw **uzyskać** funkcja zawiera białe znaki ekstraktor wyłącza biały znak podczas **skipws** flaga jest ustawiona (ustawienie domyślne). Drugi, **uzyskać** funkcji jest mniej może spowodować strumienia wyjściowego wiązanej (`cout`, na przykład) do opróżnienia.  
  
 Odmiana **uzyskać** funkcja określa adres buforu i maksymalną liczbę znaków do odczytania. Jest to przydatne w przypadku ograniczenie liczby znaków wysyłane do określonej zmiennej, jak pokazano na poniższym przykładzie:  
  
```  
// ioo_get_function.cpp  
// compile with: /EHsc  
// Type up to 24 characters and a terminating character.   
// Any remaining characters can be extracted later.  
#include <iostream>  
using namespace std;  
  
int main()  
{  
   char line[25];  
   cout << " Type a line terminated by carriage return\n>";  
   cin.get( line, 25 );  
   cout << line << endl;  
}  
```  
  
### <a name="input"></a>Dane wejściowe  
  
```  
1234  
```  
  
### <a name="sample-output"></a>Przykładowe dane wyjściowe  
  
```  
1234  
```  
  
##  <a name="vclrfthegetlinefunctionanchor13"></a>Getline
 **Getline** funkcja członkowska jest podobny do **uzyskać** funkcji. Obie funkcje umożliwiają trzeci argument, który określa znaku zakończenia dla danych wejściowych. Wartość domyślna to znak nowego wiersza. Funkcjami zarezerwować dla wymaganego znaku zakończenia o jeden znak. Jednak **uzyskać** pozostawia znaku zakończenia w strumieniu i **getline** usuwa znaku zakończenia.  
  
 W poniższym przykładzie znaku zakończenia dla strumienia wejściowego:  
  
```  
// getline_func.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main( )  
{  
   char line[100];  
   cout << " Type a line terminated by 't'" << endl;  
   cin.getline( line, 100, 't' );  
   cout << line;  
}  
```  
  
### <a name="input"></a>Dane wejściowe  
  
```  
test  
```  
  
##  <a name="vclrfthereadfunctionanchor14"></a>Odczyt
 **Odczytu** funkcji członkowskiej odczytuje bajtów z pliku do określonego obszaru pamięci. Długość argumentu określa liczbę bajtów do odczytu. Jeśli ten argument nie zostanie uwzględniony, odczytu zatrzymuje po osiągnięciu fizycznych koniec pliku, lub w przypadku pliku tekstowej, gdy osadzonych `EOF` znak jest do odczytu.  
  
 Ten przykład odczytuje binarne rekordu z pliku Lista płac w strukturze:  
  
```  
#include <fstream>  
#include <iostream>  
using namespace std;  
  
int main()  
{  
   struct  
   {  
      double salary;  
      char name[23];  
   } employee;  
  
   ifstream is( "payroll" );  
   if( is ) {  // ios::operator void*()  
      is.read( (char *) &employee, sizeof( employee ) );  
      cout << employee.name << ' ' << employee.salary << endl;  
   }  
   else {  
      cout << "ERROR: Cannot open file 'payroll'." << endl;  
   }  
}  
```  
  
 Program zakłada, czy rekordy są sformatowane dokładnie określone przez strukturę bez przerywania znaków powrotu karetki i wysuwu wiersza.  
  
##  <a name="vclrftheseekgandtellgfunctionsanchor7"></a>Funkcje seekg i tellg  
 Plik wejściowy strumieni Zachowaj wewnętrznego wskaźnika do pozycji w pliku, w których dane są odczytywane obok. Ustaw ten wskaźnik z `seekg` funkcji, jak pokazano poniżej:  
  
```  
#include <iostream>  
#include <fstream>  
using namespace std;  
  
int main( )  
{  
   char ch;  
  
   ifstream tfile( "payroll" );  
   if( tfile ) {  
      tfile.seekg( 8 );        // Seek 8 bytes in (past salary)  
      while ( tfile.good() ) { // EOF or failure stops the reading  
         tfile.get( ch );  
         if( !ch ) break;      // quit on null  
         cout << ch;  
      }  
   }  
   else {  
      cout << "ERROR: Cannot open file 'payroll'." << endl;  
   }  
}  
```  
  
 Aby użyć `seekg` Aby zaimplementować systemy zarządzania zorientowane na rekordy danych, należy pomnożyć rozmiar rekordu o stałej długości przez numer uzyskać Pozycja bajtu względem koniec pliku, a następnie użyć **uzyskać** obiektu do odczytu rekord.  
  
 `tellg` Funkcji członkowskiej Zwraca bieżące położenie pliku do odczytu. Ta wartość jest typu `streampos`, `typedef` zdefiniowane w \<iostream >. W poniższym przykładzie odczytuje plik i wyświetla komunikaty informujące pozycji spacji.  
  
```  
#include <fstream>  
#include <iostream>  
using namespace std;  
  
int main( )  
{  
   char ch;  
   ifstream tfile( "payroll" );  
   if( tfile ) {  
       while ( tfile.good( ) ) {  
          streampos here = tfile.tellg();  
          tfile.get( ch );  
          if ( ch == ' ' )  
             cout << "\nPosition " << here << " is a space";  
       }  
   }  
   else {  
      cout << "ERROR: Cannot open file 'payroll'." << endl;  
   }  
}  
```  
  
##  <a name="vclrftheclosefunctionforinputstreamsanchor15"></a>Zamknij funkcji dla strumieni danych wejściowych  
 **Zamknąć** funkcji członkowskiej zamyka skojarzone ze strumienia wejściowego pliku dysku i zwalnia dojście do pliku systemu operacyjnego. [Ifstream](../standard-library/basic-ifstream-class.md) destruktora zamyka plik dla Ciebie, ale może użyć **zamknąć** funkcji, aby otworzyć inny plik dla tego samego obiektu strumienia.  
  
## <a name="see-also"></a>Zobacz też  
 [Strumienie wejściowe](../standard-library/input-streams.md)

