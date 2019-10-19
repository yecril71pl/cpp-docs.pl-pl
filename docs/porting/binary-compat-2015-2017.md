---
title: C++Zgodność binarna między programami Visual Studio 2015 i Visual Studio 2019
ms.date: 10/17/2019
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
ms.openlocfilehash: 6365ded349ad08a167b76ca9f6ab43e6e7752987
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72587902"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2019"></a>C++Zgodność binarna między programami Visual Studio 2015 i Visual Studio 2019

W Visual Studio 2013 i starszych, zgodność binarna między plikami obiektów (przywołujące obj zawierały), bibliotekami statycznymi (LIBs), bibliotekami dynamicznymi (dll) i plikami wykonywalnymi (exe) utworzonymi przy użyciu różnych wersji zestawu narzędzi kompilatora i bibliotek środowiska uruchomieniowego nie została zagwarantowana. 

W programie Visual Studio 2015 i nowszych głównym C++ numerem zestawu narzędzi jest 14 (wersji 140 for visual Studio 2015, najnowsze 141 for visual Studio 2017 i V142 for visual Studio 2019). Odzwierciedla to fakt, że zarówno biblioteki środowiska uruchomieniowego, jak i aplikacje skompilowane z każdą wersją kompilatora są zgodne ze standardami binarnymi. Oznacza to, że jeśli masz bibliotekę innych firm, która została skompilowana przy użyciu programu Visual Studio 2015, nie musisz jej ponownie skompilować, aby wykorzystać ją z aplikacji skompilowanej za pomocą programu Visual Studio 2017 lub Visual Studio 2019.

Jedyny wyjątek od tej reguły polega na tym, że biblioteki statyczne lub pliki obiektów, które są kompilowane za pomocą przełącznika kompilatora `/GL` nie są zgodne ze standardami binarnymi. 

Gdy Mieszasz pliki binarne skompilowane z różnymi obsługiwanymi wersjami zestawu narzędzi MSVC C++ , pakiet redystrybucyjny wizualizacji, w którym jest uruchomiona aplikacja, nie może być starsza niż dowolna wersja zestawu narzędzi używana do kompilowania aplikacji lub wszelkich bibliotek, których używa. 

## <a name="upgrade-microsoft-visual-c-redistributable-from-visual-studio-2015-or-2017-to-visual-studio-2019"></a>Uaktualnij pakiet C++ redystrybucyjny Microsoft Visual z wersji visual Studio 2015 lub 2017 do programu visual Studio 2019

Ponieważ zachowano kompatybilność binarną i zachowano wersję główną (14) w ramach pakietu redystrybucyjnego C++ wizualizacji dla programu visual Studio 2015, 2017 i 2019, w każdej chwili można zainstalować tylko C++ jedną wersję pakietu redystrybucyjnego wizualizacji. Nowsza wersja spowoduje zastąpienie zainstalowanej starszej wersji. Jeśli masz pakiet redystrybucyjny wizualizacji C++ z poziomu programu visual Studio 2015 lub 2017, a następnie zostanie zainstalowany system 2019, wersja 2019 spowoduje zastąpienie starszej wersji. Ponieważ firma Microsoft gwarantuje, że Najnowsza wersja zawiera wszystkie najnowsze funkcje i poprawki błędów, w tym poprawki zabezpieczeń, zawsze zalecamy uaktualnienie do najnowszej dostępnej wersji.

Podobnie nie zezwalamy na instalowanie starszej wersji pakietu redystrybucyjnego wizualizacji C++ na komputerze, na którym już istnieje nowszy. Zainstalowanie pakietu redystrybucyjnego wizualizacji C++ z programu visual Studio 2015 lub 2017 na komputerze, który już ma 2019, spowoduje niepowodzenie instalacji. Błąd będzie wyglądać podobnie do tego:

```
*0x80070666 - Another version of this product is already installed. Installation of this version cannot continue. To configure or remove the existing version of this product, use Add/Remove Programs on the Control Panel.*.
```

Ten błąd jest zaprojektowany. Zalecamy pozostawienie zainstalowanej najnowszej instalacji.

## <a name="see-also"></a>Zobacz także

* [Historia C++ zmian wizualnych](../porting/visual-cpp-change-history-2003-2015.md)
* [Najnowsze obsługiwane pliki redystrybucyjne wizualizacji C++](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) 
