---
title: Połączenie wewnętrzne
ms.date: 11/04/2016
helpviewer_keywords:
- internal linkage
- linkage [C++], internal
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
ms.openlocfilehash: 2871ee68b7ae880d6ec5c33ea69eb1bfcc3e284c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509900"
---
# <a name="internal-linkage"></a>Połączenie wewnętrzne

Jeśli deklaracja identyfikatora zakresu plików dla obiektu lub funkcji zawiera *specyfikator klasy magazynu* **`static`** , identyfikator ma wewnętrzny związek... W przeciwnym razie identyfikator ma powiązania zewnętrzne. Zobacz [klasy magazynu](../c-language/c-storage-classes.md) , aby zapoznać się z omówieniem nieterminalu *specyfikatora klasy Storage* .

W jednej jednostce translacji każde wystąpienie identyfikatora z wewnętrznym powiązaniem oznacza ten sam identyfikator lub funkcję. Wewnętrznie połączone identyfikatory są unikatowe dla jednostki tłumaczenia.

## <a name="see-also"></a>Zobacz też

[Użycie zewnętrznie w celu określenia powiązania](../cpp/extern-cpp.md)
