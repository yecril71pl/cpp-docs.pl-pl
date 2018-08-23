---
title: Przenoszenie bibliotek innych firm | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/10/2017
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- 3rd-party libraries
- vspkg
ms.assetid: b055ed20-8a9e-45b2-ac2a-e3d94271c009
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3e1edc9e4a6172b3ac55e7a8bc9b21cdc571774d
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2018
ms.locfileid: "42465883"
---
# <a name="porting-third-party-libraries"></a>Przenoszenie bibliotek innych firm

Po uaktualnieniu projektu do bieżącej wersji programu Visual C++, należy uaktualnić wszystkie biblioteki, które używa projekt, tak, aby biblioteki, a projekt są tworzone za pomocą tę samą wersję i wersja kompilatora. (Aby uzyskać więcej informacji, zobacz [omówienie potencjalnych problemów z uaktualnieniem](overview-of-potential-upgrade-issues-visual-cpp.md)). 

## <a name="introducing-vcpkg"></a>Wprowadzenie do vcpkg

W przeszłości Znajdowanie i uaktualnianie 3rd bibliotek innych firm był czasami nietrywialnymi zadania. Aby ułatwić uzyskiwanie i Odbuduj C++ 3rd bibliotek typu open source innych firm, zespołu Visual C++ został utworzony z wiersza polecenia narzędzia o nazwie **narzędzia pakowania VC ++** lub **vcpkg**. Vcpkg ma przeszukiwanie wykazu wielu popularnych bibliotek typu open-source języka C++. Można zainstalować wszystkie biblioteki w wykazie bezpośrednio z poziomu wiersza polecenia vcpkg. Podczas instalowania biblioteki Vcpkg tworzy drzewo katalogów na komputerze i dodaje .h, lib i plikach binarnych, w tym folderze. Możesz użyć tego folderu w wierszu polecenia kompilacji, lub zintegrować ją z programu Visual Studio 2015 lub później za pomocą vcpkg integracja polecenia install. Po zintegrowaniu lokalizację biblioteki programu Visual Studio można je znaleźć i dodać go do nowego projektu, które tworzysz. Aby użyć biblioteki, po prostu `#include` i programu Visual Studio będzie automatycznie dodać ścieżkę .lib do ustawień projektu i skopiuj bibliotekę dll do folderu rozwiązania. Aby uzyskać więcej informacji, zobacz [vcpkg: Menedżer pakietów dla języka C++](../vcpkg.md).

## <a name="reporting-issues"></a>Raportowanie problemów

Jeśli biblioteka nie jest obecny w **vcpkg** katalogu, można otworzyć zgłoszenie na [repozytorium GitHub](https://github.com/Microsoft/vcpkg/issues) gdzie społeczności i zespołu Visual C++ może go wyświetlać i potencjalnie tworzenia pliku port dla tej biblioteki.

Aby uzyskać zastrzeżonej 3rd bibliotek innych firm (inne niż Otwórz źródło) firma Microsoft zaleca, skontaktuj się z dostawcą biblioteki. Jednak Dbamy o dowolnym własności libs jest używany i nie można zablokować, Daj nam znać, który z nich, na których polegasz (skontaktuj się z nami pod adresem vcupgrade@microsoft.com).
  
## <a name="see-also"></a>Zobacz też  

[Przewodnik po przenoszeniu i uaktualnianiu pakietu Visual C++](visual-cpp-porting-and-upgrading-guide.md)