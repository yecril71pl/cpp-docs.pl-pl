---
title: Słowa zastrzeżone | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- code
- CONFORMING
- DISCARDABLE
- Description
- base
- APPLOADER
- Data
- DYNAMIC
- DEV386
dev_langs:
- C++
helpviewer_keywords:
- .def files [C++], reserved words
- def files [C++], reserved words
- linker [C++], reserved words
- reserved words [C++]
ms.assetid: 9b9f49e5-0739-45ab-a37e-81e3915ceb25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 132bd8e5ba66cbf9486a6da4747994c667e2f6e7
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705663"
---
# <a name="reserved-words"></a>Słowa zastrzeżone

Wyrazy są zastrzeżone przez konsolidator. Te nazwy mogą być używane jako argumenty w [instrukcji definicji modułu](../../build/reference/module-definition-dot-def-files.md) tylko wtedy, gdy nazwa jest ujęta w znaki podwójnego cudzysłowu ("").

||||
|-|-|-|
|**ELEMENTU APPLOADER**<sup>1</sup>|**INITINSTANCE**<sup>2</sup>|**WSTĘPNEGO ŁADOWANIA**|
|**PODSTAWA**|**IOPL**|**PRYWATNE**|
|**KOD**|**BIBLIOTEKA**<sup>1</sup>|**PROTMODE**<sup>2</sup>|
|**ZGODNE**|**LOADONCALL**<sup>1</sup>|**CZYSTY**<sup>1</sup>|
|**DANE**|**LONGNAMES**<sup>2</sup>|**TYLKO DO ODCZYTU**|
|**OPIS ELEMENTU**|**RUCHOME**<sup>1</sup>|**READWRITE**|
|**DEV386**|**RUCHOMA**<sup>1</sup>|**REALMODE**<sup>1</sup>|
|**DISCARDABLE**|**WIELE**|**REZYDENTNE**|
|**DYNAMICZNE**|**NAZWA**|**RESIDENTNAME**<sup>1</sup>|
|**TYLKO DO WYKONANIA**|**NEWFILES**<sup>2</sup>|**SEKCJE**|
|**EXECUTEONLY**|**NODATA**<sup>1</sup>|**SEGMENTY**|
|**EXECUTEREAD**|**NOIOPL**<sup>1</sup>|**UDOSTĘPNIONE**|
|**EXETYPE**|**NONAME**|**POJEDYNCZY**|
|**EXPORTS**|**NIEZGODNE**<sup>1</sup>|**STACKSIZE**|
|**STAŁE**<sup>1</sup>|**NONDISCARDABLE**|**STUB**|
|**FUNKCJE**<sup>2</sup>|**BRAK**|**WERSJA**|
|**HEAPSIZE**|**UDOSTĘPNIANA**|**WINDOWAPI**|
|**IMPORTY**|**NOTWINDOWCOMPAT**<sup>1</sup>|**WINDOWCOMPAT**|
|**OCZYŚCIĆ ZANIECZYSZCZONY**<sup>1</sup>|**OBIEKTY**|**SYSTEMU WINDOWS**|
|**OBEJMUJĄ**<sup>2</sup>|**STARY**<sup>1</sup>||

<sup>1</sup> konsolidator emituje ostrzeżenie ("ignorowane") po napotkaniu tego terminu. Wyraz jest jednak nadal zastrzeżone.

<sup>2</sup> konsolidator ignoruje tego wyrazu, ale emituje bez ostrzeżenia.

## <a name="see-also"></a>Zobacz także

- [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)
- [Opcje konsolidatora](../../build/reference/linker-options.md)