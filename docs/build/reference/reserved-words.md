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
ms.openlocfilehash: 7d51f599dfb81dfa860e1bdba86c4372e80379fb
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822447"
---
# <a name="reserved-words"></a>Słowa zastrzeżone

Wyrazy są zarezerwowane przez konsolidator. Te nazwy mogą być używane jako argumenty w [instrukcji definicji modułu](module-definition-dot-def-files.md) tylko wtedy, gdy nazwa jest ujęta w znaki podwójnego cudzysłowu ("").

||||
|-|-|-|
|**ELEMENTU APPLOADER**<sup>1</sup>|**INITINSTANCE**<sup>2</sup>|**WSTĘPNE ZAŁADOWANIE**|
|**BASE**|**IOPL**|**PRYWATNE**|
|**KOD**|**BIBLIOTEKA**<sup>1</sup>|**PROTMODE**<sup>2</sup>|
|**ZGODNE**|**LOADONCALL**<sup>1</sup>|**CZYSTY**<sup>1</sup>|
|**DANE**|**LONGNAMES**<sup>2</sup>|**TYLKO DO ODCZYTU**|
|**OPIS ELEMENTU**|**MOVABLE**<sup>1</sup>|**ODCZYTU I ZAPISU**|
|**DEV386**|**RUCHOMA**<sup>1</sup>|**REALMODE**<sup>1</sup>|
|**DISCARDABLE**|**WIELE**|**NA TERENIE TEGO KRAJU**|
|**DYNAMICZNE**|**NAZWA**|**RESIDENTNAME**<sup>1</sup>|
|**TYLKO DO WYKONANIA**|**NEWFILES**<sup>2</sup>|**SEKCJE**|
|**EXECUTEONLY**|**NODATA**<sup>1</sup>|**SEGMENTY**|
|**EXECUTEREAD**|**NOIOPL**<sup>1</sup>|**UDOSTĘPNIONE**|
|**EXETYPE**|**BEZ NAZWY**|**POJEDYNCZY**|
|**EXPORTS**|**NIEZGODNE**<sup>1</sup>|**STACKSIZE**|
|**NAPRAWIONO**<sup>1</sup>|**NONDISCARDABLE**|**STUB**|
|**FUNCTIONS**<sup>2</sup>|**BRAK**|**WERSJA**|
|**HEAPSIZE**|**NIEUDOSTĘPNIONYCH**|**WINDOWAPI**|
|**IMPORTS**|**NOTWINDOWCOMPAT**<sup>1</sup>|**WINDOWCOMPAT**|
|**OCZYŚCIĆ ZANIECZYSZCZONY**<sup>1</sup>|**OBJECTS**|**SYSTEMU WINDOWS**|
|**OBEJMUJĄ**<sup>2</sup>|**OLD**<sup>1</sup>||

<sup>1</sup> konsolidator emituje ostrzeżenie ("zignorowana"), po napotkaniu ten termin. Jednak słowo jest nadal zarezerwowany.

<sup>2</sup> konsolidator ignoruje ten wyraz, ale emituje ostrzeżenie.

## <a name="see-also"></a>Zobacz także

- [Odwołania konsolidatora MSVC](linking.md)
- [Opcje konsolidatora MSVC](linker-options.md)