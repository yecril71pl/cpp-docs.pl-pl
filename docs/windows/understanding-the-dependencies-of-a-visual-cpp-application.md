---
title: Poznanie zależności aplikacji Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- application deployment [C++], dependencies
- Dependency Walker
- dependencies [C++], application deployment and
- deploying applications [C++], dependencies
- DUMPBIN utility
- DLLs [C++], dependencies
- depends.exe
- libraries [C++], application deployment issues
ms.assetid: 62a44c95-c389-4c5f-82fd-07d7ef09dbf9
ms.openlocfilehash: 92db11778de7d31bbab67e649cd58e264da331e6
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787442"
---
# <a name="understanding-the-dependencies-of-a-visual-c-application"></a>Poznanie zależności aplikacji Visual C++

Aby określić, które bibliotek języka Visual C++, zależy od aplikacji, możesz wyświetlić właściwości projektu. (W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy nad projektem i wybierz polecenie **właściwości** otworzyć **stron właściwości** okno dialogowe.) W systemie Windows 8 i starszych można również użyć modułu przeszukiwania zależności (depends.exe), który daje bardziej wszechstronny obraz zależności. Aby uzyskać nowsze wersje systemu Windows [lucasg/zależności](https://github.com/lucasg/Dependencies) narzędzie zapewnia podobne funkcje (jest to narzędzia innych firm nie jest gwarantowana przez firmę Microsoft).

W **stron właściwości** okno dialogowe, możesz sprawdzić różne strony **właściwości konfiguracji** Aby zrozumieć zależności. Na przykład, jeśli projekt używa bibliotek MFC, a następnie wybierz **użycie MFC**, **Użyj MFC w współdzielonej bibliotece DLL** na **właściwości konfiguracji**, **ogólne**  strony aplikacji w czasie wykonywania jest zależna od biblioteki MFC DLL takie jak mfc\<wersji > .dll. Jeśli aplikacja nie używa MFC, może być zależna od biblioteki CRT wybranie **biblioteki środowiska uruchomieniowego** wartość **Multi-threaded DLL debugowania (/ MDd)** lub **Multi-threaded biblioteki DLL (/ MD)** na **właściwości konfiguracji**, **C/C++**, **generowania kodu** strony.

Korzystając z depends.exe, można sprawdzić listę bibliotek DLL, które są połączone z aplikacji w czasie ładowania oraz listę jego bibliotek DLL załadowanych z opóźnieniem. Jeśli chcesz uzyskać pełną listę bibliotek DLL, które są ładowane dynamicznie w czasie wykonywania, służy funkcja profilowania w depends.exe do testowania aplikacji, dopóki nie jesteś pewien, że wszystkie ścieżki kodu zostały wykonane. Po zakończeniu sesji profilowania depends.exe pokazuje, które biblioteki DLL zostały dynamicznie załadowane w czasie wykonywania.

Korzystając z depends.exe, należy pamiętać, że biblioteka DLL może zależeć od innej biblioteki DLL lub od określonej wersji biblioteki DLL. Można użyć depends.exe na komputerze deweloperskim lub na komputerze docelowym. Na komputerze deweloperskim depends.exe raportuje biblioteki DLL, które są wymagane do obsługi aplikacji. Jeśli masz problemy z uruchomieniem aplikacji na komputerze docelowym, możesz skopiować do niego depends.exe i następnie otworzyć aplikację za pomocą narzędzia, aby określić, czy któryś wymagany plik DLL jest niedostępny lub nieprawidłowy.

Jeśli wiadomo, od których plików DLL zależy aplikacja, możesz określić te, które trzeba rozpowszechniać wraz z aplikacją, kiedy wdraża się ją na innym komputerze. W większości przypadków nie trzeba redystrybuować systemowych bibliotek DLL, ale może być konieczna Redystrybucja dll dla bibliotek języka Visual C++. Aby uzyskać więcej informacji, zobacz [Determining Which DLLs to Redistribute](determining-which-dlls-to-redistribute.md).

## <a name="see-also"></a>Zobacz także

[Wdrażanie aplikacji komputerowych](deploying-native-desktop-applications-visual-cpp.md)
