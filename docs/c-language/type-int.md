---
title: Typ int
ms.date: 11/04/2016
helpviewer_keywords:
- int data type
- type int
- portability [C++], type int
- signed integers
ms.assetid: 0067ce9a-281e-491a-ae63-632952981e13
ms.openlocfilehash: c69d2308abe2ee3d7e6b392f5a9e78a004791501
ms.sourcegitcommit: ea9d78dbb93bf3f8841dde93dbc12bd66f6f32ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72778358"
---
# <a name="type-int"></a>Typ int

Rozmiar oznaczonego lub nieoznaczonego elementu `int` jest standardowym rozmiarem liczby całkowitej na danym komputerze. Na przykład w 16-bitowych systemach operacyjnych, typ `int` ma zazwyczaj 16 bitów lub 2 bajty. W 32-bitowych systemach operacyjnych, typ `int` ma zazwyczaj 32 bity lub 4 bajty. W tym celu typ `int` jest równoważny `short int` lub **długiej wartości int** , a typ `unsigned int` jest odpowiednikiem typu **unsigned Short** lub `unsigned long`, w zależności od środowiska docelowego. Wszystkie typy `int` reprezentują wartości oznaczone, chyba że określono inaczej.

Specyfikatory typu `int` i `unsigned int` (lub po prostu `unsigned`) definiują pewne funkcje języka C (na przykład typ `enum`). W tych przypadkach definicje `int` i unsigned int dla określonej implementacji określają rzeczywistą pamięć.

**Specyficzne dla firmy Microsoft**

Oznaczone liczby całkowite są zapisywane w kodzie dopełnień do dwóch. Najbardziej znaczący bit utrzymuje znak: 1 dla wartości ujemnych, 0 dla wartości dodatnich i zera. Zakres wartości jest podawany w [limitach C C++ i Integer](../c-language/cpp-integer-limits.md), które są pobierane z limitów. H plik nagłówkowy.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

> [!NOTE]
>  Specyfikatory typu int i unsigned int są szeroko używane w programach języka C, ponieważ umożliwiają obsługę wartości całkowitych przez komputer w najbardziej efektywny sposób. Jednak ponieważ rozmiar int i unsigned int może być różny, programy zależące od konkretnego rozmiaru int mogą nie być przenoszone na inne komputery. Aby programy były bardziej przenośne, można użyć wyrażeń z operatorem sizeof (jak to opisano w [operatorze sizeof](../c-language/sizeof-operator-c.md)) zamiast zakodowanych rozmiarów danych.

## <a name="see-also"></a>Zobacz także

[Magazyn typów podstawowych](../c-language/storage-of-basic-types.md)
