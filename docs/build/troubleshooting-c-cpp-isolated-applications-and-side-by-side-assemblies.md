---
title: Rozwiązywanie problemów związanych z aplikacjami izolowanymi C/C++ oraz aplikacjami wykonywanymi równocześnie
ms.date: 11/04/2016
helpviewer_keywords:
- troubleshooting side-by-side assemblies
- troubleshooting isolated applications
- troubleshooting Visual C++
ms.assetid: 3257257a-1f0b-4ede-8564-9277a7113a35
ms.openlocfilehash: 1bd0d7638a8e7f2e3c671229e1f8d118d681e6f4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492575"
---
# <a name="troubleshooting-cc-isolated-applications-and-side-by-side-assemblies"></a>Rozwiązywanie problemów związanych z aplikacjami izolowanymi C/C++ oraz aplikacjami wykonywanymi równocześnie

Ładowanie aplikacji C/C++ może zakończyć się niepowodzeniem, jeśli nie można znaleźć bibliotek zależnych. W tym artykule opisano niektóre typowe przyczyny niepowodzenia załadowania aplikacji C/C++ i przedstawiono kroki umożliwiające rozwiązanie problemów.

Jeśli nie można załadować aplikacji, ponieważ zawiera ona manifest, który określa zależność od zestawu równoległego, a zestaw nie jest zainstalowany jako zestaw prywatny w tym samym folderze, w którym znajduje się plik wykonywalny, ani w natywnej pamięci podręcznej zestawów w folderze%WINDIR%\WinSxS\ może zostać wyświetlony jeden z następujących komunikatów o błędach w zależności od wersji systemu Windows, w której próbujesz uruchomić aplikację.

- Nie można poprawnie zainicjować aplikacji (0xc0000135).

- Nie można uruchomić tej aplikacji, ponieważ konfiguracja aplikacji jest nieprawidłowa. Ponowne zainstalowanie aplikacji może rozwiązać ten problem.

- System nie może wykonać określonego programu.

Jeśli aplikacja nie ma manifestu i zależy od biblioteki DLL, którą system Windows nie może odnaleźć w typowych lokalizacjach wyszukiwania, może zostać wyświetlony komunikat o błędzie podobny do następującego:

- Uruchomienie tej aplikacji nie powiodło się, ponieważ nie znaleziono *wymaganej biblioteki DLL* . Ponowne zainstalowanie aplikacji może rozwiązać ten problem.

Jeśli aplikacja jest wdrażana na komputerze, który nie ma programu Visual Studio, i ulega awarii z komunikatami o błędach przypominającymi poprzednie, należy sprawdzić następujące kwestie:

1. Wykonaj kroki opisane w artykule [Omówienie zależności aplikacji C++ wizualnej](../windows/understanding-the-dependencies-of-a-visual-cpp-application.md). Analizator zależności może wyświetlać większość zależności dla aplikacji lub biblioteki DLL. Jeśli zauważysz, że brakuje niektórych bibliotek DLL, zainstaluj je na komputerze, na którym próbujesz uruchomić aplikację.

1. Moduł ładujący systemu operacyjnego używa manifestu aplikacji do ładowania zestawów, od których zależy aplikacja. Manifest może być osadzony w pliku binarnym jako zasób lub instalowany jako osobny plik w folderze aplikacji. Aby sprawdzić, czy manifest jest osadzony w pliku binarnym, Otwórz plik binarny w programie Visual Studio i poszukaj RT_MANIFEST na liście zasobów. Jeśli nie możesz znaleźć osadzonego manifestu, poszukaj w folderze aplikacji pliku o nazwie, takiej jak < binary_name >. \<rozszerzenie >. manifest.

1. Jeśli aplikacja jest zależna od zestawów równoległych, a manifest nie istnieje, należy się upewnić, że konsolidator generuje manifest dla projektu. Zaznacz opcję konsolidatora **Generuj manifest** w oknie dialogowym **właściwości projektu** dla projektu.

1. Jeśli manifest jest osadzony w pliku binarnym, upewnij się, że identyfikator RT_MANIFEST jest prawidłowy dla tego typu danych binarnych. Aby uzyskać więcej informacji o IDENTYFIKATORze zasobu, który ma być używany, zobacz [używanie zestawów równoległych jako zasobów (Windows)](/windows/win32/SbsCs/using-side-by-side-assemblies-as-a-resource). Jeśli manifest znajduje się w osobnym pliku, otwórz go w edytorze XML lub edytorze tekstu. Aby uzyskać więcej informacji na temat manifestów i reguł wdrożenia, [](/windows/win32/sbscs/manifests)Zobacz Manifests.

   > [!NOTE]
   > Jeśli istnieją zarówno manifest osadzony, jak i oddzielny plik manifestu, moduł ładujący systemu operacyjnego korzysta z osadzonego manifestu i ignoruje oddzielny plik. Jednak w systemie Windows XP przeciwieństwem jest true — używany jest oddzielny plik manifestu, a osadzony manifest jest ignorowany.

1. Zalecamy osadzenie manifestu w każdej bibliotece DLL, ponieważ zewnętrzne manifesty są ignorowane, gdy biblioteka DLL jest załadowana przy `LoadLibrary` użyciu wywołania. Aby uzyskać więcej informacji, zobacz [manifesty zestawu](/windows/win32/SbsCs/assembly-manifests).

