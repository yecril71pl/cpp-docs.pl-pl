---
title: Używanie środowiska IDE programu Visual Studio do tworzenia aplikacji pulpitu języka C++ | Dokumentacja firmy Microsoft
ms.date: 06/08/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDE [C++]
- Visual Studio IDE [C++]
ms.assetid: d985c230-8e81-49d6-92be-2db9cac8d023
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4aa276c0e9d97cd5b723499a21432290772a49a7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390308"
---
# <a name="using-the-visual-studio-ide-for-c-desktop-development"></a>Projektowania aplikacji w języku C++ w środowisku Visual Studio IDE

Zintegrowanego rozwoju środowiska (IDE) Visual Studio oferuje zestaw funkcji, które ułatwiają zarządzanie dużą i projektów mały kod, zapisu i Refaktoryzuj swój kod i wykrywaj i poprawiaj błędy przy użyciu zarówno analizy statycznej, jak i zaawansowane narzędzia do debugowania. Ten zestaw artykułów zaprojektowano przeprowadzi Cię przez kolejne kroki, które będą potrzebne do zarządzania projektami, napisać, przetestować, debugowanie kodu i wdrożyć ją na inny komputer.

## <a name="prerequisites"></a>Wymagania wstępne

Jeśli jeszcze nie zainstalowano programu Visual Studio, nadszedł czas. Łącza pobierania oraz szybkiego przewodnika, zobacz [Instalowanie obsługi języka C++ w programie Visual Studio](../build/vscpp-step-0-installation.md). Aby uzyskać więcej informacji o sposobie instalowania programu Visual Studio, ogólnie rzecz biorąc, a wskazówki dotyczące rozwiązywania problemów, jeśli coś pójdzie nie tak, zobacz [Zainstaluj program Visual Studio](/visualstudio/install/install-visual-studio). Pamiętaj wybrać **programowanie aplikacji klasycznych w języku C++** obciążenia, aby uwzględnić, kompilatory języków C++, narzędzi i bibliotek po zainstalowaniu programu Visual Studio, ponieważ nie są zainstalowane domyślnie.

Te przewodniki założono zainstalowanego programu Visual Studio i języka Visual C++ i składniki wymagane do tworzenia aplikacji pulpitu Windows. Przyjęto również założenie, że rozumiesz podstawy języka C++. Jeśli potrzebujesz dowiedzieć się, C++, Brak dostępnych wiele książek i zasobów sieci web. Jeden dobrym miejscem do rozpoczęcia jest [wprowadzenie](https://isocpp.org/get-started) strony witryny sieci Web, Standard C++ Foundation.

Jeśli jeszcze nie zainstalowano programu Visual Studio, nadszedł czas.

**Instalacja programu Visual Studio 2017**

Aby uzyskać program Visual Studio 2017, możesz ją pobrać z [pobieranie Visual Studio](http://www.visualstudio.com/downloads/download-visual-studio-vs.aspx). Pamiętaj obejmują narzędzia deweloperskie programu Visual C++, po zainstalowaniu programu Visual Studio, ponieważ nie są zainstalowane domyślnie. Aby uzyskać więcej informacji o sposobie instalowania programu Visual Studio, zobacz [Zainstaluj program Visual Studio](/visualstudio/install/install-visual-studio).

**Instalacja programu Visual Studio 2015**

Aby zainstalować program Visual Studio 2015, przejdź do [pobieranie starszych wersji programu Visual Studio](https://www.visualstudio.com/vs/older-downloads/). Uruchom program instalacyjny, a następnie wybierz **Instalacja niestandardowa** , a następnie wybierz składnik C++.

Ogólnie rzecz biorąc zdecydowanie zaleca się użycie programu Visual Studio 2017, nawet wtedy, gdy należy przeprowadzić kompilowanie kodu przy użyciu kompilatora Visual Studio 2015. Aby uzyskać więcej informacji, zobacz [Użyj natywnej wielowersyjności kodu w programie Visual Studio do kompilacji starych projektów](../porting/use-native-multi-targeting.md).

Po zakończeniu instalacji programu Visual Studio, jesteś gotowy kontynuować.

## <a name="get-started"></a>Wprowadzenie

Aby rozpocząć pracę, przy użyciu programu Visual Studio IDE do tworzenia aplikacji w języku C++, pracować za pośrednictwem każdej z tych tematów w kolejności. Każdy z nich jest oparta na pracy, który ukończone w poprzednich tematach:

- [Przewodnik: praca z projektami i rozwiązaniami (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)

- [Przewodnik: tworzenie projektu (C++)](../ide/walkthrough-building-a-project-cpp.md)

- [Przewodnik: testowanie projektu (C++)](../ide/walkthrough-testing-a-project-cpp.md)

- [Przewodnik: debugowanie projektu (C++)](../ide/walkthrough-debugging-a-project-cpp.md)

- [Przewodnik: wdrażanie Twojego programu (C++)](../ide/walkthrough-deploying-your-program-cpp.md)

## <a name="next-steps"></a>Następne kroki

Po wykonaniu tych przewodników, możesz rozpocząć tworzenie własnych projektów. Aby uzyskać więcej informacji i zasoby projektowe Visual C++, zobacz [Visual C++ w programie Visual Studio](../visual-cpp-in-visual-studio.md).

## <a name="see-also"></a>Zobacz także

[Rozpocznij tworzenie aplikacji za pomocą programu Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio)