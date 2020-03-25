---
title: Błąd BSCMAKE BK1503
ms.date: 11/04/2016
f1_keywords:
- BK1503
helpviewer_keywords:
- BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
ms.openlocfilehash: e0f05b3979024cb053394c51fa9337197b5de7bf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197863"
---
# <a name="bscmake-error-bk1503"></a>Błąd BSCMAKE BK1503

nie można zapisać w pliku "filename" [: Przyczyna]

BSCMAKE łączy pliki. sbr generowane podczas kompilacji w jedną bazę danych przeglądarki. Jeśli wynikająca baza danych przeglądarki przekracza 64 MB lub liczba plików wejściowych (. sbr) przekracza 4092, ten błąd zostanie wyemitowany.

Jeśli problem jest spowodowany przez więcej niż 4092 plików. sbr, należy zmniejszyć liczbę plików wejściowych. W programie Visual Studio można to osiągnąć przez [/fr](../../build/reference/fr-fr-create-dot-sbr-file.md) całego projektu, a następnie ponowne sprawdzenie pliku według pliku.

Jeśli problem jest spowodowany przez plik. bsc o rozmiarze większym niż 64 MB, zmniejszenie liczby plików. sbr jako danych wejściowych spowoduje zmniejszenie rozmiaru wynikowego pliku. BSC. Ponadto ilość informacji o przeglądaniu może być ograniczona przez użycie/em (wykluczanie rozwiniętych symboli makr),/El (wykluczanie zmiennych lokalnych) i/es (Wyklucz pliki systemowe).

## <a name="see-also"></a>Zobacz też

[Opcje BSCMAKE](../../build/reference/bscmake-options.md)
