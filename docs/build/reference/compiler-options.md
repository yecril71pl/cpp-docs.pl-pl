---
title: Opcje kompilatora | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- cl.exe compiler
- IPF Visual C++ compiler
- Itanium Visual C++ compiler
- compiler options, C++
- x64 Visual C++ compiler
ms.assetid: ed3376c8-bef4-4c9a-80e9-3b5da232644c
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c433abea04ff81c69fe1b73569ea7e043e6e81ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-options"></a>Opcje kompilatora
Cl.exe to narzędzie, które kontroluje Kompilatory języka Microsoft C i C++ i konsolidatora. Cl.exe można uruchomić tylko w systemach operacyjnych, które obsługuje program Microsoft Visual Studio.  
  
> [!NOTE]
>  Można uruchomić to narzędzie tylko z [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] wiersza polecenia. Nie można uruchomić go z wiersza polecenia systemu lub z Eksploratora plików.  
  
 Kompilatory tworzenia plików obiektu (.obj) Format wspólnej pliku obiektu (COFF). Konsolidator tworzy pliki wykonywalne (.exe) lub biblioteki dołączanej (dynamicznie dll).  
  
 Należy pamiętać, że wszystkie opcje kompilatora jest uwzględniana wielkość liter.  
  
 Aby skompilować bez konsolidacji, należy użyć [/c](../../build/reference/c-compile-without-linking.md).  
  
## <a name="finding-an-option"></a>Znajdowanie opcję  
 Aby znaleźć opcję kompilatora określonego, zobacz jedną z następujących list:  
  
-   [Opcje kompilatora w porządku alfabetycznym](../../build/reference/compiler-options-listed-alphabetically.md)  
  
-   [Opcje kompilatora w rozbiciu na kategorie](../../build/reference/compiler-options-listed-by-category.md)  
  
## <a name="specifying-options"></a>Określenie opcji  
 Temat dla każdej opcji kompilatora opisano, jak można ją ustawić w środowisku programistycznym. Informacje dotyczące określania opcji poza Środowisko deweloperskie zobacz:  
  
-   [Składnia wiersza polecenia kompilatora](../../build/reference/compiler-command-line-syntax.md)  
  
-   [Pliki poleceń CL](../../build/reference/cl-command-files.md)  
  
-   [Zmienne środowiskowe CL](../../build/reference/cl-environment-variables.md)  
  
## <a name="related-build-tools"></a>Narzędzia kompilacji pokrewne  
 Użyj [NMAKE](../../build/nmake-reference.md) do tworzenia pliku wyjściowego.  
  
 Użyj [BSCMAKE](../../build/reference/bscmake-reference.md) do obsługi przeglądanie klasy.  
  
 [Opcje konsolidatora](../../build/reference/linker-options.md) wpłynąć na sposób składa się z programem.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie kompilacji C/C++](../../build/reference/c-cpp-building-reference.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [Szybka kompilacja](../../build/reference/fast-compilation.md)   
 [CL wywołuje konsolidator](../../build/reference/cl-invokes-the-linker.md)