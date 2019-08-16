---
title: Redystrybucja składników za pomocą modułów scalania
ms.date: 11/04/2016
helpviewer_keywords:
- merge modules, using
- redistributing applications, using merge modules
ms.assetid: 93b84211-bf9b-4a78-9f22-474ac2ef7840
ms.openlocfilehash: 36dc115987b051f117264991927c2599a88deda6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514776"
---
# <a name="redistributing-components-by-using-merge-modules"></a>Redystrybucja składników za pomocą modułów scalania

Program Visual Studio zawiera [moduły scalania](/windows/win32/Msi/about-merge-modules) dla każdego C++ składnika wizualnego, który jest licencjonowany do dystrybucji za pomocą aplikacji. Gdy moduł scalania jest wkompilowany w plik instalacyjny Instalatora Windows, umożliwia on wdrażanie określonych bibliotek DLL na komputerach, które mają określoną platformę. W pliku konfiguracji należy określić, że moduły scalania stanowią wymagania wstępne dotyczące aplikacji. Po zainstalowaniu programu Visual Studio moduły scalania są instalowane w \Program Files\Common Files\Merge modules\\. (Mogą być rozpowszechniane tylko wersje Visual C++ dll, które nie są debugowania). Aby uzyskać więcej informacji i link do listy modułów scalania, które są licencjonowane do redystrybucji, zobacz [redystrybuuj pliki C++ wizualne](redistributing-visual-cpp-files.md).

Za pomocą modułów scalania można włączyć instalację C++ bibliotek DLL redystrybucyjnych w folderze%SYSTEMROOT%\system32\. (W programie Visual Studio jest stosowana ta technika). Jednakże instalacja w tym folderze się nie uda, chyba że użytkownik ma prawa administratora.

Nie zalecamy korzystania z modułów scalania z wyjątkiem przypadków, kiedy nie musisz świadczyć serwisu aplikacji i nie zależy ona od więcej niż jednej wersji biblioteki DLL. Modułów scalania dla różnych wersji tej samej biblioteki DLL nie można włączyć do jednego instalatora, moduły scalania utrudniają serwisowanie bibliotek DLL niezależnie od aplikacji. Zamiast tego zaleca się zainstalowanie pakietu redystrybucyjnego C++ Visual.

## <a name="see-also"></a>Zobacz także

[Ponowne dystrybuowanie plików programu Visual C++](redistributing-visual-cpp-files.md)
