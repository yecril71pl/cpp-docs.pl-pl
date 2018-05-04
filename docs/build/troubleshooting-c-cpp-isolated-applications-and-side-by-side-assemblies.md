---
title: Rozwiązywanie problemów z C/C++ izolowany aplikacji i zestawy Side-by-side | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- troubleshooting side-by-side assemblies
- troubleshooting isolated applications
- troubleshooting Visual C++
ms.assetid: 3257257a-1f0b-4ede-8564-9277a7113a35
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f5645270cbc8fbb71dd841cb4f1affa6bef1295
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="troubleshooting-cc-isolated-applications-and-side-by-side-assemblies"></a>Rozwiązywanie problemów związanych z aplikacjami izolowanymi C/C++ oraz aplikacjami wykonywanymi równocześnie
Podczas ładowania aplikacji C/C++ może zakończyć się niepowodzeniem, jeśli nie można odnaleźć zależnych bibliotek. W tym artykule opisano niektóre typowe przyczyny niepowodzenia aplikacji C/C++ załadować, a także sugeruje czynności umożliwiające rozwiązywanie problemów.  
  
 Jeśli aplikacja nie może załadować, ponieważ ma ona manifestu, który określa zależność zestawu side-by-side i zestaw nie jest zainstalowany jako zestaw prywatny, w tym samym folderze co plik wykonywalny, ani w pamięć podręczna zestawów natywnych w folderze %WINDIR%\WinSxS\ , jeden z następujących komunikatów o błędach mogą być wyświetlane, w zależności od wersji systemu Windows, na którym zostanie podjęta próba uruchomienia aplikacji.  
  
-   Aplikacja nie została poprawnie zainicjowana (0xc0000135).  
  
-   Tej aplikacji nie powiodło się, ponieważ konfiguracja aplikacji jest niepoprawna. Ponowna instalacja aplikacji może naprawić ten problem.  
  
-   System nie może wykonać określonego programu.  
  
 Jeśli aplikacja ma nie manifestu i zależy od systemu Windows nie można znaleźć w lokalizacjach, typowe wyszukiwania pliku DLL, komunikat o błędzie podobny do tego mogą być wyświetlane:  
  
-   Tej aplikacji nie powiodło się, ponieważ *wymaganej biblioteki DLL* nie został znaleziony. Ponowne zainstalowanie aplikacji może naprawić ten problem.  
  
 Jeśli wdrażania aplikacji na komputerze, który nie ma programu Visual Studio, a jego ulega awarii i komunikaty o błędach podobne poprzednie, sprawdź następujące elementy:  
  
1.  Wykonaj kroki opisane w [poznanie zależności aplikacji Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md). Walkera zależności można wyświetlić większości zależności dla aplikacji lub DLL. Jeśli zauważysz, że brakuje niektórych bibliotek DLL, zainstaluj je na komputerze, na którym chcesz uruchomić aplikację.  
  
2.  Modułu ładującego systemu operacyjnego używa manifest aplikacji do ładowania zestawów, które zależy od aplikacji. Manifest można być osadzone w danych binarnych jako zasób lub zainstalowany jako osobny plik w folderze aplikacji. Aby sprawdzić, czy plik manifestu jest osadzony w danych binarnych, otwórz plik binarny w [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] i poszukaj RT_MANIFEST na liście zasobów. Jeśli nie można odnaleźć osadzonych manifestu, poszukaj w folderze aplikacji dla pliku, który ma o nazwie przypominać < binary_name >. \<rozszerzenia > manifest.  
  
3.  Jeśli aplikacja jest zależna od zestawy side-by-side, ale nie ma manifestu, masz upewnij się, że konsolidator generuje manifest w projekcie. Zaznacz opcję konsolidatora **Generuj manifest** w **właściwości projektu** okno dialogowe dla projektu.  
  
