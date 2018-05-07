---
title: Manifest wejściowy narzędzia i dane wyjściowe właściwości (Visual C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCManifestTool.OutputManifestFile
- VC.Project.VCManifestTool.InputResourceManifests
- VC.Project.VCManifestTool.EmbedManifest
- VC.Project.VCManifestTool.AdditionalManifestFiles
- VC.Project.VCManifestTool.DependencyInformationFile
- VC.Project.VCManifestTool.OutputResourceManifest
- VC.Project.VCManifestTool.GenerateCatalogFiles
dev_langs:
- C++
ms.assetid: a8bb20f6-7ace-45ca-bab0-b4f4a5caf170
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 15be7636188bb670febd7875974d683c1d78360f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="input-and-output-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Dane wejściowe i wyjściowe narzędzie, właściwości konfiguracji manifestu &lt;Projectname&gt; stron właściwości — okno dialogowe
To okno dialogowe służy do określania opcji wejściowymi i wyjściowymi dla [Mt.exe](http://msdn.microsoft.com/library/aa375649).  
  
 Aby uzyskać dostęp do tej strony właściwości — okno dialogowe, otwórz strony właściwości projektu lub arkuszu właściwości. Rozwiń węzeł **narzędziu manifestu** węźle **właściwości konfiguracji**, a następnie wybierz **wejściowa i wyjściowa**.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Dodatkowe pliki manifestu**  
 Używa **/manifest** opcję, aby określić pełne ścieżki dodatkowe pliki manifestu przetwarzające narzędzia manifestu lub scalania. Pełne ścieżki są rozdzielone średnikami.  
  
 **Manifesty zasobów wejściowych**  
 Używa **/inputresource** opcję, aby określić pełną ścieżkę zasobu typu RT_MANIFEST jako danych wejściowych narzędzia manifestu. Ścieżka może następować identyfikator określonego zasobu. Na przykład:  
  
 `dll_with_manifest.dll;#1`  
  
 Identyfikator zasobu jest opcjonalny i domyślnie ustawiany na CREATEPROCESS_MANIFEST_RESOURCE_ID w winuser.h.  
  
 **Osadź Manifest**  
 **Tak** określa system projektu zostanie osadzić pliku manifestu aplikacji w zestawie.  
  
 **Nie** Określa, czy system projektu spowoduje utworzenie pliku manifestu aplikacji jako plik samodzielny.  
  
 **Plik wynikowy manifestu**  
 Określa nazwę pliku manifestu wyjściowego. Ta właściwość jest opcjonalna, gdy tylko jeden plik manifestu jest wykonywane są operacje za pomocą narzędzia manifestu.  
  
 **Plik zasobu manifestu**  
 Określa dane wyjściowe pliki zasobów używany do osadzania manifestu w danych wyjściowych projektu.  
  
 **Generuj pliki katalogów**  
 Używa **/makecdfs** opcję, aby określić, że narzędzia manifestu wygeneruje katalogu definicji plików (.cdf), które służą do tworzenia katalogów.  
  
 **Generuj Manifest z biblioteki ManagedAssembly**  
 Generuje manifest z zarządzanego zestawu. (**- managedassemblyname: *** pliku*).  
  
 **Pomijanie elementu zależności**  
 Używane z **- managedassembly** opcji. Ten tag pomija generację zależności elementów w manifeście końcowym.  
  
 **Generowanie tagi kategorii**  
 Używane z **- managedassembly** opcji. Ten tag powoduje, że tagi kategorii do wygenerowania.  
  
 **Włącz świadomości DPI**  
 Określa, czy aplikacja jest obsługującą ustawienia DPI. Domyślnym ustawieniem jest **tak** w projektach MFC i **nr** inaczej, ponieważ tylko projekty MFC utworzone w świadomości DPI. Można zastąpić to ustawienie, aby **tak** Jeśli dodasz kod obsługujący różne ustawienia DPI. Aplikacja może wyglądać rozmytego lub mały, jeśli zostanie ustawiona jako obsługującą ustawienia DPI gdy nie jest.  
  
## <a name="see-also"></a>Zobacz też  
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)   
 [Strony właściwości narzędzia manifestu](../ide/manifest-tool-property-pages.md)   
 [Praca z właściwościami projektu](../ide/working-with-project-properties.md)   