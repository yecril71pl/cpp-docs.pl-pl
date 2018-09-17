---
title: Typy skalarne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 07c9195e-b6c7-4083-8ef0-8a93032e4d1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ad0fa75380ca971f7ac2dfa4c370c076f7d552e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700963"
---
# <a name="scalar-types"></a>Typy skalarne

Mimo że dostępu do danych może wynikać z dowolnej wyrównanie, zaleca się, że dane być wyrównane do jego granicę fizycznych, aby uniknąć utraty wydajności (lub jej wielokrotność). Typy wyliczeniowe są stałych liczb całkowitych i są traktowane jako 32-bitowych liczb całkowitych. W poniższej tabeli opisano definicji typu i zalecany magazyn dla niego w odniesieniu do wyrównania, używając następujących wartości wyrównania:

- Byte — 8 bitów

- Word — 16 bitów

- Podwójne słowo — 32-bitowy

- Word Quad - 64-bitowy

- Word ośmiu - 128 bitów

|||||
|-|-|-|-|
|Typ skalarny|Typ danych C|Rozmiar magazynu (w bajtach)|Zalecane wyrównania|
|**INT8**|**char**|1|Byte|
|**UINT8**|**unsigned char**|1|Byte|
|**INT16**|**short**|2|Word|
|**UINT16**|**short bez znaku**|2|Word|
|**INT32**|**int**, **długi**|4|Bitowego|
|**UINT32**|**unsigned int, niepodpisane długa**|4|Bitowego|
|**INT64**|**__int64**|8|Quadword|
|**UINT64 —**|**__int64 bez znaku**|8|Quadword|
|**FP32 (Pojedyncza precyzja)**|**float**|4|Bitowego|
|**FP64 (Podwójna precyzja)**|**double**|8|Quadword|
|**WSKAŹNIK**|<strong>\*</strong>|8|Quadword|
|**__m64**|**__m64 — struktura**|8|Quadword|
|**__m128**|**__m128 — struktura**|16|Octaword|

## <a name="see-also"></a>Zobacz też

[Typy i magazyn](../build/types-and-storage.md)