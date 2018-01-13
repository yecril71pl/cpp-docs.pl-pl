---
title: "-LN (Utwórz moduł MSIL) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /LN
dev_langs: C++
helpviewer_keywords:
- -LN compiler option [C++]
- /LN compiler option [C++]
ms.assetid: 4f38f4f4-3176-4caf-8200-5c7585dc1ed3
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0278d59af9a62393f90a91655e3d7f0323e08118
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ln-create-msil-module"></a>/LN (Utwórz moduł MSIL)
Określa, że nie można wstawić manifest zestawu do pliku wyjściowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
/LN  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie **/LN** nie jest włączone (manifest zestawu są wstawiane do pliku wyjściowego).  
  
 Gdy **/LN** jest używany jeden z [/CLR (kompilacja języka wspólnego środowiska wykonawczego)](../../build/reference/clr-common-language-runtime-compilation.md) należy użyć opcji.  
  
 Zarządzane program, który nie ma metadanych zestawu w manifeście nosi nazwę modułu. Jeśli kompilacji z [/c (Kompiluj bez konsolidacji)](../../build/reference/c-compile-without-linking.md) i **/LN**, określ [/noassembly (Utwórz moduł MSIL)](../../build/reference/noassembly-create-a-msil-module.md) w fazie konsolidatora można utworzyć pliku wyjściowego.  
  
 Możesz utworzyć moduły, jeśli chcesz przełączyć się na tworzeniu zestawów składników opartego.  Oznacza to, że można tworzyć typy i kompilowania ich do modułów.  Następnie można wygenerować zestawu z jednego lub większej liczby modułów.  Aby uzyskać więcej informacji o tworzeniu zestawów z modułów, zobacz [modułu .netmodule pliki jako dane wejściowe konsolidatora](../../build/reference/netmodule-files-as-linker-input.md) lub [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).  
  
 Domyślne rozszerzenie pliku dla modułu jest modułu .netmodule.  
  
 W [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] wersje przed Visual C++ 2005, moduł został utworzony z **/clr:noAssembly**.  
  
 Konsolidatora Visual C++ akceptuje modułu .netmodule pliki jako dane wejściowe i będzie utworzony przez konsolidator plik wyjściowy zestawu lub moduł .netmodule z ma zależności środowiska wykonawczego na żadnym z modułów .netmodule, że dane wejściowe do konsolidatora.  Aby uzyskać więcej informacji, zobacz [modułu .netmodule pliki jako dane wejściowe konsolidatora](../../build/reference/netmodule-files-as-linker-input.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
-   Określ [/noassembly (Utwórz moduł MSIL)](../../build/reference/noassembly-create-a-msil-module.md) w fazie konsolidatora można utworzyć pliku wyjściowego.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Nie można zmienić tej opcji kompilatora programowo.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)