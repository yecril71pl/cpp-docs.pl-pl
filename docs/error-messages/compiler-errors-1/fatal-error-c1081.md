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
ms.openlocfilehash: b34f2f19a0bb8770ea9292fef120c415c0fb255a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060535"
---
# <a name="fatal-error-c1081"></a>Błąd krytyczny C1081

'symbol': Nazwa pliku jest za długa

Długość nazwy ścieżki pliku przekracza `_MAX_PATH` (zdefiniowanej przez STDLIB.h jako 260 znaków). Skróć nazwę pliku.

Wywołanie CL.exe z krótkiej nazwy pliku, kompilator może trzeba będzie wygenerować pełną nazwę ścieżki. Na przykład `cl -c myfile.cpp` może spowodować, że kompilator do wygenerowania:

```
D:\<very-long-directory-path>\myfile.cpp
```