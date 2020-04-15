---
title: Redystrybuowanie biblioteki MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, redistributing
- redistributing MFC library
ms.assetid: 72714ce1-385e-4c1c-afa5-96b03e873866
ms.openlocfilehash: e1434bee6d134d4c02b2c06125d340a68a6c305d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359901"
---
# <a name="redistributing-the-mfc-library"></a>Redystrybuowanie biblioteki MFC

Jeśli dynamicznie połączyć aplikację z biblioteki MFC, należy redystrybuować pasujące MFC DLL. Na przykład jeśli aplikacja MFC jest zbudowany przy użyciu wersji MFC, który jest dostarczany z visual studio 2015, należy redystrybuować mfc140.dll lub mfc140u.dll, w zależności od tego, czy aplikacja jest skompilowana dla wąskich znaków lub obsługi Unicode.

> [!NOTE]
> Pliki mfc140.dll zostały pominięte w katalogu plików redystrybucyjnych w programie Visual Studio 2015 RTM. Wersji zainstalowanych w programie Visual Studio 2015 można używać w katalogach Windows\system32 i Windows\syswow64.

Ponieważ wszystkie biblioteki DLL MFC używają udostępnionej wersji biblioteki wykonawczej C (CRT), może być również konieczne rozpowszechnienie crt. Wersja MFC, która jest dostarczana z programem Visual Studio 2015 używa uniwersalnej biblioteki CRT, która jest dystrybuowana jako część systemu Windows 10. Aby uruchomić aplikację MFC skompilowane przy użyciu programu Visual Studio 2015 we wcześniejszych wersjach systemu Windows, należy rozpowszechniać uniwersalny crt. Aby uzyskać informacje na temat redystrybucji uniwersalnego CRT jako składnika systemu operacyjnego lub przy użyciu wdrożenia [lokalnego, zobacz Wprowadzenie uniwersalnego CRT](https://devblogs.microsoft.com/cppblog/introducing-the-universal-crt/). Aby pobrać uniwersalny crt do centralnego wdrożenia w obsługiwanych wersjach systemu Windows, zobacz [Uniwersalny czas pracy systemu Windows 10 C](https://www.microsoft.com/download/details.aspx?id=48234). Redystrybucyjne wersje ucrtbase.dll specyficzne dla architektury dla wdrożenia lokalnego znajdują się w zestawie Windows SDK. Domyślnie program Visual Studio instaluje je w języku C:\Program Files (x86)\Windows Kits\10\Redist\ucrt\DLLs\ w katalogu podrzędnym specyficznym dla architektury.

Jeśli aplikacja jest zbudowana przy użyciu wcześniejszej wersji biblioteki MFC, należy rozpowszechniać pasujące biblioteki DLL CRT z katalogu plików redystrybucyjnych. Na przykład jeśli aplikacja MFC jest zbudowany przy użyciu zestawu narzędzi Visual Studio 2013 (vc120), należy redystrybuować msvcr120.dll. Należy również redystrybuować`<version>`pasujące mfc`<version>`u.dll lub mfc .dll.

Jeśli statycznie połączyć aplikację z MFC (oznacza to, że jeśli określisz **Użyj MFC w bibliotece statycznej** na karcie **Ogólne** w oknie dialogowym **Strony właściwości),** nie trzeba redystrybuować biblioteki DLL MFC. Jednak mimo że łączenie statyczne może działać do testowania i wdrażania wewnętrznego aplikacji, zaleca się, aby nie używać go do redystrybucji MFC. Aby uzyskać więcej informacji na temat zalecanych strategii wdrażania bibliotek języka Visual C++, zobacz [Wybieranie metody wdrażania](choosing-a-deployment-method.md).

Jeśli aplikacja używa klas MFC, które implementują formant WebBrowser (na przykład [CHtmlView Class](../mfc/reference/chtmlview-class.md) lub [CHtmlEditView Class),](../mfc/reference/chtmleditview-class.md)zaleca się również zainstalowanie najnowszej wersji programu Microsoft Internet Explorer, tak aby komputer docelowy miał najbardziej aktualne typowe pliki kontrolne. (Co najmniej wymagany jest program Internet Explorer 4.0). Informacje dotyczące instalowania składników programu Internet Explorer są dostępne w artykule "Artykuł 185375: Jak utworzyć pojedynczą instalację programu EXE programu Internet Explorer" w witrynie pomocy technicznej firmy Microsoft.

Jeśli aplikacja używa klas bazy danych MFC (na przykład [CRecordset Class](../mfc/reference/crecordset-class.md) i [CRecordView Class),](../mfc/reference/crecordview-class.md)należy rozpowszechniać odbc i wszystkie sterowniki ODBC, które używa aplikacji.

Jeśli aplikacja MFC używa formantów Windows Forms, należy rozpowszechniać mfcmifc80.dll z aplikacją. Ta biblioteka DLL jest zestawem .NET podpisanym o silnej nazwie, który można redystrybuować za pomocą aplikacji w folderze lokalnym aplikacji lub wdrażając ją w globalnej pamięci podręcznej zestawów (GAC) przy użyciu [programu Gacutil.exe (Global Assembly Cache Tool).](/dotnet/framework/tools/gacutil-exe-gac-tool)

Jeśli ponownie rozdzielasz bibliotekę DLL MFC, upewnij się, że ponownie rozpowszechniasz wersję sieci sprzedaży detalicznej, a nie wersję debugowania. Wersje debugowania bibliotek DLL nie są redystrybucyjne. Nazwy wersji debugowania bibliotek DLL MFC kończą się na "d", na przykład Mfc140d.dll.

Można redystrybuować MFC przy*architecture*użyciu architektury VCRedist_ .exe, modułów scalania, które są zainstalowane w programie Visual Studio lub przez wdrożenie biblioteki DLL MFC do tego samego folderu co aplikacja. Aby uzyskać więcej informacji na temat redystrybucji MFC, zobacz [Redystrybucja plików Visual C++](redistributing-visual-cpp-files.md).

## <a name="installation-of-localized-mfc-components"></a>Instalacja zlokalizowanych komponentów MFC

Jeśli zdecydujesz się zlokalizować aplikację, instalując bibliotekę DLL lokalizacji MFC, należy użyć redystrybucyjnych plików scalania (.msm). Na przykład, jeśli chcesz zlokalizować aplikację na komputerze x86, należy`<version>`scalić Microsoft_VC _MFCLOC_x86.msm do pakietu instalacyjnego dla komputera x86.

Redystrybucyjne pliki .msm zawierają biblioteki DLL, które są używane do lokalizacji. Dla każdego obsługiwanego języka jest jedna biblioteka DLL. Proces instalacji instaluje te biblioteki DLL w folderze %windir%\system32\ na komputerze docelowym.

Aby uzyskać więcej informacji na temat lokalizowania aplikacji MFC, zobacz [TN057: Lokalizacja składników MFC](../mfc/tn057-localization-of-mfc-components.md).

Biblioteki DLL lokalizacji MFC można redystrybuować, wdrażając bibliotekę DLL MFC w folderze lokalnym aplikacji. Aby uzyskać więcej informacji na temat redystrybucji bibliotek programu Visual C++, zobacz [Redystrybucja plików Visual C++](redistributing-visual-cpp-files.md).

## <a name="see-also"></a>Zobacz też

[Ponowne dystrybuowanie plików programu Visual C++](redistributing-visual-cpp-files.md)
