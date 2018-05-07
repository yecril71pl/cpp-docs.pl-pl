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
ms.openlocfilehash: 5256f787534ab408920f7154122ae0c5934019c1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="tn032-mfc-exception-mechanism"></a>TN032: mechanizm wyjątków MFC
Poprzednie wersje programu Visual C++ nie obsługuje standardowe mechanizm wyjątków C++ i MFC udostępniona makra **TRY/CATCH/THROW** który użyto zamiast tego. Ta wersja programu Visual C++ w pełni obsługuje wyjątków języka C++. Ta uwaga objętych niektóre szczegóły implementacji zaawansowane makra poprzedniego tym jak automatycznie Oczyszczanie na podstawie stosu obiektów. Ponieważ wyjątki C++ obsługuje odwijanie domyślnie stosu, ta uwaga techniczna nie jest już konieczne.  
  
 Zapoznaj się [wyjątkami: za pomocą makr MFC i wyjątków języka C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) Aby uzyskać więcej informacji na temat różnic między makr MFC i nowych słów kluczowych języka C++.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

