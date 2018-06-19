---
title: Kompilatora (poziom 3) ostrzeżenie C4278 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4278
dev_langs:
- C++
helpviewer_keywords:
- C4278
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b556166f61c5d77ac34fb7243ac25d5baeaa2b1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33296679"
---
# <a name="compiler-warning-level-3-c4278"></a>Kompilator C4278 ostrzegawcze (poziom 3)
'Identyfikator': identyfikator w bibliotece typów "tlb" jest już makrem; Użyj kwalifikatora "rename"  
  
 Korzystając z [#import](../../preprocessor/hash-import-directive-cpp.md), identyfikator w bibliotece typów, importowany próbuje zadeklarować identyfikatora ***identyfikator***. Jest to jednak już prawidłowy symbol.  
  
 Użyj `#import` **zmienić** atrybut można przypisać aliasu do symbolu w bibliotece typów.