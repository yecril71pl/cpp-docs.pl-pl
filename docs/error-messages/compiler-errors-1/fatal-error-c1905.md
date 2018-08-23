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
ms.openlocfilehash: 608702deb1ebaed9bab56fe8d08ca3102d5c5d89
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465254"
---
# <a name="fatal-error-c1905"></a>Błąd krytyczny C1905
Frontonu i zaplecza nie jest zgodne (muszą wskazywać tego samego procesora)  
  
 Ten błąd występuje, gdy w pliku .obj, który jest generowany przez kompilator fronton (C1.dll) ten jeden procesor celów, takich jak x86, ARM lub x64, ale jest odczytywany przez zaplecze (C2.dll) który jest przeznaczony dla inny procesor.  
  
 Aby rozwiązać ten problem, upewnij się, że używasz pasującego frontonu i zaplecza. Jest to wartość domyślna dla projektów w programie Visual Studio. Ten błąd może wystąpić, jeśli edytować plik projektu i używać różnych ścieżek do narzędzia kompilatora. Jeśli nie ustawiono wyraźnie ścieżkę dla narzędzia kompilatora, ten błąd może wystąpić, jeśli instalacja programu Visual Studio jest uszkodzony. Na przykład może zostały skopiowane pliki dll kompilatora z jednej lokalizacji do innej. Użyj **programy i funkcje** w Panelu sterowania Windows, aby naprawić lub zainstalować ponownie program Visual Studio.