---
title: "-cgthreads (wątki generowania kodu) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /cgthreads
dev_langs: C++
helpviewer_keywords:
- /cgthreads compiler option (C++)
- -cgthreads compiler option (C++)
- cgthreads compiler option (C++)
- cgthreads
ms.assetid: 64bc768c-6caa-4baf-9dea-7cfa1ffb01c2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9eb497aa36a111db647e457a6f1a71475ef74d1e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cgthreads-code-generation-threads"></a>/cgthreads (wątki generowania kodu)
Ustawia liczbę wątków używanych podczas generowania optymalizacji i kod cl.exe.  
  
## <a name="syntax"></a>Składnia  
  
```  
/cgthreads[1-8]  
```  
  
## <a name="arguments"></a>Argumenty  
 liczba  
 Maksymalna liczba wątków dla cl.exe do użycia z zakresu od 1 do 8.  
  
## <a name="remarks"></a>Uwagi  
 **/Cgthreads** opcja określa maksymalną liczbę wątków cl.exe używa równolegle do optymalizacji i kodu generowania fazy kompilacji. Zwróć uwagę, że mogą być bez spacji między **/cgthreads** i `number` argumentu. Domyślnie cl.exe używa czterech wątków tak, jakby **/cgthreads4** zostały określone. Jeśli są dostępne, większej liczby rdzeni procesora większego `number` wartość może skrócić czas kompilacji. Ta opcja jest szczególnie przydatne, gdy jest połączona z [/GL (optymalizacja całego programu)](../../build/reference/gl-whole-program-optimization.md).  
  
 Można określić wiele poziomów równoległości dla kompilacji. Przełącznik msbuild.exe **/maxcpucount** określa liczbę procesów MSBuild, które mogą być uruchamiane równolegle. [/MP (kompilacja z wieloma procesami)](../../build/reference/mp-build-with-multiple-processes.md) flagi kompilatora określa liczbę procesów cl.exe, jednocześnie kompilowane do plików źródłowych. **/Cgthreads** opcji określa liczbę wątków używanych przez każdy proces cl.exe. Ponieważ procesor można uruchamiać tylko jako wiele wątków jednocześnie jako rdzeni procesora, nie jest przydatne do określenia większe wartości dla wszystkich tych opcji, w tym samym czasie i mogą być unikają szkodliwych dla produkcji. Aby uzyskać więcej informacji na temat sposobu tworzenia projektów równolegle, zobacz [tworzenie wielu projektów równolegle](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **właściwości konfiguracji**, **C/C++** folderu.  
  
3.  Wybierz **wiersza polecenia** strony właściwości.  
  
4.  Modyfikowanie **dodatkowe opcje** właściwości, aby uwzględnić **/cgthreads**`N`, gdzie `N` jest wartość z zakresu od 1 do 8, a następnie wybierz **OK**.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)