---
title: Kompilatora (poziom 1) ostrzeżenie C4098 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4098
dev_langs:
- C++
helpviewer_keywords:
- C4098
ms.assetid: 8c8aef1c-1639-44ec-a3dd-c0dfe9aa727d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 889c9aa926a8400d977de00ef5c288316ae84782
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4098"></a>Kompilator C4098 ostrzegawcze (poziom 1)
"Funkcja": funkcja typu void zwracanie wartości  
  
 Funkcja zadeklarowana z typem zwracanym [void](../../cpp/void-cpp.md) ma `return` instrukcji, która nie zwraca wartości. Kompilator zakłada, funkcja zwraca wartość typu `int`.