---
title: Łącznie z nazwami plików w nawiasach
ms.date: 11/04/2016
ms.assetid: 6a4e5411-c35e-48b8-90ef-b37ac324ed94
ms.openlocfilehash: 87de00814f58ed86ee33abdcf96dd210f418c5ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233102"
---
# <a name="including-bracketed-filenames"></a>Łącznie z nazwami plików w nawiasach

**ANSI 3.8.2** metody lokalizowania pliki źródłowe do zawarcia

Specyfikacji pliku ujęta w nawiasy ostre preprocesor nie wyszukiwania katalogów pliku nadrzędnego. Plik "nadrzędny" znajduje się plik, który ma [#include](../preprocessor/hash-include-directive-c-cpp.md) dyrektywy w nim. Zamiast tego należy go rozpoczyna się od wyszukiwania pliku w określonym następującego wiersza polecenia kompilatora / I. Jeśli opcja /I nie istnieje lub nie powiedzie się, preprocesor wykorzysta zmienną środowiskową INCLUDE, aby znaleźć wszystkie pliki dołączane w nawiasach kątowych. Zmienna środowiskowa INCLUDE może zawierać wiele ścieżek oddzielonych średnikami (**;**). Jeśli więcej niż jeden katalog pojawia się jako część opcji /I lub w ramach zmienną środowiskową INCLUDE, preprocesor przeszukuje je w kolejności, w jakiej są wyświetlane.

## <a name="see-also"></a>Zobacz także

[Dyrektywy przetwarzania wstępnego](../c-language/preprocessing-directives.md)
