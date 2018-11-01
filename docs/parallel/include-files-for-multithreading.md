---
title: Uwzględnianie plików na potrzeby wielowątkowości
ms.date: 11/04/2016
helpviewer_keywords:
- threading [C++], include files
- include files, multithreading
- multithreading [C++], include files
ms.assetid: 98d764f9-71f4-4da5-8f3a-8d2d26e96799
ms.openlocfilehash: cf7a5ff7e42ffbcf57027014411e089722df16fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591935"
---
# <a name="include-files-for-multithreading"></a>Uwzględnianie plików na potrzeby wielowątkowości

Standardowe pliki nagłówkowe zadeklarować funkcji biblioteki wykonawczej języka C zaimplementowanego w bibliotekach. Jeśli używasz [Pełna optymalizacja](../build/reference/ox-full-optimization.md) (/ Ox) lub [fastcall konwencji wywoływania](../build/reference/gd-gr-gv-gz-calling-convention.md) (/ Gr) opcja, kompilator zakłada, że wszystkie funkcje powinna być wywoływana za pomocą rejestru konwencji wywoływania. Funkcje bibliotek wykonawczych zostały skompilowane przy użyciu konwencji wywoływania C i deklaracji w standardowych plikach dołączanych nakazuje kompilatorowi Generowanie poprawne odwołania zewnętrzne tych funkcji.

## <a name="see-also"></a>Zobacz też

[Wielowątkowość z językiem C i podsystemem Win32](multithreading-with-c-and-win32.md)