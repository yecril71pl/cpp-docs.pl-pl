---
title: "Konwersje z typów zmiennoprzecinkowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/29/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- converting floating point
- floating-point conversion
ms.assetid: 96804c8e-fa3b-4742-9006-0082ed9e57f2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 80e84ba9a78f78fd93d7bd7fedbcbfaf168a7ec2
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2018
---
# <a name="conversions-from-floating-point-types"></a>Konwersje z typów zmiennoprzecinkowych

A **float** konwertowane na wartość **podwójne** lub **podwójnej długości**, lub **podwójne** przekonwertować **liczba typu double**, ulega ma zmiany w wartości. A **podwójne** konwertowane na wartość **float** wartość jest reprezentowany dokładnie, jeśli to możliwe. Dokładność mogą zostać utracone, jeśli wartość nie może być reprezentowany dokładnie. Jeśli wynik jest poza zakresem, zachowanie jest niezdefiniowany. Zobacz [limity dla stałych Floating-Point](../c-language/limits-on-floating-point-constants.md) dla typów zmiennoprzecinkowych.

Wartość zmiennoprzecinkowa jest konwertowana na wartością całkowitą, konwertując pierwszy **długi**, następnie z **długi** wartość określoną wartość całkowitą. Część zmiennej wartości zostaną odrzucone podczas konwersji do **długi**. Jeśli wynik nadal jest zbyt duży, aby zmieścić w **długi**, wynik konwersji jest niezdefiniowany.

**Microsoft Specific**

Podczas konwertowania **podwójne** lub **podwójnej długości** liczba zmiennoprzecinkowa do mniejsza liczba zmiennoprzecinkowa, wartość zmiennej liczb zmiennoprzecinkowych zostały obcięte kierunku zera po wystąpieniu niedopełnienie. Przepełnienie powoduje błąd w czasie wykonywania. Należy pamiętać, że kompilator Microsoft C mapuje **podwójnej długości** na typ **podwójne**.

**KOŃCOWY określonych firmy Microsoft**

Poniższa tabela zawiera podsumowanie konwersje z typów zmiennoprzecinkowych.

## <a name="conversions-from-floating-point-types"></a>Konwersje z typów zmiennoprzecinkowych

|Z|Do|Metoda|
|----------|--------|------------|
|**float**|**char**|Konwertuj na **długi**; przekonwertować **długi** do **char**|
|**float**|**short**|Konwertuj na **długi**; przekonwertować **długi** do **krótki**|
|**float**|**long**|Obciąć po punkcie dziesiętnym. Jeśli wynik jest za duży, może być reprezentowana jako **długi**, wynikiem jest niezdefiniowany.|
|**float**|**short bez znaku**|Konwertuj na **długi**; przekonwertować **długi** do **krótko bez znaku**|
|**float**|**unsigned long**|Konwertuj na **długi**; przekonwertować **długi** do **unsigned long**|
|**float**|**double**|Zmień reprezentacji wewnętrznej|
|**float**|**Liczba typu double**|Zmień reprezentacji wewnętrznej|
|**double**|**char**|Konwertuj na **float**; przekonwertować **float** do **char**|
|**double**|**short**|Konwertuj na **float**; przekonwertować **float** do **krótki**|
|**double**|**long**|Obciąć po punkcie dziesiętnym. Jeśli wynik jest za duży, może być reprezentowana jako **długi**, wynikiem jest niezdefiniowany.|
|**double**|**short bez znaku**|Konwertuj na **długi**; przekonwertować **długi** do **krótko bez znaku**|
|**double**|**unsigned long**|Konwertuj na **długi**; przekonwertować **długi** do **unsigned long**|
|**double**|**float**|Reprezentuje jako **float**. Jeśli **podwójne** wartość nie może być reprezentowany dokładnie jako **float**, utrata dokładności. Jeśli wartość jest za duży, może być reprezentowana jako **float**, wynikiem jest niezdefiniowany.|
|**Liczba typu double**|**char**|Konwertuj na **float**; przekonwertować **float** do **char**|
|**Liczba typu double**|**short**|Konwertuj na **float**; przekonwertować **float** do **krótki**|
|**Liczba typu double**|**long**|Obciąć po punkcie dziesiętnym. Jeśli wynik jest za duży, może być reprezentowana jako **długi**, wynikiem jest niezdefiniowany.|
|**Liczba typu double**|**short bez znaku**|Konwertuj na **długi**; przekonwertować **długi** do **krótko bez znaku**|
|**Liczba typu double**|**unsigned long**|Konwertuj na **długi**; przekonwertować **długi** do **unsigned long**|
|**Liczba typu double**|**float**|Reprezentuje jako **float**. Jeśli **podwójne** wartość nie może być reprezentowany dokładnie jako **float**, utrata dokładności. Jeśli wartość jest za duży, może być reprezentowana jako **float**, wynikiem jest niezdefiniowany.|
|**Liczba typu double**|**double**|**Podwójnej długości** wartość jest traktowana jako **podwójne**.|

Konwersje z **float**, **podwójne**, lub **podwójnej długości** wartości do **unsigned long** nie są dokładne, jeśli wartość konwertowanej jest większa niż maksymalna dodatnich **długi** wartość.

## <a name="see-also"></a>Zobacz także

[Konwersje przypisań](../c-language/assignment-conversions.md)  
