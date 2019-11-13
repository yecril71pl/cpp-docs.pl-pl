---
title: Redystrybuowanie biblioteki MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, redistributing
- redistributing MFC library
ms.assetid: 72714ce1-385e-4c1c-afa5-96b03e873866
ms.openlocfilehash: 7b38299bc39ce282769e40e915847b2220ec28ca
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965606"
---
# <a name="redistributing-the-mfc-library"></a>Redystrybuowanie biblioteki MFC

W przypadku dynamicznego łączenia aplikacji z biblioteką MFC należy ponownie rozpowszechnić zgodną bibliotekę MFC DLL. Na przykład jeśli aplikacja MFC została skompilowana przy użyciu wersji MFC, która jest dostarczana z programem Visual Studio 2015, należy ponownie rozpowszechnić mfc140. dll lub mfc140u. dll, w zależności od tego, czy aplikacja jest skompilowana dla wąskich znaków lub obsługi Unicode.

> [!NOTE]
>  Pliki mfc140. dll zostały pominięte w katalogu plików redystrybucyjnych w programie Visual Studio 2015 RTM. Zamiast tego można użyć wersji zainstalowanych przez program Visual Studio 2015 w katalogach Windows\System32 i Windows\syswow64.

Ponieważ wszystkie biblioteki MFC DLL używają udostępnionej wersji biblioteki środowiska uruchomieniowego języka C (CRT), może być również konieczne ponowne rozproszenie CRT. Wersja MFC, która jest dostarczana z programem Visual Studio 2015, korzysta z uniwersalnej biblioteki CRT, która jest dystrybuowana w ramach systemu Windows 10. Aby uruchomić aplikację MFC skompilowaną przy użyciu programu Visual Studio 2015 we wcześniejszych wersjach systemu Windows, należy ponownie rozpowszechnić uniwersalną CRT. Aby uzyskać informacje na temat sposobu redystrybucji uniwersalnej platformy CRT jako składnika systemu operacyjnego lub przy użyciu wdrożenia lokalnego, zobacz [wprowadzenie do uniwersalnej CRT](https://devblogs.microsoft.com/cppblog/introducing-the-universal-crt/). Aby pobrać uniwersalne środowisko CRT do wdrożenia centralnego w obsługiwanych wersjach systemu Windows, zobacz [Windows 10 Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=48234). W Windows SDK znajdują się informacje o architekturze redystrybucyjnej z wersjami ucrtbase. dll dla lokalnego wdrożenia. Domyślnie program Visual Studio instaluje je w folderze C:\Program Files (x86) \Windows Kits\10\Redist\ucrt\DLLs\ w podkatalogu specyficznym dla architektury.

Jeśli aplikacja została skompilowana przy użyciu wcześniejszej wersji biblioteki MFC, należy ponownie rozpowszechnić zgodną bibliotekę DLL CRT z katalogu plików redystrybucyjnych. Na przykład jeśli aplikacja MFC została skompilowana przy użyciu zestawu narzędzi Visual Studio 2013 (vc120), należy ponownie rozpowszechnić msvcr120. dll. Należy również ponownie rozpowszechnić pasującą MFC`<version>`u. dll lub MFC`<version>`. dll.

W przypadku statycznego łączenia aplikacji z MFC (oznacza to, że w przypadku określenia **użycia MFC w bibliotece statycznej** na karcie **Ogólne** w oknie dialogowym **strony właściwości** ) nie trzeba ponownie rozpowszechniać biblioteki MFC DLL. Chociaż konsolidacja statyczna może być używana do testowania i wewnętrznego wdrażania aplikacji, zaleca się, aby nie używać jej do redystrybucji MFC. Aby uzyskać więcej informacji na temat zalecanych strategii wdrażania C++ bibliotek wizualizacji, zobacz [Wybieranie metody wdrażania](choosing-a-deployment-method.md).

Jeśli aplikacja używa klas MFC, które implementują formant WebBrowser (na przykład [Klasa CHtmlView](../mfc/reference/chtmlview-class.md) lub [Klasa CHtmlEditView](../mfc/reference/chtmleditview-class.md)), zalecamy także zainstalowanie najnowszej wersji programu Microsoft Internet Explorer, aby komputer docelowy miał najbardziej aktualne pliki wspólnych kontrolek. (Co najmniej wymagany jest program Internet Explorer 4,0). Informacje dotyczące sposobu instalowania składników programu Internet Explorer są dostępne w artykule "artykuł 185375: jak utworzyć pojedynczy plik EXE instalacji programu Internet Explorer" w witrynie sieci Web pomoc techniczna firmy Microsoft.

Jeśli aplikacja używa klas baz danych MFC (na przykład Klasa [CRecordset](../mfc/reference/crecordset-class.md) i [Klasa formularzy CRecordView](../mfc/reference/crecordview-class.md)), należy ponownie rozesłać ODBC i wszystkie sterowniki ODBC używane przez aplikację.

Jeśli aplikacja MFC używa formantów Windows Forms, należy ponownie rozpowszechnić mfcmifc80. dll z aplikacją. Ta biblioteka DLL jest zestawem .NET ze znakiem silnej nazwy, który można rozpowszechniać za pomocą aplikacji w lokalnym folderze aplikacji lub przez wdrożenie go w globalnej pamięci podręcznej zestawów (GAC) przy użyciu programu [Gacutil. exe (Global Assembly Cache Tool)](/dotnet/framework/tools/gacutil-exe-gac-tool).

Jeśli ponownie dystrybuujesz bibliotekę MFC DLL, pamiętaj o ponownym rozproszeniu wersji detalicznej, a nie wersji do debugowania. Wersje debugowania bibliotek DLL nie są redystrybucyjne. Nazwy wersji debugowania bibliotek DLL MFC kończą się znakiem "d", na przykład Mfc140d. dll.

Można redystrybuować MFC przy użyciu programu VCRedist_*Architecture*. exe, modułów scalania, które są zainstalowane z programem Visual Studio, lub przez wdrożenie biblioteki MFC DLL w tym samym folderze, w którym znajduje się aplikacja. Aby uzyskać więcej informacji na temat sposobu redystrybucji MFC, zobacz redystrybuuj [pliki wizualne C++ ](redistributing-visual-cpp-files.md).

## <a name="installation-of-localized-mfc-components"></a>Instalacja zlokalizowanych składników MFC

W przypadku podjęcia decyzji o zlokalizowaniu aplikacji przez zainstalowanie biblioteki DLL lokalizacji MFC należy użyć plików scalonych (. msm). Jeśli na przykład chcesz zlokalizować aplikację na komputerze z procesorem x86, musisz scalić Microsoft_VC`<version>`_MFCLOC_x86. MSM z pakietem instalacyjnym dla komputera x86.

Pliki redystrybucyjne. MSM zawierają biblioteki DLL, które są używane do lokalizacji. Istnieje jedna biblioteka DLL dla każdego obsługiwanego języka. Proces instalacji instaluje te biblioteki DLL w folderze%windir%\system32\ na komputerze docelowym.

Aby uzyskać więcej informacji o sposobie lokalizowania aplikacji MFC, zobacz [TN057: Lokalizacja składników MFC](../mfc/tn057-localization-of-mfc-components.md).

Można redystrybuować biblioteki DLL lokalizacji MFC przez wdrożenie biblioteki MFC DLL w folderze lokalnym aplikacji. Aby uzyskać więcej informacji na temat sposobu rozpowszechniania C++ bibliotek wizualizacji, zobacz [Redystrybuowanie plików wizualnych C++ ](redistributing-visual-cpp-files.md).

## <a name="see-also"></a>Zobacz także

[Ponowne dystrybuowanie plików programu Visual C++](redistributing-visual-cpp-files.md)
