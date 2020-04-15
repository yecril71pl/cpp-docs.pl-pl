---
title: Projektowania aplikacji w języku C++ w środowisku Visual Studio IDE
ms.date: 04/25/2019
helpviewer_keywords:
- IDE [C++]
- Visual Studio IDE [C++]
ms.assetid: d985c230-8e81-49d6-92be-2db9cac8d023
ms.openlocfilehash: 082aa353d3046d9c9b20669e075e200c96017bce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371764"
---
# <a name="using-the-visual-studio-ide-for-c-desktop-development"></a>Projektowania aplikacji w języku C++ w środowisku Visual Studio IDE

Visual Studio Zintegrowane środowisko programistyczne (IDE) oferuje zestaw funkcji, które ułatwiają zarządzanie dużych i małych projektów kodu, zapisu i refaktoryzacji kodu i wykrywania i poprawiania błędów przy użyciu analizy statycznej i zaawansowanych narzędzi debugowania. Ten zestaw artykułów jest przeznaczony do przechodzenia przez każdy krok, który będzie potrzebny do zarządzania projektami, pisania, testowania i debugowania kodu, a następnie wdrożyć go na innym komputerze.

## <a name="prerequisites"></a>Wymagania wstępne

Jeśli program Visual Studio nie został jeszcze zainstalowany, teraz jest czas. Aby uzyskać łącza do pobierania i szybki przewodnik, zobacz [Instalowanie pomocy technicznej języka C++ w programie Visual Studio](../build/vscpp-step-0-installation.md). Aby uzyskać więcej informacji na temat instalowania programu Visual Studio w ogóle i porad dotyczących rozwiązywania problemów, jeśli coś pójdzie nie tak, zobacz [Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio). Pamiętaj, aby wybrać **programowanie pulpitu z c++** obciążenia, aby uwzględnić kompilatory C++, narzędzia i biblioteki podczas instalowania programu Visual Studio, ponieważ nie są one instalowane domyślnie.

W tych instruktażach przyjęto założenie, że zainstalowano program Visual Studio i składniki Języka C++ wymagane dla tworzenia pulpitu systemu Windows. Zakładamy również, że rozumiesz podstawy języka C++. Jeśli chcesz nauczyć się języka C++, dostępnych jest wiele książek i zasobów internetowych. Dobrym miejscem do rozpoczęcia jest strona [Wprowadzenie](https://isocpp.org/get-started) na stronie Internetowej Fundacji Standard C++.

Jeśli program Visual Studio nie został jeszcze zainstalowany, teraz jest czas. Ogólnie rzecz biorąc zdecydowanie zaleca się, aby używać programu Visual Studio 2019, nawet jeśli trzeba skompilować kod przy użyciu visual studio 2017 lub Visual Studio 2015 kompilatora. Aby uzyskać więcej informacji, zobacz [Używanie natywnego kierowania wielokrotnego w programie Visual Studio do tworzenia starych projektów.](../porting/use-native-multi-targeting.md)

**Instalacja programu Visual Studio 2019**

Aby pobrać program Visual Studio 2019, można go pobrać z [programu Visual Studio Downloads](https://www.visualstudio.com/downloads/). Pamiętaj, aby dołączyć narzędzia programistyczne języka C++ podczas instalowania programu Visual Studio, ponieważ nie są one instalowane domyślnie. Aby uzyskać więcej informacji dotyczących instalowania programu Visual Studio, zobacz [Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio).

**Instalacja programu Visual Studio 2017**

Aby pobrać program Visual Studio 2017, można go pobrać ze [starszych wersji programu Visual Studio](https://www.visualstudio.com/vs/older-downloads/). Pamiętaj, aby dołączyć narzędzia programistyczne języka C++ podczas instalowania programu Visual Studio, ponieważ nie są one instalowane domyślnie. Aby uzyskać więcej informacji dotyczących instalowania programu Visual Studio, zobacz [Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio). Aby wyświetlić instrukcje dotyczące programu Visual Studio 2017, ustaw kontrolka **selektora wersji** programu Visual Studio na Visual Studio 2017. Znajduje się w górnej części spisu treści na stronie.

**Instalacja programu Visual Studio 2015**

Aby zainstalować program Visual Studio 2015, przejdź do [pobierz starsze wersje programu Visual Studio](https://www.visualstudio.com/vs/older-downloads/). Uruchom program instalacyjny i wybierz pozycję **Instalacja niestandardowa,** a następnie wybierz składnik C++.

Po zakończeniu instalacji programu Visual Studio można przystąpić do kontynuowania.

## <a name="get-started"></a>Wprowadzenie

Aby rozpocząć korzystanie z ide programu Visual Studio do tworzenia aplikacji języka C++, przejdź przez każdy z tych tematów w kolejności. Każdy z nich opiera się na pracy wykonanej w poprzednich tematach:

- [Przewodnik: praca z projektami i rozwiązaniami (C++)](walkthrough-working-with-projects-and-solutions-cpp.md)

- [Przewodnik: tworzenie projektu (C++)](walkthrough-building-a-project-cpp.md)

- [Przewodnik: testowanie projektu (C++)](walkthrough-testing-a-project-cpp.md)

- [Przewodnik: debugowanie projektu (C++)](walkthrough-debugging-a-project-cpp.md)

- [Przewodnik: wdrażanie Twojego programu (C++)](walkthrough-deploying-your-program-cpp.md)

## <a name="next-steps"></a>Następne kroki

Po zakończeniu tych instruktajni, jesteś gotowy, aby rozpocząć tworzenie własnych projektów. Aby uzyskać więcej informacji i zasobów dotyczących programowania języka C++, zobacz [Visual C++ w programie Visual Studio](../overview/visual-cpp-in-visual-studio.md).

## <a name="see-also"></a>Zobacz też

[Rozpoczęcie tworzenia programu Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio)
