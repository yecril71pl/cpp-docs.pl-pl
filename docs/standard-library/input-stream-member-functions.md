---
title: Input Stream Member — Funkcje
ms.date: 11/04/2016
helpviewer_keywords:
- input stream objects
- input streams, member functions
ms.assetid: b4b9465d-0da9-4ccf-859d-72a68418982e
ms.openlocfilehash: b046ea1995d5a8eaa39dced9feb7a5e4c422c253
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663986"
---
# <a name="input-stream-member-functions"></a>Input Stream Member — Funkcje

Funkcje składowe strumienia wejściowego są używane dla dysku danych wejściowych. Funkcje elementów członkowskich obejmują:

- [Otwórz funkcję dla strumieni danych wejściowych](#vclrftheopenfunctionforinputstreamsanchor11)

- [Get](#vclrfthegetfunctionanchor12)

- [Getline —](#vclrfthegetlinefunctionanchor13)

- [Odczyt](#vclrfthereadfunctionanchor14)

- [Seekg — i tellg — funkcje](#vclrftheseekgandtellgfunctionsanchor7)

- [Zamknij funkcji dla strumieni danych wejściowych](#vclrftheclosefunctionforinputstreamsanchor15)

## <a name="vclrftheopenfunctionforinputstreamsanchor11"></a> Otwórz funkcję dla strumieni danych wejściowych

Jeśli używasz strumień pliku wejściowego (ifstream) należy skojarzyć tego strumienia z plikiem danych określony dysk. Można to zrobić w konstruktorze lub można użyć `open` funkcji. W obu przypadkach argumenty są takie same.

Zwykle określasz [ios_base::openmode](../standard-library/ios-base-class.md#openmode) Flaga po otwarciu pliku skojarzone z strumień wejściowy (jest to domyślny tryb `ios::in`). Aby uzyskać listę `open_mode` flag zobacz [Otwórz](#vclrftheopenfunctionforinputstreamsanchor11). Flagi mogą być łączone z bitowe OR ( &#124; ) — operator.

Aby odczytać plik, należy najpierw użyć `fail` funkcja elementu członkowskiego, aby ustalić, czy istnieje:

```cpp
istream ifile("FILENAME");

if (ifile.fail())
// The file does not exist ...
```

## <a name="vclrfthegetfunctionanchor12"></a> Get

Niesformatowany `get` funkcja elementu członkowskiego działa jak `>>` operatora z dwoma wyjątkami. Po pierwsze, `get` funkcja zawiera białe znaki, ekstraktor wyłącza biały znak po `skipws` flaga jest ustawiona (ustawienie domyślne). Drugi `get` funkcji jest mniej prawdopodobne, że strumień wyjściowy wiązanej (`cout`, na przykład) opróżnienia.

Odmiana `get` funkcja określa adres buforu i maksymalną liczbę znaków do odczytania. Jest to przydatne w przypadku ograniczenie liczby znaków wysyłane do określonej zmiennej, jak pokazano w tym przykładzie:

```cpp
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

```Input
1234
```

### <a name="sample-output"></a>Przykładowe dane wyjściowe

```Output
1234
```

## <a name="vclrfthegetlinefunctionanchor13"></a> Getline —

`getline` Funkcja członkowska jest podobne do `get` funkcji. Obie funkcje umożliwiają trzeci argument, który określa kończącego znaku dla danych wejściowych. Wartość domyślna to znak nowego wiersza. Obie funkcje zarezerwować jednego znaku w przypadku końcowego znaku wymagane. Jednak `get` pozostawia kończący znak w strumieniu i `getline` usuwa kończącego znaku.

W poniższym przykładzie określono kończący znak do strumienia danych wejściowych:

```cpp
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

```Input
test
```

## <a name="vclrfthereadfunctionanchor14"></a> Odczyt

`read` Funkcja elementu członkowskiego odczytuje bajtów z pliku do określonego obszaru pamięci. Długość argumentu określa liczbę odczytanych bajtów. Jeśli ten argument nie zostanie uwzględniony, odczytu nie będzie możliwy po przekroczeniu fizycznych koniec pliku, lub w przypadku trybu tekstowego pliku osadzonego `EOF` odczytem znaku.

W tym przykładzie odczytuje binarny rekordu z pliku listy płac w strukturze:

```cpp
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

Program przyjęto założenie, że rekordy są sformatowane dokładnie tak jak określono przez strukturę bez kończący znaków powrotu karetki i wysuwu wiersza.

## <a name="vclrftheseekgandtellgfunctionsanchor7"></a> Seekg — i tellg — funkcje

Strumienie pliku wejściowego Zachowaj wewnętrzny wskaźnik do położenia w pliku, w którym dane są następnie odczytywane. Ustaw ten wskaźnik przy użyciu `seekg` funkcji, jak pokazano poniżej:

```cpp
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

Do użycia `seekg` do zaimplementowania dane zorientowane systemami zarządzania, należy pomnożyć rozmiar rekordu o stałej długości przez liczbę rekordów do uzyskania Pozycja bajtu względem koniec pliku, a następnie użyj `get` obiektu do odczytu w rekordzie.

`tellg` Funkcja elementu członkowskiego zwraca bieżącą pozycję w pliku do odczytu. Ta wartość jest typu `streampos`, `typedef` zdefiniowane w \<iostream >. Poniższy przykład odczytuje plik i wyświetla komunikaty informujące pozycji miejsca do magazynowania.

```cpp
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

## <a name="vclrftheclosefunctionforinputstreamsanchor15"></a> Zamknij funkcji dla strumieni danych wejściowych

`close` Funkcja elementu członkowskiego zamyka pliku dysku skojarzonego z strumienia pliku wejściowego i zwalnia uchwyt pliku systemu operacyjnego. [Ifstream](../standard-library/basic-ifstream-class.md) destruktor zamyka plik dla Ciebie, ale można użyć `close` działać, jeśli trzeba otworzyć inny plik dla tego samego obiektu strumienia.

## <a name="see-also"></a>Zobacz także

[Strumienie wejściowe](../standard-library/input-streams.md)<br/>
