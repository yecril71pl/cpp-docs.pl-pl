---
title: Strumienie binarne i tekstowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- binary streams
- text streams
ms.assetid: 57035e4a-955d-4e04-a560-fcf67ce68b4e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e91881f738c1b6411179c4f8e10e30f69e7b8667
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="text-and-binary-streams"></a>Strumienie binarne i tekstowe
Strumień tekstu składa się z jednego lub więcej wierszy tekstu, które mogą być zapisywane na wyświetlenie tekstowych, dzięki czemu mogą być odczytywane. Podczas odczytywania ze strumienia tekstu, program odczytuje `NL` (nowego wiersza) pod koniec każdego wiersza. Podczas zapisywania do strumienia tekstu, program zapisuje `NL` która sygnalizuje koniec wiersza. Odpowiadające różne konwencje między środowiska docelowego reprezentujący tekstu w plikach funkcji biblioteki można zmienić numer reprezentacje znaków przesyłane między programem a strumienia tekstu.  
  
 W związku z tym pozycjonowania w strumieniu tekst jest ograniczona. Wskaźnik położenia pliku bieżącego można uzyskać przez wywołanie metody [fgetpos —](../c-runtime-library/reference/fgetpos.md) lub [ftell —](../c-runtime-library/reference/ftell-ftelli64.md). Można umieścić strumienia tekstu na pozycji uzyskane w ten sposób lub początek lub koniec strumienia, wywołując [fsetpos —](../c-runtime-library/reference/fsetpos.md) lub [fseek](../c-runtime-library/reference/fseek-fseeki64.md). Zmiany pozycji może również nie być obsługiwany.  
  
 Przenośności maksymalna program nie powinien zapisać:  
  
-   Pustych plików.  
  
-   Spacje na końcu linii.  
  
-   Częściowo (, pomijając `NL` na końcu pliku).  
  
-   znaki inne niż drukowalne znaki NL, i `HT` (tabulator poziomy).  
  
 Jeśli wykonujesz te reguły sekwencja znaków odczytu ze strumienia tekstu (albo jako bajtów lub znaków wielobajtowych) będzie odpowiadała sekwencja znaków napisanym strumienia tekstu podczas tworzenia pliku. W przeciwnym razie funkcje biblioteki można usunąć pliku, które tworzysz, jeśli plik jest pusty, po jego zamknięciu. Lub mogą zmienić lub usunąć znaki, które można zapisać do pliku.  
  
 Strumień binarny składa się z jednego lub więcej bajtów dowolnych informacji. Można zapisać wartości przechowywane w dowolnego obiektu do (zorientowane na bajt) strumienia danych binarnych i Przeczytaj dokładnie co to są przechowywane w obiekcie podczas zostało napisane. Funkcje bibliotek nie należy zmieniać przesyłane między programem a binarne strumienia bajtów. Można jednak Dołącz dowolnej liczby bajtów null do pliku, który zapisu za pomocą strumienia binarnego. Program musi uwzględniać następujące dodatkowe bajty zerowe na końcu wszystkie strumienia danych binarnych.  
  
 W związku z tym pozycjonowania w strumienia binarnego jest dobrze zdefiniowany, z wyjątkiem pozycjonowanie względem koniec strumienia. Można uzyskać i alter wskaźnik położenia pliku bieżącego takie same jak w przypadku strumienia tekstu. Ponadto przesunięcia używane przez [ftell —](../c-runtime-library/reference/ftell-ftelli64.md) i [fseek](../c-runtime-library/reference/fseek-fseeki64.md) liczba bajtów od początku strumienia (czyli bajtów zero), więc całkowitą arytmetycznego na przesunięcia daje przewidywalne wyniki.  
  
 Strumień bajtów traktuje pliku jako sekwencję bajtów. W programie strumienia wygląda takiej samej kolejności bajtów, z wyjątkiem możliwości zmiany opisane powyżej.  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki i strumienie](../c-runtime-library/files-and-streams.md)