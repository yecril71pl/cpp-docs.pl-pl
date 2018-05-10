---
title: Dołącz pliki dla wielowątkowości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- threading [C++], include files
- include files, multithreading
- multithreading [C++], include files
ms.assetid: 98d764f9-71f4-4da5-8f3a-8d2d26e96799
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 62b94f4a7a394b78cb7c6f23275709e4aeacc774
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="include-files-for-multithreading"></a>Uwzględnianie plików na potrzeby wielowątkowości
Standardowe pliki nagłówkowe zadeklarować funkcji biblioteki wykonawczej języka C zaimplementowanego w bibliotekach. Jeśli używasz [Pełna optymalizacja](../build/reference/ox-full-optimization.md) (/ Ox) lub [fastcall konwencji wywoływania](../build/reference/gd-gr-gv-gz-calling-convention.md) (/ Gr) opcja, kompilator zakłada, że wszystkie funkcje powinna być wywoływana za pomocą rejestru konwencji wywoływania. Funkcje biblioteki wykonawczej zostały skompilowane przy użyciu konwencji wywoływania C i deklaracjami w pliki nagłówkowe standardowej nakazuje kompilatorowi Generowanie poprawne zewnętrznych odwołań do tych funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Wielowątkowość z językiem C i podsystemem Win32](../parallel/multithreading-with-c-and-win32.md)