---
title: Połączenie wewnętrzne
ms.date: 11/04/2016
helpviewer_keywords:
- internal linkage
- linkage [C++], internal
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
ms.openlocfilehash: 3709ca815877b98fe5dfe6e5b2eca6b5c627641b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229600"
---
# <a name="internal-linkage"></a>Połączenie wewnętrzne

Jeśli deklaracja identyfikatora zakresu plików dla obiektu lub funkcji zawiera *specyfikator klasy magazynu* **`static`** , identyfikator ma wewnętrzny związek... W przeciwnym razie identyfikator ma powiązania zewnętrzne. Zobacz [klasy magazynu](../c-language/c-storage-classes.md) , aby zapoznać się z omówieniem nieterminalu *specyfikatora klasy Storage* .

W jednej jednostce translacji każde wystąpienie identyfikatora z wewnętrznym powiązaniem oznacza ten sam identyfikator lub funkcję. Wewnętrznie połączone identyfikatory są unikatowe dla jednostki tłumaczenia.

## <a name="see-also"></a>Zobacz także

[Użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md)
