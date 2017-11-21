---
title: "Rzutowanie liczb całkowitych na wartości zmiennoprzecinkowe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: integers, casting to floating-point values
ms.assetid: 81fd5b7d-15eb-4c11-a8c8-e1621ff54fd3
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0c91c9533baec350ba66ae1ab4db472c0ea8bcdf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="casting-integers-to-floating-point-values"></a>Rzutowanie liczb całkowitych na wartości zmiennoprzecinkowe
**ANSI 3.2.1.3** kierunek obcięcie po przekonwertowaniu do liczby zmiennoprzecinkowej, która nie może reprezentować dokładnie oryginalnej wartości liczbą całkowitą  
  
 Gdy liczbą całkowitą jest rzutowane na wartości zmiennoprzecinkowej nie można reprezentować dokładnie wartości, wartość jest zaokrąglana (w górę lub w dół) do najbliższej odpowiednią wartość.  
  
 Na przykład rzutowanie **unsigned long** (z 32-bitowy precyzji) do **float** (których mantysa ma 23 bity precyzji) Zaokrągla liczbę do najbliższej wielokrotności 256. **Długi** 4,294,966,913 do 4,294,967,167 wartości są zaokrąglane do **float** wartość 4,294,967,040.  
  
## <a name="see-also"></a>Zobacz też  
 [Zmiennoprzecinkowej matematyczny](../c-language/floating-point-math.md)