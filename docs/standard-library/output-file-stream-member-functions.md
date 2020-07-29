---
title: Funkcje elementów członkowskich strumienia pliku danych wyjściowych
ms.date: 11/04/2016
helpviewer_keywords:
- output streams [C++], member functions
ms.assetid: 38aaf710-8035-4a34-a0c4-123a5327f28a
ms.openlocfilehash: f20ed4e238d23211a6eeec4a3091daeb4d02a9b3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217678"
---
# <a name="output-file-stream-member-functions"></a>Funkcje elementów członkowskich strumienia pliku danych wyjściowych

Funkcje składowe strumienia wyjściowego mają trzy typy: te, które są równoważne z manipulowania, te, które wykonują niesformatowane operacje zapisu, oraz te, które w przeciwnym razie modyfikują stan strumienia i nie mają równoważnego Manipulator lub operatora wstawiania. Dla sekwencyjnych, sformatowanych danych wyjściowych można używać tylko operatorów wstawiania i manipulowania. Aby uzyskać dostęp do danych wyjściowych na dyskach binarnych, użyj innych funkcji Członkowskich, z operatorami wstawiania lub bez.

## <a name="the-open-function-for-output-streams"></a>Funkcja Open dla strumieni wyjściowych

Aby użyć strumienia pliku wyjściowego ([ofstream](../standard-library/basic-ofstream-class.md)), należy skojarzyć ten strumień z określonym plikiem dysku w konstruktorze lub `open` funkcji. Jeśli używasz `open` funkcji, możesz ponownie użyć tego samego obiektu Stream z serią plików. W obu przypadkach argumenty opisujące plik są takie same.

Gdy otworzysz plik skojarzony z strumieniem wyjściowym, zazwyczaj określisz `open_mode` flagę. Można połączyć te flagi, które są zdefiniowane jako Numeratory w `ios` klasie z operatorem bitowym lub (&#124;). Aby wyświetlić listę modułów wyliczających, zobacz [ios_base:: openmode](../standard-library/ios-base-class.md#openmode) .

Trzy typowe sytuacje związane ze strumieniem wyjściowym obejmują opcje trybu:

- Tworzenie pliku. Jeśli plik już istnieje, stara wersja zostanie usunięta.

   ```cpp
   ostream ofile("FILENAME");
   // Default is ios::out

   ofstream ofile("FILENAME", ios::out);
   // Equivalent to above
   ```

- Dołączanie rekordów do istniejącego pliku lub tworzenie go, jeśli nie istnieje.

   ```cpp
   ofstream ofile("FILENAME", ios::app);
   ```

- Otwieranie dwóch plików, po jednym naraz, w tym samym strumieniu.

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

## <a name="the-put"></a>Umieszczenie

Funkcja **Put** zapisuje jeden znak w strumieniu wyjściowym. Poniższe dwie instrukcje są te same domyślnie, ale na sekundę mają wpływ argumenty formatu strumienia:

```cpp
cout.put('A');

// Exactly one character written
cout <<'A'; // Format arguments 'width' and 'fill' apply
```

## <a name="the-write"></a>Zapis

`write`Funkcja zapisuje blok pamięci do strumienia pliku wyjściowego. Argument długości określa liczbę zapisanych bajtów. Ten przykład tworzy strumień pliku wyjściowego i zapisuje wartość binarną `Date` struktury do niej:

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

`write`Funkcja nie zatrzymuje się, gdy dotrze do znaku null, więc zostanie zapisywana kompletna struktura klasy. Funkcja przyjmuje dwa argumenty: **`char`** wskaźnik i liczba znaków do zapisania. **`char`** Przed adresem obiektu struktury należy zwrócić uwagę na wymagane rzutowanie <strong>\*</strong> .

## <a name="the-seekp-and-tellp-functions"></a>Funkcje seekp i tellp

Strumień pliku wyjściowego przechowuje wewnętrzny wskaźnik wskazujący położenie, w którym dane mają być zapisywane dalej. `seekp`Funkcja członkowska ustawia ten wskaźnik i w ten sposób zapewnia dostęp do danych wyjściowych na dysku. `tellp`Funkcja członkowska zwraca pozycję pliku. Aby zapoznać się z przykładami korzystającymi z odpowiedników strumienia wejściowego do `seekp` i `tellp` , zobacz [funkcje seekg i tellg](../standard-library/input-stream-member-functions.md).

## <a name="the-close-function-for-output-streams"></a>Funkcja Close dla strumieni wyjściowych

`close`Funkcja członkowska zamyka plik dysku skojarzony ze strumieniem pliku wyjściowego. Plik musi być zamknięty, aby można było ukończyć wszystkie dane wyjściowe na dysku. W razie potrzeby `ofstream` destruktor zamknie plik, ale można użyć `close` funkcji, jeśli trzeba otworzyć inny plik dla tego samego obiektu strumienia.

Destruktor strumienia wyjściowego automatycznie zamyka plik strumienia tylko wtedy, gdy Konstruktor lub `open` funkcja członkowska otworzyła plik. Jeśli przekazujesz konstruktora deskryptora pliku dla już otwartego pliku lub Użyj `attach` funkcji składowej, musisz zamknąć plik jawnie.

## <a name="error-processing-functions"></a><a name="vclrferrorprocessingfunctionsanchor10"></a>Błąd podczas przetwarzania funkcji

Użyj tych funkcji elementów członkowskich do testowania pod kątem błędów podczas zapisywania do strumienia:

|Funkcja|Wartość zwracana|
|--------------|------------------|
|[ściągaln](basic-ios-class.md#bad)|Zwraca **`true`** Jeśli wystąpił nieodwracalny błąd.|
|[udało](basic-ios-class.md#fail)|Zwraca **`true`** czy wystąpił nieodwracalny błąd lub warunek "oczekiwany", taki jak błąd konwersji lub jeśli plik nie zostanie znaleziony. Przetwarzanie może być często wznawiane po wywołaniu `clear` z argumentem zero.|
|[aukcj](basic-ios-class.md#good)|Zwraca **`true`** czy nie istnieje warunek błędu (nieodwracalny lub inny), a flaga końca pliku nie została ustawiona.|
|[końca](basic-ios-class.md#eof)|Zwraca wartość **`true`** dla stanu końca pliku.|
|[Wyczyść](basic-ios-class.md#clear)|Ustawia stan błędu wewnętrznego. Jeśli wywoływana z argumentami domyślnymi, czyści wszystkie bity błędów.|
|[rdstate] (podstawowa — iOS-Class. MD # rdstate|Zwraca bieżący stan błędu.|

**!** operator jest przeciążony, aby wykonać tę samą funkcję co `fail` Funkcja. W tym celu wyrażenie:

```cpp
if(!cout)...
```

jest równoważne:

```cpp
if(cout.fail())...
```

Operator **void \* ()** jest przeciążony jako przeciwieństwo **!** zakład w tym celu wyrażenie:

```cpp
if(cout)...
```

równa się:

```cpp
if(!cout.fail())...
```

Operator **void \* ()** nie jest odpowiednikiem, `good` ponieważ nie sprawdza końca pliku.

## <a name="see-also"></a>Zobacz także

[Strumienie wyjściowe](../standard-library/output-streams.md)
