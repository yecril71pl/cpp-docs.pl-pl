---
title: Łącznie z nazwami plików w cudzysłowie
ms.date: 11/04/2016
ms.assetid: 789a047e-ea38-4c99-b71d-a2ad9c81daee
ms.openlocfilehash: 11beaa3a91f476348c57b12ab3febad7cb9c89fc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656719"
---
# <a name="including-quoted-filenames"></a>Łącznie z nazwami plików w cudzysłowie

**ANSI 3.8.2** obsługę nazw pliki źródłowe do zawarcia w cudzysłowie

Jeśli określisz pełną, jednoznaczną specyfikację ścieżki do dołączanego pliku między dwoma zestawami podwójnego cudzysłowu (""), preprocesor przeszukuje tylko tę specyfikację ścieżki i ignoruje katalogi standardowe.

Dla plików dołączanych określonych jako [#include](../preprocessor/hash-include-directive-c-cpp.md) "path-spec", katalog wyszukiwanie rozpoczyna się od katalogów pliku nadrzędnego, a następnie przechodzi przez katalogi plików nadrzędnych wobec niego. Tym samym wyszukiwanie rozpoczyna się względem katalogu zawierającego plik źródłowy w danej chwili przetwarzany. Jeśli plik pokolenia nie istnieje, a plik nie został znaleziony, wyszukiwanie jest kontynuowane tak, jakby nazwa pliku została ujęta w nawiasy ostre.

## <a name="see-also"></a>Zobacz też

[Dyrektywy przetwarzania wstępnego](../c-language/preprocessing-directives.md)