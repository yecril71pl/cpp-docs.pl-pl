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

**3.8.2 ANSI** Metoda lokalizowania plików źródłowych zawarcia

W przypadku specyfikacji plików ujętych w nawiasy ostre preprocesor nie przeszukuje katalogów plików nadrzędnych. Plik "nadrzędny" jest plikiem, który zawiera dyrektywę [#include](../preprocessor/hash-include-directive-c-cpp.md) . Zamiast tego rozpoczyna się od wyszukania pliku w katalogach określonych w wierszu polecenia kompilatora po/I. Jeśli/I opcja nie jest obecna lub kończy się niepowodzeniem, preprocesor używa zmiennej środowiskowej INCLUDE do znajdowania dowolnych plików dołączanych w nawiasach kątowych. Zmienna środowiskowa INCLUDE może zawierać wiele ścieżek oddzielonych średnikami (**;**). Jeśli więcej niż jeden katalog jest wyświetlany jako część opcji/I lub w zmiennej środowiskowej INCLUDE, preprocesor przeszukuje je w kolejności, w jakiej są wyświetlane.

## <a name="see-also"></a>Zobacz też

[Dyrektywy przetwarzania wstępnego](../c-language/preprocessing-directives.md)
