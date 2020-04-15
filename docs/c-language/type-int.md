---
title: Typ int
ms.date: 11/04/2016
helpviewer_keywords:
- int data type
- type int
- portability [C++], type int
- signed integers
ms.assetid: 0067ce9a-281e-491a-ae63-632952981e13
ms.openlocfilehash: ebce276c8c4efa822601fe36652057b37e922570
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334437"
---
# <a name="type-int"></a>Typ int

Rozmiar oznaczonego lub nieoznaczonego elementu `int` jest standardowym rozmiarem liczby całkowitej na danym komputerze. Na przykład w 16-bitowych systemach operacyjnych, typ `int` ma zazwyczaj 16 bitów lub 2 bajty. W 32-bitowych systemach operacyjnych, typ `int` ma zazwyczaj 32 bity lub 4 bajty. W związku `int` z tym typ `short int` jest odpowiednikiem typu long `unsigned int` int lub **long,** a typ jest `unsigned long` odpowiednikiem **niepodpisanego krótkiego** lub typu, w zależności od środowiska docelowego. Wszystkie typy `int` reprezentują wartości oznaczone, chyba że określono inaczej.

Specyfikatory typu `int` i `unsigned int` (lub po prostu `unsigned`) definiują pewne funkcje języka C (na przykład typ `enum`). W tych przypadkach definicje `int` i unsigned int dla określonej implementacji określają rzeczywistą pamięć.

**Specyficzne dla firmy Microsoft**

Oznaczone liczby całkowite są zapisywane w kodzie dopełnień do dwóch. Najbardziej znaczący bit utrzymuje znak: 1 dla wartości ujemnych, 0 dla wartości dodatnich i zera. Zakres wartości jest podany w [C i C++ Limity liczby całkowitej](../c-language/cpp-integer-limits.md), który jest pobierany z limitów. H.

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

> [!NOTE]
> Specyfikatory typu int i unsigned int są szeroko używane w programach języka C, ponieważ umożliwiają obsługę wartości całkowitych przez komputer w najbardziej efektywny sposób. Jednak ponieważ rozmiar int i unsigned int może być różny, programy zależące od konkretnego rozmiaru int mogą nie być przenoszone na inne komputery. Aby programy były bardziej przenośne, można użyć wyrażeń z operatorem sizeof (jak omówiono w [the sizeof Operator](../c-language/sizeof-operator-c.md)) zamiast zakodowanych rozmiarów danych.

## <a name="see-also"></a>Zobacz też

[Magazyn typów podstawowych](../c-language/storage-of-basic-types.md)
