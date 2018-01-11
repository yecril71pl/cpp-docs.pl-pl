---
title: "Wybieranie metody wdrażania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "35"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1c444b3319c60b80bdfdc14000a41d65869d0514
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="choosing-a-deployment-method"></a>Wybieranie metody wdrażania
Jeśli aplikacji Visual C++ nie jest niezależna i można wdrożyć przy użyciu polecenia kopiowania, zalecane jest użycie Instalatora systemu Windows dla wdrożenia. Instalator Windows obsługuje instalację, naprawę oraz dezinstalację, a także obsługuje atomowe aktualizowanie plików aplikacji, zależności i wpisów rejestru.  
  
> [!NOTE]
>  Mimo że [ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) wdrażanie natywnych aplikacji Visual C++ w programie Visual Studio i wymaga wykonania dodatkowych czynności. Aby uzyskać więcej informacji, zobacz [wdrożenie rozwiązania ClickOnce dla aplikacji Visual C++](../ide/clickonce-deployment-for-visual-cpp-applications.md).  
  
## <a name="visual-c-libraries-are-shared-dlls"></a>Biblioteki Visual C++ to współdzielone biblioteki DLL  
 Ponieważ biblioteki Visual C++ są instalowane w katalogu %windir%\system32\ przez instalator Visual Studio, podczas tworzenia aplikacji Visual C++, która od nich zależy, będzie ona działała zgodnie z oczekiwaniami. Aby wdrożyć aplikację na komputerach, które nie mają Visual Studio, zalecamy, aby się upewnić, że odpowiednie biblioteki są instalowane wraz z aplikacją.  
  
## <a name="redistributing-visual-c-libraries"></a>Redystrybucja bibliotek Visual C++  
 We wdrożeniach można redystrybuować dowolną wersję biblioteki Visual C++, której licencja na to pozwala. Poniżej przedstawiono trzy sposoby ich wdrożenia:  
  
-   Centralnej wdrożenie przy użyciu pakietu redystrybucyjnego pakiety, w którym bibliotek języka Visual C++ jest instalowany jako pliki dll w %windir%\system32\\. (Instalacja w tym folderze wymaga uprawnień administratora). Można utworzyć program Instalatora lub skrypt, który uruchamia pakiet redystrybucyjny przed zainstalowaniem aplikacji na komputerze docelowym. Pakiety redystrybucyjne są dostępne dla platform x86, x64 i ARM (VCRedist_x86.exe, VCRedist_x64.exe lub VCRedist_arm.exe). Visual Studio zawiera te pakiety w % ProgramFiles (x86) %\Microsoft Visual Studio `version`\VC\Redist\\`locale ID`\\. Można również pobrać je z [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?linkid=132793). (W Centrum pobierania, wyszukaj "Pakiet redystrybucyjny Visual C++ *wersji programu Visual Studio i aktualizacji*", które odpowiadają aplikacji. Na przykład, jeśli użyłeś Visual Studio 2012 update 4 do stworzenia aplikacji, wyszukaj „Visual C++ Redistributable Package 2012 update 4”.) Aby uzyskać informacje o sposobie używania pakiet redystrybucyjny, zobacz [wskazówki: Wdrażanie Visual C++ aplikacji za pomocą pakietu redystrybucyjnego Visual C++](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).  
  
-   Wdrożenie centralnej za pomocą modułów scalania, z których każdy jest instalowany jako udostępnionej biblioteki DLL w %windir%\system32 określonej biblioteki Visual C++\\. (Instalacja w tym folderze wymaga uprawnień administratora.) Moduły scalania stają się częścią pliku .msi Instalatora aplikacji. Visual C++ redistributable scalania modułów znajdują się w programie Visual Studio w \Common Files\Merge pliki (x86) \Program modułów\\. Aby uzyskać więcej informacji, zobacz [redystrybuowanie przez za pomocą scalania modułów](../ide/redistributing-components-by-using-merge-modules.md).  
  
-   Wdrożenia lokalnego, skopiuj określonej biblioteki dll z programu Visual C++ z instalacji programu Visual Studio — zwykle w \Program Files (x86) \Microsoft Visual Studio `version`\VC\Redist\\`platform`\\`library`\—and Zainstaluj je na komputerach docelowych w tym samym folderze co plik wykonywalny aplikacji. Możesz użyć tej metody wdrożenia, aby umożliwić instalację przez użytkowników, którzy nie mają praw administratora, lub dla aplikacji, które mogą być uruchamiane z udziału sieciowego.  
  
 Jeśli wdrożenie korzysta z modułów scalania pakietu redystrybucyjnego i instalacja jest uruchomiona przez użytkownika, który nie ma praw administracyjnych, bibliotek DLL programu Visual C++ nie są zainstalowane i nie uruchomi aplikacji. Ponadto programy instalacyjne aplikacji, skompilowane z wykorzystaniem modułów scalania, które zezwalają na instalację dla poszczególnych użytkowników, instalują biblioteki we współdzielonej lokalizacji, która wpływa na wszystkich użytkowników systemu. Wdrożenia lokalnego umożliwia instalowanie wymaganych bibliotek DLL programu Visual C++ w katalogu aplikacji określonego użytkownika bez wpływu na innych użytkowników i wymagające uprawnień administracyjnych. Ponieważ może to prowadzić do problemów użytkowanie, nie zaleca się lokalnego wdrożenia programu Visual C++ redistributable biblioteki dll.  
  
 Nieprawidłowe wdrożenie bibliotek Visual C++ może spowodować błędy w czasie wykonywania aplikacji, która od nich zależy. Gdy system operacyjny ładuje aplikację, wykorzystuje kolejność wyszukiwania opisane w [LoadLibraryEx](http://go.microsoft.com/fwlink/p/?linkid=132792)  
  
## <a name="dynamic-linking-is-better-than-static-linking"></a>Łączenie dynamiczne jest lepsze niż łączenie statyczne  
 Zaleca się unikać statyczne połączenie w przypadku ponownego rozsyłania bibliotek języka Visual C++. Chociaż łączenie statyczne prawie nigdy nie zwiększa znacznie wydajności aplikacji, to prawie zawsze sprawia, że serwisowanie jest droższe. Rozważmy na przykład aplikację, statycznie połączoną z biblioteką, która to biblioteka została zaktualizowana, aby poprawić jej zabezpieczenia — aplikacja z nich nie skorzysta, chyba że zostanie zrekompilowana i ponownie wdrożona. Zamiast tego zaleca się dynamiczne łączenie aplikacji z bibliotekami, od których zależą, aby można było aktualizować biblioteki, kiedy zostaną wdrożone.  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażanie natywnych aplikacji komputerowych](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [Nie w kompilacji: Wybieranie strategii wdrażania](http://msdn.microsoft.com/en-us/ecd632d8-063c-4028-b785-81bba045107b)   
 [Omówienie wdrożenia Instalatora Windows](http://msdn.microsoft.com/en-us/3ce4610a-b54f-404e-b650-42f4a55dfc3b)   
 [Zabezpieczenia ClickOnce i wdrażania](/visualstudio/deployment/clickonce-security-and-deployment)   
 [Przykłady wdrożeń](../ide/deployment-examples.md)