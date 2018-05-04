---
title: Rzutowanie liczb całkowitych na wartości zmiennoprzecinkowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- integers, casting to floating-point values
ms.assetid: 81fd5b7d-15eb-4c11-a8c8-e1621ff54fd3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e00fdfc44c5939dbed2fb3258f0cab0023feeda0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="casting-integers-to-floating-point-values"></a>Rzutowanie liczb całkowitych na wartości zmiennoprzecinkowe
**ANSI 3.2.1.3** kierunek obcięcie po przekonwertowaniu do liczby zmiennoprzecinkowej, która nie może reprezentować dokładnie oryginalnej wartości liczbą całkowitą  
  
 Gdy liczbą całkowitą jest rzutowane na wartości zmiennoprzecinkowej nie można reprezentować dokładnie wartości, wartość jest zaokrąglana (w górę lub w dół) do najbliższej odpowiednią wartość.  
  
 Na przykład rzutowanie **unsigned long** (z 32-bitowy precyzji) do **float** (których mantysa ma 23 bity precyzji) Zaokrągla liczbę do najbliższej wielokrotności 256. **Długi** 4,294,966,913 do 4,294,967,167 wartości są zaokrąglane do **float** wartość 4,294,967,040.  
  
## <a name="see-also"></a>Zobacz też  
 [Obliczenia matematyczne na liczbach zmiennoprzecinkowych](../c-language/floating-point-math.md)