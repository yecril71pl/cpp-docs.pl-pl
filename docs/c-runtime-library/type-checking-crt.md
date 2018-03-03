---
title: Typ sprawdzania (CRT) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.types
dev_langs:
- C++
helpviewer_keywords:
- checking type
- variable argument functions
- type checking
ms.assetid: 1ba7590b-d1c0-4636-b6a0-e231395abdad
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d18ae0818dd839bee0d93bd7194dadcc9abf6627
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="type-checking-crt"></a>Sprawdzać typ (CRT)
Kompilator wykonuje ograniczone typu sprawdzanie na funkcje, które można wykonać zmienną liczbę argumentów w następujący sposób:  
  
|Wywołanie funkcji|Zaznaczone typu argumentów|  
|-------------------|-----------------------------|  
|`_cprintf_s`, `_cscanf_s`, `printf_s`, `scanf_s`|Pierwszy argument (ciąg formatu)|  
|`fprintf_s`, `fscanf_s`, `sprintf_s`, `sscanf_s`|Pierwsze dwa argumenty (pliku lub buforu i formatu ciągu)|  
|`_snprintf_s`|Pierwsze trzy argumenty (pliku lub buforu, liczby wartości oraz ciąg formatu)|  
|`_open`|Pierwsze dwa argumenty (ścieżka i `_open` flagi)|  
|`_sopen_s`|Pierwsze trzy argumenty (ścieżka `_open` flagę i tryb udostępniania)|  
|`_execl`, `_execle`, `_execlp`, `_execlpe`|Pierwsze dwa argumenty (ścieżka i pierwszy argument wskaźnika)|  
|`_spawnl`, `_spawnle`, `_spawnlp`, `_spawnlpe`|Pierwsze trzy argumenty (flagi trybu, ścieżkę i pierwszy argument wskaźnika)|  
  
 Kompilator wykonuje ten sam typ ograniczony sprawdzanie na odpowiedniki znaków dwubajtowych tych funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)