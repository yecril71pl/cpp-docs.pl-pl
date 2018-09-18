---
title: Błąd krytyczny C1002 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1002
dev_langs:
- C++
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82f08255484b11f9f5d87fb67ac8ac7b401d4f6e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044148"
---
# <a name="fatal-error-c1002"></a>Błąd krytyczny C1002

Kompilator nie ma miejsca na stercie w przebiegu 2

Kompilator za mało miejsca w pamięci dynamicznej podczas jego drugi — dostęp próbny, prawdopodobnie z powodu program o zbyt wiele symboli lub złożonych wyrażeń.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem, korzystając z poniższymi możliwymi rozwiązaniami

1. Dzielenie pliku źródłowego na kilka mniejszych plików.

1. Podziel wyrażenia na mniejsze podwyrażenia.

1. Usuń inne programy i sterowniki, których wartość użycia pamięci.