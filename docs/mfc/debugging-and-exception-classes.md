---
title: Klasy debugowania i wyjątków
ms.date: 11/04/2016
f1_keywords:
- vc.classes.debug
helpviewer_keywords:
- debugging [MFC], exception classes
- debugging [MFC], classes for debugging
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
ms.openlocfilehash: 5549ea3e67f06e82e441c1ca5afc4a1b859dd410
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587979"
---
# <a name="debugging-and-exception-classes"></a>Klasy debugowania i wyjątków

Te klasy zapewniają obsługę dynamicznej alokacji pamięci debugowania i do przekazywania informacji wyjątku przez funkcję, gdzie wyjątek jest zgłaszany do funkcji, gdzie zostanie przechwycony.

Używanie klas [CDumpContext](../mfc/reference/cdumpcontext-class.md) i [CMemoryState](../mfc/reference/cmemorystate-structure.md) podczas programowania, która pomaga w debugowaniu, zgodnie z opisem w [debugowania aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques). Użyj [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) można określić klasę dowolnego obiektu w czasie wykonywania, zgodnie z opisem w artykule [uzyskiwania dostępu do środowiska wykonawczego informacji o klasie](../mfc/accessing-run-time-class-information.md). Środowisko wykorzystuje `CRuntimeClass` dynamicznie utworzyć obiekty określonej klasy.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../mfc/class-library-overview.md)

