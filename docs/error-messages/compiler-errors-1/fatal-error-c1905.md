---
title: Błąd krytyczny C1905 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1905
dev_langs:
- C++
helpviewer_keywords:
- C1905
ms.assetid: fefc6769-477f-45a2-9878-6f0a5f42472c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d15bf00432cab6900c252d85cd642c414bdbbb22
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1905"></a>Błąd krytyczny C1905
Frontonu i zaplecza nie jest zgodne (muszą wskazywać tego samego procesora)  
  
 Ten błąd występuje, gdy plik .obj jest generowany przez kompilator fronton (C1.dll) przeznaczonego dla jednego procesora, takich jak x86, ARM, lub [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], ale jest odczytywany przez zaplecze (C2.dll) przeznaczonego dla innego procesora.  
  
 Aby rozwiązać ten problem, upewnij się, używasz zgodnego frontonu i zaplecza. Jest to wartość domyślna dla projektów utworzonych w programie Visual Studio. Ten błąd może wystąpić, jeśli mają edytować pliku projektu i stosować różne ścieżki do narzędzi kompilatora. Jeśli nie ustawiono specjalnie ścieżka do narzędzia kompilatora, ten błąd może wystąpić, jeśli instalację programu Visual Studio jest uszkodzona. Na przykład może skopiowano plików dll kompilatora z jednej lokalizacji do innej. Użyj **programy i funkcje** w Panelu sterowania systemu Windows do naprawy lub ponownej instalacji programu Visual Studio.