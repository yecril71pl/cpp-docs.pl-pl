---
title: Błąd krytyczny C1081 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1081
dev_langs:
- C++
helpviewer_keywords:
- C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b5ea18ff3f2714d9621d4372cf541be2f9b225a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230525"
---
# <a name="fatal-error-c1081"></a>Błąd krytyczny C1081
"symbol": Nazwa pliku jest za długa  
  
 Długość nazwy ścieżki pliku przekracza `_MAX_PATH` (zdefiniowany przez STDLIB.h jako 260 znaków). Skróć nazwę pliku.  
  
 CL.exe można wywołać z krótką nazwą pliku, kompilator może być konieczne do wygenerowania pełną nazwę ścieżki. Na przykład `cl -c myfile.cpp` może spowodować kompilatorowi Generowanie:  
  
```  
D:\<very-long-directory-path>\myfile.cpp  
```