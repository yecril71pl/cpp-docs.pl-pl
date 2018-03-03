---
title: Eksportowanie bibliotek innych firm | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/10/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- 3rd-party libraries
- vspkg
ms.assetid: b055ed20-8a9e-45b2-ac2a-e3d94271c009
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2d712765ea8b7251b07a1cb407cd6bf1f64372da
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="porting-third-party-libraries"></a>Eksportowanie bibliotek innych firm

Po uaktualnieniu projektu do bieżącej wersji programu Visual C++, należy uaktualnić żadnych bibliotek, które korzysta z projektu, tak aby biblioteki i projektu są tworzone z tej samej wersji i wersji kompilatora. (Aby uzyskać więcej informacji, zobacz [omówienie potencjalne problemy z uaktualnieniem](overview-of-potential-upgrade-issues-visual-cpp.md)). 

## <a name="introducing-vcpkg"></a>Wprowadzenie do vcpkg
W przeszłości Znajdowanie i uaktualnianie 3 bibliotek strony było czasami nieuproszczony zadań. Aby ułatwić nabywanie i Odbuduj C++ 3 biblioteki typu open source firmy, zespołu Visual C++ utworzył narzędzie wiersza polecenia o nazwie **narzędzia pakowania VC ++** lub **vcpkg**. Vcpkg ma wyszukiwanie katalogu wielu popularnych bibliotek języka C++ open source. Wszystkie biblioteki można zainstalować w katalogu bezpośrednio z poziomu wiersza polecenia vcpkg. Po zainstalowaniu biblioteki Vcpkg tworzy drzewa katalogów na tym komputerze i dodaje .h, lib i plików binarnych w tym folderze. Możesz użyć tego folderu w wierszu polecenia kompilacji, lub zintegrować ją z programu Visual Studio 2015 lub później za pomocą vcpkg integracji polecenia install. Po zintegrowaniu lokalizację biblioteki programu Visual Studio można go znaleźć i dodać go do nowego projektu, który utworzono. Aby używać biblioteki, po prostu #include go i automatycznie dodać ścieżka lib w ustawieniach projektu i skopiuj bibliotekę dll do folderu rozwiązania Visual Studio. Aby uzyskać więcej informacji, zobacz [vcpkg: Menedżer pakietów dla języka C++](../vcpkg.md).


## <a name="reporting-issues"></a>Zgłaszanie problemów
Jeśli biblioteka nie jest obecny w katalogu vcpkg, można otworzyć problemu na [repozytorium GitHub](https://github.com/Microsoft/vcpkg/issues) gdzie społeczności i zespołu Visual C++ mogą go wyświetlać i potencjalnie Utwórz plik port dla tej biblioteki.

Dla zastrzeżonych 3 bibliotek firm (z systemem innym niż Otwórz źródła) firma Microsoft zaleca, skontaktuj się z dostawcą biblioteki. Jednak Dbamy zna wszystkie zastrzeżone biblioteki używany i nie można zablokować, Daj nam znać, które z nich zależą (skontaktuj się z nami pod adresem vcupgrade@microsoft.com).

  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik po przenoszeniu i uaktualnianiu pakietu Visual C++](visual-cpp-porting-and-upgrading-guide.md)
