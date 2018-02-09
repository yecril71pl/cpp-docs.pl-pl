---
title: 'Zasoby zlokalizowane w aplikacjach MFC: biblioteki DLL Satellite | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- multiple language support [C++]
- localization [C++], MFC resources
- localized resources [C++]
- MFC DLLs [C++], localizing
- DLLs [C++], localizing MFC
- resources [MFC], localizing
- resource-only DLLs [C++]
- resource-only DLLs [C++], MFC applications
- satellite DLLs [C++]
ms.assetid: 3a1100ae-a9c8-47b5-adbd-cbedef5992ef
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dc97e73998c581a40ed7d344b1ade5ca90b94ac2
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="localized-resources-in-mfc-applications-satellite-dlls"></a>Zasoby zlokalizowane w aplikacjach MFC: biblioteki DLL Satellite
MFC w wersji 7.0 lub nowszym obsługuje satelitarne bibliotek DLL, funkcją, która pomaga w tworzeniu aplikacji zlokalizowane dla wielu języków. Biblioteka DLL jest Satelita [DLL tylko z zasobami](../build/creating-a-resource-only-dll.md) zawierający zasoby aplikacji są zlokalizowane dla określonego języka. Po rozpoczęciu wykonywania aplikacji MFC automatycznie ładuje zlokalizowany zasób najbardziej odpowiednie dla środowiska. Na przykład można mieć aplikację z języka angielskiego zasobów przy użyciu dwóch satelitarne bibliotek DLL, zawierający francuskim tłumaczenie zasobów, a drugi zawierający translację niemieckiego. Gdy aplikacja jest uruchamiana w systemie język angielski, używa zasobów angielskiej wersji językowej. Jeśli działa w systemie francuskim, używa zasobów francuskim; Jeśli działa w systemie niemieckim, używa zasobów niemieckim.  
  
 Aby obsługiwać zasoby zlokalizowane w aplikacji MFC próbuje załadować satelitarnej biblioteki DLL MFC zawierającego zasoby zlokalizowane dla określonego języka. Satelitarne biblioteki DLL są nazywane *ApplicationNameXXX*dll, gdzie *ApplicationName* jest nazwą .exe lub .dll za pomocą MFC, i *XXX* jest trzyliterowy kod języka zasoby (na przykład "ENU" lub "DEU").  
  
 MFC próbuje załadować biblioteki DLL zasobów dla każdego z następujących języków w kolejności, zatrzymywanie, gdy zostanie znaleziony:  
  
1. Bieżący użytkownik domyślny język interfejsu użytkownika, ponieważ zwrócony z interfejsu API Win32 GetUserDefaultUILanguage().  
  
2.  Bieżący użytkownik w domyślny język interfejsu użytkownika, bez żadnych szczególnych odmianą języka (oznacza to, że ENC [kanadyjskich angielskim] staje się ENU [stany USA English]).  
  
3.  System domyślny język interfejsu użytkownika, ponieważ zwrócony z interfejsu API GetSystemDefaultUILanguage(). Na innych platformach jest język systemu operacyjnego, do samej siebie.  
  
4.  System domyślny język interfejsu użytkownika, bez żadnych odmianą określonego języka.  
  
5.  Fałszywych języka z 3-znakowy kod LOC.  
  
 MFC nie może znaleźć żadnych satelitarne bibliotek DLL, używa, niezależnie od zasobów znajdują się w samej aplikacji.  
  
 Na przykład załóżmy, że aplikacja LangExample.exe używa MFC i działa na wielu interfejsu użytkownika systemu. język interfejsu użytkownika systemu to ENU [stany USA Angielski] i FRC [kanadyjskich francuski] ustawiony jest język interfejsu użytkownika bieżącego użytkownika. MFC szuka następujących bibliotek DLL w następującej kolejności:  
  
1.  LangExampleFRC.dll (język interfejsu użytkownika dla użytkownika).  
  
2.  LangExampleFRA.dll (język Interfejsu użytkownika bez odmianą języka, w tym przykładzie francuski (Francja).  
  
3.  LangExampleENU.dll (język interfejsu użytkownika systemu).  
  
4.  LangExampleLOC.dll.  
  
 Jeśli żaden z tych biblioteki DLL nie zostaną znalezione, MFC LangExample.exe używa zasobów.  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki dll w programie Visual C++](../build/dlls-in-visual-cpp.md)   
 [TN057: lokalizacja składników MFC](../mfc/tn057-localization-of-mfc-components.md)