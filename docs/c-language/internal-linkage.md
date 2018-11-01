---
title: Połączenie wewnętrzne
ms.date: 11/04/2016
helpviewer_keywords:
- internal linkage
- linkage [C++], internal
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
ms.openlocfilehash: 857badd1284378a066c6c19c7159c1535e313593
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452369"
---
# <a name="internal-linkage"></a>Połączenie wewnętrzne

Jeśli zawiera deklaracji z zakresem pliku identyfikator obiektu lub funkcji *storage-class-specifier* **statyczne**, identyfikator ma powiązania wewnętrznego. W przeciwnym razie identyfikator ma powiązania zewnętrzne. Zobacz [klasy magazynu](../c-language/c-storage-classes.md) dyskusję na temat *storage-class-specifier* nieterminalnych.

W ramach jednej jednostki translacji każde wystąpienie identyfikatora z wewnętrznym powiązaniem wskazuje ten sam identyfikator lub funkcji. Wewnętrznie połączone identyfikatory są unikatowe dla jednostki translacji.

## <a name="see-also"></a>Zobacz też

[Użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md)