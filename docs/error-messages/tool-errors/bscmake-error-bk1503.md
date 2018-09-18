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
ms.openlocfilehash: 16bf228804cb24f4fe7a2428dc581116d4cec91d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064675"
---
# <a name="bscmake-error-bk1503"></a>Błąd BSCMAKE BK1503

Nie można zapisać do pliku 'NazwaPliku' [: przyczyny]

BSCMAKE łączy pliki SBR, wygenerowane podczas kompilacji w jednej bazy danych dla przeglądarki. Jeśli wynikowe baza danych przeglądarki przekracza 64 MB lub jeżeli liczba plików wejściowych (.sbr) przekracza 4092, ten błąd będzie emitowane.

Jeśli ten problem jest spowodowany przez więcej niż 4092 pliki SBR, należy zmniejszyć liczbę plików wejściowych. Z poziomu programu Visual Studio, można to osiągnąć przez [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) swoje całego projektu, a następnie ponowne na podstawie przez plik.

Jeśli ten problem jest spowodowany przez plik .bsc większym niż 64MB, zmniejszenie liczby plików SBR jako dane wejściowe zmniejszy rozmiar wynikowego pliku .bsc. Ponadto ilość informacji o przeglądaniu może zostać zmniejszony /Em (Wyklucz — makro rozwinięte symbole), /El (zmienne lokalne Wyklucz) i /Es (wyklucz pliki systemu).

## <a name="see-also"></a>Zobacz też

[Opcje BSCMAKE](../../build/reference/bscmake-options.md)