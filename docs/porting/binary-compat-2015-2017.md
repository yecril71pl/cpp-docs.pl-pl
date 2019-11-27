---
title: C++ — zgodność binarna 2015–2019
description: Opisuje sposób, w jaki zgodność binarna działa między skompilowanymi C++ plikami w programie Visual Studio 2015, 2017 i 2019. Jeden pakiet redystrybucyjny Microsoft Visual C++ działa dla wszystkich trzech wersji.
ms.date: 11/18/2019
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
ms.openlocfilehash: b729cdcc4a494e60ec58314fe23b02c1816e8412
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188787"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-2017-and-2019"></a>C++zgodność binarna między programami Visual Studio 2015, 2017 i 2019

Zestawy narzędzi C++ kompilatorów firmy Microsoft (MSVC) w Visual Studio 2013 i starszych nie gwarantują zgodności binarnej w różnych wersjach. Nie można połączyć plików obiektów, bibliotek statycznych, bibliotek dynamicznych i plików wykonywalnych utworzonych przez różne wersje. Interfejsy ABI, formaty obiektów i biblioteki środowiska uruchomieniowego są niezgodne.

To zachowanie zostało zmienione w programie Visual Studio 2015, 2017 i 2019. Biblioteki i aplikacje środowiska uruchomieniowego skompilowane przez dowolną z tych wersji kompilatora są zgodne ze standardami binarnymi. Jest on widoczny w numerze głównym zestawu C++ narzędzi, który jest 14 dla wszystkich trzech wersji. (Wersja zestawu narzędzi to wersji 140 dla programu Visual Studio 2015, najnowsze 141 dla 2017 i v142 for 2019). Załóżmy, że masz biblioteki innych firm utworzone przez program Visual Studio 2015. Nadal można z nich korzystać w aplikacji utworzonej przez program Visual Studio 2017 lub 2019. Nie ma potrzeby ponownej kompilacji przy użyciu zgodnego zestawu narzędzi. Najnowsza wersja pakietu redystrybucyjnego Microsoft C++ Visual (redystrybucyjna) działa dla wszystkich z nich.

Istnieją trzy ważne ograniczenia dotyczące zgodności binarnej:

- Można mieszać pliki binarne utworzone przez różne wersje zestawu narzędzi. Należy jednak użyć zestawu narzędzi co najmniej jako najnowszego pliku binarnego, aby połączyć aplikację. Oto przykład: można połączyć aplikację skompilowaną przy użyciu zestawu narzędzi 2017 do biblioteki statycznej skompilowanej przy użyciu 2019, jeśli są one połączone przy użyciu zestawu narzędzi 2019.

- Pakiet redystrybucyjny używany przez aplikację ma podobne ograniczenia zgodności binarnej. Podczas mieszania plików binarnych utworzonych przez różne obsługiwane wersje zestawu narzędzi, wersja redystrybucyjna musi być co najmniej równa nowemu zestawowi narzędzi używanym przez dowolny składnik aplikacji.

- Biblioteki statyczne lub pliki obiektów skompilowane przy użyciu przełącznika kompilatora [/GL (Optymalizacja całego programu)](../build/reference/gl-whole-program-optimization.md) *nie są* zgodne ze standardami binarnymi w różnych wersjach. Wszystkie pliki obiektów i biblioteki skompilowane przy użyciu `/GL` muszą używać dokładnie tego samego zestawu narzędzi do kompilowania i finalnego linku.

## <a name="upgrade-the-microsoft-visual-c-redistributable-from-visual-studio-2015-or-2017-to-visual-studio-2019"></a>Uaktualnij pakiet redystrybucyjny Microsoft Visual C++ w programie visual Studio 2015 lub 2017 do programu visual Studio 2019

W przypadku programu Visual Studio 2015 C++ , 2017 i 2019 został pokazany główny numer wersji pakietu redystrybucyjnego Microsoft Visual Oznacza to, że w danym momencie można zainstalować tylko jedno wystąpienie pakietu redystrybucyjnego. Nowsza wersja zastępuje wszystkie starsze wersje, które są już zainstalowane. Na przykład jedna aplikacja może zainstalować pakiet redystrybucyjny z programu Visual Studio 2015. Następnie inna aplikacja instaluje pakiet redystrybucyjny z poziomu programu Visual Studio 2019. Wersja 2019 zastępuje starszą wersję, ale ponieważ są zgodne ze standardem Binary, Starsza aplikacja nadal działa prawidłowo. Upewnij się, że Najnowsza wersja pakietu redystrybucyjnego zawiera wszystkie najnowsze funkcje, aktualizacje zabezpieczeń i poprawki błędów. Dlatego zawsze zalecamy przeprowadzenie uaktualnienia do najnowszej dostępnej wersji.

Podobnie nie można zainstalować starszego pakietu redystrybucyjnego, gdy nowsza wersja jest już zainstalowana. Instalator zgłasza błąd w przypadku próby. Jeśli zainstalujesz pakiet redystrybucyjny 2015 lub 2017 na komputerze, który ma już wersję 2019, zobaczysz błąd podobny do tego:

```Output
0x80070666 - Another version of this product is already installed. Installation of this version cannot continue. To configure or remove the existing version of this product, use Add/Remove Programs on the Control Panel.
```

Ten błąd jest zaprojektowany. Zalecamy zachowanie najnowszej zainstalowanej wersji. Upewnij się, że Instalator może odzyskać z tego błędu w trybie dyskretnym.

## <a name="see-also"></a>Zobacz także

[Historia C++ zmian wizualnych](../porting/visual-cpp-change-history-2003-2015.md)\
[Najnowsze obsługiwane pliki redystrybucyjne wizualizacji C++](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads)