4.  Manifest jest osadzony w danych binarnych, upewnij się, że identyfikator RT_MANIFEST jest prawidłowa dla tego typu danych binarnych. Aby uzyskać więcej informacji na temat identyfikator zasobu, w którym do użycia, zobacz [używanie zestawów Side-by-Side jako zasób (system Windows)](http://msdn.microsoft.com/library/windows/desktop/aa376617.aspx). Jeśli manifest w osobnym pliku, otwórz go w edytorze XML lub edytorze tekstów. Aby uzyskać więcej informacji na temat manifestów i reguł dotyczących wdrażania, zobacz [manifesty](http://msdn.microsoft.com/library/aa375365).  
  
    > [!NOTE]
    >  Jeśli istnieją zarówno manifest osadzone, jak i oddzielny plik manifestu modułu ładującego systemu operacyjnego używa osadzonych manifestu i ignoruje oddzielny plik. Jednak w systemie Windows XP przeciwieństwem ma wartość true — oddzielny plik manifestu jest używany i osadzone manifestu jest ignorowana.  
  
5.  Firma Microsoft zaleca osadzanie manifestu w każdej biblioteki DLL, ponieważ manifestów zewnętrzne są ignorowane, podczas ładowania biblioteki DLL jednak `LoadLibrary` wywołania. Aby uzyskać więcej informacji, zobacz [manifesty zestawu](http://msdn.microsoft.com/library/aa374219).  
  
6.  Sprawdź, czy wszystkie zestawy, które są wymienione w manifeście są poprawnie zainstalowane na komputerze. Każdy zestaw jest określona w manifeście, jego nazwa, numer wersji i architektury procesora. Jeśli aplikacja jest zależna od zestawy side-by-side, sprawdź, czy te zestawy są poprawnie zainstalowane na komputerze, aby modułu ładującego systemu operacyjnego można znaleźć, zgodnie z opisem w [sekwencji wyszukiwania zestawu](http://msdn.microsoft.com/library/aa374224). Należy pamiętać, że zestawy 64-bitowe nie może zostać załadowany w procesach 32-bitowych i nie można wykonać na 32-bitowych systemach operacyjnych.  
  
## <a name="example"></a>Przykład  
 Załóżmy, że mamy aplikacji appl.exe, która została skompilowana przy użyciu programu Visual C++. Manifest aplikacji albo jest osadzony w appl.exe jako zasobu binarnego RT_MANIFEST, co ma identyfikator równy 1 lub jest przechowywana jako appl.exe.manifest oddzielny plik. Zawartość tego manifestu podobny to:  
  
```  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <dependency>  
    <dependentAssembly>  
      <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"></assemblyIdentity>  
    </dependentAssembly>  
  </dependency>  
</assembly>  
```  
  
 Do modułu ładującego systemu operacyjnego tego manifestu mówi tego appl.exe zależy od zestawu o nazwie Fabrikam.SxS.Library, wersja 2.0.20121.0, który jest przeznaczony dla x86 32-bitowy procesor. Można zainstalować zestawu zależnego side-by-side jako zestaw udostępnionego lub zestaw prywatny.  
  
 Manifest zestawu dla udostępnionego zestawu jest zainstalowany w folderze %WINDIR%\WinSxS\Manifests\. Określa zestaw i wyświetla jego zawartość — to znaczy bibliotek DLL, które są częścią zestawu:  
  
```  
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
   <noInheritable/>  
   <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>  
   <file name="Fabrikam.Main.dll" hash="3ca5156e8212449db6c622c3d10f37d9adb1ab12" hashalg="SHA1"/>  
   <file name="Fabrikam.Helper.dll" hash="92cf8a9bb066aea821d324ca4695c69e55b2d1c2" hashalg="SHA1"/>  
</assembly>  
```  
  
 Zestawy Side-by-side można również użyć [pliki konfiguracji wydawcy](http://msdn.microsoft.com/library/aa375682)— znanej także jako pliki zasad — Aby globalnie przekierować aplikacje i zestawy, do używania jednej wersji zestawu side-by-side zamiast inna wersja tego samego zestaw. Zestaw udostępnionego w folderze %WINDIR%\WinSxS\Policies\ można sprawdzić zasad. Oto przykładowy plik zasad:  
  
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
  
 Ten plik zasad określa, czy każda aplikacja lub zestawu z pytaniem, czy wersja 2.0.10000.0 tego zestawu zamiast tego użyj wersji 2.0.20121.0, która jest bieżącą wersję, która jest zainstalowana w systemie. Jeśli wersja zestawu, który jest wymieniony w manifeście aplikacji określono w pliku zasad, moduł ładujący szuka wersja tego zestawu, który określono w manifeście w folderze %WINDIR%\WinSxS\ i jeśli ta wersja nie jest zainstalowany, obciążenia nie powiedzie się. A jeśli nie jest zainstalowana wersja zestawu 2.0.20121.0, obciążenia nie powiedzie się dla aplikacji z prośbą o podanie wersji zestawu 2.0.10000.0.  
  
 Jednak zestaw można również zainstalować jako prywatnych zestawu side-by-side, w folderze zainstalowanych aplikacji. Jeśli system operacyjny nie można znaleźć zestawu jako zestaw udostępnionego, szuka go jako zestaw prywatny, w następującej kolejności:  
  
1.  Sprawdź folder aplikacji o tej nazwie pliku manifestu \<assemblyName > manifest. W tym przykładzie moduł ładujący podejmie próbę odnalezienia Fabrikam.SxS.Library.manifest w folderze, który zawiera appl.exe. Jeśli znajdzie plik manifestu, moduł ładujący ładuje zestaw w folderze aplikacji. Nie odnaleziono zestawu, obciążenia nie powiedzie się.  
  
2.  Spróbuj otworzyć \\< assemblyName\>\ folderu w folderze, który zawiera appl.exe, a jeśli \\< assemblyName\>\ istnieje, spróbuj załadować pliku manifestu, który ma nazwę \<assemblyName >. Manifest z tego folderu. Jeśli zostanie znaleziony plik manifestu, moduł ładujący ładuje zestaw z \\< assemblyName\>\ folderu. Nie odnaleziono zestawu, obciążenia nie powiedzie się.  
  
 Aby uzyskać więcej informacji na temat jak moduł ładujący wyszukuje zestawów zależnych, zobacz [sekwencji wyszukiwania zestawu](http://msdn.microsoft.com/library/aa374224). Jeśli moduł ładujący nie można znaleźć zestawu zależnego jako zestaw prywatny, obciążenia nie powiedzie się i zostanie wyświetlony komunikat "system nie może wykonać określonego programu". Aby rozwiązać ten problem, upewnij się, że zestawów zależnych — i bibliotek DLL, które są częścią ich — są zainstalowane na komputerze jako prywatne lub współużytkowane zestawy.  
  
## <a name="see-also"></a>Zobacz też  
 [Aplikacje izolowane i zestawy Side-by-side](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)