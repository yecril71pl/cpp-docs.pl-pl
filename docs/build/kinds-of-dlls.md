---
title: Rodzaje bibliotek DLL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC DLLs [C++], types
- DLLs [C++], types
- DLLs [C++], MFC
ms.assetid: f6a30db9-6138-4b2c-90cc-a17855e499a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 605d60535df8d0a94d58e120df89f975402b8a22
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="kinds-of-dlls"></a>Rodzaje bibliotek DLL
Ten temat zawiera informacje ułatwiające wybór rodzaju biblioteki DLL do kompilacji.  
  
##  <a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a> Różne rodzaje dostępnych bibliotek DLL  
 Visual C++ można utworzyć biblioteki DLL systemu Win32 w języka C lub C++, który nie należy używać biblioteki Microsoft Foundation Class (MFC). Kreator aplikacji Win32, można utworzyć projektu z systemem innym niż MFC DLL.  
  
 Biblioteki MFC sam jest dostępna, albo biblioteki dołączanej statycznie lub liczba biblioteki DLL przy użyciu Kreatora biblioteki DLL MFC. Jeśli biblioteki DLL używa MFC, Visual C++ obsługuje trzy różne scenariusze programowania biblioteki DLL:  
  
-   Tworzenie zwykły biblioteki MFC DLL, które statycznie łączy MFC  
  
-   Tworzenie zwykły biblioteki MFC DLL, który dynamicznie łączy MFC  
  
-   Tworzenie biblioteki DLL rozszerzenia MFC, która zawsze dynamiczne łącze MFC  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [Biblioteki DLL inne niż MFC: omówienie](../build/non-mfc-dlls-overview.md)  
  
-   [Regularne biblioteki DLL MFC połączone statycznie z MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [Regularne biblioteki DLL MFC połączone dynamicznie z MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Biblioteki DLL rozszerzeń MFC: omówienie](../build/extension-dlls-overview.md)  
  
-   [Jakiego rodzaju biblioteki DLL do użycia](#_core_which_kind_of_dll_to_use)  
  
##  <a name="_core_which_kind_of_dll_to_use"></a> Jakiego typu biblioteki DLL do użycia  
 Jeśli biblioteki DLL nie korzysta z MFC, użyj Visual C++ do kompilacji z systemem innym niż — MFC Win32 biblioteki DLL. Łączenie biblioteki DLL z MFC (statycznie lub dynamicznie) zajmuje znacznej ilości miejsca i pamięci. Nie należy połączyć MFC, chyba że biblioteki DLL MFC korzysta.  
  
 Jeśli biblioteki DLL będą używać MFC i będą używane przez MFC lub innego typu niż MFC aplikacji, należy utworzyć regularne biblioteki DLL MFC, która łączy dynamicznie z MFC lub regularne biblioteki DLL MFC, która łączy statycznie z MFC. W większości przypadków prawdopodobnie chcesz użyć regularne biblioteki DLL MFC, łączącą dynamicznie z MFC oszczędności w pamięci z udostępnionego wersji MFC mogą być istotne, ponieważ będzie znacznie mniejszy rozmiar pliku biblioteki dll. Jeśli łączysz się statycznie z MFC, rozmiar pliku biblioteki DLL będzie większa i potencjalnie zajmują dodatkową pamięć, ponieważ ładuje własną prywatną kopię kod biblioteki MFC.  
  
 Tworzenie biblioteki DLL, która łączy dynamicznie z MFC jest szybsza niż Tworzenie biblioteki DLL, które statycznie łączy się MFC, ponieważ nie jest konieczne łączenie MFC sam. Jest to szczególnie ważne w kompilacjach debugowania, w którym konsolidator musi compact informacje o debugowaniu. Łącząc się z biblioteki DLL, który już zawiera informacje o debugowaniu, jest mniej informacji debugowania kompaktowania w obrębie biblioteki DLL.  
  
 Łączenie dynamicznie z MFC jeden wadą jest to, że musisz przeprowadzić dystrybucję udostępnionego Mfcx0.dll bibliotek DLL i Msvcrxx.dll (lub podobny plików) z biblioteki DLL. Biblioteki DLL MFC są za darmo do dystrybucji, ale nadal należy zainstalować bibliotek DLL programu Instalatora. Ponadto muszą dostarczać Msvcrxx.dll, który zawiera biblioteki wykonawczej języka C, który jest używany zarówno przez Twojego programu oraz biblioteki DLL MFC, same.  
  
 Biblioteki DLL będzie używany tylko pliki wykonywalne MFC, masz wybór między budowania regularnych biblioteki MFC DLL lub biblioteki DLL rozszerzenia MFC. Jeśli musisz przekazać pochodnych MFC obiektów między aplikacją a biblioteki DLL biblioteki DLL implementuje klasy wielokrotnego użytku, pochodnych istniejących klas MFC, należy utworzyć bibliotekę DLL rozszerzenia MFC.  
  
 Jeśli biblioteki DLL łączy dynamicznie z MFC, biblioteki MFC dll może być rozpowszechniane za pomocą biblioteki DLL. Taka architektura jest szczególnie przydatne w przypadku udostępniania biblioteki klas między wiele plików wykonywalnych w celu zaoszczędzenia miejsca na dysku i ograniczania użycia pamięci.  
  
 Przed w wersji 4.0, Visual C++ tylko obsługiwane dwa rodzaje bibliotek DLL, które używane MFC: USRDLLs i AFXDLLs. Regularne biblioteki DLL MFC połączone statycznie z MFC mają te same parametry jako wcześniejsze USRDLL. Biblioteki DLL rozszerzenia MFC mają te same parametry jako wcześniejsze AFXDLLs.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [Biblioteki DLL inne niż MFC: omówienie](../build/non-mfc-dlls-overview.md)  
  
-   [Regularne biblioteki DLL MFC połączone statycznie z MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [Regularne biblioteki DLL MFC połączone dynamicznie z MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Biblioteki DLL rozszerzeń MFC: omówienie](../build/extension-dlls-overview.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki DLL w programie Visual C++](../build/dlls-in-visual-cpp.md)