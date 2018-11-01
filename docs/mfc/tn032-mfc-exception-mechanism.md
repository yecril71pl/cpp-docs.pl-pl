---
title: 'TN032: mechanizm wyjątków MFC'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.exceptions
helpviewer_keywords:
- TN032
- MFC, exceptions
- CException class [MFC], using
ms.assetid: 0271f0aa-82cb-47a2-b7ea-e88126fc7e43
ms.openlocfilehash: f3f13bb40151d3b9ef0d57c7e769ca30fa629177
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633397"
---
# <a name="tn032-mfc-exception-mechanism"></a>TN032: mechanizm wyjątków MFC

Poprzednie wersje programu Visual C++ nie obsługuje standardowe mechanizmie wyjątków C++ i MFC podane makra **TRY/CATCH/THROW** , użyto zamiast tego. Ta wersja programu Visual C++ w pełni obsługuje wyjątki C++. Ta uwaga objętych usługą, niektóre szczegóły implementacji zaawansowanej poprzedniego makra w tym sposobu automatycznego oczyszczania stosu na podstawie obiektów. Ponieważ wyjątki C++ obsługuje odwijanie domyślnie stosu, ta uwaga techniczna nie jest już konieczne.

Zapoznaj się [wyjątki: wykorzystanie makr MFC i wyjątków języka C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) Aby uzyskać więcej informacji na temat różnic między makr MFC i nowych słów kluczowych języka C++.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