1. Sprawdź, czy wszystkie zestawy, które są wyliczane w manifeście, są poprawnie zainstalowane na komputerze. Każdy zestaw jest określony w manifeście według jego nazwy, numeru wersji i architektury procesora. Jeśli aplikacja jest zależna od zestawów równoległych, sprawdź, czy te zestawy są prawidłowo zainstalowane na komputerze, tak aby program ładujący system operacyjny mógł je znaleźć, zgodnie z opisem w [sekwencji wyszukiwania zestawu](/windows/win32/SbsCs/assembly-searching-sequence). Należy pamiętać, że zestawy 64-bitowe nie mogą być ładowane w procesach 32-bitowych i nie mogą być wykonywane w 32-bitowych systemach operacyjnych.

## <a name="example"></a>Przykład

Załóżmy, że mamy aplikację, program Application. exe, która jest skompilowana za pomocą C++wizualizacji. Manifest aplikacji jest osadzony w pliku Application. exe jako RT_MANIFEST zasobów binarnych, który ma identyfikator równy 1 lub jest przechowywany jako oddzielny plik Application. exe. manifest. Zawartość tego manifestu jest podobna do poniższej:

```
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
  <dependency>
    <dependentAssembly>
      <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"></assemblyIdentity>
    </dependentAssembly>
  </dependency>
</assembly>
```

Do modułu ładującego systemu operacyjnego ten manifest wskazuje, że program Assembly. exe zależy od zestawu o nazwie fabrikam. SxS. Library, w wersji 2.0.20121.0, która została skompilowana dla 32-bitowej architektury procesora x86. Zależny zestaw równoległy może być instalowany jako zestaw współużytkowany lub prywatny.

Manifest zestawu udostępnionego zestawu jest instalowany w folderze%WINDIR%\WinSxS\Manifests\. Identyfikuje zestaw i wyświetla jego zawartość — czyli biblioteki DLL, które są częścią zestawu:

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
   <noInheritable/>
   <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>
   <file name="Fabrikam.Main.dll" hash="3ca5156e8212449db6c622c3d10f37d9adb1ab12" hashalg="SHA1"/>
   <file name="Fabrikam.Helper.dll" hash="92cf8a9bb066aea821d324ca4695c69e55b2d1c2" hashalg="SHA1"/>
</assembly>
```

Zestawy równoległe mogą również używać [plików konfiguracji wydawcy](/windows/win32/SbsCs/publisher-configuration-files)(nazywanych również plikami zasad), aby globalnie przekierowywać aplikacje i zestawy do korzystania z jednej wersji zestawu równoległego zamiast innej wersji tego samego zestawu. Zasady dotyczące zestawu udostępnionego można sprawdzić w folderze%WINDIR%\WinSxS\Policies\. Oto przykładowy plik zasad:

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

Ten plik zasad określa, że każda aplikacja lub zestaw, który pyta o wersję 2.0.10000.0 tego zestawu, powinien zamiast tego używać wersji 2.0.20121.0, która jest bieżącą wersją zainstalowaną w systemie. Jeśli w pliku zasad zostanie określona wersja zestawu, który jest wymieniony w manifeście aplikacji, program ładujący szuka wersji tego zestawu, która jest określona w manifeście w folderze%WINDIR%\WinSxS\, a jeśli ta wersja nie jest zainstalowana, ładowanie nie powiedzie się. Jeśli nie zainstalowano wersji zestawu 2.0.20121.0, ładowanie nie powiedzie się dla aplikacji, które proszą o wersję zestawu 2.0.10000.0.

Zestaw można również zainstalować jako prywatny zestaw równoległy w folderze zainstalowanym aplikacji. Jeśli system operacyjny nie może znaleźć zestawu jako zestawu udostępnionego, szuka go jako zestawu prywatnego, w następującej kolejności:

1. Sprawdź folder aplikacji dla pliku manifestu, który ma nazwę \<AssemblyName >. manifest. W tym przykładzie moduł ładujący próbuje znaleźć plik fabrikam. SxS. Library. manifest w folderze, który zawiera program. exe. W przypadku znalezienia manifestu moduł ładujący ładuje zestaw z folderu aplikacji. Jeśli zestaw nie zostanie znaleziony, ładowanie nie powiedzie się.

1. Spróbuj \\otworzyć folder < AssemblyName \\\>\ w folderze, który zawiera program. exe, a jeśli < AssemblyName\>\ istnieje, spróbuj załadować plik manifestu, który ma nazwę \<AssemblyName >. Manifest z tego folderu. W przypadku znalezienia manifestu moduł ładujący ładuje zestaw z \\< AssemblyName\>\ folder. Jeśli zestaw nie zostanie znaleziony, ładowanie nie powiedzie się.

Aby uzyskać więcej informacji na temat sposobu wyszukiwania zestawów zależnych przez moduł ładujący, zobacz [sekwencja wyszukiwania zestawów](/windows/win32/SbsCs/assembly-searching-sequence). Jeśli moduł ładujący nie może znaleźć zestawu zależnego jako zestawu prywatnego, ładowanie nie powiedzie się i zostanie wyświetlony komunikat "system nie może wykonać określonego programu". Aby rozwiązać ten problem, upewnij się, że zestawy zależne — i biblioteki DLL, które są ich częścią, są zainstalowane na komputerze jako zestawy prywatne lub udostępnione.

## <a name="see-also"></a>Zobacz także

[Pojęcia związane z aplikacjami izolowanymi oraz aplikacjami wykonywanymi równocześnie](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
