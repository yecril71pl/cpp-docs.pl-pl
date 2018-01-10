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
ms.workload: cplusplus
ms.openlocfilehash: 022c0e0aac8d231963ddf6d5d3715d55f726a8b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4192"></a>Kompilator C4192 ostrzegawcze (poziom 3)
automatycznie pomija "name" podczas importowania biblioteki typów "library"  
  
 A `#import` biblioteka zawiera element *nazwa*, która jest także zdefiniowana w nagłówkach systemu Win32. Ze względu na ograniczenia bibliotek typów, takich jak nazwy **IUnknown** lub identyfikator GUID często zdefiniowane w bibliotece typów duplikowania definicji z nagłówków systemu. `#import`wykryje te elementy i odmówić włączenie ich pliki nagłówkowe .tlh — i .tli.  
  
 Aby zmienić to zachowanie, użyj `#import` atrybuty [no_auto_exclude —](../../preprocessor/no-auto-exclude.md) i [include()](../../preprocessor/include-parens.md).