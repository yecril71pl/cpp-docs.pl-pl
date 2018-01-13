---
title: -Fd (nazwa pliku bazy danych programu) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /FD
- VC.Project.VCCLWCECompilerTool.ProgramDataBaseFileName
- VC.Project.VCCLCompilerTool.ProgramDataBaseFileName
dev_langs: C++
helpviewer_keywords:
- /FD compiler option [C++]
- program database file name [C++]
- -FD compiler option [C++]
- PDB files, creating
- program database compiler option [C++]
- .pdb files, creating
- FD compiler option [C++]
ms.assetid: 3977a9ed-f0ac-45df-bf06-01cedd2ba85a
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a9cda26f310ec110c452394e960d3fb81d1f3e8a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fd-program-database-file-name"></a>/Fd (Nazwa pliku bazy danych programu)
Określa nazwę pliku dla pliku bazy danych (PDB) programu utworzone przez [/z7, / zi, /ZI (Format informacji debugowania)](../../build/reference/z7-zi-zi-debug-information-format.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
/Fdpathname  
```  
  
## <a name="remarks"></a>Uwagi  
 Bez **/Fd**, wartością domyślną nazwę pliku PDB VC*x*0.pdb, gdzie *x* jest wersję główną programu Visual C++ w użyciu.  
  
 Jeśli określono nazwę ścieżki, która nie zawiera nazwy pliku (ścieżka kończy się ukośnikiem), kompilator tworzy plik PDB o nazwie VC*x*pdb 0 w określonym katalogu.  
  
 Jeśli określono nazwę pliku, który nie zawiera rozszerzenia, kompilator używa .pdb jako rozszerzenie.  
  
 Ta opcja również nazwy pliku stanu (.idb), minimalna ponowna kompilacja i kompilacji przyrostowej.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **pliki wyjściowe** strony właściwości.  
  
4.  Modyfikowanie **nazwa pliku bazy danych programu** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ProgramDataBaseFileName%2A>.  
  
## <a name="example"></a>Przykład  
 Ten wiersz polecenia powoduje utworzenie pliku .pdb o nazwie PROG.pdb i .idb plik o nazwie PROG.idb:  
  
```  
CL /DDEBUG /Zi /FdPROG.PDB PROG.CPP  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Plik wyjściowy (/ F) opcje](../../build/reference/output-file-f-options.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [Określanie nazwy ścieżki](../../build/reference/specifying-the-pathname.md)