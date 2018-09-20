---
title: Poznanie zależności aplikacji Visual C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7cdcc3af65f5a3a45b4a3549348a564a0cb0830e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425122"
---
# <a name="understanding-the-dependencies-of-a-visual-c-application"></a>Poznanie zależności aplikacji Visual C++

Aby określić, które bibliotek języka Visual C++, zależy od aplikacji, możesz wyświetlić właściwości projektu. (W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy nad projektem i wybierz polecenie **właściwości** otworzyć **stron właściwości** okno dialogowe.) Można również użyć modułu przeszukiwania zależności (depends.exe), który daje bardziej wszechstronny obraz zależności.

W **stron właściwości** okno dialogowe, możesz sprawdzić różne strony **właściwości konfiguracji** Aby zrozumieć zależności. Na przykład, jeśli projekt używa bibliotek MFC, a następnie wybierz **użycie MFC**, **Użyj MFC w współdzielonej bibliotece DLL** na **właściwości konfiguracji**, **ogólne**  strony aplikacji w czasie wykonywania jest zależna od biblioteki MFC DLL takie jak mfc\<wersji > .dll. Jeśli aplikacja nie używa MFC, może być zależna od biblioteki CRT wybranie **biblioteki środowiska uruchomieniowego** wartość **Multi-threaded DLL debugowania (/ MDd)** lub **Multi-threaded biblioteki DLL (/ MD)** na **właściwości konfiguracji**, **C/C++**, **generowania kodu** strony.

Bardziej wszechstronnym sposobem ustalenia, które biblioteki DLL zależy aplikacja ma użyć modułu przeszukiwania zależności (depends.exe), aby otworzyć aplikację. Możesz pobrać narzędzia z [modułu przeszukiwania zależności](http://go.microsoft.com/fwlink/p/?LinkId=132640) witryny sieci web.

Korzystając z depends.exe, można sprawdzić listę bibliotek DLL, które są połączone z aplikacji w czasie ładowania oraz listę jego bibliotek DLL załadowanych z opóźnieniem. Jeśli chcesz uzyskać pełną listę bibliotek DLL, które są ładowane dynamicznie w czasie wykonywania, służy funkcja profilowania w depends.exe do testowania aplikacji, dopóki nie jesteś pewien, że wszystkie ścieżki kodu zostały wykonane. Po zakończeniu sesji profilowania depends.exe pokazuje, które biblioteki DLL zostały dynamicznie załadowane w czasie wykonywania.

Korzystając z depends.exe, należy pamiętać, że biblioteka DLL może zależeć od innej biblioteki DLL lub od określonej wersji biblioteki DLL. Można użyć depends.exe na komputerze deweloperskim lub na komputerze docelowym. Na komputerze deweloperskim depends.exe raportuje biblioteki DLL, które są wymagane do obsługi aplikacji. Jeśli masz problemy z uruchomieniem aplikacji na komputerze docelowym, możesz skopiować do niego depends.exe i następnie otworzyć aplikację za pomocą narzędzia, aby określić, czy któryś wymagany plik DLL jest niedostępny lub nieprawidłowy.

Jeśli wiadomo, od których plików DLL zależy aplikacja, możesz określić te, które trzeba rozpowszechniać wraz z aplikacją, kiedy wdraża się ją na innym komputerze. W większości przypadków nie trzeba redystrybuować systemowych bibliotek DLL, ale może być konieczna Redystrybucja dll dla bibliotek języka Visual C++. Aby uzyskać więcej informacji, zobacz [Determining Which DLLs to Redistribute](../ide/determining-which-dlls-to-redistribute.md).

## <a name="see-also"></a>Zobacz też

[Wdrażanie aplikacji komputerowych](../ide/deploying-native-desktop-applications-visual-cpp.md)