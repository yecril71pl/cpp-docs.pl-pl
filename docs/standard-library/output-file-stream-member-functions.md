---
title: "Funkcje elementów członkowskich strumienia pliku wyjściowego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: output streams [C++], member functions
ms.assetid: 38aaf710-8035-4a34-a0c4-123a5327f28a
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dec5db670afd169093125f2830551aec85b61e35
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="output-file-stream-member-functions"></a>Funkcje elementów członkowskich strumienia pliku danych wyjściowych
Funkcje elementów członkowskich strumienia wyjściowego ma trzy typy: te, które są równoważne manipulatory, które wykonać niesformatowany operacji zapisu, a te, które w przeciwnym razie zmodyfikować strumienia o stanie i nie równoważne manipulatora ani operator wstawiania. Dla danych wyjściowych sekwencyjnych, sformatowany może używać tylko operatorów wstawiania i manipulatory. Dla danych wyjściowych dostępie swobodnym binarne dysku Użyj innych funkcji elementów członkowskich z lub bez operatorów wstawiania.  
  
## <a name="the-open-function-for-output-streams"></a>Otwórz funkcja dla strumienie wyjściowe  
 Umożliwia strumienia pliku wyjściowego ([ofstream](../standard-library/basic-ofstream-class.md)), strumieniu należy skojarzyć z plikiem dysku określonego w konstruktorze lub **Otwórz** funkcji. Jeśli używasz **Otwórz** funkcji, można ponownie użyć tego samego obiektu strumienia z szeregu plików. W obu przypadkach argumenty opisujące pliku są takie same.  
  
 Po otwarciu pliku skojarzone z strumienia wyjściowego należy określają **open_mode** flagi. Można połączyć te flagi, które są zdefiniowane jako wyliczenia w `ios` klasy z bitowego OR (&#124;) — operator. Zobacz [ios_base::openmode](../standard-library/ios-base-class.md#openmode) listę wyliczenia.  
  
 Trzy typowe problemy strumienia wyjściowego wymaga opcji trybu:  
  
-   Tworzenie pliku. Jeśli plik już istnieje, stara wersja została usunięta.  
  
 ```  
    ostream ofile("FILENAME");
// Default is ios::out  
    ofstream ofile("FILENAME", ios::out);

// Equivalent to above  
```  
  
-   Rekordy są dołączane do istniejącego pliku lub utworzenie jednego, jeśli nie istnieje.  
  
 ```  
    ofstream ofile("FILENAME", ios::app);
```  
  
-   Otwieranie dwóch plików, jeden z nich na tym samym strumienia.  
  
 ```  
    ofstream ofile();
ofile.open("FILE1",
    ios::in);
// Do some output  
    ofile.close();

// FILE1 closed  
    ofile.open("FILE2",
    ios::in);
// Do some more output  
    ofile.close();

// FILE2 closed  // When ofile goes out of scope it is destroyed.  
```  
  
## <a name="the-put"></a>Metody put
 **Put** funkcja zapisuje jeden znak w strumieniu wyjściowym. Dwa poniższe instrukcje są takie same, domyślnie, ale druga dotyczy argumenty format strumienia:  
  
```  
cout.put('A');

// Exactly one character written  
cout <<'A'; // Format arguments 'width' and 'fill' apply   
```  
  
## <a name="the-write"></a>Zapisu
 **Zapisu** funkcja zapisuje bloku pamięci do strumienia pliku wyjściowego. Długość argumentu określa liczba zapisanych bajtów. W tym przykładzie tworzy strumień pliku wyjściowego i zapisuje wartość binarna `Date` struktury do niej:  
  
```  
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
  
 **Zapisu** funkcji nie zatrzymać po osiągnięciu znak null, są zapisywane w strukturze klas ukończone. Funkcja przyjmuje dwa argumenty: `char` wskaźnik i liczbę znaków do zapisu. Należy pamiętać, wymagane Rzutowanie na **char\***  przed adresu obiektu struktury.  
  
## <a name="the-seekp-and-tellp-functions"></a>Funkcje seekp i tellp  
 Strumień pliku wyjściowego zachowuje wewnętrznego wskaźnika, który wskazuje miejsce, w których są dane do zapisania obok. `seekp` Funkcji członkowskiej ustawia ten wskaźnik, a tym samym zapewnia dostęp losowy dysku pliku wyjściowego. `tellp` Funkcji członkowskiej zwraca położenie pliku. Przykłady używających odpowiedniki strumień wejściowy `seekp` i `tellp`, zobacz [funkcji seekg i tellg](../standard-library/input-stream-member-functions.md).  
  
## <a name="the-close-function-for-output-streams"></a>Zamknij funkcja dla strumienie wyjściowe  
 **Zamknąć** funkcji członkowskiej zamyka plik dysku skojarzonego z strumienia pliku danych wyjściowych. Plik musi zostać zamknięty do ukończenia wszystkich dysków danych wyjściowych. W razie potrzeby `ofstream` destruktora zamyka plik dla Ciebie, ale może użyć **zamknąć** funkcji, aby otworzyć inny plik dla tego samego obiektu strumienia.  
  
 Destruktor strumień wyjściowy jest automatycznie zamykany strumienia pliku tylko wtedy, gdy Konstruktor lub **Otwórz** funkcji członkowskiej otworzyć plik. Przekazania pliku deskryptora już otwartego pliku lub użyj Konstruktora **dołączyć** funkcji członkowskiej, musisz zamknąć plik jawnie.  
  
##  <a name="vclrferrorprocessingfunctionsanchor10"></a>Wystąpił błąd podczas przetwarzania funkcje  
 Użyj tych funkcji elementu członkowskiego, aby sprawdzić błędy podczas zapisywania do strumienia:  
  
|Funkcja|Wartość zwracana|  
|--------------|------------------|  
|[Zły](http://msdn.microsoft.com/Library/4038d331-e9c9-48b0-bf49-c6505744469c)|Zwraca **true** Jeśli wystąpił nieodwracalny błąd.|  
|[Niepowodzenie](http://msdn.microsoft.com/Library/619f1b36-1e72-4551-8b48-888ae4e370d2)|Zwraca **true** przypadku nieodwracalny błąd lub warunek "Oczekiwano", na przykład błąd konwersji, lub jeśli plik nie został znaleziony. Przetwarzanie często można wznowić po wywołaniu **wyczyść** z argumentem zero.|  
|[dobra](http://msdn.microsoft.com/Library/77f0aa17-2ae1-48ae-8040-592d301e3972)|Zwraca **true** Jeśli nie jest brak błędu (nieodwracalny ani w inny sposób) i nie jest ustawiona flaga końca pliku.|  
|[EOF](http://msdn.microsoft.com/Library/3087f631-1268-49cd-86cf-ff4108862329)|Zwraca **true** pod warunkiem końca pliku.|  
|[Wyczyść](http://msdn.microsoft.com/Library/dc172694-1267-45f8-8f5c-e822e16fc271)|Ustawia stan błąd wewnętrzny. Jeśli wywołana z argumentami domyślnymi, czyści wszystkie bity błędu.|  
|[rdstate](http://msdn.microsoft.com/Library/e235e4e2-7e95-4777-a160-3938d263dd9c)|Zwraca bieżący stan błędu.|  
  
 **!** operator jest przeciążone w celu wykonania taką samą funkcję jak **niepowodzenie** funkcji. W związku z tym wyrażenie:  
  
```  
if(!cout)...  
```  
  
 odpowiada to:  
  
```  
if(cout.fail())...  
```  
  
 **Void\*()** operator jest przeciążony być przeciwieństwem **!** operator; w związku z tym wyrażenie:  
  
```  
if(cout)...  
```  
  
 jest równe:  
  
```  
if(!cout.fail())...  
```  
  
 **Void\*()** operator nie jest odpowiednikiem **dobrej** ponieważ Testuj na końcu pliku.  
  
## <a name="see-also"></a>Zobacz też  
 [Strumienie wyjściowe](../standard-library/output-streams.md)

