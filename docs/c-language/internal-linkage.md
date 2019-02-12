---
title: Połączenie wewnętrzne
ms.date: 11/04/2016
helpviewer_keywords:
- internal linkage
- linkage [C++], internal
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
ms.openlocfilehash: 79601af27f847a3afe7e8bdaefa926cd45459847
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150743"
---
# <a name="internal-linkage"></a>Połączenie wewnętrzne

Jeśli zawiera deklaracji z zakresem pliku identyfikator obiektu lub funkcji *storage-class-specifier* **statyczne**, identyfikator ma powiązania wewnętrznego. W przeciwnym razie identyfikator ma powiązania zewnętrzne. Zobacz [klasy magazynu](../c-language/c-storage-classes.md) dyskusję na temat *storage-class-specifier* nieterminalnych.

W ramach jednej jednostki translacji każde wystąpienie identyfikatora z wewnętrznym powiązaniem wskazuje ten sam identyfikator lub funkcji. Wewnętrznie połączone identyfikatory są unikatowe dla jednostki translacji.

## <a name="see-also"></a>Zobacz także

[Użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md)
