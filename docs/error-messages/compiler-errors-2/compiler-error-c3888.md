---
title: Błąd kompilatora C3888
ms.date: 11/04/2016
f1_keywords:
- C3888
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
ms.openlocfilehash: 40156dfaad5965d30a32d3aa2ac574a5f91999ba
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176407"
---
# <a name="compiler-error-c3888"></a>Błąd kompilatora C3888

"name": wyrażenie const skojarzone z tym literałem składowej danych nie jest obsługiwane C++przez/CLI

*Nazwa* elementu członkowskiego danych zadeklarowanego za pomocą słowa kluczowego [Literal](../../extensions/literal-cpp-component-extensions.md) jest inicjowana z wartością, której kompilator nie obsługuje. Kompilator obsługuje tylko stałe typy całkowite, wyliczenia lub String. Najprawdopodobniej przyczyną błędu **C3888** jest zainicjowanie składowej danych z tablicą bajtów.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Sprawdź, czy zadeklarowany element członkowski danych jest obsługiwany.

## <a name="see-also"></a>Zobacz też

[literal](../../extensions/literal-cpp-component-extensions.md)
