---
title: Projektowania aplikacji w języku C++ w środowisku Visual Studio IDE
ms.date: 04/25/2019
helpviewer_keywords:
- IDE [C++]
- Visual Studio IDE [C++]
ms.assetid: d985c230-8e81-49d6-92be-2db9cac8d023
ms.openlocfilehash: 2cf2844fd4247c3c69648823302a6ad56ff5fd45
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171779"
---
# <a name="using-the-visual-studio-ide-for-c-desktop-development"></a>Projektowania aplikacji w języku C++ w środowisku Visual Studio IDE

Zintegrowane środowisko programistyczne (IDE) programu Visual Studio oferuje zestaw funkcji, które ułatwiają zarządzanie dużymi i małymi projektami kodu, pisaniem i refaktoryzacją kodu oraz wykrywanie i poprawianie błędów przy użyciu zarówno analizy statycznej, jak i zaawansowanych narzędzi do debugowania. Ten zestaw artykułów został zaprojektowany, aby przeprowadzić Cię przez każdy krok, aby zarządzać projektami, pisać, testować i debugować kod, a następnie wdrożyć go na innym komputerze.

## <a name="prerequisites"></a>Wymagania wstępne

Jeśli jeszcze nie zainstalowano programu Visual Studio, teraz jest to czas. Aby uzyskać łącza do plików do pobrania i krótki przewodnik, zobacz [Install C++ Support in Visual Studio](../build/vscpp-step-0-installation.md). Aby uzyskać więcej informacji o tym, jak zainstalować program Visual Studio w ogólności i porady dotyczące rozwiązywania problemów, jeśli coś się nie udaje, zobacz [Install Visual Studio](/visualstudio/install/install-visual-studio). Upewnij się, że wybrano opcję **programowanie C++ aplikacji klasycznych** , C++ aby uwzględnić kompilatory, narzędzia i biblioteki podczas instalowania programu Visual Studio, ponieważ nie są instalowane domyślnie.

W tych przewodnikach przyjęto założenie, że zainstalowano program Visual Studio i C++ składniki wymagane do tworzenia aplikacji klasycznych systemu Windows. Załóżmy również, że rozumiesz podstawy C++ języka. Jeśli potrzebujesz informacji C++, masz dostęp do wielu książek i zasobów sieci Web. Jednym z miejsc do rozpoczęcia [jest strona wprowadzenie w witrynie](https://isocpp.org/get-started) sieci Web w C++ warstwie Standardowa.

Jeśli jeszcze nie zainstalowano programu Visual Studio, teraz jest to czas. Ogólnie rzecz biorąc, zdecydowanie zalecamy użycie programu Visual Studio 2019, nawet jeśli trzeba skompilować kod przy użyciu kompilatora Visual Studio 2017 lub Visual Studio 2015. Aby uzyskać więcej informacji, zobacz [Używanie natywnego wielu elementów docelowych w programie Visual Studio do kompilowania starych projektów](../porting/use-native-multi-targeting.md).

**Instalacja programu Visual Studio 2019**

Aby uzyskać program Visual Studio 2019, możesz pobrać go z programu [Visual Studio downloads](https://www.visualstudio.com/downloads/). Należy pamiętać o dodaniu C++ narzędzi programistycznych podczas instalowania programu Visual Studio, ponieważ nie są one instalowane domyślnie. Aby uzyskać więcej informacji na temat sposobu instalowania programu Visual Studio, zobacz [Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio).

**Instalacja programu Visual Studio 2017**

Aby uzyskać program Visual Studio 2017, możesz pobrać go ze [starszej wersji programu Visual Studio](https://www.visualstudio.com/vs/older-downloads/). Należy pamiętać o dodaniu C++ narzędzi programistycznych podczas instalowania programu Visual Studio, ponieważ nie są one instalowane domyślnie. Aby uzyskać więcej informacji na temat sposobu instalowania programu Visual Studio, zobacz [Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio) i Ustawianie selektora wersji na stronie do **programu Visual Studio 2017**.

**Instalacja programu Visual Studio 2015**

Aby zainstalować program Visual Studio 2015, przejdź do [pozycji Pobierz starsze wersje programu Visual Studio](https://www.visualstudio.com/vs/older-downloads/). Uruchom program instalacyjny i wybierz pozycję **Instalacja niestandardowa** , a C++ następnie wybierz składnik.

Po zakończeniu instalacji programu Visual Studio możesz kontynuować pracę.

## <a name="get-started"></a>Wprowadzenie

Aby rozpocząć korzystanie z programu Visual Studio IDE do kompilowania C++ aplikacji, należy wykonać czynności opisane w poszczególnych tematach w kolejności. Każdy z nich kompiluje się w pracy wykonanej w poprzednich tematach:

- [Przewodnik: praca z projektami i rozwiązaniami (C++)](walkthrough-working-with-projects-and-solutions-cpp.md)

- [Przewodnik: tworzenie projektu (C++)](walkthrough-building-a-project-cpp.md)

- [Przewodnik: testowanie projektu (C++)](walkthrough-testing-a-project-cpp.md)

- [Przewodnik: debugowanie projektu (C++)](walkthrough-debugging-a-project-cpp.md)

- [Przewodnik: wdrażanie Twojego programu (C++)](walkthrough-deploying-your-program-cpp.md)

## <a name="next-steps"></a>Następne kroki

Po zakończeniu tych instruktaży możesz zacząć tworzyć własne projekty. Aby uzyskać więcej informacji i zasobów C++ na potrzeby programowania, zobacz [Visual C++ Studio](../overview/visual-cpp-in-visual-studio.md).

## <a name="see-also"></a>Zobacz też

[Wprowadzenie do programowania w programie Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio)
