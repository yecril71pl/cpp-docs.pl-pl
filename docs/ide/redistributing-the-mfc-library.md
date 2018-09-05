---
title: Redystrybuowanie biblioteki MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, redistributing
- redistributing MFC library
ms.assetid: 72714ce1-385e-4c1c-afa5-96b03e873866
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e23358e17558c436d82a3226f84c35a59bf63a1
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691219"
---
# <a name="redistributing-the-mfc-library"></a>Redystrybuowanie biblioteki MFC
Jeśli dynamicznie połączysz aplikację do biblioteki MFC, należy ponownie rozesłać zgodne biblioteki MFC DLL. Na przykład jeśli aplikacja MFC został utworzony przy użyciu wersji MFC, który jest dostarczany z programem Visual Studio 2015, należy ponownie rozesłać mfc140.dll lub mfc140u.dll, w zależności od tego, czy aplikacja jest kompilowana wąskie znaki lub obsługi standardu Unicode.  
  
> [!NOTE]
>  Pliki mfc140.dll zostały pominięte pliki redystrybucyjne katalogu w Visual Studio 2015 RTM. Wersje zainstalowane przez program Visual Studio 2015 w katalogach Windows\system32 i Windows\syswow64 zamiast tego można użyć.  
  
 Ponieważ wszystkie biblioteki MFC DLL używają udostępnionych wersji biblioteki wykonawczej języka C (CRT), konieczne może być Ponowna dystrybucja CRT. Wersji MFC, który jest dostarczany z programem Visual Studio 2015 korzysta z biblioteki CRT uniwersalnej jest rozpowszechniany jako element systemu Windows 10. Aby uruchomić aplikację MFC skompilowanych przy użyciu programu Visual Studio 2015 w starszych wersjach systemu Windows, należy ponownie rozesłać Universal CRT. Aby uzyskać informacji na temat sposobu redystrybucji universal CRT, jako składnik systemu operacyjnego lub za pomocą lokalnego wdrażania, zobacz [wprowadzenie do Universal CRT](http://go.microsoft.com/fwlink/p/?linkid=617977). Aby pobrać uniwersalne CRT w przypadku wdrożenia centralnego w obsługiwanych wersjach systemu Windows, zobacz [systemu Windows 10 uniwersalnego środowiska uruchomieniowego C](http://go.microsoft.com/fwlink/p/?LinkId=619489). Pakiet redystrybucyjny architektury wersje ucrtbase.dll lokalnego wdrożenia znajdują się w zestawie Windows SDK. Domyślnie program Visual Studio instaluje je w \Windows Kits\10\Redist\ucrt\DLLs\ C:\Program Files (x86) w podkatalogu architektury.  
  
 Jeśli aplikacja został utworzony przy użyciu starszej wersji biblioteki MFC, należy ponownie rozesłać pasującego DLL CRT z katalogu pliki redystrybucyjne. Na przykład jeśli aplikacja MFC został utworzony przy użyciu zestawu narzędzi Visual Studio 2013 (vc120), należy ponownie rozesłać msvcr120.dll. Masz również do redystrybucji mfc pasującego`<version>`u.dll lub mfc`<version>`.dll.  
  
 Jeśli statycznie połączysz aplikacje do MFC (to znaczy, jeśli określisz **Użyj MFC w bibliotece statycznej** na **ogólne** karcie **stron właściwości** okno dialogowe), nie masz Redystrybucja biblioteki MFC DLL. Jednak mimo że łączenie statyczne może działać w przypadku testowania i wewnętrznego wdrażania aplikacji, zaleca się że nie używasz go do redystrybucji MFC. Aby uzyskać więcej informacji dotyczących zalecanych strategii wdrażania bibliotek Visual C++, zobacz [Wybieranie metody wdrażania](../ide/choosing-a-deployment-method.md).  
  
 Jeśli aplikacja używa klas MFC, które implementują formant WebBrowser (na przykład [klasa CHtmlView](../mfc/reference/chtmlview-class.md) lub [klasa CHtmlEditView](../mfc/reference/chtmleditview-class.md)), firma Microsoft zaleca również zainstalowanie najbardziej aktualnej wersji Program Microsoft Internet Explorer, aby komputer docelowy będzie miał najbardziej aktualne pliki wspólnej kontroli. (Co najmniej program Internet Explorer 4.0 jest wymagany). Informacje dotyczące sposobu instalowania składników programu Internet Explorer są dostępne w "Artykule 185375: jak do utworzyć pojedynczy EXE instalacji programu Internet Explorer" w witrynie Microsoft Support.  
  
 Jeśli aplikacja używa klas baz danych MFC (na przykład [klasa CRecordset](../mfc/reference/crecordset-class.md) i [klasa CRecordView](../mfc/reference/crecordview-class.md)), można redystrybuować ODBC i wszystkie sterowniki ODBC używane przez aplikację.  
  
 Jeśli aplikacja MFC używa formantów Windows Forms, musi ponownie rozdzielić mfcmifc80.dll z aplikacją. Ta biblioteka DLL jest silne podpisanym zestaw .NET, który można rozpowszechniać za pomocą aplikacji w aplikacji folderu lokalnego lub wdrażając go do globalnej pamięci podręcznej zestawów (GAC) za pomocą [Gacutil.exe (Global Assembly Cache Tool)](/dotnet/framework/tools/gacutil-exe-gac-tool).  
  
 Jeśli ponownie dystrybuujesz bibliotekę MFC DLL, upewnij się ponownie rozesłać wersję handlową, a nie wersji do debugowania. Wersje debugowania bibliotek DLL nie są do dystrybucji. Nazwy wersji do debugowania biblioteki MFC DLL kończyć się znakiem "d", na przykład Mfc140d.dll.  
  
 Można redystrybuować MFC przy użyciu albo VCRedist_*architektury*.exe, moduły scalania, które są instalowane z programem Visual Studio lub wdrażając biblioteki MFC DLL w tym samym folderze co aplikacja. Aby uzyskać więcej informacji na temat sposobu redystrybucji MFC, zobacz [Redistributing Visual C++ Files](../ide/redistributing-visual-cpp-files.md).  
  
## <a name="installation-of-localized-mfc-components"></a>Instalacja składników zlokalizowanej MFC  
 Jeśli zdecydujesz się zlokalizować aplikację przez zainstalowanie lokalizacji MFC DLL, należy użyć plików scalania do (dystrybucji.msm). Na przykład, jeśli chcesz zlokalizować aplikację na x86 komputera, musisz scalić Microsoft_VC`<version>`_MFCLOC_x86.msm pakietem instalacyjnym dla x86 komputera.  
  
 Pliki pakietu redystrybucyjnego .msm zawierają biblioteki dll, które są używane dla lokalizacji. Istnieje jeden DLL dla każdego z obsługiwanych języków. Proces instalacji instaluje te biblioteki dll w folderze %windir%\system32\ na komputerze docelowym.  
  
 Aby uzyskać więcej informacji o sposobie lokalizowania aplikacji MFC, zobacz [TN057: Lokalizacja składników MFC](../mfc/tn057-localization-of-mfc-components.md).
  
 Można redystrybuować Lokalizacja biblioteki MFC DLL przez wdrożenie biblioteki MFC DLL w lokalnym folderze aplikacji. Aby uzyskać więcej informacji na temat sposobu redystrybucji bibliotek Visual C++, zobacz [Redistributing Visual C++ Files](../ide/redistributing-visual-cpp-files.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Ponowne dystrybuowanie plików programu Visual C++](../ide/redistributing-visual-cpp-files.md)
