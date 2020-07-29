---
title: Typ int
ms.date: 11/04/2016
helpviewer_keywords:
- int data type
- type int
- portability [C++], type int
- signed integers
ms.assetid: 0067ce9a-281e-491a-ae63-632952981e13
ms.openlocfilehash: 2bfd9e108b36f073635c6d9e55e2299764dcb309
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87198869"
---
# <a name="type-int"></a>Typ int

Rozmiar **`signed int`** lub **`unsigned int`** element jest standardowym rozmiarem liczby całkowitej na określonym komputerze. Na przykład w 16-bitowych systemach operacyjnych **`int`** Typ ma zwykle 16 bitów lub 2 bajty. W 32-bitowych systemach operacyjnych **`int`** Typ jest zazwyczaj 32 bitów lub 4 bajty. W tym celu **`int`** Typ jest odpowiednikiem albo **`short int`** **`long int`** typu, a **`unsigned int`** Typ jest odpowiednikiem albo **`unsigned short`** **`unsigned long`** typu, w zależności od środowiska docelowego. **`int`** Wszystkie typy reprezentują wartości podpisane, chyba że określono inaczej.

Specyfikatory typu **`int`** i **`unsigned int`** (lub po prostu **`unsigned`** ) definiują niektóre funkcje języka C (na przykład **`enum`** Typ). W takich przypadkach definicje **`int`** i **`unsigned int`** dla konkretnej implementacji określają faktyczny magazyn.

**Specyficzne dla firmy Microsoft**

Oznaczone liczby całkowite są zapisywane w kodzie dopełnień do dwóch. Najbardziej znaczący bit utrzymuje znak: 1 dla wartości ujemnych, 0 dla wartości dodatnich i zera. Zakres wartości jest wyrażony w [limitach liczb całkowitych C i C++](../c-language/cpp-integer-limits.md), które są pobierane z limitów. H plik nagłówkowy.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

> [!NOTE]
> **`int`** **`unsigned int`** Specyfikatory typu i są szeroko stosowane w programach języka C, ponieważ umożliwiają konkretnemu komputerowi obsługę wartości całkowitych w najbardziej efektywny sposób dla tej maszyny. Jednak ponieważ rozmiary **`int`** i **`unsigned int`** są różne, programy, które są zależne od określonego **`int`** rozmiaru mogą nie być przenośne na innych maszynach. Aby programy były bardziej przenośne, można użyć wyrażeń z **`sizeof`** operatorem (jak to opisano w [ `sizeof` operatorze](../c-language/sizeof-operator-c.md)) zamiast zakodowanych rozmiarów danych.

## <a name="see-also"></a>Zobacz także

[Magazyn typów podstawowych](../c-language/storage-of-basic-types.md)
