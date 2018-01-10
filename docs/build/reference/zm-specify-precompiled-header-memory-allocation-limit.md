---
title: "-Zm (Określ Limit alokacji pamięci Prekompilowanego nagłówka) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /zm
dev_langs: C++
helpviewer_keywords:
- PCH files, memory allocation limit
- Zm compiler option [C++]
- /Zm compiler option [C++]
- precompiled header files, memory allocation limit
- Specify Precompiled Header Memory Allocation Limit compiler option
- cl.exe compiler, memory allocation limit
- .pch files, memory allocation limit
- memory allocation, Memory Allocation Limit compiler option
- -Zm compiler option [C++]
ms.assetid: 94c77d5e-6672-46a7-92e0-3f69e277727d
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2a45425215fcaf336c0b1630634d0adf37ba3984
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="zm-specify-precompiled-header-memory-allocation-limit"></a>/Zm (Określ limit alokacji pamięci prekompilowanego nagłówka)
Określa ilość pamięci przydzielanej przez kompilator do konstruowania wstępnie skompilowanych nagłówków.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Zmfactor  
```  
  
## <a name="arguments"></a>Argumenty  
 `factor`  
 Czynnik skalowania określa ilość pamięci, której kompilator używa do konstruowania wstępnie skompilowanych nagłówków.  
  
 `factor` Argument jest procentem domyślny rozmiar buforu pracy zdefiniowanych przez kompilator. Wartość domyślna `factor` to 100 (procent), ale można określić więcej lub mniej.  
  
## <a name="remarks"></a>Uwagi  
 We wcześniejszych wersjach Visual C++ kompilator używał kilku stert dyskretnych, a każda miała skończony limit. Obecnie kompilator dynamicznie powiększa sterty w miarę potrzeb, aż do całkowitego limitu rozmiaru sterty, i wymaga bufora o stałym rozmiarze wyłącznie w celu konstruowania wstępnie skompilowanych nagłówków. W rezultacie **/Zm** — opcja kompilatora jest rzadko niezbędne.  
  
 Jeśli kompilator skończy się miejsce na stercie i emituje [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) komunikat o błędzie, gdy używasz **/Zm** — opcja kompilatora, może być zarezerwowana zbyt dużej ilości pamięci. Rozważ usunięcie **/Zm** opcji. Jeśli kompilator emituje [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) komunikat o błędzie, towarzyszącego [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) wiadomości określa `factor` argument do użycia podczas skompiluj przy użyciu **/Zm** — Opcja kompilatora.  
  
 W poniższej tabeli przedstawiono sposób `factor` argument dotyczy limit alokacji pamięci, jeśli użytkownik ponosi rozmiar buforu prekompilowany nagłówek domyślny jest 75 MB.  
  
|Wartość`factor`|Limit alokacji pamięci|  
|-----------------------|-----------------------------|  
|10|7.5 MB|  
|100|75 MB|  
|200|150 MB|  
|1000|750 MB|  
|2000|1500 MB|  
  
## <a name="other-ways-to-set-the-memory-allocation-limit"></a>Inne sposoby ustawiania limitu alokacji pamięci  
  
#### <a name="to-set-the-zm-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić opcję kompilatora /Zm w środowisku programistycznym Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  W okienku nawigacji wybierz **właściwości konfiguracji**, **C/C++**, **wiersza polecenia**.  
  
3.  Wprowadź **/Zm** w — opcja kompilatora **dodatkowe opcje** pole.  
  
#### <a name="to-set-the-zm-compiler-option-programmatically"></a>Aby programowo ustawić opcję kompilatora /Zm  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)