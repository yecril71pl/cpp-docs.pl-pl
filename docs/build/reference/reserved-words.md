---
title: Słowa zastrzeżone
ms.date: 11/04/2016
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
helpviewer_keywords:
- .def files [C++], reserved words
- def files [C++], reserved words
- linker [C++], reserved words
- reserved words [C++]
ms.assetid: 9b9f49e5-0739-45ab-a37e-81e3915ceb25
ms.openlocfilehash: 360baf479f9100483fe694ca8860dfc1d7ebfe11
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502469"
---
# <a name="reserved-words"></a>Słowa zastrzeżone

Wyrazy są zarezerwowane przez konsolidator. Te nazwy mogą być używane jako argumenty w [instrukcji definicji modułu](../../build/reference/module-definition-dot-def-files.md) tylko wtedy, gdy nazwa jest ujęta w znaki podwójnego cudzysłowu ("").

||||
|-|-|-|
|**ELEMENTU APPLOADER**<sup>1</sup>|**INITINSTANCE**<sup>2</sup>|**WSTĘPNE ZAŁADOWANIE**|
|**PODSTAWOWY**|**IOPL**|**PRYWATNE**|
|**KOD**|**BIBLIOTEKA**<sup>1</sup>|**PROTMODE**<sup>2</sup>|
|**ZGODNE**|**LOADONCALL**<sup>1</sup>|**CZYSTY**<sup>1</sup>|
|**DANE**|**LONGNAMES**<sup>2</sup>|**TYLKO DO ODCZYTU**|
|**OPIS ELEMENTU**|**RUCHOMY**<sup>1</sup>|**ODCZYTU I ZAPISU**|
|**DEV386**|**RUCHOMA**<sup>1</sup>|**REALMODE**<sup>1</sup>|
|**DISCARDABLE**|**WIELE**|**NA TERENIE TEGO KRAJU**|
|**DYNAMICZNE**|**NAZWA**|**RESIDENTNAME**<sup>1</sup>|
|**TYLKO DO WYKONANIA**|**NEWFILES**<sup>2</sup>|**SEKCJE**|
|**EXECUTEONLY**|**NODATA**<sup>1</sup>|**SEGMENTY**|
|**EXECUTEREAD**|**NOIOPL**<sup>1</sup>|**UDOSTĘPNIONE**|
|**EXETYPE**|**BEZ NAZWY**|**POJEDYNCZY**|
|**EXPORTS**|**NIEZGODNE**<sup>1</sup>|**STACKSIZE**|
|**NAPRAWIONO**<sup>1</sup>|**NONDISCARDABLE**|**STUB**|
|**FUNKCJE**<sup>2</sup>|**BRAK**|**WERSJA**|
|**HEAPSIZE**|**NIEUDOSTĘPNIONYCH**|**WINDOWAPI**|
|**IMPORTY**|**NOTWINDOWCOMPAT**<sup>1</sup>|**WINDOWCOMPAT**|
|**OCZYŚCIĆ ZANIECZYSZCZONY**<sup>1</sup>|**OBIEKTY**|**SYSTEMU WINDOWS**|
|**OBEJMUJĄ**<sup>2</sup>|**STARY**<sup>1</sup>||

<sup>1</sup> konsolidator emituje ostrzeżenie ("zignorowana"), po napotkaniu ten termin. Jednak słowo jest nadal zarezerwowany.

<sup>2</sup> konsolidator ignoruje ten wyraz, ale emituje ostrzeżenie.

## <a name="see-also"></a>Zobacz także

- [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)
- [Opcje konsolidatora](../../build/reference/linker-options.md)