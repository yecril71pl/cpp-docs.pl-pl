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
ms.openlocfilehash: d816d932ce518e006e5537075fe4ac7782362ad4
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206987"
---
# <a name="redistributing-components-by-using-merge-modules"></a>Redystrybucja składników za pomocą modułów scalania
Program Visual Studio obejmuje [modułów scalania,](/windows/desktop/Msi/about-merge-modules) dla każdego składnika Visual C++, którego licencja pozwala na redystrybucję z aplikacją. Gdy moduł scalania jest wkompilowany w plik instalacyjny Instalatora Windows, umożliwia on wdrażanie określonych bibliotek DLL na komputerach, które mają określoną platformę. W pliku konfiguracji należy określić, że moduły scalania stanowią wymagania wstępne dotyczące aplikacji. Po zainstalowaniu programu Visual Studio, moduły scalania są zainstalowane w \Program Files\Common Files\Merge Modules\\. (Może być rozpowszechniany wyłącznie bez debugowania wersje bibliotek DLL Visual C++.) Aby uzyskać więcej informacji i łącze do listy modułów scalania, których licencja pozwala na redystrybucję, zobacz [Redistributing Visual C++ Files](../ide/redistributing-visual-cpp-files.md).  
  
 Można użyć modułów scalania, aby umożliwić instalację redystrybucyjnych bibliotek DLL Visual C++ do folderu %SYSTEMROOT%\system32\. (Visual Studio używa tej techniki.) Jednakże instalacja w tym folderze się nie uda, chyba że użytkownik ma prawa administratora.  
  
 Nie zalecamy korzystania z modułów scalania z wyjątkiem przypadków, kiedy nie musisz świadczyć serwisu aplikacji i nie zależy ona od więcej niż jednej wersji biblioteki DLL. Modułów scalania dla różnych wersji tej samej biblioteki DLL nie można włączyć do jednego instalatora, moduły scalania utrudniają serwisowanie bibliotek DLL niezależnie od aplikacji. Zamiast tego zaleca się, że możesz zainstalować pakiet redystrybucyjny Visual C++.  
  
## <a name="see-also"></a>Zobacz też  
 [Ponowne dystrybuowanie plików programu Visual C++](../ide/redistributing-visual-cpp-files.md)