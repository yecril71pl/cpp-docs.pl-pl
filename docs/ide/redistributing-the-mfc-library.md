---
title: Redystrybuowanie biblioteki MFC | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, redistributing
- redistributing MFC library
ms.assetid: 72714ce1-385e-4c1c-afa5-96b03e873866
caps.latest.revision: "32"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9ca153ec9ca079bf13b1c1c1dcedd6e41497307f
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="redistributing-the-mfc-library"></a>Redystrybuowanie biblioteki MFC
Dynamiczne łącze aplikacji do biblioteki MFC, należy wykonać ponowną dystrybucję zgodne biblioteki MFC DLL. Na przykład jeśli aplikacja MFC jest zbudowany przy użyciu wersji biblioteki MFC, który jest dostarczany z programem Visual Studio 2015, należy ponownie rozesłać mfc140.dll lub mfc140u.dll, w zależności od tego, czy aplikacja jest kompilowany dla wąskie znaków lub obsługi formatu Unicode.  
  
> [!NOTE]
>  Pliki mfc140.dll zostały pominięte z katalogu plików pakietu redystrybucyjnego programu Visual Studio 2015 RTM. Wersje zainstalowane przez Visual Studio 2015 w katalogach Windows\system32 i Windows\syswow64 zamiast tego można użyć.  
  
 Ponieważ wszystkie biblioteki DLL MFC korzystają z udostępnionej wersji biblioteki środowiska uruchomieniowego C (CRT), konieczne może być ponownie rozesłać CRT. Wersja MFC, który jest dostarczany z programem Visual Studio 2015 korzysta z biblioteki CRT uniwersalnego jest rozpowszechniany jako część systemu Windows 10. Aby uruchomić aplikację MFC utworzony za pomocą programu Visual Studio 2015 we wcześniejszych wersjach systemu Windows, należy ponownie rozesłać Universal CRT. Aby uzyskać informacje na temat sposobu ponownej dystrybucji universal CRT jako składnik systemu operacyjnego lub przy użyciu lokalnego wdrożenia, zobacz [wprowadzenie Universal CRT](http://go.microsoft.com/fwlink/p/?linkid=617977). Aby pobrać uniwersalne CRT centralnej wdrożenia w obsługiwanych wersjach systemu Windows, zobacz [Windows 10 Universal C Runtime](http://go.microsoft.com/fwlink/p/?LinkId=619489). Pakiet redystrybucyjny wersje architektury ucrtbase.dll dla wdrożenia lokalnego znajdują się w zestawie Windows SDK. Domyślnie program Visual Studio instaluje je w \Windows Kits\10\Redist\ucrt\DLLs\ C:\Program Files (x86) w podkatalogu architektury.  
  
 Jeśli aplikacja jest zbudowany przy użyciu wcześniejszej wersji biblioteki MFC, należy ponownie rozesłać pasującego DLL CRT z katalogu plików pakietu redystrybucyjnego. Na przykład jeśli aplikacja MFC jest utworzony za pomocą narzędzi Visual Studio 2013 (vc120), należy ponownie rozesłać msvcr120.dll. Należy ponownie rozesłać pasującego mfc`<version>`u.dll lub mfc`<version>`dll.  
  
 Jeśli statycznie Połącz swoją aplikację MFC (to znaczy, jeśli określono **Użyj MFC w bibliotece statycznej** na **ogólne** karcie **strony właściwości** okno dialogowe), nie masz Aby ponownie rozesłać biblioteki MFC DLL. Jednak mimo że statycznego łączenia mogą działać w przypadku testowania i wewnętrznego wdrażania aplikacji, zaleca się czy nie umożliwia ona ponownie rozesłać MFC. Aby uzyskać więcej informacji na temat zalecanych strategii wdrażania bibliotek języka Visual C++, zobacz [Wybieranie metody wdrażania](../ide/choosing-a-deployment-method.md).  
  
 Jeśli aplikacja korzysta z klas MFC, które implementują formant WebBrowser (na przykład [klasy CHtmlView](../mfc/reference/chtmlview-class.md) lub [klasy CHtmlEditView](../mfc/reference/chtmleditview-class.md)), zalecamy również zainstalowanie najnowszej wersji programu Program Microsoft Internet Explorer, aby komputer docelowy miał najbardziej aktualne wspólne pliki formantu. (Program Internet Explorer w wersji 4.0 jest wymagany.) Informacje o sposobie instalowania składników programu Internet Explorer są dostępne w "Artykułu 185375: jak do tworzenia pojedynczego EXE instalacji programu Internet Explorer" w witrynie sieci Web Microsoft Support.  
  
 Jeśli aplikacja korzysta z klasami baz danych MFC (na przykład [crecordset — klasa](../mfc/reference/crecordset-class.md) i [CRecordView — klasa](../mfc/reference/crecordview-class.md)), należy ponownie rozesłać ODBC i aplikacja używa sterowników ODBC. Aby uzyskać więcej informacji, zobacz [redystrybuowanie plików obsługi baz danych](../ide/redistributing-database-support-files.md).  
  
 Jeśli aplikacja MFC używa formanty formularzy systemu Windows, należy ponownie rozesłać mfcmifc80.dll z aplikacją. Ta biblioteka DLL jest silnej nazwy podpisany zestaw .NET, które mogą być rozpowszechniane za pomocą aplikacji w swojej aplikacji w lokalnym folderze lub przez wdrożenie jej do globalnej pamięci podręcznej zestawów (GAC) przy użyciu [Gacutil.exe (narzędzie globalnej pamięci podręcznej zestawów)](/dotnet/framework/tools/gacutil-exe-gac-tool).  
  
 Jeśli wszystkie biblioteki MFC DLL, upewnij się, że Ponowna dystrybucja wersji detalicznej, a nie wersji do debugowania. Wersje bibliotek DLL do debugowania nie są do dystrybucji. Nazwy wersje biblioteki MFC dll do debugowania kończyć się "d", na przykład Mfc140d.dll.  
  
 Ponowna dystrybucja MFC przy użyciu albo VCRedist_*architektura*.exe, modułów scalania, które są zainstalowane z programem Visual Studio lub przez wdrożenie biblioteki MFC DLL w folderze aplikacji. Aby uzyskać więcej informacji o sposobie Ponowna dystrybucja MFC, zobacz [redystrybuowanie pliki Visual C++](../ide/redistributing-visual-cpp-files.md).  
  
## <a name="installation-of-localized-mfc-components"></a>Instalacja zlokalizowanych składników MFC  
 Jeśli zdecydujesz się do zlokalizowania aplikacji, instalując Lokalizacja biblioteki MFC DLL, należy użyć plików pakietu redystrybucyjnego scalania (.msm). Na przykład, jeśli chcesz, do zlokalizowania aplikacji na x86 komputera, należy scalić Microsoft_VC`<version>`_MFCLOC_x86.msm do pakietu instalacyjnego dla x86 komputera.  
  
 Pliki pakietu redystrybucyjnego .msm zawierają bibliotek DLL, które są używane do lokalizacji. Brak jednej biblioteki DLL dla każdego z obsługiwanych języków. Proces instalacji instaluje te biblioteki dll w folderze %windir%\system32\ na komputerze docelowym.  
  
 Aby uzyskać więcej informacji na temat do zlokalizowania w aplikacjach MFC, zobacz [TN057: Lokalizacja składników MFC](../mfc/tn057-localization-of-mfc-components.md)oraz [208983 artykuł: jak przy użyciu Lokalizacja biblioteki DLL MFC](http://go.microsoft.com/fwlink/p/?linkid=198025) w witrynie sieci Web Microsoft Support.  
  
 Można ponownie rozesłać Lokalizacja biblioteki MFC DLL przez wdrożenie biblioteki MFC DLL w lokalnym folderze aplikacji. Aby uzyskać więcej informacji o sposobie Ponowna dystrybucja bibliotek języka Visual C++, zobacz [redystrybuowanie pliki Visual C++](../ide/redistributing-visual-cpp-files.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Ponowne dystrybuowanie plików programu Visual C++](../ide/redistributing-visual-cpp-files.md)