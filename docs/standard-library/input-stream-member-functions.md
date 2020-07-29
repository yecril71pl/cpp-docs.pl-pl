---
title: Input Stream Member — Funkcje
ms.date: 07/19/2019
helpviewer_keywords:
- input stream objects
- input streams, member functions
ms.assetid: b4b9465d-0da9-4ccf-859d-72a68418982e
ms.openlocfilehash: 8aa211a03bb6e9b1d910db360066b4a2ca76571a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233174"
---
# <a name="input-stream-member-functions"></a>Input Stream Member — Funkcje

Funkcje elementów członkowskich strumienia wejściowego są używane na potrzeby danych wejściowych na dysku.

## <a name="open"></a><a name="vclrftheopenfunctionforinputstreamsanchor11"></a>Otwórz

Jeśli używasz strumienia pliku wejściowego ( `ifstream` ), musisz powiązać ten strumień z określonym plikiem dysku. Można to zrobić w konstruktorze lub użyć `open` funkcji. W obu przypadkach argumenty są takie same.

Na ogół określa się flagę [ios_base:: openmode](../standard-library/ios-base-class.md#openmode) podczas otwierania pliku skojarzonego ze strumieniem wejściowym (domyślny tryb to `ios::in` ). Aby uzyskać listę `openmode` flag, zobacz [ios_base:: openmode](../standard-library/ios-base-class.md#openmode). Flagi można łączyć z operatorem bitowym lub (&#124;).

Aby odczytać plik, najpierw Użyj `fail` funkcji elementu członkowskiego, aby określić, czy istnieje:

```cpp
istream ifile("FILENAME");

if (ifile.fail())
// The file does not exist ...
```

## <a name="get"></a><a name="vclrfthegetfunctionanchor12"></a>Pobierz

Niesformatowana `get` funkcja członkowska działa jak `>>` operator z dwoma wyjątkami. Najpierw `get` Funkcja zawiera znaki odstępu, podczas gdy podczas `skipws` ustawiania flagi (wartość domyślna) wyodrębnianie wyklucza biały znak. Po drugie `get` Funkcja jest mniej przyczyną, że powiązany strumień wyjściowy ( `cout` na przykład) ma zostać opróżniony.

Odmiana `get` funkcji określa adres buforu i maksymalną liczbę znaków do odczytania. Jest to przydatne w przypadku ograniczania liczby znaków wysyłanych do określonej zmiennej, jak pokazano w tym przykładzie:

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

## <a name="getline"></a><a name="vclrfthegetlinefunctionanchor13"></a>getline

`getline`Funkcja członkowska jest podobna do `get` funkcji. Obie funkcje zezwalają na trzeci argument, który określa znak kończący dla danych wejściowych. Wartość domyślna to znak nowego wiersza. Obie funkcje rezerwują jeden znak dla wymaganego znaku kończącego. Jednakże `get` pozostawia znak kończący w strumieniu i `getline` usuwa znak kończący.

W poniższym przykładzie określono znak kończący strumienia wejściowego:

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

## <a name="read"></a><a name="vclrfthereadfunctionanchor14"></a>Przeczytaj

`read`Funkcja członkowska odczytuje bajty z pliku do określonego obszaru pamięci. Argument długości określa liczbę odczytanych bajtów. Jeśli ten argument nie zostanie uwzględniony, Odczyt jest zatrzymywany po osiągnięciu fizycznego końca pliku lub w przypadku pliku trybu tekstowego, gdy `EOF` odczytywany jest znak osadzony.

Ten przykład odczytuje rekord binarny z pliku listy płac do struktury:

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

Program zakłada, że rekordy danych są sformatowane dokładnie tak, jak określono przez strukturę bez przerywania powrotu karetki lub wysuwu wiersza.

## <a name="seekg-and-tellg"></a><a name="vclrftheseekgandtellgfunctionsanchor7"></a>seekg i tellg

Strumienie plików wejściowych zachowują wewnętrzny wskaźnik do położenia w pliku, w którym dane mają zostać odczytane dalej. Ten wskaźnik ustawia się za pomocą `seekg` funkcji, jak pokazano poniżej:

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

Aby użyć `seekg` programu do implementacji opartych na rekordach systemach zarządzania danymi, należy pomnożyć rozmiar rekordu o stałej długości przez numer rekordu, aby uzyskać położenie bajtów względem końca pliku, a następnie użyć `get` obiektu do odczytania tego rekordu.

`tellg`Funkcja członkowska zwraca bieżącą pozycję pliku do odczytu. Ta wartość jest typu `streampos` , a **`typedef`** zdefiniowana w \<iostream> . Poniższy przykład odczytuje plik i wyświetla komunikaty pokazujące położenia spacji.

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

## <a name="close"></a><a name="vclrftheclosefunctionforinputstreamsanchor15"></a>ściśle

`close`Funkcja członkowska zamyka plik dysku skojarzony ze strumieniowym plikiem wejściowym i zwalnia dojście do pliku systemu operacyjnego. [`ifstream`](../standard-library/basic-ifstream-class.md)Destruktor zamyka plik, ale można użyć `close` funkcji, jeśli trzeba otworzyć inny plik dla tego samego obiektu strumienia.

## <a name="see-also"></a>Zobacz także

[Strumienie wejściowe](../standard-library/input-streams.md)
