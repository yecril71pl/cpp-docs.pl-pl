---
title: -Fe (Nazwij plik EXE) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /fe
dev_langs: C++
helpviewer_keywords:
- -Fe compiler option [C++]
- executable files, renaming
- rename file compiler option [C++]
- /Fe compiler option [C++]
- Fe compiler option [C++]
ms.assetid: 49f594fd-5e94-45fe-a1bf-7c9f2abb6437
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b66c473c49527dff395d206594a314b527c4f914
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fe-name-exe-file"></a>/Fe (Nazwij plik EXE)
Określa nazwę i katalog dla pliku .exe lub DLL utworzony przez kompilator.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Fepathname  
```  
  
## <a name="remarks"></a>Uwagi  
 Bez tej opcji kompilator zapewnia pliku domyślnej nazwy przy użyciu podstawowego nazwa pierwszego pliku źródłowego lub obiekt określony w wierszu polecenia i rozszerzenie .exe lub .dll.  
  
 Jeśli określisz[/c (Kompiluj bez konsolidacji)](../../build/reference/c-compile-without-linking.md), aby skompilować bez konsolidacji, **/Fe** nie ma wpływu.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **ogólne**strony właściwości.  
  
4.  Modyfikowanie **pliku wyjściowego** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.  
  
## <a name="example"></a>Przykład  
 Następujące polecenie w wierszu kompiluje i łączy wszystkie pliki źródłowe C w bieżącym katalogu. Wynikowy plik wykonywalny nosi nazwę PROCESS.exe i jest tworzone w katalogu C:\BIN.  
  
```  
CL /FeC:\BIN\PROCESS *.C  
```  
  
## <a name="example"></a>Przykład  
 Następujące polecenie w wierszu tworzy plik wykonywalny w `C:\BIN` o takiej samej nazwie podstawowej jako pierwszy plik źródła lub obiektu:  
  
```  
CL /FeC:\BIN\ *.C  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Plik wyjściowy (/ F) opcje](../../build/reference/output-file-f-options.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [Określanie nazwy ścieżki](../../build/reference/specifying-the-pathname.md)