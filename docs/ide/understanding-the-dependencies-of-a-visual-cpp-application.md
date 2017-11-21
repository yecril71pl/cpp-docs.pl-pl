---
title: "Poznanie zależności aplikacji Visual C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 94e1978c5c0188410cf8d6d6bfdfe08d9af620e0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="understanding-the-dependencies-of-a-visual-c-application"></a>Poznanie zależności aplikacji Visual C++
Aby ustalić, które biblioteki Visual C++, zależy od aplikacji, można wyświetlić właściwości projektu. (W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **właściwości** otworzyć **strony właściwości** okno dialogowe.) Można również użyć modułu przeszukiwania zależności (depends.exe), który daje bardziej wszechstronny obraz zależności.  
  
 W **strony właściwości** okno dialogowe, należy zbadać różnych stronach w obszarze **właściwości konfiguracji** zrozumieć zależności. Na przykład, jeśli projekt korzysta z bibliotek MFC i użytkownik wybierze **Użyj MFC**, **Użyj MFC w bibliotece DLL udostępnionych** na **właściwości konfiguracji**, **ogólne**  strony, aplikacji w czasie wykonywania jest zależna od biblioteki DLL MFC takich jak mfc\<wersji > .dll. Jeśli aplikacja nie używać MFC, może być zależna biblioteki CRT wybranie **biblioteki wykonawczej** wartość **Multi-threaded DLL debugowania (/ MDd)** lub **Multi-threaded DLL (/ MD)**na **właściwości konfiguracji**, **C/C++**, **generowania kodu** strony.  
  
 Bardziej zaawansowane można określić, które biblioteki DLL zależy od aplikacji jest Użyj Walkera zależności (depends.exe), aby otworzyć aplikację. Możesz pobrać narzędzie z [Walkera zależności](http://go.microsoft.com/fwlink/p/?LinkId=132640) witryny sieci web.  
  
 Za pomocą depends.exe, można sprawdzić listę bibliotek DLL, które są połączone z aplikacji w czasie ładowania oraz listę jego bibliotek DLL załadowanych z opóźnieniem. Jeśli chcesz uzyskać pełną listę bibliotek DLL ładowanych dynamicznie w czasie wykonywania, funkcja profilowania w depends.exe Aby przetestować aplikację, dopóki nie masz pewności, że zostały wykonane wszystkie ścieżki kodu. Po zakończeniu sesji profilowania depends.exe pokazuje, które biblioteki DLL dynamicznie zostały załadowane w czasie wykonywania.  
  
 Korzystając z depends.exe, należy pamiętać, że biblioteka DLL może zależeć od innej biblioteki DLL lub od określonej wersji biblioteki DLL. Można użyć depends.exe na komputerze deweloperskim lub na komputerze docelowym. Na komputerze deweloperskim depends.exe raportuje biblioteki DLL, które są wymagane do obsługi aplikacji. Jeśli masz problemy z uruchomieniem aplikacji na komputerze docelowym, możesz skopiować do niego depends.exe i następnie otworzyć aplikację za pomocą narzędzia, aby określić, czy któryś wymagany plik DLL jest niedostępny lub nieprawidłowy.  
  
 Jeśli wiadomo, od których plików DLL zależy aplikacja, możesz określić te, które trzeba rozpowszechniać wraz z aplikacją, kiedy wdraża się ją na innym komputerze. W większości przypadków nie trzeba przeprowadzać ponownej dystrybucji systemowej biblioteki dll, ale może być konieczne Ponowna dystrybucja bibliotek DLL dla bibliotek języka Visual C++. Aby uzyskać więcej informacji, zobacz [określania które biblioteki dll do ponownej dystrybucji](../ide/determining-which-dlls-to-redistribute.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażanie natywnych aplikacji komputerowych](../ide/deploying-native-desktop-applications-visual-cpp.md)