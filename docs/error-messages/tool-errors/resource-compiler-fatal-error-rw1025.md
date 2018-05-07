---
title: Błąd krytyczny kompilatora zasobów RW1025 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW1025
dev_langs:
- C++
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ba216e63cb0cae92b4541800493a2fb6195553a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-fatal-error-rw1025"></a>Błąd krytyczny kompilatora zasobów RW1025
Za mało pamięci sterty daleko  
  
 Sprawdź, czy rezydentny oprogramowania, które mogą być zajmują zbyt dużej ilości miejsca. Aby dowiedzieć się, ile pamięci masz, należy użyć programu CHKDSK.  
  
 W przypadku tworzenia pliku zasobu dużych podzielone dwa pliki skryptów zasobów. Po utworzeniu dwa pliki .res, aby połączyć je za pomocą wiersza polecenia systemu MS-DOS:  
  
```  
copy first.res /b + second.res /b full.res  
```