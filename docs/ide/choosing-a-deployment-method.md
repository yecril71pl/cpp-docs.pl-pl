---
title: Wybieranie metody wdrażania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- redistributing DLLs
- manifests [C++]
- DLLs [C++], redistributing
- side-by-side assemblies [C++]
- dynamic linking [C++]
- application deployment [C++], methods
- deploying applications [C++], methods
- static linking [C++]
- libraries [C++], application deployment issues
ms.assetid: fd8eb956-f4a0-4ffb-b401-328c73e66986
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdf024f75f03b55465ccd15670c47d3c761e56e8
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33338669"
---
# <a name="choosing-a-deployment-method"></a>Wybieranie metody wdrażania
Jeśli aplikacji Visual C++ nie jest niezależna i można wdrożyć przy użyciu polecenia kopiowania, zalecane jest użycie Instalatora systemu Windows dla wdrożenia. Instalator Windows obsługuje instalację, naprawę oraz dezinstalację, a także obsługuje atomowe aktualizowanie plików aplikacji, zależności i wpisów rejestru.  
  
> [!NOTE]
>  Mimo że [ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) wdrażanie natywnych aplikacji Visual C++ w programie Visual Studio i wymaga wykonania dodatkowych czynności. Aby uzyskać więcej informacji, zobacz [wdrożenie rozwiązania ClickOnce dla aplikacji Visual C++](../ide/clickonce-deployment-for-visual-cpp-applications.md).  
  
## <a name="visual-c-libraries-are-shared-dlls"></a>Biblioteki Visual C++ to współdzielone biblioteki DLL  
 Ponieważ biblioteki Visual C++ są instalowane w katalogu %windir%\system32\ przez instalator Visual Studio, podczas tworzenia aplikacji Visual C++, która od nich zależy, będzie ona działała zgodnie z oczekiwaniami. Aby wdrożyć aplikację na komputerach, które nie mają Visual Studio, zalecamy, aby się upewnić, że odpowiednie biblioteki są instalowane wraz z aplikacją.  
  
## <a name="redistributing-visual-c-libraries"></a>Redystrybucja bibliotek Visual C++  
 We wdrożeniach można redystrybuować dowolną wersję biblioteki Visual C++, której licencja na to pozwala. Poniżej przedstawiono trzy sposoby ich wdrożenia:  
  
-   Centralnej wdrożenie przy użyciu pakietu redystrybucyjnego pakiety, w którym bibliotek języka Visual C++ jest instalowany jako pliki dll w %windir%\system32\\. (Instalacja w tym folderze wymaga uprawnień administratora). Można utworzyć program Instalatora lub skrypt, który uruchamia pakiet redystrybucyjny przed zainstalowaniem aplikacji na komputerze docelowym. Pakiety redystrybucyjne są dostępne dla platform x86, x64 i ARM (VCRedist_x86.exe, VCRedist_x64.exe lub VCRedist_arm.exe). Visual Studio zawiera te pakiety w % ProgramFiles (x86) %\Microsoft Visual Studio `version`\VC\Redist\\`locale ID`\\. Można również pobrać je z [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?linkid=132793). (Użyj pola wyszukiwania w Centrum pobierania, aby wyszukać "Pakiet redystrybucyjny Visual C++ *wersji programu Visual Studio i aktualizacji*", które odpowiadają aplikacji. For example, jeśli używasz programu Visual Studio 2015 update 3 do tworzenia aplikacji, następnie wyszukaj "Visual C++ Redistributable pakietu 2015 update 3".) Aby uzyskać informacje o sposobie używania pakiet redystrybucyjny, zobacz [wskazówki: Wdrażanie Visual C++ aplikacji za pomocą pakietu redystrybucyjnego Visual C++](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).  
  
-   Wdrożenie centralnej za pomocą modułów scalania, z których każdy jest instalowany jako udostępnionej biblioteki DLL w %windir%\system32 określonej biblioteki Visual C++\\. (Instalacja w tym folderze wymaga uprawnień administratora.) Moduły scalania stają się częścią pliku .msi Instalatora aplikacji. Visual C++ redistributable scalania modułów znajdują się w programie Visual Studio w \Common Files\Merge pliki (x86) \Program modułów\\. Aby uzyskać więcej informacji, zobacz [redystrybuowanie przez za pomocą scalania modułów](../ide/redistributing-components-by-using-merge-modules.md).  
  
-   Wdrożenia lokalnego, skopiuj określonej biblioteki dll z programu Visual C++ z instalacji programu Visual Studio — zwykle w \Program Files (x86) \Microsoft Visual Studio `version`\VC\Redist\\`platform`\\`library`\—and Zainstaluj je na komputerach docelowych w tym samym folderze co plik wykonywalny aplikacji. Możesz użyć tej metody wdrożenia, aby umożliwić instalację przez użytkowników, którzy nie mają praw administratora, lub dla aplikacji, które mogą być uruchamiane z udziału sieciowego.  
  
 Jeśli wdrożenie korzysta z modułów scalania pakietu redystrybucyjnego i instalacja jest uruchomiona przez użytkownika, który nie ma praw administracyjnych, bibliotek DLL programu Visual C++ nie są zainstalowane i nie uruchomi aplikacji. Ponadto programy instalacyjne aplikacji, skompilowane z wykorzystaniem modułów scalania, które zezwalają na instalację dla poszczególnych użytkowników, instalują biblioteki we współdzielonej lokalizacji, która wpływa na wszystkich użytkowników systemu. Wdrożenia lokalnego umożliwia instalowanie wymaganych bibliotek DLL programu Visual C++ w katalogu aplikacji określonego użytkownika bez wpływu na innych użytkowników i wymagające uprawnień administracyjnych. Ponieważ może to prowadzić do problemów użytkowanie, nie zaleca się lokalnego wdrożenia programu Visual C++ redistributable biblioteki dll.  
  
 Nieprawidłowe wdrożenie bibliotek Visual C++ może spowodować błędy w czasie wykonywania aplikacji, która od nich zależy. Gdy system operacyjny ładuje aplikację, wykorzystuje kolejność wyszukiwania opisane w [LoadLibraryEx](http://go.microsoft.com/fwlink/p/?linkid=132792)  
  
## <a name="dynamic-linking-is-better-than-static-linking"></a>Łączenie dynamiczne jest lepsze niż łączenie statyczne  
 Zaleca się unikać statyczne połączenie w przypadku ponownego rozsyłania bibliotek języka Visual C++. Chociaż łączenie statyczne prawie nigdy nie zwiększa znacznie wydajności aplikacji, to prawie zawsze sprawia, że serwisowanie jest droższe. Rozważmy na przykład aplikację, statycznie połączoną z biblioteką, która to biblioteka została zaktualizowana, aby poprawić jej zabezpieczenia — aplikacja z nich nie skorzysta, chyba że zostanie zrekompilowana i ponownie wdrożona. Zamiast tego zaleca się dynamiczne łączenie aplikacji z bibliotekami, od których zależą, aby można było aktualizować biblioteki, kiedy zostaną wdrożone.  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażanie natywnych aplikacji komputerowych](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [Zabezpieczenia ClickOnce i wdrażania](/visualstudio/deployment/clickonce-security-and-deployment)   
 [Przykłady wdrożeń](../ide/deployment-examples.md)