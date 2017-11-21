---
title: "Dołącz pliki dla wielowątkowości | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- threading [C++], include files
- include files, multithreading
- multithreading [C++], include files
ms.assetid: 98d764f9-71f4-4da5-8f3a-8d2d26e96799
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bcc8282680588585335eaa2c876128d2c2cf23a3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="include-files-for-multithreading"></a>Uwzględnianie plików na potrzeby wielowątkowości
Standardowe pliki nagłówkowe zadeklarować funkcji biblioteki wykonawczej języka C zaimplementowanego w bibliotekach. Jeśli używasz [Pełna optymalizacja](../build/reference/ox-full-optimization.md) (/ Ox) lub [fastcall konwencji wywoływania](../build/reference/gd-gr-gv-gz-calling-convention.md) (/ Gr) opcja, kompilator zakłada, że wszystkie funkcje powinna być wywoływana za pomocą rejestru konwencji wywoływania. Funkcje biblioteki wykonawczej zostały skompilowane przy użyciu konwencji wywoływania C i deklaracjami w pliki nagłówkowe standardowej nakazuje kompilatorowi Generowanie poprawne zewnętrznych odwołań do tych funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Wielowątkowość z C i Win32](../parallel/multithreading-with-c-and-win32.md)