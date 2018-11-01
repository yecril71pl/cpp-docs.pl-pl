---
title: Funkcje elementów członkowskich strumienia pliku danych wyjściowych
ms.date: 11/04/2016
helpviewer_keywords:
- output streams [C++], member functions
ms.assetid: 38aaf710-8035-4a34-a0c4-123a5327f28a
ms.openlocfilehash: eba627c69437754a9c0a819167443aa00c025fef
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621770"
---
# <a name="output-file-stream-member-functions"></a>Funkcje elementów członkowskich strumienia pliku danych wyjściowych

Funkcje składowe strumienia wyjściowego ma trzy typy: te, które są równoważne manipulatory, te, które wykonują niesformatowany operacje zapisu w magazynie, a te, które w przeciwnym razie zmodyfikuj strumienia stanu i mieć równoważne manipulator lub operator wstawiania. Sekwencyjne sformatowanych danych wyjściowych można skorzystać tylko z operatorów wstawiania i manipulatory. W danych wyjściowych dysku binarne dostępu swobodnego należy użyć innych funkcji Członkowskich z lub bez operatorów wstawiania.

## <a name="the-open-function-for-output-streams"></a>Otwórz funkcję dla strumieni wyjściowych

Za pomocą usługi stream pliku wyjściowego ([ofstream](../standard-library/basic-ofstream-class.md)), strumieniu należy skojarzyć z plikiem dyskowym określonych w konstruktorze lub `open` funkcji. Jeśli używasz `open` funkcji, można ponownie użyć tego samego obiektu strumienia z serii plików. W obu przypadkach argumenty opisujące pliku są takie same.

