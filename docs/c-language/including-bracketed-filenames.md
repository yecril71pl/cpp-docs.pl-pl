---
title: Łącznie z nazwami plików w nawiasach kwadratowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 6a4e5411-c35e-48b8-90ef-b37ac324ed94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 37b4d0e6ccf0c0c01671082d2596528632fba6cb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100867"
---
# <a name="including-bracketed-filenames"></a>Łącznie z nazwami plików w nawiasach

**ANSI 3.8.2** metody lokalizowania pliki źródłowe do zawarcia

Specyfikacji pliku ujęta w nawiasy ostre preprocesor nie wyszukiwania katalogów pliku nadrzędnego. Plik "nadrzędny" znajduje się plik, który ma [#include](../preprocessor/hash-include-directive-c-cpp.md) dyrektywy w nim. Zamiast tego należy go rozpoczyna się od wyszukiwania pliku w określonym następującego wiersza polecenia kompilatora / I. Jeśli opcja /I nie istnieje lub nie powiedzie się, preprocesor wykorzysta zmienną środowiskową INCLUDE, aby znaleźć wszystkie pliki dołączane w nawiasach kątowych. Zmienna środowiskowa INCLUDE może zawierać wiele ścieżek oddzielonych średnikami (**;**). Jeśli więcej niż jeden katalog pojawia się jako część opcji /I lub w ramach zmienną środowiskową INCLUDE, preprocesor przeszukuje je w kolejności, w jakiej są wyświetlane.

## <a name="see-also"></a>Zobacz też

[Dyrektywy przetwarzania wstępnego](../c-language/preprocessing-directives.md)