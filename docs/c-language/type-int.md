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
ms.openlocfilehash: 5ed3fcd9b11a76f8ff211bf8be5cf50ee6664cda
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389179"
---
# <a name="type-int"></a>Typ int
Rozmiar oznaczonego lub nieoznaczonego elementu `int` jest standardowym rozmiarem liczby całkowitej na danym komputerze. Na przykład w 16-bitowych systemach operacyjnych, typ `int` ma zazwyczaj 16 bitów lub 2 bajty. W 32-bitowych systemach operacyjnych, typ `int` ma zazwyczaj 32 bity lub 4 bajty. W związku z tym `int` typu jest odpowiednikiem albo `short int` lub **długi int** typu i `unsigned int` typu jest odpowiednikiem albo **niepodpisane krótko** lub `unsigned long` Typ, w zależności od środowiska docelowego. Wszystkie typy `int` reprezentują wartości oznaczone, chyba że określono inaczej.  
  
 Specyfikatory typu `int` i `unsigned int` (lub po prostu `unsigned`) definiują pewne funkcje języka C (na przykład typ `enum`). W tych przypadkach definicje `int` i unsigned int dla określonej implementacji określają rzeczywistą pamięć.  
  
 **Microsoft Specific**  
  
 Oznaczone liczby całkowite są zapisywane w kodzie dopełnień do dwóch. Najbardziej znaczący bit utrzymuje znak: 1 dla wartości ujemnych, 0 dla wartości dodatnich i zera. Zakres wartości znajduje się w [limity liczb całkowitych C++](../c-language/cpp-integer-limits.md), który jest pobierana z limitów. Plik nagłówka H.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
> [!NOTE]
>  Specyfikatory typu int i unsigned int są szeroko używane w programach języka C, ponieważ umożliwiają obsługę wartości całkowitych przez komputer w najbardziej efektywny sposób. Jednak ponieważ rozmiar int i unsigned int może być różny, programy zależące od konkretnego rozmiaru int mogą nie być przenoszone na inne komputery. Aby programy przenośną, można używać wyrażeń z sizeof — operator (zgodnie z opisem w [sizeof — Operator](../c-language/sizeof-operator-c.md)) zamiast rozmiary ustalony danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Magazyn typów podstawowych](../c-language/storage-of-basic-types.md)