---
title: Sterowanie strumieniami
description: Omówienie pracy z strumieniami w bibliotece środowiska uruchomieniowego Microsoft C.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Controlling Streams
helpviewer_keywords:
- streams, controlling
- controlling streams
- streams
ms.assetid: 267e9013-9afc-45f6-91e3-ca093230d9d9
ms.openlocfilehash: 0caa9eca7c960acbb581358c1a92afcc6a8af066
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589721"
---
# <a name="controlling-streams"></a>Sterowanie strumieniami

[fopen](../c-runtime-library/reference/fopen-wfopen.md) zwraca adres obiektu typu `FILE` . Ten adres jest używany jako `stream` argument kilku funkcji biblioteki do wykonywania różnych operacji na otwartym pliku. W przypadku strumienia bajtów wszystkie dane wejściowe odbywają się tak, jakby każdy znak był odczytywany przez wywołanie [fgetc](../c-runtime-library/reference/fgetc-fgetwc.md), a wszystkie dane wyjściowe są wykonywane tak, jakby każdy znak został zapisany przez wywołanie [fputc](../c-runtime-library/reference/fputc-fputwc.md). W przypadku strumienia szerokiego wszystkie dane wejściowe są wykonywane tak, jakby każdy znak był odczytywany przez wywołanie [fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md), a wszystkie dane wyjściowe są wykonywane tak, jakby każdy znak został zapisany przez wywołanie [fputwc](../c-runtime-library/reference/fputc-fputwc.md).

Można zamknąć plik, wywołując [fclose](../c-runtime-library/reference/fclose-fcloseall.md), po którym adres `FILE` obiektu jest nieprawidłowy.

`FILE`Obiekt przechowuje stan strumienia, w tym:

- Wskaźnik błędu ustawia niezerową przez funkcję, która napotka błąd odczytu lub zapisu.

- Wskaźnik końca pliku ustawił niezerową przez funkcję, która napotka koniec pliku podczas odczytywania.

- Wskaźnik położenia pliku określa następny bajt w strumieniu do odczytu lub zapisu, jeśli plik może obsługiwać żądania pozycjonowania.

- [Stan strumienia](../c-runtime-library/stream-states.md) określa, czy strumień będzie akceptować operacje odczytu i/lub zapisu oraz czy strumień jest niepowiązany, zorientowany na bajtach czy zorientowany na szerokie.

- Stan konwersji pamięta stan dowolnego częściowo złożonego lub wygenerowanego uogólnionego znaku wielobajtowego, a także dowolnego stanu przesunięcia sekwencji bajtów w pliku.

- Bufor plików określa adres i rozmiar obiektu tablicy, za pomocą którego funkcje biblioteki mogą zwiększyć wydajność operacji odczytu i zapisu w strumieniu.

Nie należy zmieniać żadnej wartości przechowywanej w `FILE` obiekcie ani w buforze plików określonym do użycia z tym obiektem. Nie można skopiować `FILE` obiektu ani portowo użyć adresu kopiowania jako `stream` argumentu funkcji biblioteki.

## <a name="see-also"></a>Zobacz też

[Pliki i strumienie](../c-runtime-library/files-and-streams.md)
