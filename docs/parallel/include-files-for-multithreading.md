---
title: Uwzględnianie plików na potrzeby wielowątkowości | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 73444c72878073d881abec08c474eb1f1ce64f02
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2018
ms.locfileid: "42466417"
---
# <a name="include-files-for-multithreading"></a>Uwzględnianie plików na potrzeby wielowątkowości
Standardowe pliki nagłówkowe zadeklarować funkcji biblioteki wykonawczej języka C zaimplementowanego w bibliotekach. Jeśli używasz [Pełna optymalizacja](../build/reference/ox-full-optimization.md) (/ Ox) lub [fastcall konwencji wywoływania](../build/reference/gd-gr-gv-gz-calling-convention.md) (/ Gr) opcja, kompilator zakłada, że wszystkie funkcje powinna być wywoływana za pomocą rejestru konwencji wywoływania. Funkcje bibliotek wykonawczych zostały skompilowane przy użyciu konwencji wywoływania C i deklaracji w standardowych plikach dołączanych nakazuje kompilatorowi Generowanie poprawne odwołania zewnętrzne tych funkcji.  
  
## <a name="see-also"></a>Zobacz też  

[Wielowątkowość z językiem C i podsystemem Win32](../parallel/multithreading-with-c-and-win32.md)