---
title: Błąd kompilatora C3888
ms.date: 11/04/2016
f1_keywords:
- C3888
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
ms.openlocfilehash: e4d52946126e7be6c6f2aef34b5eb5a93a0babad
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033644"
---
# <a name="compiler-error-c3888"></a>Błąd kompilatora C3888

"name": wyrażenie const powiązane z tym literałem składowej danych nie jest obsługiwana przez C++sposób niezamierzony

*Nazwa* składowej danych, która jest zadeklarowana za pomocą [literału](../../extensions/literal-cpp-component-extensions.md) — słowo kluczowe jest inicjowany z wartością, kompilator nie obsługuje. Kompilator obsługuje tylko stałe całkowite, enum lub typu ciągu. Prawdopodobną przyczyną **C3888** błąd to, że element członkowski danych jest inicjowany z tablicy typu byte.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Sprawdź, czy zadeklarowane literał składowej danych jest nieobsługiwany.

## <a name="see-also"></a>Zobacz także

[literal](../../extensions/literal-cpp-component-extensions.md)