---
title: Połączenie wewnętrzne
ms.date: 11/04/2016
helpviewer_keywords:
- internal linkage
- linkage [C++], internal
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
ms.openlocfilehash: 79601af27f847a3afe7e8bdaefa926cd45459847
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325926"
---
# <a name="internal-linkage"></a>Połączenie wewnętrzne

Jeśli deklaracja identyfikatora zakresu plików dla obiektu lub funkcji zawiera **statyczny** *specyfikator klasy Storage* , identyfikator ma połączenie wewnętrzne. W przeciwnym razie identyfikator ma powiązania zewnętrzne. Zobacz [klasy magazynu](../c-language/c-storage-classes.md) , aby zapoznać się z omówieniem nieterminalu *specyfikatora klasy Storage* .

W jednej jednostce translacji każde wystąpienie identyfikatora z wewnętrznym powiązaniem oznacza ten sam identyfikator lub funkcję. Wewnętrznie połączone identyfikatory są unikatowe dla jednostki tłumaczenia.

## <a name="see-also"></a>Zobacz też

[Użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md)
