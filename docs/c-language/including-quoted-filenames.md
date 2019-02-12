---
title: Łącznie z nazwami plików w cudzysłowie
ms.date: 11/04/2016
ms.assetid: 789a047e-ea38-4c99-b71d-a2ad9c81daee
ms.openlocfilehash: 4083519d6f6b9b4d037b0c2998737f3a5062c6cf
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149872"
---
# <a name="including-quoted-filenames"></a>Łącznie z nazwami plików w cudzysłowie

**ANSI 3.8.2** obsługę nazw pliki źródłowe do zawarcia w cudzysłowie

Jeśli określisz pełną, jednoznaczną specyfikację ścieżki do dołączanego pliku między dwoma zestawami podwójnego cudzysłowu (""), preprocesor przeszukuje tylko tę specyfikację ścieżki i ignoruje katalogi standardowe.

Dla plików dołączanych określonych jako [#include](../preprocessor/hash-include-directive-c-cpp.md) "path-spec", katalog wyszukiwanie rozpoczyna się od katalogów pliku nadrzędnego, a następnie przechodzi przez katalogi plików nadrzędnych wobec niego. Tym samym wyszukiwanie rozpoczyna się względem katalogu zawierającego plik źródłowy w danej chwili przetwarzany. Jeśli plik pokolenia nie istnieje, a plik nie został znaleziony, wyszukiwanie jest kontynuowane tak, jakby nazwa pliku została ujęta w nawiasy ostre.

## <a name="see-also"></a>Zobacz także

[Dyrektywy przetwarzania wstępnego](../c-language/preprocessing-directives.md)
