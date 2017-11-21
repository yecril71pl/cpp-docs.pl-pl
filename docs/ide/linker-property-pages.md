---
title: "Strony właściwości konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.RegisterOutput
- VC.Project.VCLinkerTool.OVERWRITEImportLibrary
- VC.Project.VCLinkerTool.UseLibraryDependencyInputs
- VC.Project.VCLinkerTool.LinkLibraryDependencies
dev_langs: C++
helpviewer_keywords:
- per-user redirection
- Linker property pages
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c958b0bce27effc5362d107a3b6abe9fcc761d39
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-property-pages"></a>Strony właściwości konsolidatora
W tym temacie omówiono następujące właściwości na **ogólne** strony właściwości konsolidatora:  
  
 **Ignoruj bibliotekę importowaną**  
 Informuje konsolidatora, aby nie próbował łączyć żadnych plików wyjściowych .lib wygenerowanych podczas tej kompilacji z żadnym zależnym projektem. Dzięki temu system projektu może obsługiwać pliki .dll, które podczas kompilacji nie tworzą pliku .lib. Jeżeli projekt zależy od innego projektu, który tworzy bibliotekę DLL, system projektu automatycznie połączy plik .lib generowany przez ten projekt podrzędny. Może to być niepotrzebne w projektach generujących pliki COM DLL lub pliki DLL z samymi zasobami, ponieważ te pliki DLL nie eksportują żadnych istotnych danych. Jeśli biblioteka DLL nie eksportuje żadnych danych, konsolidator nie utworzy pliku .lib. Jeśli na dysku nie ma pliku .lib eksportu, a system projektu nakaże konsolidatorowi nawiązanie połączenia z tym (brakującym) plikiem DLL, operacja łączenia nie powiedzie się.  
  
 Użyj **Ignoruj bibliotekę importowaną** Aby rozwiązać ten problem. Po ustawieniu wartości `Yes` system projektu będzie ignorował obecność lub brak takiego pliku .lib oraz spowoduje, że żaden projekt zależny od tego projektu nie będą się łączył z tym nieistniejącym plikiem .lib.  
  
 Do uzyskania programowego dostępu do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>.  
  
 **Rejestruj wynik**  
 Powoduje wykonanie polecenia regsvr32.exe/s $(TargetPath), które działa tylko wobec projektów bibliotek .dll. W projektach plików .exe właściwość jest ignorowana. Aby zarejestrować dane wyjściowe pliku .exe, należy w konfiguracji zdefiniować zdarzenie uruchamiane po kompilacji, które będzie wykonywało niestandardową rejestrację zawsze wymaganą przy rejestrowaniu plików .exe.  
  
 Do uzyskania programowego dostępu do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>.  
  
 **Przekierowanie na użytkownika**  
 Rejestracja w programie Visual Studio tradycyjnie przeprowadzono wpisów z HKEY_CLASSES_ROOT (HKCR). Z [!INCLUDE[wiprlhext](../c-runtime-library/reference/includes/wiprlhext_md.md)], aby dostęp HKCR należy uruchomić program Visual Studio w trybie podniesionych uprawnień. Deweloperzy nie zawsze chcą pracować w trybie podwyższonych uprawnień, a mimo to muszą dokonywać rejestracji. Przekierowanie na użytkownika umożliwia rejestrowanie bez konieczności pracy w tym trybie.  
  
 Mechanizm przekierowania na użytkownika wymusza, aby wszelkie operacje zapisu do klucza HKCR były przekierowywane do klucza HKEY_CURRENT_USER (HKCU). Przekierowanie na użytkownika jest wyłączona, może spowodować [projektu kompilacji błąd PRJ0050](../error-messages/tool-errors/project-build-error-prj0050.md) kiedy program próbuje zapisać w kluczu HKCR.  
  
 **Zależności biblioteki konsolidacji**  
 Pozwala wybrać, czy ma być stosowane łączenie plików .lib generowanych przez zależne projekty. Zazwyczaj jest to pożądane.  
  
 Można również określić plik .obj, podając nazwę pliku i ścieżki względnej, na przykład **... \\.. \MyLibProject\MyObjFile.obj**. Jeśli kodu źródłowego dla pliku obj. #includes prekompilowanego nagłówka, na przykład pch.h, a następnie pch.obj plik znajduje się w tym samym folderze co **MyObjFile.obj** i musisz również dodać **pch.obj** jako dodatkowego zależności.  
  
 **Używaj wejścia zależności biblioteki**  
 W dużym projekcie, gdy projekt zależny tworzy plik .lib, łączenie przyrostowe jest wyłączone. Jeśli istnieje wiele projektów zależnych generujących pliki .lib, kompilowanie aplikacji może trwać długo. Gdy ta właściwość ma wartość `Yes`, system projektu łączy pliki .obj dla plików .libs tworzonych przez projekty zależne, umożliwiając w ten sposób łączenie przyrostowe.  
  
 Aby uzyskać informacje dotyczące dostępu do **ogólne** strony właściwości konsolidatora, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Katalogi VC ++, projekty i rozwiązania, opcje — Okno dialogowe](http://msdn.microsoft.com/en-us/e027448b-c811-4c3d-8531-4325ad3f6e02)   
 [Strony właściwości](../ide/property-pages-visual-cpp.md)