Gdy otworzysz plik skojarzony ze strumienia wyjściowego, zwykle określasz `open_mode` flagi. Można połączyć te flagi, które są zdefiniowane jako moduły wyliczające w `ios` klasy za pomocą bitowej OR ( &#124; ) — operator. Zobacz [ios_base::openmode](../standard-library/ios-base-class.md#openmode) lista modułów wyliczających.

Trzy typowe sytuacje strumień danych wyjściowych obejmują opcje trybu:

- Tworzenie pliku. Jeśli plik już istnieje, stara wersja jest usuwany.

   ```cpp
   ostream ofile("FILENAME");
   // Default is ios::out

   ofstream ofile("FILENAME", ios::out);
   // Equivalent to above
   ```

- Rekordy są dołączane do istniejącego pliku lub Tworzenie katalogu, jeśli nie istnieje.

   ```cpp
   ofstream ofile("FILENAME", ios::app);
   ```

- Otwieranie dwóch plików pojedynczo, w tym samym strumieniu.

   ```cpp
   ofstream ofile();
   ofile.open("FILE1", ios::in);
   // Do some output
   ofile.close();    // FILE1 closed
   ofile.open("FILE2", ios::in);
   // Do some more output
   ofile.close();    // FILE2 closed
   // When ofile goes out of scope it is destroyed.
   ```

## <a name="the-put"></a>Put

**Umieścić** funkcja zapisuje znak do strumienia wyjściowego. Następujące dwie instrukcje są takie same, domyślnie, ale druga jest zależna od argumentów format strumienia:

```cpp
cout.put('A');

// Exactly one character written
cout <<'A'; // Format arguments 'width' and 'fill' apply
```

## <a name="the-write"></a>Zapis

`write` Funkcja zapisuje blok pamięci w strumieniu wyjściowym pliku. Długość argumentu określa liczba zapisanych bajtów. W tym przykładzie tworzy strumień wyjściowy plik i zapisuje wartość binarna `Date` struktury do niego:

```cpp
// write_function.cpp
// compile with: /EHsc
#include <fstream>
using namespace std;

struct Date
{
   int mo, da, yr;
};

int main( )
{
   Date dt = { 6, 10, 92 };
   ofstream tfile( "date.dat" , ios::binary );
   tfile.write( (char *) &dt, sizeof dt );
}
```

`write` — Funkcja nie zatrzymuje się po osiągnięciu znak null, więc są zapisywane w strukturze klas ukończone. Funkcja przyjmuje dwa argumenty: **char** wskaźnik i liczba znaków do zapisania. Należy pamiętać, wymagane Rzutowanie na **char** <strong>\*</strong> przed adres obiektu, struktury.

## <a name="the-seekp-and-tellp-functions"></a>Seekp — i tellp — funkcje

Strumień wyjściowy plik przechowuje wewnętrzny wskaźnik, który wskazuje miejsce, w którym dane są następnie zapisanie. `seekp` Funkcja elementu członkowskiego ustawia ten wskaźnik, a tym samym zapewnia dane wyjściowe pliku dysku dostępu swobodnego. `tellp` Funkcja elementu członkowskiego zwraca położenie pliku. Aby uzyskać przykłady z zastosowaniem odpowiedniki strumienia wejściowego, do `seekp` i `tellp`, zobacz [funkcji seekg — i tellg —](../standard-library/input-stream-member-functions.md).

## <a name="the-close-function-for-output-streams"></a>Zamknij funkcję dla strumieni wyjściowych

`close` Funkcja elementu członkowskiego zamyka pliku dysku skojarzonego z strumienia pliku wyjściowego. Plik musi zostać zamknięty do ukończenia wszystkich dysków danych wyjściowych. Jeśli to konieczne, `ofstream` destruktor zamyka plik dla Ciebie, ale można użyć `close` działać, jeśli trzeba otworzyć inny plik dla tego samego obiektu strumienia.

Destruktor strumienia wyjściowego automatycznie zamyka strumienia pliku tylko wtedy, gdy Konstruktor lub `open` plik otwarty dla funkcji członkowskiej. W przypadku przekazania deskryptor pliku dla pliku już open lub użyj Konstruktora `attach` funkcja elementu członkowskiego musi jawnie Zamknij plik.

## <a name="vclrferrorprocessingfunctionsanchor10"></a> Wystąpił błąd podczas przetwarzania funkcji

Aby sprawdzić błędy podczas zapisywania do strumienia za pomocą tych funkcji elementu członkowskiego:

|Funkcja|Wartość zwracana|
|--------------|------------------|
|[bad](basic-ios-class.md#bad)|Zwraca **true** przypadku wystąpił nieodwracalny błąd.|
|[Niepowodzenie](basic-ios-class.md#fail)|Zwraca **true** przypadku wystąpił nieodwracalny błąd lub warunek "Oczekiwano", takie jak błąd konwersji, lub jeśli plik nie zostanie znaleziony. Przetwarzanie często wznowienie jest możliwe po wywołaniu `clear` z argumentem zero.|
|[dobre](basic-ios-class.md#good)|Zwraca **true** Jeśli brak jest nie błędu (nieodwracalny lub w inny sposób), a nie jest ustawiona flaga końca pliku.|
|[eof](basic-ios-class.md#eof)|Zwraca **true** pod warunkiem końca pliku.|
|[Usuń zaznaczenie](basic-ios-class.md#clear)|Ustawia stan błędu wewnętrznego. Jeśli wywołana z argumentami domyślnymi, czyści wszystkie bity błędu.|
|[rdstate —] (basic-ios-class.md #rdstate|Zwraca bieżący stan błędu.|

**!** operator jest przeciążony przeprowadzić taką samą funkcję jak `fail` funkcji. Ten sposób wyrażenie:

```cpp
if(!cout)...
```

jest równoważne:

```cpp
if(cout.fail())...
```

**Void\*()** operator jest przeciążony być przeciwieństwem **!** operator; ten sposób wyrażenie:

```cpp
if(cout)...
```

wynosi:

```cpp
if(!cout.fail())...
```

**Void\*()** nie jest odpowiednikiem `good` ponieważ Testuj je na końcu pliku.

## <a name="see-also"></a>Zobacz także

[Strumienie wyjściowe](../standard-library/output-streams.md)<br/>
