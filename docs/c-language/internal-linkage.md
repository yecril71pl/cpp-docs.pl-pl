---
title: Połączenie wewnętrzne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- internal linkage
- linkage [C++], internal
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 09b5a02b7892bff0233e37bbd63020a4d2904ec3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094211"
---
# <a name="internal-linkage"></a>Połączenie wewnętrzne

Jeśli zawiera deklaracji z zakresem pliku identyfikator obiektu lub funkcji *storage-class-specifier* **statyczne**, identyfikator ma powiązania wewnętrznego. W przeciwnym razie identyfikator ma powiązania zewnętrzne. Zobacz [klasy magazynu](../c-language/c-storage-classes.md) dyskusję na temat *storage-class-specifier* nieterminalnych.

W ramach jednej jednostki translacji każde wystąpienie identyfikatora z wewnętrznym powiązaniem wskazuje ten sam identyfikator lub funkcji. Wewnętrznie połączone identyfikatory są unikatowe dla jednostki translacji.

## <a name="see-also"></a>Zobacz też

[Użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md)