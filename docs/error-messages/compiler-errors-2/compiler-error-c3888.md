---
title: Błąd kompilatora C3888
ms.date: 11/04/2016
f1_keywords:
- C3888
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
ms.openlocfilehash: 20251292ec4635ea855a56890878bc55f567ab62
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58777470"
---
# <a name="compiler-error-c3888"></a>Błąd kompilatora C3888

"name": wyrażenie const powiązane z tym literałem składowej danych nie jest obsługiwana przez C + +/ CLI

*Nazwa* składowej danych, która jest zadeklarowana za pomocą [literału](../../extensions/literal-cpp-component-extensions.md) — słowo kluczowe jest inicjowany z wartością, kompilator nie obsługuje. Kompilator obsługuje tylko stałe całkowite, enum lub typu ciągu. Prawdopodobną przyczyną **C3888** błąd to, że element członkowski danych jest inicjowany z tablicy typu byte.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Sprawdź, czy zadeklarowane literał składowej danych jest nieobsługiwany.

## <a name="see-also"></a>Zobacz też

[literał](../../extensions/literal-cpp-component-extensions.md)