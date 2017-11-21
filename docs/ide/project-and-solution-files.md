---
title: "Pliki projektu i rozwiązania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.files.projectandsolution
dev_langs: C++
helpviewer_keywords:
- project files [C++]
- file types [C++], makefiles
- .sdf, browsing database file
- Makefile projects
- browsing database file, .sdf
- file types [C++], project files
ms.assetid: 5823b954-36cf-42d3-8fd5-25bab3ef63d9
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 498f4404f0b3f6b291eca0e78315d2a010cbf846
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="project-and-solution-files"></a>Pliki projektu i rozwiązania
Następujące pliki są tworzone podczas tworzenia projektu w programie Visual Studio. Są one używane do zarządzania plików projektów w rozwiązaniu.  
  
|Nazwa pliku|Lokalizacja katalogu|Lokalizacja Eksploratora rozwiązań|Opis|  
|--------------|------------------------|--------------------------------|-----------------|  
|*Solname*.sln|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*|Nie są wyświetlane w Eksploratorze rozwiązań|*Rozwiązania* pliku. Organizuje ona wszystkie elementy projektu lub wielu projektów w jedno rozwiązanie.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*.suo|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*|Nie są wyświetlane w Eksploratorze rozwiązań|*Opcje rozwiązania* pliku. Tak, aby zawsze po otwarciu pliku lub projektu w rozwiązaniu, ma wygląd i zachowanie, które mają są przechowywane własne dostosowania dla rozwiązania.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*.vcxproj|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*|Nie są wyświetlane w Eksploratorze rozwiązań|*Projektu* pliku. Przechowuje informacje specyficzne dla każdego projektu. (W starszych wersjach, ten plik został o nazwie *nazwa_projektu.nazwa_modułu.nazwa_procedury*.vcproj lub *nazwa_projektu.nazwa_modułu.nazwa_procedury*.dsp.) Na przykład plik projektu Visual C++ zobacz [pliki projektu](../ide/project-files.md).|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*.vcxitems|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*|Nie są wyświetlane w Eksploratorze rozwiązań|*Projektu udostępnionego elementów* pliku. Ten projekt nie jest skompilowany.  Zamiast tego projektu mogą się odwoływać przez inny projekt C++, oraz jej pliki staną się częścią procesu kompilacji projektu odwołującego się. Może to służyć do udostępniać typowy kod projektów C++ i platform.|
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*sdf|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*|Nie są wyświetlane w Eksploratorze rozwiązań|*Baza danych przeglądania* pliku. Obsługuje funkcje przeglądania i nawigacja takich jak **przejdź do definicji**, **Znajdź wszystkie odwołania**, i **widoku klasy**. Jest ona generowana przez analizowanie plików nagłówka.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury.* vcxproj.filters|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*|Nie są wyświetlane w Eksploratorze rozwiązań|*Filtry* pliku. Określa gdzie umieścić plik, który zostanie dodany do rozwiązania. Na przykład plik .h jest umieszczany **pliki nagłówkowe** węzła.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury.* vcxproj.user|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*|Nie są wyświetlane w Eksploratorze rozwiązań|*Użytkownika migracji* pliku. Po przeprowadzeniu migracji z programu Visual Studio 2008 projektu, ten plik zawiera informacje, które zostało skonwertowane z dowolnego pliku .vsprops —.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*.idl|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*|Źródło|(Specyficzne dla projektu) Zawiera kod źródłowy języka opisu interfejsu (IDL) dla biblioteki typu formantu. Ten plik jest używany przez Visual C++ można wygenerować biblioteki typów. Biblioteka wygenerowanego uwidacznia interfejs formantu dla innych klientów automatyzacji. Aby uzyskać więcej informacji, zobacz [plik definicji interfejsu (IDL)](http://msdn.microsoft.com/library/windows/desktop/aa378712) w zestawie Windows SDK.|  
|Readme.txt|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*|Project|*Readme* pliku. Wygenerowane przez Kreatora aplikacji, a opisuje pliki w projekcie.|  
  
## <a name="see-also"></a>Zobacz też  
 [Typy plików utworzonych dla projektów Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)