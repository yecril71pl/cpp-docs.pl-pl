---
title: "Błąd BSCMAKE BK1503 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: BK1503
dev_langs: C++
helpviewer_keywords: BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c75e8513ead68befe2ca4ecd22475dc0a9071431
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="bscmake-error-bk1503"></a>Błąd BSCMAKE BK1503
Nie można zapisać do pliku "filename" [: Przyczyna]  
  
 BSCMAKE łączy pliki SBR generowanych podczas kompilacji w przeglądarce baz danych. Jeśli wynikowy przeglądarki bazy danych przekroczy 64 MB lub 4092 przekracza liczbę plików danych wejściowych (.sbr), ten błąd będzie emitowany.  
  
 Jeśli przyczyną problemu jest więcej niż 4092 pliki SBR, należy zmniejszyć liczbę plików wejściowych. Z poziomu programu Visual Studio można to zrobić przez [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) Twojego cały projekt, a następnie sprawdź ponownie na podstawie pliku przez plik.  
  
 Jeśli przyczyną problemu jest większy niż 64MB pliku .bsc, zmniejszenie liczby plików SBR jako dane wejściowe zmniejszy rozmiar wynikowego pliku .bsc. Ponadto ilości informacji o przeglądaniu może zostać zmniejszony /Em (Wyklucz makro rozwinięty symboli), /El (zmiennych lokalnych Wyklucz) i /Es (wyklucz pliki systemowe).  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje BSCMAKE](../../build/reference/bscmake-options.md)