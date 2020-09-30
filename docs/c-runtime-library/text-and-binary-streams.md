---
title: Strumienie binarne i tekstowe
description: Opis strumieni tekstu i danych binarnych w bibliotece środowiska uruchomieniowego Microsoft C.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- binary streams
- text streams
ms.assetid: 57035e4a-955d-4e04-a560-fcf67ce68b4e
ms.openlocfilehash: 522e4d5f119e4415694b59b2b08141a45f06fe5a
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589617"
---
# <a name="text-and-binary-streams"></a>Strumienie binarne i tekstowe

Strumień tekstowy składa się z co najmniej jednego wiersza tekstu, który można zapisać w widoku zorientowanym na tekst, aby można go było odczytać. Podczas odczytywania ze strumienia tekstowego program odczytuje `NL` na końcu każdego wiersza (nowy wiersz). Podczas zapisywania do strumienia tekstowego program zapisuje znak, `NL` Aby sygnalizować koniec wiersza. Aby dopasować różne konwencje między środowiskami docelowymi dla reprezentowania tekstu w plikach, funkcje biblioteki mogą zmieniać liczbę i reprezentacje znaków przesyłanych między programem i strumieniem tekstu.

Pozycjonowanie w ramach strumienia tekstowego jest ograniczone. Bieżący wskaźnik położenia pliku można uzyskać, wywołując [fgetpos](../c-runtime-library/reference/fgetpos.md) lub [ftell](../c-runtime-library/reference/ftell-ftelli64.md). Można umieścić strumień tekstowy na miejscu uzyskanym w ten sposób lub na początku lub na końcu strumienia, wywołując [fsetpos](../c-runtime-library/reference/fsetpos.md) lub [fseek](../c-runtime-library/reference/fseek-fseeki64.md). Każda inna zmiana pozycji może być również nieobsługiwana.

W celu uzyskania maksymalnej przenośności program nie powinien pisać:

- Puste pliki.
- Spacje na końcu wiersza.
- Częściowe linie (pomijając je `NL` na końcu pliku).
- znaki inne niż drukowalne znaki, NL i `HT` (tabulacja pozioma).

W przypadku przestrzegania tych reguł sekwencja znaków odczytywanych ze strumienia tekstu (jako bajty lub znaki wielobajtowe) będzie zgodna z sekwencją znaków zapisaną w strumieniu tekstowym podczas tworzenia pliku. W przeciwnym razie funkcje biblioteki mogą usunąć utworzony plik, jeśli plik jest pusty po jego zamknięciu. Lub mogą zmieniać lub usuwać znaki zapisane w pliku.

Strumień binarny składa się z co najmniej jednego bajtu dowolnych informacji. Można napisać wartość przechowywaną w dowolnym obiekcie do strumienia binarnego (zorientowanym na bajtowo) i odczytać dokładnie zawartość zapisaną w obiekcie podczas jego tworzenia. Funkcje biblioteki nie zmieniają bajtów przesyłanych między programem i strumieniem binarnym. Mogą jednak dołączyć dowolną liczbę `NULL` bajtów do pliku zapisanego za pomocą strumienia binarnego. Program musi zająć się tymi dodatkowymi `NULL` bajtami na końcu strumienia binarnego.

Pozycjonowanie w strumieniu binarnym jest dobrze zdefiniowane, z wyjątkiem położenia względem końca strumienia. Możesz uzyskać i zmienić bieżący wskaźnik położenia pliku tak samo jak w przypadku strumienia tekstu. Przesunięcia używane przez [ftell](../c-runtime-library/reference/ftell-ftelli64.md) i [fseek](../c-runtime-library/reference/fseek-fseeki64.md) liczbę bajtów od początku strumienia (czyli bajt zero), więc liczba całkowita arytmetyczna na tych przesunięciach daje przewidywalny wynik.

Strumień bajtów traktuje plik jako sekwencję bajtów. W ramach programu strumień wygląda podobnie do tej samej sekwencji bajtów, z wyjątkiem ewentualnych zmian opisanych powyżej.

## <a name="see-also"></a>Zobacz też

[Pliki i strumienie](../c-runtime-library/files-and-streams.md)
