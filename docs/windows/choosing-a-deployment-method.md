---
title: Wybieranie metody wdrażania
ms.date: 03/14/2019
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
ms.openlocfilehash: 633b76458fdc24ef9ba551d8209c5c99720df37e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377407"
---
# <a name="choosing-a-deployment-method"></a>Wybieranie metody wdrażania

Jeśli aplikacja Visual C++ jest niezależna i można ją wdrożyć za pomocą polecenia kopia, zaleca się użycie Instalatora Windows do wdrożenia. Instalator Windows obsługuje instalację, naprawę oraz dezinstalację, a także obsługuje atomowe aktualizowanie plików aplikacji, zależności i wpisów rejestru.

> [!NOTE]
> Chociaż [clickonce](/visualstudio/deployment/clickonce-security-and-deployment) wdrożenia dla aplikacji natywnych języka Visual C++ jest możliwe w programie Visual Studio, wymaga dodatkowych kroków. Aby uzyskać więcej informacji, zobacz [ClickOnce Deployment for Visual C++ Applications](clickonce-deployment-for-visual-cpp-applications.md).

## <a name="visual-c-libraries-are-shared-dlls"></a>Biblioteki Visual C++ to współdzielone biblioteki DLL

Ponieważ biblioteki Visual C++ są instalowane w katalogu %windir%\system32\ przez instalator Visual Studio, podczas tworzenia aplikacji Visual C++, która od nich zależy, będzie ona działała zgodnie z oczekiwaniami. Aby wdrożyć aplikację na komputerach, które nie mają Visual Studio, zalecamy, aby się upewnić, że odpowiednie biblioteki są instalowane wraz z aplikacją.

## <a name="redistributing-visual-c-libraries"></a>Redystrybucja bibliotek Visual C++

We wdrożeniach można redystrybuować dowolną wersję biblioteki Visual C++, której licencja na to pozwala. Poniżej przedstawiono trzy sposoby ich wdrożenia:

- Wdrożenie centralne przy użyciu pakietów redystrybucyjnych, które instalują biblioteki Visual\\C++ jako udostępnione biblioteki DLL w %windir%\system32 . (Instalacja w tym folderze wymaga uprawnień administratora). Przed zainstalowaniem aplikacji na komputerze docelowym można utworzyć skrypt lub program instalacyjny, który uruchamia pakiet redystrybucyjny. Pakiety redystrybucyjne są dostępne dla platform x86, x64 i ARM (VCRedist_x86.exe, VCRedist_x64.exe lub VCRedist_arm.exe). Program `version`Visual Studio zawiera te pakiety w programie %ProgramFiles(x86)%\Microsoft Visual Studio \VC\Redist\\`locale ID`\\. Można je również pobrać z [Centrum pobierania Microsoft](https://www.microsoft.com/download). (Użyj pola wyszukiwania w Centrum pobierania, aby wyszukać wersję i aktualizację programu Visual C++ Redystrybucyjny *program Visual Studio,* która pasuje do aplikacji. Na przykład jeśli do utworzenia aplikacji użyto aktualizacji programu Visual Studio 2015 3, wyszukaj hasło "Visual C++ Redistributable Package 2015 update 3")." Aby uzyskać informacje dotyczące używania pakietu redystrybucyjnego, zobacz [Przewodnik: Wdrażanie aplikacji Visual C++ przy użyciu pakietu redystrybucyjnego Visual C++](deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).

- Wdrażanie centralne przy użyciu modułów scalania, z których każda instaluje określoną bibliotekę Visual\\C++ jako udostępnioną bibliotekę DLL w %windir%\system32 . (Instalacja w tym folderze wymaga uprawnień administratora). Moduły scalania stają się częścią pliku instalatora msi dla twojej aplikacji. Moduły korespondencji redystrybucyjnej visual C++ są zawarte w programie Visual Studio\\w programie \Program Files (x86)\Common Files\Merge Modules . Aby uzyskać więcej informacji, zobacz [Redystrybucja przy użyciu modułów scalania](redistributing-components-by-using-merge-modules.md).

- Wdrożenie lokalne, w którym można skopiować określone biblioteki DLL programu Visual C++ z instalacji programu `version`Visual Studio —\\`platform`\\`library`zazwyczaj w folderze \Program Files (x86)\Microsoft Visual Studio \VC\Redist \— i zainstalować je na komputerach docelowych w tym samym folderze co plik wykonywalny aplikacji. Możesz użyć tej metody wdrożenia, aby umożliwić instalację przez użytkowników, którzy nie mają praw administratora, lub dla aplikacji, które mogą być uruchamiane z udziału sieciowego.

Jeśli wdrożenie używa redystrybucyjnych modułów scalania, a instalacja jest uruchamiana przez użytkownika, który nie ma praw administracyjnych, biblioteki DLL visual C++ nie są zainstalowane i aplikacja nie zostanie uruchomiony. Ponadto programy instalacyjne aplikacji, skompilowane z wykorzystaniem modułów scalania, które zezwalają na instalację dla poszczególnych użytkowników, instalują biblioteki we współdzielonej lokalizacji, która wpływa na wszystkich użytkowników systemu. Za pomocą wdrożenia lokalnego można zainstalować wymagane biblioteki DLL języka Visual C++ w katalogu aplikacji określonego użytkownika bez wpływu na innych użytkowników lub wymagania uprawnień administratora. Ponieważ może to spowodować problemy z możliwością serwisowania, nie zaleca się lokalnego wdrażania bibliotek bibliotek DLL redystrybucyjnych w języku Visual C++.

Nieprawidłowe wdrożenie bibliotek Visual C++ może spowodować błędy w czasie wykonywania aplikacji, która od nich zależy. Gdy system operacyjny ładuje aplikację, używa kolejności wyszukiwania opisanej w [loadlibraryex](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw).

## <a name="dynamic-linking-is-better-than-static-linking"></a>Łączenie dynamiczne jest lepsze niż łączenie statyczne

Zaleca się unikanie łączenia statycznego podczas redystrybucji bibliotek języka Visual C++. Chociaż łączenie statyczne prawie nigdy nie zwiększa znacznie wydajności aplikacji, to prawie zawsze sprawia, że serwisowanie jest droższe. Rozważmy na przykład aplikację, statycznie połączoną z biblioteką, która to biblioteka została zaktualizowana, aby poprawić jej zabezpieczenia — aplikacja z nich nie skorzysta, chyba że zostanie zrekompilowana i ponownie wdrożona. Zamiast tego zaleca się dynamiczne łączenie aplikacji z bibliotekami, od których zależą, aby można było aktualizować biblioteki, kiedy zostaną wdrożone.

## <a name="see-also"></a>Zobacz też

[Wdrażanie aplikacji klasycznych](deploying-native-desktop-applications-visual-cpp.md)<br>
[Kliknijonce zabezpieczenia i wdrażanie](/visualstudio/deployment/clickonce-security-and-deployment)<br>
[Przykłady wdrożeń](deployment-examples.md)
