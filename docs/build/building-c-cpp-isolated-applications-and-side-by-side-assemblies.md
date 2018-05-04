---
title: Tworzenie C/C++ izolowany aplikacji i zestawy Side-by-side | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- isolated applications [C++]
- WinSxS [C++]
- native assembly cache [C++]
- builds [C++], isolated applications
- side-by-side applications [C++]
- builds [C++], side-by-side assemblies
ms.assetid: 9465904e-76f7-48bd-bb3f-c55d8f1699b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ca99de7403ad56ae82fdd25af8ff22167084b91
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="building-cc-isolated-applications-and-side-by-side-assemblies"></a>Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie
Visual C++ obsługuje model wdrożenia dla aplikacji klienckich systemu Windows oparte na koncepcja [izolowanych](http://msdn.microsoft.com/library/aa375190) i [zestawy side-by-side](http://msdn.microsoft.com/library/ff951640). Domyślnie program Visual C++ kompilacje wszystkich natywnych aplikacji C/C++ jako izolowanych aplikacji, które używają [manifesty](http://msdn.microsoft.com/library/aa375365) do opisywania ich zależności na bibliotek języka Visual C++.  
  
 Kompilowanie programów C/C++ jako izolowanych aplikacji zawiera szereg korzyści. Na przykład izolowanych aplikacji nie mają wpływu, gdy inne aplikacje C/C++ zainstalować lub odinstalować bibliotek języka Visual C++. Bibliotek języka Visual C++ używane przez aplikacje izolowane nadal można rozpowszechniać w folderze lokalnym w aplikacji lub przez instalację pamięć podręczna zestawów natywnych (folderze WinSxS); jednak obsługa bibliotek języka Visual C++ dla już wdrożonych aplikacji można uprościć przy użyciu [wydawcy pliku konfiguracji](http://msdn.microsoft.com/library/aa375680). Model wdrażania aplikacji izolowanych ułatwia upewnij się, że aplikacji C/C++, które są uruchomione na określonym komputerze używać najnowszej wersji biblioteki Visual C++, pozostawiając nadal otwarty możliwości dla administratorów systemów i Aplikacja autorom powiązanie jawne wersji aplikacji do ich zależnych bibliotek DLL.  
  
 W tej sekcji omówiono sposób tworzenia aplikacji jako aplikacji izolowanych C/C++ i upewnij się, że jest on powiązany z bibliotek języka Visual C++ przy użyciu manifestu. Informacje przedstawione w tej sekcji dotyczą przede wszystkim native lub niezarządzane, aplikacji Visual C++. Aby uzyskać informacje o wdrażaniu natywnych aplikacji skompilowanej za pomocą języka Visual C++, zobacz [redystrybuowanie pliki Visual C++](../ide/redistributing-visual-cpp-files.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Pojęcia związane z aplikacjami izolowanymi oraz aplikacjami wykonywanymi równocześnie](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)  
  
 [Kompilowanie izolowanych aplikacji C/C++](../build/building-c-cpp-isolated-applications.md)  
  
 [Kompilowanie wykonywanych jednocześnie aplikacji C/C++](../build/building-c-cpp-side-by-side-assemblies.md)  
  
 [Instrukcje: kompilowanie komponentów COM bez rejestrowania](../build/how-to-build-registration-free-com-components.md)  
  
 [Instrukcje: kompilowanie izolowanych aplikacji korzystających ze składników COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)  
  
 [Ogólne informacje o tworzeniu manifestu dla programów C/C++](../build/understanding-manifest-generation-for-c-cpp-programs.md)  
  
 [Rozwiązywanie problemów związanych z aplikacjami izolowanymi C/C++ oraz aplikacjami wykonywanymi równocześnie](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Aplikacje izolowane i Side-by-side zestawów](http://msdn.microsoft.com/library/dd408052)  
  
 [Wdrażanie natywnych aplikacji komputerowych](../ide/deploying-native-desktop-applications-visual-cpp.md)