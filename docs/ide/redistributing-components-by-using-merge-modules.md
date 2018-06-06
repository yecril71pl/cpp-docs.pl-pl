---
title: Redystrybucja składników za pomocą modułów scalania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- merge modules, using
- redistributing applications, using merge modules
ms.assetid: 93b84211-bf9b-4a78-9f22-474ac2ef7840
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d95b6d2a69b4b40c4464136dd33a8c5231185f5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33329117"
---
# <a name="redistributing-components-by-using-merge-modules"></a>Redystrybucja składników za pomocą modułów scalania
Visual Studio zawiera [scalania modułów](http://msdn.microsoft.com/library/aa367434) dla każdego składnika Visual C++, która jest licencjonowana do można rozpowszechniać za pomocą aplikacji. Gdy moduł scalania jest wkompilowany w plik instalacyjny Instalatora Windows, umożliwia on wdrażanie określonych bibliotek DLL na komputerach, które mają określoną platformę. W pliku konfiguracji należy określić, że moduły scalania stanowią wymagania wstępne dotyczące aplikacji. Po zainstalowaniu programu Visual Studio modułów scalania są zainstalowane w \Program Files\Common modułów Files\Merge\\. (Można rozpowszechniać tylko bez debugowania wersje programu Visual C++ bibliotek DLL). Więcej informacji oraz link do listy modułów scalania, które są licencjonowane dla redystrybucji, zobacz [redystrybuowanie pliki Visual C++](../ide/redistributing-visual-cpp-files.md).  
  
 W przeciwnym razie instalacja pakietu redystrybucyjnego dll programu Visual C++ do folderu %SYSTEMROOT%\system32\, można użyć modułów scalania. (Visual Studio sam korzysta z tej techniki). Jednakże instalacja w tym folderze się nie uda, chyba że użytkownik ma prawa administratora.  
  
 Nie zalecamy korzystania z modułów scalania z wyjątkiem przypadków, kiedy nie musisz świadczyć serwisu aplikacji i nie zależy ona od więcej niż jednej wersji biblioteki DLL. Modułów scalania dla różnych wersji tej samej biblioteki DLL nie można włączyć do jednego instalatora, moduły scalania utrudniają serwisowanie bibliotek DLL niezależnie od aplikacji. Zamiast tego zaleca się, że zainstaluj pakiet redystrybucyjny Visual C++.  
  
## <a name="see-also"></a>Zobacz też  
 [Ponowne dystrybuowanie plików programu Visual C++](../ide/redistributing-visual-cpp-files.md)