---
title: "-CGTHREADS (wątki kompilatora) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- /CGTHREADS linker option
- -CGTHREADS linker option
- CGTHREADS linker option
ms.assetid: 4b52cfdb-3702-470b-9580-fabeb1417488
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 542e35ecbb5e56ae0d13861b9885936f3b47c9da
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cgthreads-compiler-threads"></a>/CGTHREADS (wątki kompilatora)
Ustawia liczbę wątków używanych podczas generowania optymalizacji i kod, gdy określona jest generowanie łączonych kodów czasowych cl.exe.  
  
## <a name="syntax"></a>Składnia  
  
```  
/CGTHREADS:[1-8]  
```  
  
## <a name="arguments"></a>Argumenty  
 liczba  
 Maksymalna liczba wątków dla cl.exe do użycia z zakresu od 1 do 8.  
  
## <a name="remarks"></a>Uwagi  
 **/Cgthreads** opcja określa maksymalną liczbę wątków cl.exe używa równolegle optymalizacji i generowanie kodu fazy kompilacji, gdy w czasie konsolidacji generowanie kodu ([opcję/LTCG](../../build/reference/ltcg-link-time-code-generation.md)) jest określona. Domyślnie cl.exe używa czterech wątków tak, jakby **/CGTHREADS:4** zostały określone. Jeśli są dostępne, większej liczby rdzeni procesora większego `number` wartość może skrócić czas kompilacji.  
  
 Można określić wiele poziomów równoległości dla kompilacji. Przełącznik msbuild.exe **/maxcpucount** określa liczbę procesów MSBuild, które mogą być uruchamiane równolegle. [/MP (kompilacja z wieloma procesami)](../../build/reference/mp-build-with-multiple-processes.md) flagi kompilatora określa liczbę procesów cl.exe, jednocześnie kompilowane do plików źródłowych. [/Cgthreads](../../build/reference/cgthreads-code-generation-threads.md) — opcja kompilatora określa liczbę wątków używanych przez każdy proces cl.exe. Ponieważ procesor można uruchamiać tylko jako wiele wątków jednocześnie jako rdzeni procesora, nie jest przydatne do określenia większe wartości dla wszystkich tych opcji, w tym samym czasie i mogą być unikają szkodliwych dla produkcji. Aby uzyskać więcej informacji na temat sposobu tworzenia projektów równolegle, zobacz [tworzenie wielu projektów równolegle](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **właściwości konfiguracji**, **konsolidatora** folderu.  
  
3.  Wybierz **wiersza polecenia** strony właściwości.  
  
4.  Modyfikowanie **dodatkowe opcje** właściwości, aby uwzględnić **/cgthreads:**`number`, gdzie `number` jest wartość z zakresu od 1 do 8, a następnie wybierz **OK**.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje konsolidatora](../../build/reference/linker-options.md)   
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)