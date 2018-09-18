---
title: Int — typ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- int data type
- type int
- portability [C++], type int
- signed integers
ms.assetid: 0067ce9a-281e-491a-ae63-632952981e13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: da73fc26bb6afa6455ac569148ab06370a728948
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107747"
---
# <a name="type-int"></a>Typ int

Rozmiar oznaczonego lub nieoznaczonego elementu `int` jest standardowym rozmiarem liczby całkowitej na danym komputerze. Na przykład w 16-bitowych systemach operacyjnych, typ `int` ma zazwyczaj 16 bitów lub 2 bajty. W 32-bitowych systemach operacyjnych, typ `int` ma zazwyczaj 32 bity lub 4 bajty. W efekcie `int` jest równoważny z typem typu `short int` lub **long int** typu i `unsigned int` jest równoważny z typem typu **typ unsigned short** lub `unsigned long` Typ, w zależności od środowiska docelowego. Wszystkie typy `int` reprezentują wartości oznaczone, chyba że określono inaczej.

Specyfikatory typu `int` i `unsigned int` (lub po prostu `unsigned`) definiują pewne funkcje języka C (na przykład typ `enum`). W tych przypadkach definicje `int` i unsigned int dla określonej implementacji określają rzeczywistą pamięć.

**Microsoft Specific**

Oznaczone liczby całkowite są zapisywane w kodzie dopełnień do dwóch. Najbardziej znaczący bit utrzymuje znak: 1 dla wartości ujemnych, 0 dla wartości dodatnich i zera. Zakres wartości jest podany w [limity liczb całkowitych C++](../c-language/cpp-integer-limits.md), który pochodzi z limitów. Plik nagłówkowy H.

**END specyficzny dla Microsoft**

> [!NOTE]
>  Specyfikatory typu int i unsigned int są szeroko używane w programach języka C, ponieważ umożliwiają obsługę wartości całkowitych przez komputer w najbardziej efektywny sposób. Jednak ponieważ rozmiar int i unsigned int może być różny, programy zależące od konkretnego rozmiaru int mogą nie być przenoszone na inne komputery. Aby programy były bardziej przenośne, można użyć wyrażenia z operatorem sizeof (zgodnie z opisem w [sizeof Operator](../c-language/sizeof-operator-c.md)) zamiast ilości zakodowanych danych.

## <a name="see-also"></a>Zobacz też

[Magazyn typów podstawowych](../c-language/storage-of-basic-types.md)