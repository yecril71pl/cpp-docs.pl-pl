---
title: Błąd kompilatora C3888 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3888
dev_langs:
- C++
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9292f54fee467a5f8d01202b6ed7ca991b52d43
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096463"
---
# <a name="compiler-error-c3888"></a>Błąd kompilatora C3888

"name": wyrażenie const powiązane z tym literałem składowej danych nie jest obsługiwana przez C + +/ CLI

*Nazwa* składowej danych, która jest zadeklarowana za pomocą [literału](../../windows/literal-cpp-component-extensions.md) — słowo kluczowe jest inicjowany z wartością, kompilator nie obsługuje. Kompilator obsługuje tylko stałe całkowite, enum lub typu ciągu. Prawdopodobną przyczyną **C3888** błąd to, że element członkowski danych jest inicjowany z tablicy typu byte.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Sprawdź, czy zadeklarowane literał składowej danych jest nieobsługiwany.

## <a name="see-also"></a>Zobacz też

[literał](../../windows/literal-cpp-component-extensions.md)