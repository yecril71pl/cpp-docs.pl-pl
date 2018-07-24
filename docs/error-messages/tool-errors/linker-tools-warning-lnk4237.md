---
title: Ostrzeżenie LNK4237 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4237
dev_langs:
- C++
helpviewer_keywords:
- LNK4237
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fcc109fe3ccf06e0461deed449517850271a2024
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39209394"
---
# <a name="linker-tools-warning-lnk4237"></a>Ostrzeżenie LNK4237 narzędzi konsolidatora
Subsystem określony podczas importowania pozycji z 'dll'; Użyj opcji lub/Subsystem: Windows.  
  
 [Subsystem](../../build/reference/subsystem-specify-subsystem.md) została określona podczas tworzenia aplikacji systemu windows (Win32), który bezpośrednio korzysta z co najmniej jeden z następujących czynności:  
  
-   Kernel32.dll.  
  
-   Gdi32.dll  
  
-   User32.dll  
  
-   jedną z msvcrt\* biblioteki dll.  
  
 Rozwiązanie to ostrzeżenie, nie określając **Subsystem**.