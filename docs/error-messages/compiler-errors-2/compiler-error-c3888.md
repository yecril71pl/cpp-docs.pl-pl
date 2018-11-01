---
title: Błąd kompilatora C3888
ms.date: 11/04/2016
f1_keywords:
- C3888
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
ms.openlocfilehash: 067412e59041cb98b68cb373c4671c243ab8a0ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479069"
---
# <a name="compiler-error-c3888"></a>Błąd kompilatora C3888

"name": wyrażenie const powiązane z tym literałem składowej danych nie jest obsługiwana przez C + +/ CLI

*Nazwa* składowej danych, która jest zadeklarowana za pomocą [literału](../../windows/literal-cpp-component-extensions.md) — słowo kluczowe jest inicjowany z wartością, kompilator nie obsługuje. Kompilator obsługuje tylko stałe całkowite, enum lub typu ciągu. Prawdopodobną przyczyną **C3888** błąd to, że element członkowski danych jest inicjowany z tablicy typu byte.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Sprawdź, czy zadeklarowane literał składowej danych jest nieobsługiwany.

## <a name="see-also"></a>Zobacz też

[literał](../../windows/literal-cpp-component-extensions.md)