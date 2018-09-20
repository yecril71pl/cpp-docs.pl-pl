---
title: Klasy debugowania i wyjątków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.debug
dev_langs:
- C++
helpviewer_keywords:
- debugging [MFC], exception classes
- debugging [MFC], classes for debugging
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b7c88c5d12f56318bbb37a825e28c2bfcbc132d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418180"
---
# <a name="debugging-and-exception-classes"></a>Klasy debugowania i wyjątków

Te klasy zapewniają obsługę dynamicznej alokacji pamięci debugowania i do przekazywania informacji wyjątku przez funkcję, gdzie wyjątek jest zgłaszany do funkcji, gdzie zostanie przechwycony.

Używanie klas [CDumpContext](../mfc/reference/cdumpcontext-class.md) i [CMemoryState](../mfc/reference/cmemorystate-structure.md) podczas programowania, która pomaga w debugowaniu, zgodnie z opisem w [debugowania aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques). Użyj [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) można określić klasę dowolnego obiektu w czasie wykonywania, zgodnie z opisem w artykule [uzyskiwania dostępu do środowiska wykonawczego informacji o klasie](../mfc/accessing-run-time-class-information.md). Środowisko wykorzystuje `CRuntimeClass` dynamicznie utworzyć obiekty określonej klasy.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../mfc/class-library-overview.md)

