---
title: Błąd BSCMAKE BK1503
ms.date: 11/04/2016
f1_keywords:
- BK1503
helpviewer_keywords:
- BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
ms.openlocfilehash: c81e955b912e03b322c0429097410fae74713b9d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280142"
---
# <a name="bscmake-error-bk1503"></a>Błąd BSCMAKE BK1503

Nie można zapisać do pliku 'NazwaPliku' [: przyczyny]

BSCMAKE łączy pliki SBR, wygenerowane podczas kompilacji w jednej bazy danych dla przeglądarki. Jeśli wynikowe baza danych przeglądarki przekracza 64 MB lub jeżeli liczba plików wejściowych (.sbr) przekracza 4092, ten błąd będzie emitowane.

Jeśli ten problem jest spowodowany przez więcej niż 4092 pliki SBR, należy zmniejszyć liczbę plików wejściowych. Z poziomu programu Visual Studio, można to osiągnąć przez [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) swoje całego projektu, a następnie ponowne na podstawie przez plik.

Jeśli ten problem jest spowodowany przez plik .bsc większym niż 64MB, zmniejszenie liczby plików SBR jako dane wejściowe zmniejszy rozmiar wynikowego pliku .bsc. Ponadto ilość informacji o przeglądaniu może zostać zmniejszony /Em (Wyklucz — makro rozwinięte symbole), /El (zmienne lokalne Wyklucz) i /Es (wyklucz pliki systemu).

## <a name="see-also"></a>Zobacz także

[Opcje BSCMAKE](../../build/reference/bscmake-options.md)