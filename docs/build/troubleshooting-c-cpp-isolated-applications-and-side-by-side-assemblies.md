---
title: Rozwiązywanie problemów związanych z aplikacjami izolowanymi C/C++ oraz aplikacjami wykonywanymi równocześnie
ms.date: 11/04/2016
helpviewer_keywords:
- troubleshooting side-by-side assemblies
- troubleshooting isolated applications
- troubleshooting Visual C++
ms.assetid: 3257257a-1f0b-4ede-8564-9277a7113a35
ms.openlocfilehash: 0dc8488acc90f1a38a4c0de0f052590ef4f398af
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335440"
---
# <a name="troubleshooting-cc-isolated-applications-and-side-by-side-assemblies"></a>Rozwiązywanie problemów związanych z aplikacjami izolowanymi C/C++ oraz aplikacjami wykonywanymi równocześnie

Ładowanie aplikacji C/C++ może zakończyć się niepowodzeniem, jeśli nie można odnaleźć bibliotek zależnych. W tym artykule opisano niektóre typowe powody, dla których aplikacja C/C++ nie można załadować i sugeruje kroki, aby rozwiązać problemy.

Jeśli aplikacja nie może załadować, ponieważ ma manifest określający zależność od zestawu side-by-side, a zestaw nie jest zainstalowany jako zestaw prywatny w tym samym folderze co plik wykonywalny ani w pamięci podręcznej natywnego zestawu w folderze %WINDIR%\WinSxS\, może być wyświetlany jeden z następujących komunikatów o błędach, w zależności od wersji systemu Windows, w której próbujesz uruchomić aplikację.

- Nie można poprawnie zainicjować aplikacji (0xc0000135).

- Uruchomienie tej aplikacji nie powiodło się, ponieważ konfiguracja aplikacji jest niepoprawna. Ponowna instalacja aplikacji może rozwiązać ten problem.

- System nie może wykonać określonego programu.

Jeśli aplikacja nie ma manifestu i zależy od biblioteki DLL, że system Windows nie można znaleźć w typowych lokalizacjach wyszukiwania, komunikat o błędzie, który przypomina ten może być wyświetlany:

- Uruchomienie tej aplikacji nie powiodło się, ponieważ nie znaleziono *wymaganej biblioteki DLL.* Ponowna instalacja aplikacji może rozwiązać ten problem.

Jeśli aplikacja jest wdrażana na komputerze, który nie ma programu Visual Studio i ulega awarii z komunikatami o błędach, które przypominają poprzednie, sprawdź następujące czynności:

1. Wykonaj kroki opisane w [opisie zależności aplikacji Visual C++.](../windows/understanding-the-dependencies-of-a-visual-cpp-application.md) Walker zależności można wyświetlić większość zależności dla aplikacji lub biblioteki DLL. Jeśli zauważysz, że brakuje niektórych bibliotek DLL, zainstaluj je na komputerze, na którym próbujesz uruchomić aplikację.

1. Moduł ładujący system operacyjny używa manifestu aplikacji do ładowania zestawów, od których zależy aplikacja. Manifest może być osadzony w pliku binarnym jako zasób lub zainstalowany jako oddzielny plik w folderze aplikacji. Aby sprawdzić, czy manifest jest osadzony w pliku binarnym, otwórz plik binarny w programie Visual Studio i poszukaj RT_MANIFEST na swojej liście zasobów. Jeśli nie możesz znaleźć osadzonego manifestu, poszukaj w folderze aplikacji pliku o nazwie <binary_name>. \<>.manifest.

1. Jeśli aplikacja zależy od zestawów side-by-side i manifest nie jest obecny, należy upewnić się, że konsolidator generuje manifest dla projektu. Sprawdź opcję konsolidatora **Generowanie manifestu** w oknie dialogowym **Właściwości projektu** dla projektu.

1. Jeśli manifest jest osadzony w pliku binarnym, upewnij się, że identyfikator RT_MANIFEST jest poprawna dla tego typu pliku binarnego. Aby uzyskać więcej informacji o identyfikatorze zasobu, zobacz [Używanie zestawów side-by-side jako zasobu (Windows).](/windows/win32/SbsCs/using-side-by-side-assemblies-as-a-resource) Jeśli manifest znajduje się w oddzielnym pliku, otwórz go w edytorze XML lub edytorze tekstu. Aby uzyskać więcej informacji na temat manifestów i reguł wdrażania, zobacz [Manifesty](/windows/win32/sbscs/manifests).

   > [!NOTE]
   > Jeśli zarówno osadzony manifest, jak i oddzielny plik manifestu są obecne, moduł ładujący systemu operacyjnego używa osadzonego manifestu i ignoruje oddzielny plik. Jednak w systemie Windows XP jest odwrotnie — używany jest oddzielny plik manifestu, a osadzony manifest jest ignorowany.

1. Zaleca się osadzenie manifestu w każdej biblioteki DLL, ponieważ manifesty zewnętrzne `LoadLibrary` są ignorowane, gdy biblioteka DLL jest ładowana, chociaż wywołanie. Aby uzyskać więcej informacji, zobacz [Manifesty zestawu](/windows/win32/SbsCs/assembly-manifests).

