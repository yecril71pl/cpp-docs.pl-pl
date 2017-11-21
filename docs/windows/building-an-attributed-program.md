---
title: Kompilowanie programu opartego na atrybutach | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- tlb files
- MIDL
- MIDL, linker output
- IDL files
- tlb files, building attributed programs
- .tlb files, building attributed programs
- IDL files, building
- attributes [C++], building type libraries and .idl files
- .tlb files
- .idl files, building
- type libraries, linker options for building
ms.assetid: 04997b5f-bf2c-46ec-b868-c4adebbef5f4
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a757cbbb7bb9e080a9492ecabfd0542714cf2c7a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="building-an-attributed-program"></a>Kompilowanie programu opartego na atrybutach
Po wprowadzeniu atrybutów języka Visual C++ w kodzie źródłowym może być kompilatora Visual C++, aby wygenerować plik biblioteki i .idl typu dla Ciebie. Konsolidator następujące opcje tworzenia plików .tlb i .idl pomocy:  
  
-   [/ IDLOUT](../build/reference/idlout-name-midl-output-files.md)  
  
-   [/ IGNOREIDL](../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)  
  
-   [/ MIDL](../build/reference/midl-specify-midl-command-line-options.md)  
  
-   [/ TLBOUT](../build/reference/tlbout-name-dot-tlb-file.md)  
  
 Niektóre projekty zawierają wiele plików .idl niezależne. Są one używane do utworzenia dwóch lub więcej plików .tlb i opcjonalnie powiązać je do bloku zasobów. W tym scenariuszu nie jest obecnie obsługiwane w programie Visual C++.  
  
 Ponadto konsolidatora Visual C++ dane wyjściowe obejmują wszystkie informacje o atrybutach dotyczące IDL w jednym pliku MIDL. Nie będzie można wygenerować dwóch bibliotek typów na podstawie pojedynczego projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../windows/attributed-programming-concepts.md)