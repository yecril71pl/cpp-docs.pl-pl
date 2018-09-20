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
ms.openlocfilehash: 407972d9df042854ec1cd5a61964782422f359a6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433533"
---
# <a name="choosing-a-deployment-method"></a>Wybieranie metody wdrażania

O ile aplikacji Visual C++ jest niezależna i można ją wdrożyć za pomocą polecenia Kopiuj, zaleca się użyć Instalatora Windows dla wdrożenia. Instalator Windows obsługuje instalację, naprawę oraz dezinstalację, a także obsługuje atomowe aktualizowanie plików aplikacji, zależności i wpisów rejestru.

> [!NOTE]
>  Mimo że [ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) wdrażanie natywnych aplikacji Visual C++ jest możliwe w programie Visual Studio, wymaga dodatkowych kroków. Aby uzyskać więcej informacji, zobacz [wdrożenie rozwiązania ClickOnce dla aplikacji Visual C++](../ide/clickonce-deployment-for-visual-cpp-applications.md).

## <a name="visual-c-libraries-are-shared-dlls"></a>Biblioteki Visual C++ to współdzielone biblioteki DLL

Ponieważ biblioteki Visual C++ są instalowane w katalogu %windir%\system32\ przez instalator Visual Studio, podczas tworzenia aplikacji Visual C++, która od nich zależy, będzie ona działała zgodnie z oczekiwaniami. Aby wdrożyć aplikację na komputerach, które nie mają Visual Studio, zalecamy, aby się upewnić, że odpowiednie biblioteki są instalowane wraz z aplikacją.

## <a name="redistributing-visual-c-libraries"></a>Redystrybucja bibliotek Visual C++

We wdrożeniach można redystrybuować dowolną wersję biblioteki Visual C++, której licencja na to pozwala. Poniżej przedstawiono trzy sposoby ich wdrożenia:

- Wdrożenie centralne przy użyciu pakietów redystrybucyjnych, które instaluje biblioteki Visual C++ jako współdzielone Dlll w %windir%\system32\\. (Instalacja w tym folderze wymaga uprawnień administratora). Można utworzyć program Instalatora lub skrypt, który uruchamia pakiet redystrybucyjny przed zainstalowaniem aplikacji na komputerze docelowym. Pakiety redystrybucyjne są dostępne dla platform x86, x64 i ARM (VCRedist_x86.exe, VCRedist_x64.exe lub VCRedist_arm.exe). Program Visual Studio zawiera te pakiety w % ProgramFiles (x86) %\Microsoft Visual Studio `version`\VC\Redist\\`locale ID`\\. Można również pobrać je z [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?linkid=132793). (Użyj pola wyszukiwania w Centrum pobierania, aby wyszukać "Pakiet redystrybucyjny Visual C++ *wersji programu Visual Studio i zaktualizuj*" który odpowiada aplikacji. Adapterem, jeśli program Visual Studio 2015 update 3 jest używany do tworzenia aplikacji, wyszukaj "Visual C++ Redistributable pakietu 2015 update 3".) Aby uzyskać informacje o sposobie korzystania z pakietu redystrybucyjnego, zobacz [wskazówki: Wdrażanie Visual C++ Application By Using the Visual C++ Redistributable Package](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).

- Wdrożenie centralne przy użyciu modułów scalania, każdy z nich instaluje określoną bibliotekę języka Visual C++ jako współdzieloną DLL w %windir%\system32\\. (Instalacja w tym folderze wymaga uprawnień administratora.) Moduły scalania stają się częścią pliku .msi Instalatora aplikacji. Visual C++ redystrybucyjnych modułów scalania znajdują się w programie Visual Studio, w \Program pliki (x86) \Common modułów\\. Aby uzyskać więcej informacji, zobacz [Redystrybucja za pomocą scalonych modułów](../ide/redistributing-components-by-using-merge-modules.md).

- Wdrożenie lokalne, w którym kopiujesz określone dll Visual C++ z instalacji programu Visual Studio — zazwyczaj w \Program Files (x86) \Microsoft Visual Studio `version`\VC\Redist\\`platform`\\`library`\—and Zainstaluj je na komputerach docelowych w tym samym folderze co plik wykonywalny aplikacji. Możesz użyć tej metody wdrożenia, aby umożliwić instalację przez użytkowników, którzy nie mają praw administratora, lub dla aplikacji, które mogą być uruchamiane z udziału sieciowego.

Jeśli wdrożenie używa redystrybucyjnych modułów scalania, a instalację uruchamia użytkownik, który nie ma praw administracyjnych, bibliotek DLL Visual C++ nie są instalowane i aplikacja nie będzie działać. Ponadto programy instalacyjne aplikacji, skompilowane z wykorzystaniem modułów scalania, które zezwalają na instalację dla poszczególnych użytkowników, instalują biblioteki we współdzielonej lokalizacji, która wpływa na wszystkich użytkowników systemu. Aby zainstalować wymagane dll Visual C++ w katalogu aplikacji danego użytkownika bez wywierania wpływu na innych użytkowników lub wymagania praw administratora, można użyć lokalnego wdrożenia. Ponieważ może to do problemów z serwisowaniem, firma Microsoft nie zaleca się lokalnego wdrażania redystrybucyjnych bibliotek DLL Visual C++.

Nieprawidłowe wdrożenie bibliotek Visual C++ może spowodować błędy w czasie wykonywania aplikacji, która od nich zależy. Podczas ładowania aplikacji system operacyjny używa kolejności wyszukiwania opisanej w [LoadLibraryEx](http://go.microsoft.com/fwlink/p/?linkid=132792)

## <a name="dynamic-linking-is-better-than-static-linking"></a>Łączenie dynamiczne jest lepsze niż łączenie statyczne

Zaleca się unikać łączenia statycznego, gdy redystrybucji bibliotek Visual C++. Chociaż łączenie statyczne prawie nigdy nie zwiększa znacznie wydajności aplikacji, to prawie zawsze sprawia, że serwisowanie jest droższe. Rozważmy na przykład aplikację, statycznie połączoną z biblioteką, która to biblioteka została zaktualizowana, aby poprawić jej zabezpieczenia — aplikacja z nich nie skorzysta, chyba że zostanie zrekompilowana i ponownie wdrożona. Zamiast tego zaleca się dynamiczne łączenie aplikacji z bibliotekami, od których zależą, aby można było aktualizować biblioteki, kiedy zostaną wdrożone.

## <a name="see-also"></a>Zobacz też

[Wdrażanie aplikacji komputerowych](../ide/deploying-native-desktop-applications-visual-cpp.md)<br>
[Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)<br>
[Przykłady wdrożeń](../ide/deployment-examples.md)