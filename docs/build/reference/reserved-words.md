---
title: "Słowa zastrzeżone | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- .def files [C++], reserved words
- def files [C++], reserved words
- linker [C++], reserved words
- reserved words [C++]
ms.assetid: 9b9f49e5-0739-45ab-a37e-81e3915ceb25
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 35f9a3e907b72b4b8cf8e673e771832ba3fc0527
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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