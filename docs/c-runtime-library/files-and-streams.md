---
title: Pliki i strumienie
description: Omówienie plików i strumieni w bibliotece środowiska uruchomieniowego Microsoft C.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files [C++]
- streams
ms.assetid: f61e712b-eac9-4c28-bb18-97c3786ef387
ms.openlocfilehash: 39133cfdb4784c42561a159d6d176bcbd23644af
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589968"
---
# <a name="files-and-streams"></a>Pliki i strumienie

Program komunikuje się ze środowiskiem docelowym poprzez odczytywanie i zapisywanie plików. Plik może być:

- Zestaw danych, który można odczytywać i zapisywać wielokrotnie.

- Strumień bajtów generowany przez program (na przykład potok).

- Strumień bajtów odebranych z lub wysłanych na urządzenie peryferyjne.

Ostatnie dwa elementy to pliki interaktywne. Pliki są zazwyczaj podmiotem zabezpieczeń, za pomocą którego można korzystać z programu. Wszystkie te rodzaje plików są przetwarzane w taki sam sposób — przez wywoływanie funkcji biblioteki. Dołączenie standardowego nagłówka STDIO. H, aby zadeklarować większość tych funkcji.

Aby można było wykonać wiele operacji na pliku, należy otworzyć plik. Otwarcie pliku powoduje skojarzenie go ze strumieniem, strukturą danych w standardowej bibliotece języka C, która zabłyszcząca wiele różnic między plikami różnych rodzajów. Biblioteka zachowuje stan każdego strumienia w obiekcie typu plik.

Środowisko docelowe otwiera trzy pliki przed uruchomieniem programu. Możesz otworzyć plik, wywołując funkcję biblioteki [fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md) z dwoma argumentami. ( `fopen` Funkcja jest przestarzała, użyj [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md) zamiast niej). Pierwszym argumentem jest nazwa pliku. Drugi argument jest ciągiem C, który określa:

- Czy zamierzasz odczytywać dane z pliku, czy zapisywać do nich dane.

- Czy zamierzasz generować nową zawartość dla pliku (lub utworzyć plik, jeśli jeszcze nie istnieje) lub pozostawić istniejącą zawartość na miejscu.

- Czy operacje zapisu w pliku mogą zmieniać istniejącą zawartość lub dołączać tylko bajty na końcu pliku.

- Czy chcesz manipulować strumieniem tekstu lub strumieniem binarnym.

Po pomyślnym otwarciu pliku można określić, czy strumień jest zorientowany na bajty (strumień bajtów) czy zorientowany na szerokie (szeroki strumień). Na początku nie powiązano strumienia. Wywoływanie niektórych funkcji w strumieniu sprawia, że jest to zorientowane na bajty, a niektóre inne funkcje sprawiają, że są zorientowane na szeroką. Po ustanowieniu strumień zachowuje swoją orientację, dopóki nie zostanie zamknięty przez wywołanie [fclose](../c-runtime-library/reference/fclose-fcloseall.md) lub [freopen](../c-runtime-library/reference/freopen-wfreopen.md).

© 1989-2001 według P.J. Plauger i Jim Brodie. All rights reserved.

## <a name="see-also"></a>Zobacz też

[Strumienie tekstu i danych binarnych](../c-runtime-library/text-and-binary-streams.md)<br/>
[Strumienie bajtowe i szerokie](../c-runtime-library/byte-and-wide-streams.md)<br/>
[Kontrolowanie strumieni](../c-runtime-library/controlling-streams.md)<br/>
[Stany strumienia](../c-runtime-library/stream-states.md)