1. Sprawdź, czy wszystkie zestawy, które są wyliczone w manifeście są poprawnie zainstalowane na komputerze. Każdy zestaw jest określony w manifeście przez jego nazwę, numer wersji i architekturę procesora. Jeśli aplikacja zależy od zespołów side-by-side, sprawdź, czy te zestawy są poprawnie zainstalowane na komputerze, tak aby program ładujący system operacyjny mógł je znaleźć, zgodnie z opisem w [sekwencji wyszukiwania zestawu](/windows/win32/SbsCs/assembly-searching-sequence). Należy pamiętać, że zestawów 64-bitowych nie można załadować w procesach 32-bitowych i nie można ich wykonać w 32-bitowych systemach operacyjnych.

## <a name="example"></a>Przykład

Załóżmy, że mamy aplikację, appl.exe, który jest zbudowany przy użyciu języka Visual C++. Manifest aplikacji jest osadzony w pliku appl.exe jako RT_MANIFEST zasobu binarnego, który ma identyfikator równy 1 lub jest przechowywany jako oddzielny plik appl.exe.manifest. Treść tego manifestu przypomina następującą:

```
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
  <dependency>
    <dependentAssembly>
      <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"></assemblyIdentity>
    </dependentAssembly>
  </dependency>
</assembly>
```

Do modułu ładującego systemu operacyjnego ten manifest mówi, że program appl.exe zależy od zestawu o nazwie Fabrikam.SxS.Library w wersji 2.0.20121.0, który jest zbudowany dla 32-bitowej architektury procesora x86. Zależny zestaw obok siebie może być zainstalowany jako zestaw udostępniony lub jako zestaw prywatny.

Manifest zestawu dla zestawu udostępnionego jest zainstalowany w folderze %WINDIR%\WinSxS\Manifests\. Identyfikuje zestaw i wyświetla jego zawartość — czyli biblioteki DLL, które są częścią zestawu:

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
   <noInheritable/>
   <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>
   <file name="Fabrikam.Main.dll" hash="3ca5156e8212449db6c622c3d10f37d9adb1ab12" hashalg="SHA1"/>
   <file name="Fabrikam.Helper.dll" hash="92cf8a9bb066aea821d324ca4695c69e55b2d1c2" hashalg="SHA1"/>
</assembly>
```

Zespoły side-by-side mogą również używać [plików konfiguracyjnych wydawcy](/windows/win32/SbsCs/publisher-configuration-files)— nazywanych również plikami zasad — do globalnego przekierowywania aplikacji i zestawów w celu używania jednej wersji zestawu obok siebie zamiast innej wersji tego samego zestawu. Zasady udostępnionego zestawu można sprawdzić w folderze %WINDIR%\WinSxS\Policies\. Oto przykładowy plik zasad:

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">

   <assemblyIdentity type="win32-policy" name="policy.2.0.Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>
   <dependency>
      <dependentAssembly>
         <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>
         <bindingRedirect oldVersion="2.0.10000.0-2.0.20120.99" newVersion="2.0.20121.0"/>
      </dependentAssembly>
   </dependency>
</assembly>
```

Ten plik zasad określa, że każda aplikacja lub zestaw, który prosi o wersję 2.0.10000.0 tego zestawu zamiast tego należy użyć wersji 2.0.20121.0, która jest bieżąca wersja, która jest zainstalowana w systemie. Jeśli wersja zestawu, który jest wymieniony w manifeście aplikacji jest określony w pliku zasad, moduł ładujący szuka wersji tego zestawu, który jest określony w manifeście w folderze %WINDIR%\WinSxS\, a jeśli ta wersja nie jest zainstalowana, ładowanie kończy się niepowodzeniem. A jeśli zestaw w wersji 2.0.20121.0 nie jest zainstalowany, ładowanie kończy się niepowodzeniem dla aplikacji, które proszą o wersję zestawu 2.0.10000.0.

Jednak zestaw może być również zainstalowany jako prywatny zestaw obok siebie w zainstalowanym folderze aplikacji. Jeśli system operacyjny nie może znaleźć zestawu jako zestawu udostępnionego, wyszukuje go jako zestaw prywatny, w następującej kolejności:

1. Sprawdź folder aplikacji dla pliku manifestu, który ma nazwę \<assemblyName>.manifest. W tym przykładzie moduł ładujący próbuje znaleźć program Fabrikam.SxS.Library.manifest w folderze zawierającym plik appl.exe. Jeśli znajdzie manifest, moduł ładujący ładuje zestaw z folderu aplikacji. Jeśli zestaw nie zostanie znaleziony, obciążenie nie powiedzie się.

1. Spróbuj otworzyć \\ folder<assemblyName\>\ w folderze zawierającym plik appl.exe, a jeśli \\<assemblyName\>\ istnieje, \<spróbuj załadować plik manifestu, który ma nazwę assemblyName>.manifest z tego folderu. Jeśli manifest zostanie znaleziony, moduł ładujący ładuje zestaw z \\ \>folderu<assemblyName \. Jeśli zestaw nie zostanie znaleziony, obciążenie nie powiedzie się.

Aby uzyskać więcej informacji na temat wyszukiwania przez moduł ładujący zestawów zależnych, zobacz [Sekwencja wyszukiwania zestawu](/windows/win32/SbsCs/assembly-searching-sequence). Jeśli moduł ładujący nie może znaleźć zestawu zależnego jako zestawu prywatnego, ładowanie kończy się niepowodzeniem i wyświetlany jest komunikat "System nie może wykonać określonego programu". Aby rozwiązać ten problem, upewnij się, że zestawy zależne i biblioteki DLL, które są ich częścią, są instalowane na komputerze jako zestawy prywatne lub udostępnione.

## <a name="see-also"></a>Zobacz też

[Pojęcia związane z aplikacjami izolowanymi oraz aplikacjami wykonywanymi równocześnie](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
