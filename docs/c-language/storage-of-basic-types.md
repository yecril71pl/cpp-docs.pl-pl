---
title: Magazyn typów podstawowych
ms.date: 10/02/2019
helpviewer_keywords:
- specifiers [C++], type
- integral types, storage
- storage [C++], types
- floating-point numbers, storage
- type specifiers [C++], sizes
- arithmetic operations [C++], types
- int data type
- short data type
- signed types [C++], storage
- long double keyword [C], storage
- long keyword [C]
- double data type, storage
- types [C], arithmetic
- integral types
- data types [C], specifiers
- storing types [C++]
- unsigned types [C++], storage
- data types [C], storage
ms.assetid: bd1f33c1-c6b9-4558-8a72-afb21aef3318
ms.openlocfilehash: 64c642df4dd85e4aa09f90a143b8aa67c28b7dc2
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998763"
---
# <a name="storage-of-basic-types"></a>Magazyn typów podstawowych

Poniższa tabela zawiera podsumowanie magazynu skojarzonego z każdym typem podstawowym.

## <a name="sizes-of-fundamental-types"></a>Rozmiary typów podstawowych

|Typ|Magazyn|
|----------|-------------|
|**char**, **znak bez znaku** **, znak ze znakiem**|1 bajt|
|**krótkie**, **niepodpisane, krótkie**|2 bajty|
|**int**, **unsigned int**|4 bajty|
|**Long**, **Long unsigned**|4 bajty|
|**Long Long**, **unsigned long long**|8 bajtów|
|**float**|4 bajty|
|**double**|8 bajtów|
|**Long Double**|8 bajtów|

Typy danych języka C są podzielone na kategorie ogólne. *Typy całkowite* obejmują **int**, **char**, **Short**, **Long**i **Long Long**. Te typy mogą być kwalifikowane ze **znakiem** i **bez znaku** **, ale nie** mogą być używane jako skróty dla **niepodpisanych int**. Typy wyliczeniowe (**enum**) również są traktowane jako typy całkowite w większości celów. *Typy przestawne* obejmują wartości **zmiennoprzecinkowe**, **podwójne**i **Long Double**. *Typy arytmetyczne* obejmują wszystkie typy zmiennoprzecinkowe i całkowite.

## <a name="see-also"></a>Zobacz także

[Deklaracje i typy](../c-language/declarations-and-types.md)
