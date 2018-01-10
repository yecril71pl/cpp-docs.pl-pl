---
title: "Redystrybucja składników za pomocą modułów scalania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- merge modules, using
- redistributing applications, using merge modules
ms.assetid: 93b84211-bf9b-4a78-9f22-474ac2ef7840
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 093c732563844b14a3f99662150d4db9b2fac1fb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="redistributing-components-by-using-merge-modules"></a>Redystrybucja składników za pomocą modułów scalania
Visual Studio zawiera [scalania modułów](http://msdn.microsoft.com/library/aa367434) dla każdego składnika Visual C++, która jest licencjonowana do można rozpowszechniać za pomocą aplikacji. Gdy moduł scalania jest wkompilowany w plik instalacyjny Instalatora Windows, umożliwia on wdrażanie określonych bibliotek DLL na komputerach, które mają określoną platformę. W pliku konfiguracji należy określić, że moduły scalania stanowią wymagania wstępne dotyczące aplikacji. Po zainstalowaniu programu Visual Studio modułów scalania są zainstalowane w \Program Files\Common modułów Files\Merge\\. (Można rozpowszechniać tylko bez debugowania wersje programu Visual C++ bibliotek DLL). Więcej informacji oraz link do listy modułów scalania, które są licencjonowane dla redystrybucji, zobacz [redystrybuowanie pliki Visual C++](../ide/redistributing-visual-cpp-files.md).  
  
 W przeciwnym razie instalacja pakietu redystrybucyjnego dll programu Visual C++ do folderu %SYSTEMROOT%\system32\, można użyć modułów scalania. (Visual Studio sam korzysta z tej techniki). Jednakże instalacja w tym folderze się nie uda, chyba że użytkownik ma prawa administratora.  
  
 Nie zalecamy korzystania z modułów scalania z wyjątkiem przypadków, kiedy nie musisz świadczyć serwisu aplikacji i nie zależy ona od więcej niż jednej wersji biblioteki DLL. Modułów scalania dla różnych wersji tej samej biblioteki DLL nie można włączyć do jednego instalatora, moduły scalania utrudniają serwisowanie bibliotek DLL niezależnie od aplikacji. Zamiast tego zaleca się, że zainstaluj pakiet redystrybucyjny Visual C++.  
  
## <a name="see-also"></a>Zobacz też  
 [Ponowne dystrybuowanie plików programu Visual C++](../ide/redistributing-visual-cpp-files.md)