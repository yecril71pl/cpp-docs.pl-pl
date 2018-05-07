---
title: Kompilatora (poziom 3) ostrzeżenie C4192 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4192
dev_langs:
- C++
helpviewer_keywords:
- C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3bae9b7af95de94b8f667cb09710af21044f8b80
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4192"></a>Kompilator C4192 ostrzegawcze (poziom 3)
automatycznie pomija "name" podczas importowania biblioteki typów "library"  
  
 A `#import` biblioteka zawiera element *nazwa*, która jest także zdefiniowana w nagłówkach systemu Win32. Ze względu na ograniczenia bibliotek typów, takich jak nazwy **IUnknown** lub identyfikator GUID często zdefiniowane w bibliotece typów duplikowania definicji z nagłówków systemu. `#import` wykryje te elementy i odmówić włączenie ich pliki nagłówkowe .tlh — i .tli.  
  
 Aby zmienić to zachowanie, użyj `#import` atrybuty [no_auto_exclude —](../../preprocessor/no-auto-exclude.md) i [include()](../../preprocessor/include-parens.md).