---
title: Błąd krytyczny C1002
ms.date: 11/04/2016
f1_keywords:
- C1002
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
ms.openlocfilehash: 0588da99994be547742cc530ba435002a2d73359
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640508"
---
# <a name="fatal-error-c1002"></a>Błąd krytyczny C1002

Kompilator nie ma miejsca na stercie w przebiegu 2

Kompilator za mało miejsca w pamięci dynamicznej podczas jego drugi — dostęp próbny, prawdopodobnie z powodu program o zbyt wiele symboli lub złożonych wyrażeń.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem, korzystając z poniższymi możliwymi rozwiązaniami

1. Dzielenie pliku źródłowego na kilka mniejszych plików.

1. Podziel wyrażenia na mniejsze podwyrażenia.

1. Usuń inne programy i sterowniki, których wartość użycia pamięci.