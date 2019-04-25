---
title: Strumienie binarne i tekstowe
ms.date: 11/04/2016
helpviewer_keywords:
- binary streams
- text streams
ms.assetid: 57035e4a-955d-4e04-a560-fcf67ce68b4e
ms.openlocfilehash: 3754a62fa02bc532eb71eba6b0a8837791b179ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62304428"
---
# <a name="text-and-binary-streams"></a>Strumienie binarne i tekstowe

Strumienia tekstu składa się z jednego lub więcej wierszy tekstu, które mogą być zapisywane do wyświetlania zorientowane na tekst, tak aby można było je odczytać. Podczas odczytywania ze strumienia tekstu, program odczytuje `NL` (nowy wiersz) na końcu każdego wiersza. Podczas zapisywania do strumienia tekstu, program zapisuje `NL` celu sygnalizowania, że koniec wiersza. W celu dopasowania do różnych Konwencji między środowiskach docelowych do reprezentowania tekstu w plikach, funkcje biblioteki może zmienić numer i reprezentacje znaków przesyłane między programem a strumienia tekstu.

W efekcie pozycjonowania w strumieniu tekstu jest ograniczona. Wskaźnik położenia pliku bieżącego można uzyskać wywołując [fgetpos](../c-runtime-library/reference/fgetpos.md) lub [ftell —](../c-runtime-library/reference/ftell-ftelli64.md). Można umieścić w strumieniu tekstu na pozycji uzyskane w ten sposób lub na początku lub na końcu strumienia, wywołując [fsetpos](../c-runtime-library/reference/fsetpos.md) lub [fseek](../c-runtime-library/reference/fseek-fseeki64.md). Zmiany pozycji również mogą być nie obsługiwane.

Dla uzyskania maksymalnej przenośności program nie powinien zapisać:

- Pustych plików.

- Znaków spacji na końcu wiersza.

- Częściowe wierszy (pomijając `NL` na końcu pliku).

- znaki inne niż drukowalne znaki, NL, i `HT` (tabulator poziomy).

Jeśli należy wykonać następujące czynności, sekwencji znaków, które Odczyt ze strumienia tekstu (albo jako bajtów lub znaków wielobajtowych) będzie zgodny sekwencji znaków, napisanym w strumieniu tekstu, podczas tworzenia pliku. W przeciwnym razie funkcji biblioteki można usunąć plik, który tworzysz, jeśli plik jest pusty, gdy go zamknąć. Lub ich zmienić ani usunąć znaki, które można zapisać do pliku.

Strumień binarny składa się z co najmniej jeden bajtów dowolnych informacji. Można zapisać wartości przechowywane w dowolnego obiektu do strumienia danych binarnych (zorientowane na bajt) i Przeczytaj dokładnie co to są przechowywane w obiekcie podczas jego autorem. Funkcje bibliotek nie należy zmieniać bajtów, jaką przesyłane między programem a strumień binarny. Można jednak dołączyć dowolną liczbę bajty o wartości null do pliku, który piszesz strumień binarny. Program musi obsłużyć te dodatkowe bajty o wartości null na końcu wszelkie strumienia danych binarnych.

W efekcie pozycjonowania w strumień binarny jest dobrze zdefiniowane, z wyjątkiem pozycjonowanie względem koniec strumienia. Można uzyskać, a następnie zmienić bieżący wskaźnik pozycji pliku takie same jak dla strumienia tekstu. Ponadto przesunięcia posługują się [ftell —](../c-runtime-library/reference/ftell-ftelli64.md) i [fseek](../c-runtime-library/reference/fseek-fseeki64.md) liczba bajtów od początku strumienia (czyli zero bajtów), więc całkowitą arytmetyczne na przesunięcia daje przewidywalne wyniki.

Strumień bajtów traktuje plik jako sekwencja bajtów. W ramach programu strumień wyglądają jak ta sama sekwencja bajtów, z wyjątkiem możliwości zmiany opisane powyżej.

## <a name="see-also"></a>Zobacz także

[Pliki i strumienie](../c-runtime-library/files-and-streams.md)
