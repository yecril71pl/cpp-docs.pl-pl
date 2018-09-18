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
ms.openlocfilehash: ca0850f0e798067ba48b59a1c2585b8ba87c5451
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062179"
---
# <a name="files-and-streams"></a>Pliki i strumienie

Program komunikuje się ze środowiska docelowego, Odczyt i zapis plików. Plik może być:

- Zestaw danych, które mogą odczytywać i zapisywać w wielokrotnie.

- Strumień bajtów wygenerowany przez program (na przykład potok).

- Strumień bajtów odebranych z lub wysyłane do urządzenia peryferyjne.

Ostatnie dwa elementy są interaktywne plików. Są to zazwyczaj podmiotu zabezpieczeń oznacza, że za pomocą którego do interakcji z programem. Manipulowania wszystkie te rodzaje plików w taki sam sposób, wywołując funkcje biblioteki. Możesz dołączyć standardowy nagłówek stdio —. H, aby zadeklarować większość tych funkcji.

Aby można było wykonać wiele operacji na pliku, można otworzyć pliku. Otwieranie pliku kojarzy ją z usługą stream, struktura danych w ramach standardowej biblioteki C, która glosses przez wiele różnic między plikami różnych rodzajów. Biblioteka przechowuje informacje o stanie każdego strumienia w obiekcie typu pliku.

Środowisko docelowe otwiera trzy pliki przed uruchomieniem programu. Plik można otworzyć przez wywołanie funkcji biblioteki [fopen —, _wfopen —](../c-runtime-library/reference/fopen-wfopen.md) za pomocą dwóch argumentów. ( `fopen` Funkcja jest przestarzała, użyj [fopen_s —, _wfopen_s —](../c-runtime-library/reference/fopen-s-wfopen-s.md) zamiast.) Pierwszy argument jest nazwą pliku. Drugi argument jest ciąg C, który określa:

- Czy zamierzasz odczytu danych z pliku lub zapisywanie danych do jej lub obu.

- Czy chcesz wygenerować nowej zawartości dla pliku (lub utworzenie pliku, jeśli wcześniej nie istniał) lub nie podawaj żadnej istniejącej zawartości w miejscu.

- Operacje zapisu do pliku może zmienić istniejącą zawartość czy powinna tylko Dołącz bajtów na końcu pliku.

- Czy chcesz manipulowania strumienia tekstu lub strumienia binarnego.

Gdy plik zostanie pomyślnie otwarty, następnie można określić, czy strumień jest zorientowane na bajt (strumień bajtów) lub całego obiektowo (strumień szerokości). Strumień jest początkowo niepowiązanej. Wywoływanie niektórych funkcji do wykonywania operacji strumienia sprawia, że obiektowo, podczas gdy niektóre inne funkcje ułatwiają szerokiego zorientowanej na bajt. Po strumień obsługuje orientacji, dopóki nie jest ono zamknięte przez wywołanie [fclose —](../c-runtime-library/reference/fclose-fcloseall.md) lub [freopen —](../c-runtime-library/reference/freopen-wfreopen.md).

© 2001 1989 r. przez P.J. Plauger i Jim Brodie. Wszelkie prawa zastrzeżone.

## <a name="see-also"></a>Zobacz też

[Strumienie binarne i tekstowe](../c-runtime-library/text-and-binary-streams.md)<br/>
[Strumienie byte oraz szerokie](../c-runtime-library/byte-and-wide-streams.md)<br/>
[Sterowanie strumieniami](../c-runtime-library/controlling-streams.md)<br/>
[Stany strumieni](../c-runtime-library/stream-states.md)