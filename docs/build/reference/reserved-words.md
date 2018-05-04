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
ms.openlocfilehash: abe67e1804d436dbd44257f6d7670a71b7f74889
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="reserved-words"></a>Słowa zastrzeżone
Wyrazy są zastrzeżone przez konsolidator. Te nazwy mogą być używane jako argumenty w [instrukcji definicji modułu](../../build/reference/module-definition-dot-def-files.md) tylko wtedy, gdy nazwa jest ujęta w znaki podwójnego cudzysłowu ("").  
  
||||  
|-|-|-|  
|**ELEMENTU APPLOADER**1|**INITINSTANCE**2|**WSTĘPNEGO ŁADOWANIA**|  
|**PODSTAWA**|**IOPL**|**PRYWATNE**|  
|**KOD**|**BIBLIOTEKA**1|**PROTMODE**2|  
|**ZGODNE**|**LOADONCALL**1|**CZYSTY**1|  
|**DANE**|**LONGNAMES**2|**TYLKO DO ODCZYTU**|  
|**OPIS ELEMENTU**|**RUCHOME**1|**READWRITE**|  
|**DEV386**|**RUCHOMA**1|**REALMODE**1|  
|**DISCARDABLE**|**WIELE**|**REZYDENTNE**|  
|**DYNAMICZNE**|**NAZWA**|**RESIDENTNAME**1|  
|**TYLKO DO WYKONANIA**|**NEWFILES**2|**SEKCJE**|  
|**EXECUTEONLY**|**NODATA**1|**SEGMENTY**|  
|**EXECUTEREAD**|**NOIOPL**1|**UDOSTĘPNIONE**|  
|**EXETYPE**|**NONAME**|**POJEDYNCZY**|  
|**EXPORTS**|**NIEZGODNE**1|**STACKSIZE**|  
|**STAŁE**1|**NONDISCARDABLE**|**STUB**|  
|**FUNKCJE**2|**BRAK**|**WERSJA**|  
|**HEAPSIZE**|**UDOSTĘPNIANA**|**WINDOWAPI**|  
|**IMPORTY**|**NOTWINDOWCOMPAT**1|**WINDOWCOMPAT**|  
|**OCZYŚCIĆ ZANIECZYSZCZONY**1|**OBIEKTY**|**SYSTEMU WINDOWS**|  
|**OBEJMUJĄ**2|**STARY**1||  
  
 1 konsolidator emituje ostrzeżenie ("ignorowane") po napotkaniu tego terminu. Wyraz jest jednak nadal zastrzeżone.  
  
 2 konsolidator ignoruje tego wyrazu, ale emituje bez ostrzeżenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)