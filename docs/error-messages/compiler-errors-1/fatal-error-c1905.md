---
title: "Błąd krytyczny C1905 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1905
dev_langs: C++
helpviewer_keywords: C1905
ms.assetid: fefc6769-477f-45a2-9878-6f0a5f42472c
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9d1662b05764500d0ac6a96119f865294cac260b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1905"></a>Błąd krytyczny C1905
Frontonu i zaplecza nie jest zgodne (muszą wskazywać tego samego procesora)  
  
 Ten błąd występuje, gdy plik .obj jest generowany przez kompilator fronton (C1.dll) przeznaczonego dla jednego procesora, takich jak x86, ARM, lub [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], ale jest odczytywany przez zaplecze (C2.dll) przeznaczonego dla innego procesora.  
  
 Aby rozwiązać ten problem, upewnij się, używasz zgodnego frontonu i zaplecza. Jest to wartość domyślna dla projektów utworzonych w programie Visual Studio. Ten błąd może wystąpić, jeśli mają edytować pliku projektu i stosować różne ścieżki do narzędzi kompilatora. Jeśli nie ustawiono specjalnie ścieżka do narzędzia kompilatora, ten błąd może wystąpić, jeśli instalację programu Visual Studio jest uszkodzona. Na przykład może skopiowano plików dll kompilatora z jednej lokalizacji do innej. Użyj **programy i funkcje** w Panelu sterowania systemu Windows do naprawy lub ponownej instalacji programu Visual Studio.