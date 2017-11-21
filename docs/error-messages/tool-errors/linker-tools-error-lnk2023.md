---
title: "Błąd narzędzi konsolidatora LNK2023 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2023
dev_langs: C++
helpviewer_keywords: LNK2023
ms.assetid: c99e35a8-739a-4a20-a715-29b8c3744703
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 37370cd4637680783761e787e6ca38bdd5bada84
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk2023"></a>Błąd narzędzi konsolidatora LNK2023
Nieprawidłowy plik dll lub punkt wejścia \<biblioteki dll lub punkt wejście >  
  
 Konsolidator ładuje nieprawidłową wersję msobj90.dll. Upewnij się, że link.exe i msobj90.dll w ścieżce mają tę samą wersję.  
  
 Zależność msobj90.dll może nie być obecny. Na liście zależności msobj90.dll jest:  
  
-   Msvcr90.dll  
  
-   Kernel32.dll  
  
 Sprawdź komputer dla wszystkich kopii msobj90.dll, które mogą być nieaktualne.