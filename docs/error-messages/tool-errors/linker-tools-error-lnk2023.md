---
title: Błąd narzędzi konsolidatora LNK2023 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2023
dev_langs:
- C++
helpviewer_keywords:
- LNK2023
ms.assetid: c99e35a8-739a-4a20-a715-29b8c3744703
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b53fba3743d6d072930e430c15b79e0e31d68d2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk2023"></a>Błąd narzędzi konsolidatora LNK2023
Nieprawidłowy plik dll lub punkt wejścia \<biblioteki dll lub punkt wejście >  
  
 Konsolidator ładuje nieprawidłową wersję msobj90.dll. Upewnij się, że link.exe i msobj90.dll w ścieżce mają tę samą wersję.  
  
 Zależność msobj90.dll może nie być obecny. Na liście zależności msobj90.dll jest:  
  
-   Msvcr90.dll  
  
-   Kernel32.dll  
  
 Sprawdź komputer dla wszystkich kopii msobj90.dll, które mogą być nieaktualne.