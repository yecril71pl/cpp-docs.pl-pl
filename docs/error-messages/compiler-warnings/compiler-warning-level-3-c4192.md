---
title: "Kompilatora (poziom 3) ostrzeżenie C4192 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4192
dev_langs: C++
helpviewer_keywords: C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ff07a7fd5af7c9e4d73d9a4ce679edc7ab5e6b43
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4192"></a>Kompilator C4192 ostrzegawcze (poziom 3)
automatycznie pomija "name" podczas importowania biblioteki typów "library"  
  
 A `#import` biblioteka zawiera element *nazwa*, która jest także zdefiniowana w nagłówkach systemu Win32. Ze względu na ograniczenia bibliotek typów, takich jak nazwy **IUnknown** lub identyfikator GUID często zdefiniowane w bibliotece typów duplikowania definicji z nagłówków systemu. `#import`wykryje te elementy i odmówić włączenie ich pliki nagłówkowe .tlh — i .tli.  
  
 Aby zmienić to zachowanie, użyj `#import` atrybuty [no_auto_exclude —](../../preprocessor/no-auto-exclude.md) i [include()](../../preprocessor/include-parens.md).