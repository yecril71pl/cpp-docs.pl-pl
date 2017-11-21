---
title: -DLL (kompilowanie biblioteki DLL) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /dll
dev_langs: C++
helpviewer_keywords:
- -DLL linker option
- /DLL linker option [C++]
- exporting DLLs [C++], specifying exports
- DLLs [C++], building
- DLL linker option [C++]
ms.assetid: c7685aec-31d0-490f-9503-fb5171a23609
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6ca732d96eaa0ae7e4ffd805063156be519d41ab
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="dll-build-a-dll"></a>/DLL (Kompilowanie biblioteki DLL)
```  
/DLL  
```  
  
## <a name="remarks"></a>Uwagi  
 Opcja/dll tworzy bibliotekę DLL jako plik wyjściowy głównego. Biblioteki DLL zawiera zwykle eksportu, które mogą być używane przez inny program. Istnieją trzy metody Określanie eksportów wymienione w kolejności zalecane użycie:  
  
1.  [__declspec(dllexport)](../../cpp/dllexport-dllimport.md) w kodzie źródłowym  
  
2.  [EKSPORTÓW](../../build/reference/exports.md) instrukcji w plik .def  
  
3.  [/EXPORT](../../build/reference/export-exports-a-function.md) Specyfikacja polecenia łącza  
  
 Program można używać więcej niż jedna metoda.  
  
 Innym sposobem tworzenia biblioteki DLL jest z **biblioteki** instrukcji definicji modułu. Opcje /BASE i/dll razem są równoważne **biblioteki** instrukcji.  
  
 Nie należy określać tej opcji środowiska programistycznego; Ta opcja jest przeznaczona do użytku tylko w wierszu polecenia. Ta opcja jest ustawiana podczas tworzenia projektu biblioteki DLL przy użyciu Kreatora aplikacji.  
  
 Należy pamiętać, że w przypadku utworzenia biblioteki importu w krok wstępny, przed utworzeniem sieci dll, należy podać ten sam zestaw plików obiektów podczas tworzenia biblioteki dll, jako przekazaną podczas tworzenia biblioteki importu.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **właściwości konfiguracji** folderu.  
  
3.  Kliknij przycisk **ogólne** strony właściwości.  
  
4.  Modyfikowanie **typu konfiguracji** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCPropertySheet.ConfigurationType%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)