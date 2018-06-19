---
title: Kompilatora (poziom 1) ostrzeżenie C4445 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4445
dev_langs:
- C++
helpviewer_keywords:
- C4445
ms.assetid: 535e92a0-ba08-4dfc-89b2-af2dcdd7caeb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: abd0d15113373f752bb861d73e48091687b2f0d2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274592"
---
# <a name="compiler-warning-level-1-c4445"></a>Kompilator C4445 ostrzegawcze (poziom 1)
"Funkcja": WinRT lub typu zarządzanego metodą wirtualną nie mogą być prywatne  
  
 Jeśli funkcji wirtualnej jest oznaczony jako prywatny, nie jest dostępna przez typ pochodny. Aby naprawić ten błąd, zmień dostępność elementu wirtualnej funkcji członkowskiej do chronionych i publicznej.