---
title: Rozwiązywanie problemów związanych z aplikacjami izolowanymi C/C++ oraz aplikacjami wykonywanymi równocześnie
ms.date: 11/04/2016
helpviewer_keywords:
- troubleshooting side-by-side assemblies
- troubleshooting isolated applications
- troubleshooting Visual C++
ms.assetid: 3257257a-1f0b-4ede-8564-9277a7113a35
ms.openlocfilehash: 32896939ddc7fd0b841e1b6904124b06c9bc51c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314991"
---
# <a name="troubleshooting-cc-isolated-applications-and-side-by-side-assemblies"></a>Rozwiązywanie problemów związanych z aplikacjami izolowanymi C/C++ oraz aplikacjami wykonywanymi równocześnie

Trwa ładowanie aplikacji C/C++ może zakończyć się niepowodzeniem, jeśli nie można odnaleźć zależne biblioteki. W tym artykule opisano niektóre typowe przyczyny niepowodzenia aplikacji C/C++, aby załadować, a także sugeruje czynności, aby rozwiązać problemy.

Jeśli aplikacja nie może załadować, ponieważ ma ona manifestu, który określa zależność od zestawu side-by-side i zestaw nie jest zainstalowany jako zestaw prywatny, w tym samym folderze co plik wykonywalny, ani w pamięci podręcznej macierzystego zestawu w folderze %WINDIR%\WinSxS\ , jeden z następujących komunikatów o błędach mogą być wyświetlane, w zależności od wersji systemu Windows, na którym zostanie podjęta próba uruchomienia aplikacji.

- Aplikacja nie została poprawnie zainicjowana (0xc0000135).

- Tej aplikacji nie powiodło się, ponieważ konfiguracja aplikacji jest nieprawidłowa. Ponowna instalacja aplikacji może naprawić ten problem.

- System nie może wykonać określonego programu.

Jeśli aplikacja ma nie manifestu i jest zależna od biblioteki DLL, która Windows nie można znaleźć w typowym wyszukiwaniu lokalizacje, może być wyświetlany komunikat o błędzie podobny do następującego:

- Tej aplikacji nie powiodło się, ponieważ *wymaganej biblioteki DLL* nie został znaleziony. Ponowne zainstalowanie aplikacji może naprawić ten problem.

Jeśli aplikacja jest wdrażana na komputerze, na którym nie zainstalowano oprogramowania Visual Studio uległa awarii z komunikatami o błędach, które przypominają poprzednie, należy sprawdzić te rzeczy:

1. Postępuj zgodnie z instrukcjami opisanymi w [poznanie zależności aplikacji Visual C++](../windows/understanding-the-dependencies-of-a-visual-cpp-application.md). Modułu przeszukiwania zależności można wyświetlić większość zależności dla aplikacji lub biblioteki DLL. Jeśli zauważysz, że brakuje niektórych bibliotek DLL, należy je zainstalować na komputerze, na którym chcesz uruchomić aplikację.

1. Program ładujący systemu operacyjnego używa manifest aplikacji, aby ładować zestawy, od których zależy aplikacja. Manifest mogą być osadzone w pliku binarnym jako zasób lub zainstalowane jako osobny plik w folderze aplikacji. Aby sprawdzić, czy manifest jest osadzony w pliku binarnym, otwórz plik binarny w programie Visual Studio i poszukaj RT_MANIFEST na liście zasobów. Jeśli nie możesz znaleźć manifestu osadzonego, poszukaj w folderze aplikacji dla pliku, która ma nazwę podobną < binary_name >. \<rozszerzenia > manifest.

1. Jeśli Twoja aplikacja jest zależna od zestawów side-by-side i nie ma manifestu, należy upewnić się, że konsolidator generuje manifest dla projektu. Zaznacz opcję konsolidatora **Generuj manifest** w **właściwości projektu** okno dialogowe dla projektu.

1. Jeśli manifest jest osadzony w pliku binarnym, upewnij się, że identyfikator RT_MANIFEST jest prawidłowy dla tego typu pliku binarnego. Aby uzyskać więcej informacji na temat którego Identyfikatora zasobu, aby użyć zobacz [używanie zestawów Side-by-Side jako zasób (Windows)](/windows/desktop/SbsCs/using-side-by-side-assemblies-as-a-resource). Jeśli manifest znajduje się w oddzielnym pliku, otwórz go w edytorze XML lub edytorze tekstów. Aby uzyskać więcej informacji na temat manifestów i reguł dotyczących wdrażania, zobacz [manifesty](/windows/desktop/sbscs/manifests).

   > [!NOTE]
   > Jeśli obecne są oba wbudowanym manifeście i oddzielny plik manifestu, moduł ładujący systemu operacyjnego korzysta z manifestu osadzonego i ignoruje oddzielnym pliku. Jednak w systemie Windows XP, przeciwieństwo ma wartość true, jest używany oddzielny plik manifestu i manifestu osadzonego jest ignorowany.

1. Firma Microsoft zaleca, aby osadzić manifest w każdej biblioteki DLL, ponieważ zewnętrzne manifestów są ignorowane, gdy biblioteka DLL jest ładowany do `LoadLibrary` wywołania. Aby uzyskać więcej informacji, zobacz [zestawu manifestów](/windows/desktop/SbsCs/assembly-manifests).

