---
title: Błąd BSCMAKE BK1503 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1503
dev_langs:
- C++
helpviewer_keywords:
- BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 06d4a05a8f2d04c3f8a991d4444b35295408a7b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="bscmake-error-bk1503"></a>Błąd BSCMAKE BK1503
Nie można zapisać do pliku "filename" [: Przyczyna]  
  
 BSCMAKE łączy pliki SBR generowanych podczas kompilacji w przeglądarce baz danych. Jeśli wynikowy przeglądarki bazy danych przekroczy 64 MB lub 4092 przekracza liczbę plików danych wejściowych (.sbr), ten błąd będzie emitowany.  
  
 Jeśli przyczyną problemu jest więcej niż 4092 pliki SBR, należy zmniejszyć liczbę plików wejściowych. Z poziomu programu Visual Studio można to zrobić przez [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) Twojego cały projekt, a następnie sprawdź ponownie na podstawie pliku przez plik.  
  
 Jeśli przyczyną problemu jest większy niż 64MB pliku .bsc, zmniejszenie liczby plików SBR jako dane wejściowe zmniejszy rozmiar wynikowego pliku .bsc. Ponadto ilości informacji o przeglądaniu może zostać zmniejszony /Em (Wyklucz makro rozwinięty symboli), /El (zmiennych lokalnych Wyklucz) i /Es (wyklucz pliki systemowe).  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje BSCMAKE](../../build/reference/bscmake-options.md)