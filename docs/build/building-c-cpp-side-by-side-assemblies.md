---
title: Kompilowanie wykonywanych jednocześnie aplikacji C/C++
ms.date: 11/04/2016
helpviewer_keywords:
- side-by-side applications [C++]
ms.assetid: 7fa20b16-3737-4f76-a0b5-1dacea19a1e8
ms.openlocfilehash: 037fde58366ea4548ce3c7ff56c38cfc1a58aa17
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815193"
---
# <a name="building-cc-side-by-side-assemblies"></a>Kompilowanie wykonywanych jednocześnie aplikacji C/C++

A [zestawów side-by-side](/windows/desktop/SbsCs/about-side-by-side-assemblies-) to zbiór zasobów — Grupa bibliotek DLL, klas okien, serwerów COM, bibliotek typów lub interfejsów — dostępne do użycia w czasie wykonywania aplikacji. Główną zaletą ponowne pakowanie bibliotek DLL w zestawach to, czy można używać wielu wersji zestawów przez aplikacje w tym samym czasie i można aktualnie jest zainstalowana usługa zestawów w przypadku wydania aktualizacji.

Aplikacji Visual C++ może używać jednego lub kilku bibliotek DLL w różnych częściach aplikacji. W czasie wykonywania biblioteki DLL są ładowane do głównego procesu i wymagany kod jest wykonywany. Aplikacja zależy od systemu operacyjnego, aby zlokalizować żądany bibliotek DLL, Dowiedz się, co inne zależne biblioteki DLL muszą zostać załadowane, a następnie załadować je wraz z żądanego pliku DLL. W wersjach systemów operacyjnych Windows starszych niż Windows XP, Windows Server 2003 i Windows Vista, program ładujący systemu operacyjnego wyszukiwanie zależne biblioteki dll w lokalnym folderze aplikacji albo inny folder określony w ścieżce systemowej. Na Windows XP, Windows Server 2003 i Windows Vista, program ładujący systemu operacyjnego można również wyszukać zależne biblioteki DLL przy użyciu [manifestu](/windows/desktop/sbscs/manifests) plik i poszukaj zestawów side-by-side, które zawierają te biblioteki dll.

Domyślnie podczas kompilowania biblioteki DLL za pomocą programu Visual Studio posiada [manifest aplikacji](/windows/desktop/SbsCs/application-manifests) osadzony jako zasób RT_MANIFEST o identyfikatorze równym 2. Podobnie jak w przypadku pliku wykonywalnego tego manifestu w tym artykule opisano zależności dla tej biblioteki DLL innych zestawów. Założono, że biblioteka DLL nie jest częścią zestawu side-by-side i aplikacje, które są zależne od tej biblioteki DLL nie będą używać manifestu aplikacji, można go załadować, ale zamiast polegać na moduł ładujący systemu operacyjnego, aby znaleźć tę bibliotekę DLL na ścieżce systemowej.

> [!NOTE]
> Jest ważne dla biblioteki DLL, która używa manifest aplikacji, aby mieć manifestu osadzonego jako zasób o identyfikatorze równym 2. Jeśli biblioteka DLL jest dynamicznie ładowany w czasie wykonywania (na przykład za pomocą [LoadLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibrarya) funkcji), moduł ładujący systemu operacyjnego ładuje zestawów zależnych, określonego w manifeście biblioteki DLL. Manifest aplikacji zewnętrznej dla bibliotek DLL nie jest sprawdzany w trakcie `LoadLibrary` wywołania. Jeśli manifest nie jest zagnieżdżony, moduł ładujący może podejmować prób załadować zestawy zainstalowanie niepoprawnej wersji lub utrata możliwości ich wyszukiwanie i znajdowanie zestawów zależnych.

Jeden lub kilka związane z biblioteki dll, może to w ramach zestawu side-by-side z odpowiednią [manifestu zestawu](/windows/desktop/SbsCs/assembly-manifests), która opisuje pliki, które tworzą zestaw, a także zależność zestawu w innych side-by-side zestawy.

> [!NOTE]
> Jeśli zestaw zawiera jedną bibliotekę DLL, zalecane jest osadzanie manifestu zestawu w tę bibliotekę DLL jako zasób o identyfikatorze równa 1, a także nadać zestawowi prywatnemu taką samą nazwę jak biblioteki DLL. Na przykład, jeśli nazwa pliku DLL jest mylibrary.dll, wartość atrybutu nazwy są używane w \<assemblyIdentity > element manifestu może być również MojaBiblioteka. W niektórych przypadkach, gdy biblioteka ma rozszerzeniem innym niż dll (na przykład projektu kontrolki ActiveX MFC tworzy bibliotekę .ocx) mogą być tworzone w manifeście zestawu zewnętrznego. W takim przypadku nazwa zestawu i jego manifestu musi być inna niż nazwa biblioteki DLL (na przykład MyAssembly, MyAssembly.manifest i mylibrary.ocx). Jednak nadal zalecane jest aby zmienić nazwę biblioteki extension.dll i osadzić manifest jako zasób do zmniejszania kosztów konserwacji w przyszłości tego zestawu. Aby uzyskać więcej informacji na temat sposobu system operacyjny wyszukuje zestawy prywatne, zobacz [kolejność wyszukiwania zestawu](/windows/desktop/SbsCs/assembly-searching-sequence).

Ta zmiana może zezwolić na wdrożenie odpowiedniej biblioteki DLL jako [zestaw prywatny](/windows/desktop/Msi/private-assemblies) w lokalnym folderze aplikacji lub jako [udostępnionego zestawu](/windows/desktop/Msi/shared-assemblies) w folderze WinSxS pamięci podręcznej zestawów. Kilka kroków musi występować w celu uzyskania poprawne działanie tego nowego zestawu; zostały one opisane w [wytyczne dotyczące zestawów Side-by-side tworzenie](/windows/desktop/SbsCs/guidelines-for-creating-side-by-side-assemblies). Zestaw składowe, została poprawnie utworzona można wdrożyć jako albo współużytkowany lub prywatny zestawu razem z aplikacją, która zależy od niego. Podczas instalowania zestawów side-by-side jako zestaw współużytkowany, może być albo wykonaj wytyczne opisane w temacie [instalowanie zestawów Win32 w celu udostępniania Side-by-Side w systemie Windows XP](/windows/desktop/Msi/installing-win32-assemblies-for-side-by-side-sharing-on-windows-xp) lub użyj [modułówscalania,](/windows/desktop/msi/merge-modules). Podczas instalowania zestawów side-by-side jako zestaw prywatny, użytkownik może po prostu skopiuj odpowiedniego manifestu biblioteki DLL, potrzebne zasoby oraz zestawu jako część procesu instalacji do lokalnego folderu aplikacji na komputerze docelowym zapewnienie, że ten zestaw może być Znaleziono przez moduł ładujący w czasie wykonywania (zobacz [kolejność wyszukiwania zestawu](/windows/desktop/SbsCs/assembly-searching-sequence)). Innym sposobem jest użycie [Instalatora Windows](/windows/desktop/Msi/windows-installer-portal) i postępuj zgodnie z wytycznymi podanymi w [instalowanie zestawów Win32, przejdź do użytku prywatnego w aplikacji Windows XP](/windows/desktop/Msi/installing-win32-assemblies-for-the-private-use-of-an-application-on-windows-xp).

## <a name="see-also"></a>Zobacz także

[Kompilowanie izolowanych aplikacji C/C++](building-c-cpp-isolated-applications.md)<br/>
[Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