1. Sprawdź, czy wszystkie zestawy, które są wyliczane w manifeście są poprawnie zainstalowane na komputerze. Każdy zestaw jest określony w manifeście jej nazwa, numer wersji i architektury procesora. Jeśli Twoja aplikacja jest zależna od zestawów side-by-side, sprawdź, czy te zestawy są poprawnie zainstalowane na komputerze, aby program ładujący systemu operacyjnego można znaleźć, zgodnie z opisem w [kolejność wyszukiwania zestawu](/windows/desktop/SbsCs/assembly-searching-sequence). Należy pamiętać, że zestawów 64-bitowych nie można załadować w procesach 32-bitowe i nie można wykonać na 32-bitowych systemach operacyjnych.

## <a name="example"></a>Przykład

Załóżmy, że mamy aplikację appl.exe, która powstała przy użyciu języka Visual C++. Manifest aplikacji jest albo osadzony w appl.exe jako zasób binarny RT_MANIFEST, który ma identyfikator równy 1 lub jest przechowywany jako appl.exe.manifest oddzielny plik. Zawartość tego manifestu jest podobny do tego:

```
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
  <dependency>
    <dependentAssembly>
      <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"></assemblyIdentity>
    </dependentAssembly>
  </dependency>
</assembly>
```

Do modułu ładującego systemu operacyjnego tego manifestu wynika z tego appl.exe zależy zestaw o nazwie Fabrikam.SxS.Library, wersja 2.0.20121.0, który zaprojektowano pod kątem x86 32-bitowa architektura procesora. Można zainstalować jako zestaw współużytkowany lub prywatny zestawu zależnego zestawu side-by-side.

Manifest zestawu współużytkowanego jest zainstalowany w folderze %WINDIR%\WinSxS\Manifests\. Określa zestaw i wyświetla jego zawartość — czyli bibliotek DLL, które są częścią zestawu:

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
   <noInheritable/>
   <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>
   <file name="Fabrikam.Main.dll" hash="3ca5156e8212449db6c622c3d10f37d9adb1ab12" hashalg="SHA1"/>
   <file name="Fabrikam.Helper.dll" hash="92cf8a9bb066aea821d324ca4695c69e55b2d1c2" hashalg="SHA1"/>
</assembly>
```

Umożliwia również zestawów Side-by-side [pliki konfiguracyjne wydawcy](/windows/desktop/SbsCs/publisher-configuration-files)— nazywane również plikami zasad — globalnie przekierować aplikacje i zestawy, do korzystania z jednej wersji zestawu side-by-side zamiast inna wersja tego samego zestaw. Zestaw współużytkowany w folderze %WINDIR%\WinSxS\Policies\ może wyszukać zasady. Poniżej przedstawiono przykładowy plik zasad:

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

Ten plik zasad określa, że dowolnej aplikacji lub zestawu, która poprosi o podanie wersji 2.0.10000.0 tego zestawu zamiast tego użyj wersji 2.0.20121.0, która jest bieżącą wersję, która jest zainstalowana w systemie. Jeśli wersja zestawu, który jest wymieniony w manifeście aplikacji jest określona w pliku zasad, moduł ładujący szuka wersji tego zestawu, który jest określony w manifeście w folderze %WINDIR%\WinSxS\, a jeśli ta wersja nie jest zainstalowany, obciążenia nie powiedzie się. A jeśli nie zainstalowano wersję zestawu 2.0.20121.0, obciążenia nie powiedzie się dla aplikacji, które poproś o wersję zestawu 2.0.10000.0.

Jednak zestaw można również zainstalować jako zestaw prywatny side-by-side, w folderze zainstalowanych aplikacji. Jeśli system operacyjny nie można znaleźć zestawu jako zestaw współużytkowany, szuka go jako zestaw prywatny, w następującej kolejności:

1. Sprawdź folder aplikacji dla pliku manifestu, który ma taką nazwę \<Nazwa_zestawu > manifest. W tym przykładzie moduł ładujący próbuje znaleźć Fabrikam.SxS.Library.manifest w folderze, który zawiera appl.exe. Jeśli znajdzie manifestu, moduł ładujący ładuje zestaw z folderu aplikacji. Jeśli zestaw nie zostanie znaleziony, obciążenia nie powiedzie się.

1. Spróbuj otworzyć \\< Nazwa_zestawu\>\ folderu w folderze, który zawiera appl.exe, i, jeśli \\< assemblyName\>\ istnieje, spróbuj załadować pliku manifestu, który ma taką nazwę \<assemblyName >. Manifest z tego folderu. Jeśli zostanie znaleziony manifestu, moduł ładujący ładuje zestaw z \\< Nazwa_zestawu\>\ folderu. Jeśli zestaw nie zostanie znaleziony, obciążenia nie powiedzie się.

Aby uzyskać więcej informacji na temat jak moduł ładujący wyszukuje zależne zestawy zobacz [kolejność wyszukiwania zestawu](/windows/desktop/SbsCs/assembly-searching-sequence). Jeśli moduł ładujący nie można odnaleźć zależnego zestawu jako zestaw prywatny, obciążenia nie powiedzie się i zostanie wyświetlony komunikat "system nie może wykonać określonego programu". Aby rozwiązać ten problem, upewnij się, że zestawów zależnych — i bibliotek DLL, które należą do nich — są zainstalowane na komputerze jako prywatne lub współużytkowane zestawy.

## <a name="see-also"></a>Zobacz także

[Pojęcia związane z aplikacjami izolowanymi oraz aplikacjami wykonywanymi równocześnie](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
