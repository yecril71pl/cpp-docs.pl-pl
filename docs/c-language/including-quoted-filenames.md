---
title: Nazwy plików w tym w cudzysłowach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 789a047e-ea38-4c99-b71d-a2ad9c81daee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d3e865df95d92dcad6b414da11677b5212e9a9f3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109941"
---
# <a name="including-quoted-filenames"></a>Łącznie z nazwami plików w cudzysłowie

**ANSI 3.8.2** obsługę nazw pliki źródłowe do zawarcia w cudzysłowie

Jeśli określisz pełną, jednoznaczną specyfikację ścieżki do dołączanego pliku między dwoma zestawami podwójnego cudzysłowu (""), preprocesor przeszukuje tylko tę specyfikację ścieżki i ignoruje katalogi standardowe.

Dla plików dołączanych określonych jako [#include](../preprocessor/hash-include-directive-c-cpp.md) "path-spec", katalog wyszukiwanie rozpoczyna się od katalogów pliku nadrzędnego, a następnie przechodzi przez katalogi plików nadrzędnych wobec niego. Tym samym wyszukiwanie rozpoczyna się względem katalogu zawierającego plik źródłowy w danej chwili przetwarzany. Jeśli plik pokolenia nie istnieje, a plik nie został znaleziony, wyszukiwanie jest kontynuowane tak, jakby nazwa pliku została ujęta w nawiasy ostre.

## <a name="see-also"></a>Zobacz też

[Dyrektywy przetwarzania wstępnego](../c-language/preprocessing-directives.md)