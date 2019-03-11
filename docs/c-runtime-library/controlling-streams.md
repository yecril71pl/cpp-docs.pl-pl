---
title: Sterowanie strumieniami
ms.date: 11/04/2016
f1_keywords:
- Controlling Streams
helpviewer_keywords:
- streams, controlling
- controlling streams
- streams
ms.assetid: 267e9013-9afc-45f6-91e3-ca093230d9d9
ms.openlocfilehash: 85c7e1b22519287fbd03d89487d6639f197a8b63
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743315"
---
# <a name="controlling-streams"></a>Sterowanie strumieniami

[fopen —](../c-runtime-library/reference/fopen-wfopen.md) zwraca adres obiektu typu `FILE`. Możesz użyć tego adresu jako `stream` argument kilka funkcji biblioteki do wykonywania różnych operacji na otwartego pliku. Dla strumień bajtów wszystkich danych wejściowych odbywa się tak, jakby każdy znak jest odczytywany przez wywołanie [fgetc —](../c-runtime-library/reference/fgetc-fgetwc.md), a wszystkie dane wyjściowe odbywa się tak, jakby każdy znak jest zapisywany przez wywołanie metody [fputc](../c-runtime-library/reference/fputc-fputwc.md). Dla szerokiego strumienia wszystkich danych wejściowych odbywa się tak, jakby każdy znak jest odczytywany przez wywołanie [fgetwc —](../c-runtime-library/reference/fgetc-fgetwc.md), a wszystkie dane wyjściowe odbywa się tak, jakby każdy znak jest zapisywany przez wywołanie metody [fputwc —](../c-runtime-library/reference/fputc-fputwc.md).

Możesz zamknąć plik, wywołując [fclose —](../c-runtime-library/reference/fclose-fcloseall.md), po którym adres `FILE` obiekt jest nieprawidłowy.

A `FILE` obiekt przechowuje stan strumienia, w tym:

- Wskaźnik błędu ustawić wartość różną od zera, funkcja, która napotyka odczytu lub zapisu błędu.

- Ustaw wartość różną od zera, funkcja, która napotyka koniec pliku podczas odczytywania wskaźnik końca pliku.

- Wskaźnik położenia pliku określa następny bajt w strumień do odczytu lub zapisu, jeśli plik może obsłużyć żądania pozycjonowania.

- A [strumienia stanu](../c-runtime-library/stream-states.md) Określa, czy strumień będzie akceptować operacji odczytu i/lub operacje zapisu i tego, czy strumień jest niezwiązany, bajt zorientowanej na lub całego zorientowanej na.

- Stan konwersji pamięta, że stan dowolnego częściowo Zgromadziliśmy lub generowane uogólniony wielobajtowym, a także stan dowolnego shift sekwencji bajtów w pliku).

- Buforu pliku Określa adres i rozmiar obiektu array, używanego przez funkcje biblioteki zwiększyć wydajność odczytu i zapisu do strumienia.

Nie należy zmieniać wartości zapisanej w `FILE` obiektu lub buforu pliku, który określisz do użycia z tym obiektem. Nie można skopiować `FILE` obiektu i portably Użyj adresu Kopiuj jako `stream` argument do funkcji biblioteki.

## <a name="see-also"></a>Zobacz także

[Pliki i strumienie](../c-runtime-library/files-and-streams.md)
