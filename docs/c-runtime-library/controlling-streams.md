---
title: Sterowanie strumieniami | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Controlling Streams
dev_langs: C++
helpviewer_keywords:
- streams, controlling
- controlling streams
- streams
ms.assetid: 267e9013-9afc-45f6-91e3-ca093230d9d9
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d2211a2a2bb5121921928166626d726db8dea67f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="controlling-streams"></a>Sterowanie strumieniami
[fopen —](../c-runtime-library/reference/fopen-wfopen.md) zwraca adres typu obiektu `FILE`. Możesz użyć tego adresu jako `stream` argument kilka funkcji biblioteki można wykonywać różne operacje, w której plik otwarty. Dla strumienia bajtów wszystkich wejściowych odbywa się tak, jakby każdy znak jest do odczytu przez wywołanie metody [fgetc —](../c-runtime-library/reference/fgetc-fgetwc.md), oraz wszystkie dane wyjściowe odbywa się tak, jakby każdy znak jest zapisywane przez wywołanie metody [fputc —](../c-runtime-library/reference/fputc-fputwc.md). Dla strumienia szerokości, wszystkie wejściowych odbywa się tak, jakby każdy znak jest do odczytu przez wywołanie metody [fgetwc —](../c-runtime-library/reference/fgetc-fgetwc.md), oraz wszystkie dane wyjściowe odbywa się tak, jakby każdy znak jest zapisywane przez wywołanie metody [fputwc —](../c-runtime-library/reference/fputc-fputwc.md).  
  
 Możesz zamknąć plik wywołując [fclose —](../c-runtime-library/reference/fclose-fcloseall.md), po którym adres `FILE` obiektu jest nieprawidłowy.  
  
 A `FILE` obiekt przechowuje stan strumienia, w tym:  
  
-   Wskaźnik błędów ustawienia różną od zera przez funkcję napotka odczytu lub zapisu błędu.  
  
-   Wartość niezerową przez funkcję napotka koniec pliku podczas odczytywania wskaźnik końca pliku.  
  
-   Wskaźnik położenia pliku określa następny bajt w strumień do odczytu lub zapisu, jeśli plik może obsługiwać żądań pozycjonowania.  
  
-   A [strumienia stanu](../c-runtime-library/stream-states.md) Określa, czy strumień będzie akceptować odczyty i/lub zapisy i określa, czy strumień jest niezwiązany, zorientowane na bajt lub całego zorientowane na.  
  
-   Stan konwersji pamięta, że stan dowolnego częściowo złożony lub wygenerować uogólniony znaków wielobajtowych, a także stan dowolnego shift sekwencji bajtów w pliku).  
  
-   Bufor plików określa adres i rozmiar tablicy obiektów używanego przez funkcje biblioteki można poprawić wydajność odczytu i zapisu do strumienia.  
  
 Nie należy zmieniać wartości zapisanej w `FILE` obiektu lub w buforze plików, który określisz do użycia z tym obiektem. Nie można skopiować `FILE` obiekt portably adres i użyj go jako kopii `stream` argument funkcji biblioteki.  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki i strumienie](../c-runtime-library/files-and-streams.md)