---
title: Opcje LINK kontrolowane przez kompilator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- link
dev_langs:
- C++
helpviewer_keywords:
- LINK tool [C++], compiler-controlled options
- linker [C++], CL compiler control
- linking [C++], affected by CL features
- cl.exe compiler [C++], features that affect linking
- cl.exe compiler [C++], controlling linker
ms.assetid: e4c03896-c99c-4599-8502-e0f4bebe69d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d99a05b5f9c4d97fd42328a41ad3fe054ab42cd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371999"
---
# <a name="compiler-controlled-link-options"></a>Opcje LINK kontrolowane przez kompilator
Kompilator CL wywołuje automatycznie łącze, chyba że określono opcję/c. CL zawiera pewną kontrolę nad konsolidator przy użyciu opcji wiersza polecenia i argumentów. Poniższa tabela zawiera podsumowanie funkcji w CL, które wpływają niekorzystnie na konsolidację.  
  
|Specyfikacja CL|CL akcję, która wpływa na LINK|  
|----------------------|---------------------------------|  
|Rozszerzenia nazw plików, niż .c, .cxx, .cpp lub .def|Przekazuje nazwę pliku jako dane wejściowe, łącza|  
|*Nazwa pliku*.def|/ DEF przekazuje:*filename*.def|  
|/F*numer*|Przekazuje /STACK:*numer*|  
|/FD*filename*|Przekazuje/PDB:*filename*|  
|/Fe*filename*|Przekazuje/OUT:*filename*|  
|/FM*filename*|Przekazuje/map:*filename*|  
|/GY|Tworzy spakowanych funkcji (Comdat); Włącza konsolidacje poziomu funkcji|  
|/LD|Przekazuje/dll|  
|/ LDd|Przekazuje/dll|  
|/link|Przekazuje pozostałą część wiersza polecenia do łącza|  
|/ / MD lub/MT|Umieszcza domyślną nazwę biblioteki w pliku obj.|  
|/ MDd lub /MTd|Umieszcza domyślną nazwę biblioteki w pliku obj. Określa symbol **_DEBUG**|  
|/nologo|/ Nologo przekazuje|  
|/Zd|Przekazuje/Debug|  
|/ Zi lub/z7|Przekazuje/Debug|  
|/ZL|Pomija domyślną nazwę biblioteki z pliku obj.|  
  
 Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](../../build/reference/compiler-options.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)