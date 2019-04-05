---
title: Błąd BSCMAKE BK1503
ms.date: 11/04/2016
f1_keywords:
- BK1503
helpviewer_keywords:
- BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
ms.openlocfilehash: c81e955b912e03b322c0429097410fae74713b9d
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031595"
---
# <a name="bscmake-error-bk1503"></a>Błąd BSCMAKE BK1503

Nie można zapisać do pliku 'NazwaPliku' [: przyczyny]

BSCMAKE łączy pliki SBR, wygenerowane podczas kompilacji w jednej bazy danych dla przeglądarki. Jeśli wynikowe baza danych przeglądarki przekracza 64 MB lub jeżeli liczba plików wejściowych (.sbr) przekracza 4092, ten błąd będzie emitowane.

Jeśli ten problem jest spowodowany przez więcej niż 4092 pliki SBR, należy zmniejszyć liczbę plików wejściowych. Z poziomu programu Visual Studio, można to osiągnąć przez [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) swoje całego projektu, a następnie ponowne na podstawie przez plik.

Jeśli ten problem jest spowodowany przez plik .bsc większym niż 64MB, zmniejszenie liczby plików SBR jako dane wejściowe zmniejszy rozmiar wynikowego pliku .bsc. Ponadto ilość informacji o przeglądaniu może zostać zmniejszony /Em (Wyklucz — makro rozwinięte symbole), /El (zmienne lokalne Wyklucz) i /Es (wyklucz pliki systemu).

## <a name="see-also"></a>Zobacz także

[Opcje BSCMAKE](../../build/reference/bscmake-options.md)