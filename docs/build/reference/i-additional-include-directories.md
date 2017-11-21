---
title: "-(Dodatkowe katalogi dołączenia) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AdditionalIncludeDirectories
- VC.Project.VCCLCompilerTool.AdditionalIncludeDirectories
- /I
- VC.Project.VCNMakeTool.IncludeSearchPath
dev_langs: C++
helpviewer_keywords:
- /I compiler option [C++]
- Additional Include Directories compiler option
- I compiler option [C++]
- -I compiler option [C++]
- set include directories
- include directories, compiler option [C++]
ms.assetid: 3e9add2a-5ed8-4d15-ad79-5b411e313a49
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 91868a657e4b537c286378276701915c1e160a77
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="i-additional-include-directories"></a>/I (Dodatkowe katalogi dołączenia)
Dodaje katalog do listy katalogów wyszukiwane plików dołączanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
/I[ ]directory  
```  
  
## <a name="arguments"></a>Argumenty  
 `directory`  
 Katalog do dodania do listy katalogów wyszukiwane plików dołączanych.  
  
## <a name="remarks"></a>Uwagi  
 Aby dodać więcej niż jeden katalog, użyj tej opcji więcej niż raz. Katalogi są przeszukiwane tylko w aż do znalezienia dołączanego określonego pliku.  
  
 Tej opcji można użyć z Ignoruj standardowe ścieżki dołączanych plików ([/X (Ignoruj standardowe ścieżki dołączanych plików)](../../build/reference/x-ignore-standard-include-paths.md)) opcja.  
  
 Kompilator szuka katalogów w następującej kolejności:  
  
1.  Katalogi z plikiem źródłowym.  
  
2.  Katalogów podanych **/I** opcji w kolejności CL napotka je.  
  
3.  Katalogach określonych w **INCLUDE** zmiennej środowiskowej.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **ogólne** strony właściwości.  
  
4.  Modyfikowanie **dodatkowe katalogi dołączenia** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalIncludeDirectories%2A>.  
  
## <a name="example"></a>Przykład  
 Polecenie wyszukuje pliki nagłówkowe zażądał MAIN.c w następującej kolejności: pierwszy w katalogu zawierającego MAIN.c, następnie w katalogu \INCLUDE, a następnie w katalogu \MY\INCLUDE i finally w katalogach przypisane do uwzględnienia zmiennej środowiskowej.  
  
```  
CL /I \INCLUDE /I\MY\INCLUDE MAIN.C  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)