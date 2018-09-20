---
title: 'TN032: Mechanizm wyjątków MFC | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.exceptions
dev_langs:
- C++
helpviewer_keywords:
- TN032
- MFC, exceptions
- CException class [MFC], using
ms.assetid: 0271f0aa-82cb-47a2-b7ea-e88126fc7e43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aee8ce02af874e1c3c30243a35e8f36acfce63f0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414761"
---
# <a name="tn032-mfc-exception-mechanism"></a>TN032: mechanizm wyjątków MFC

Poprzednie wersje programu Visual C++ nie obsługuje standardowe mechanizmie wyjątków C++ i MFC podane makra **TRY/CATCH/THROW** , użyto zamiast tego. Ta wersja programu Visual C++ w pełni obsługuje wyjątki C++. Ta uwaga objętych usługą, niektóre szczegóły implementacji zaawansowanej poprzedniego makra w tym sposobu automatycznego oczyszczania stosu na podstawie obiektów. Ponieważ wyjątki C++ obsługuje odwijanie domyślnie stosu, ta uwaga techniczna nie jest już konieczne.

Zapoznaj się [wyjątki: wykorzystanie makr MFC i wyjątków języka C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) Aby uzyskać więcej informacji na temat różnic między makr MFC i nowych słów kluczowych języka C++.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

