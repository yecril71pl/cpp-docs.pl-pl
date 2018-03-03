---
title: Przygotowanie maszyny testowej do uruchomienia debugowania pliku wykonywalnego | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- debug executable, preparing a test machine to run
ms.assetid: f0400989-cc2e-4dce-9788-6bdbe91c6f5a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 344f413eb2325156996700b6975826600ab997f7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="preparing-a-test-machine-to-run-a-debug-executable"></a>Przygotowanie maszyny testowej do uruchomienia debugowania pliku wykonywalnego
Aby przygotować komputer do testowania wersji do debugowania aplikacji, która jest wbudowana w języku Visual C++, należy wdrożyć debugowania wersje biblioteki Visual C++ bibliotek DLL, która zależy od aplikacji. Aby zidentyfikować, która biblioteki DLL ma zostać wdrożony, postępuj zgodnie z instrukcjami [poznanie zależności aplikacji Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md). Zazwyczaj wersje debugowania Visual C++ biblioteki DLL mają nazwy, które kończą się "d"; na przykład pliku msvcr100.dll wersja debugowania nosi nazwę msvcr100d.dll.  
  
> [!NOTE]
>  Wersje do debugowania aplikacji nie są pakietu redystrybucyjnego i wersje debugowania Visual C++ biblioteki DLL nie są do dystrybucji. Wersje do debugowania aplikacji i programu Visual C++ bibliotek DLL może wdrożyć tylko na innych komputerach, wyłącznie w celu debugowania i testowania aplikacji na komputerze, który nie ma zainstalowanego programu Visual Studio. Aby uzyskać więcej informacji, zobacz [redystrybuowanie pliki Visual C++](../ide/redistributing-visual-cpp-files.md).  
  
 Istnieją trzy sposoby wdrażania wersji debugowania Visual C++ biblioteki dll wraz z wersji do debugowania aplikacji.  
  
-   Aby zainstalować wersję do debugowania określonej biblioteki dll programu Visual C++ do katalogu %windir%\system32\ przy użyciu instalacji projektu zawierającego modułów scalania dla odpowiedniej biblioteki wersji i architektury aplikacji przy użyciu centralnej wdrażania. Moduły scalania zostały znalezione w Program Files lub katalogu Program Files (x86) \Common Files\Merge modułów\\. Wersja debugowania moduł scalania ma debugowania, w tym przykładzie namefor Microsoft_VC110_DebugCRT_x86.msm. Przykładem tego wdrożenia można znaleźć w [wskazówki: Wdrażanie Visual C++ aplikacji za pomocą instalacji projektu](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).  
  
-   Aby zainstalować wersję do debugowania określonej biblioteki dll programu Visual C++ w katalogu instalacji aplikacji przy użyciu plików, które zostały opublikowane w Program Files lub Program Files (x86) katalogu \Microsoft Visual Studio przy użyciu lokalnego wdrażania \<wersji > \VC\redist\Debug_NonRedist\\.  
  
    > [!NOTE]
    >  Zdalne debugowanie aplikacji utworzony za pomocą programu Visual C++ 2005 lub Visual C++ 2008 na innym komputerze, należy wdrożyć wersje debugowania Visual C++, biblioteki DLL jako zestawy side-by-side udostępnione. Instalacja projektu albo Instalatora Windows można użyć do zainstalowania odpowiedniego modułów scalania.  
  
-   Użyj the_**Wdróż** opcji **programu Configuration Manager** okno dialogowe w programie Visual Studio, aby skopiować dane wyjściowe projektu i inne pliki z komputerem zdalnym. 
  
 Po zainstalowaniu programu Visual C++ bibliotek DLL, można uruchomić zdalnego debugera w udziale sieciowym. Aby uzyskać więcej informacji na temat debugowania zdalnego, zobacz [zdalnego debugowania](/visualstudio/debugger/remote-debugging.md).  
  
## <a name="see-also"></a>Zobacz też  
 
 [Wdrożenia w programie Visual C++](../ide/deployment-in-visual-cpp.md)   
 [Opcje wiersza polecenia Instalatora systemu Windows](http://msdn.microsoft.com/library/windows/desktop/aa367988.aspx)   
 [Przykłady wdrożeń](../ide/deployment-examples.md) [debugowanie zdalne](/visualstudio/debugger/remote-debugging.md)