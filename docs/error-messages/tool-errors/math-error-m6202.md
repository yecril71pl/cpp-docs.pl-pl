---
title: Błąd matematyczny M6202 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6202
dev_langs:
- C++
helpviewer_keywords:
- M6202
ms.assetid: 4d17045f-c6dc-4705-9512-e9af12c35fb4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4596b9782bc1de0e6ccd52bfcd03965415adb353
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="math-error-m6202"></a>Błąd matematyczny M6202
"Funkcja": — błąd  
  
 Argument funkcji danego była wartością singularity dla tej funkcji. Funkcja nie jest zdefiniowany dla tego argumentu.  
  
 Ten błąd wywołania `_matherr` funkcji z nazwą funkcji, argumentów i typ błędu. Można ponownie napisać `_matherr` funkcji, aby dostosować obsługę niektórych błędów czasu wykonywania zmiennoprzecinkowej matematyczny.