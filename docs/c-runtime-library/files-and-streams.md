---
title: Pliki i strumienie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- files [C++]
- streams
ms.assetid: f61e712b-eac9-4c28-bb18-97c3786ef387
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a93fc1aa0f3108d4897a45b9014970afab220439
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32390521"
---
# <a name="files-and-streams"></a>Pliki i strumienie
Program komunikuje się z środowiska docelowego za odczytywanie i zapisywanie plików. Plik może być:  
  
-   Zestaw danych, który może odczytywać i zapisać wielokrotnie.  
  
-   Strumień bajtów wygenerowany przez program (na przykład potoku).  
  
-   Strumień bajtów odebranych z lub wysyłane do urządzenia peryferyjne.  
  
 Ostatnie dwa elementy są interaktywne plików. Pliki są zwykle główna sposób interakcji z programem. Manipulowania tych typów plików w taki sam sposób, przez wywołanie funkcji biblioteki. Standardowy nagłówek stdio — możesz dołączyć. H, aby zadeklarować większość tych funkcji.  
  
 Zanim będzie można wykonywać wiele operacji na pliku, można otworzyć pliku. Otwarcie pliku kojarzy ją za pomocą strumienia strukturą danych w bibliotece C Standard glosses przez wiele różnic między plikami różnego rodzaju. Biblioteka przechowuje informacje o stanie każdego strumienia w obiekcie typu pliku.  
  
 Trzy pliki przed uruchamianie programu otworzy się w środowisku docelowym. Plik można otworzyć przez wywołanie funkcji biblioteki [fopen —, _wfopen —](../c-runtime-library/reference/fopen-wfopen.md) z dwoma argumentami. ( `fopen` Funkcja jest przestarzała, użyj [fopen_s —, _wfopen_s —](../c-runtime-library/reference/fopen-s-wfopen-s.md) zamiast.) Pierwszy argument jest nazwą pliku. Drugi argument jest ciąg C, który określa:  
  
-   Określa, czy użytkownik zamierza danych z pliku do odczytu lub zapisu danych lub oba.  
  
-   Czy chcesz wygenerować nowej zawartości w pliku (lub utworzyć plik, jeśli wcześniej nie istniał) lub pozostaw istniejącej zawartości w miejscu.  
  
-   Zapisuje dane w pliku można zmodyfikować istniejącą zawartość czy tylko powinien dołączyć bajtów na końcu pliku.  
  
-   Czy chcesz manipulowania strumienia tekst lub binarny strumienia.  
  
 Po pomyślnym otwarciu pliku, następnie można określić, czy strumień jest ukierunkowane bajtów (strumień bajtów) lub całego skoncentrowany na zadaniach (wide strumień). Strumień jest początkowo niepowiązanych. Wywoływanie niektórych funkcji działanie w strumieniu ułatwia ukierunkowane podczas niektórych innych funkcji była szeroki zorientowane na bajt. Po strumienia obsługuje orientacji, dopóki nie jest ono zamknięte przez wywołanie do [fclose —](../c-runtime-library/reference/fclose-fcloseall.md) lub [freopen —](../c-runtime-library/reference/freopen-wfreopen.md).  
  
 © 1989-2001 przez P.J. Plauger i Jim Brodie. Wszelkie prawa zastrzeżone.  
  
## <a name="see-also"></a>Zobacz też  
 [Strumienie binarne i tekstowe](../c-runtime-library/text-and-binary-streams.md)   
 [Strumienie Byte oraz szerokie](../c-runtime-library/byte-and-wide-streams.md)   
 [Sterowanie strumieniami](../c-runtime-library/controlling-streams.md)   
 [Stany strumieni](../c-runtime-library/stream-states.md)