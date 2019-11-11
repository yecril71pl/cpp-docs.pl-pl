---
title: C++zgodność binarna między programami Visual Studio 2015 i Visual Studio 2019
description: Opisuje sposób, w jaki zgodność binarna działa między skompilowanymi C++ plikami w programie Visual Studio 2015, 2017 i 2019. Jeden pakiet redystrybucyjny Microsoft Visual C++ działa dla wszystkich trzech wersji.
ms.date: 11/07/2019
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
ms.openlocfilehash: e41c34abe25deefe100f525044faeac0b0c3054a
ms.sourcegitcommit: eb254b4462a58d219376ff501bf768bd1adc07ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2019
ms.locfileid: "73912881"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2019"></a>C++zgodność binarna między programami Visual Studio 2015 i Visual Studio 2019

W Microsoft Visual Studio 2013 i starszych, zgodność binarna nie jest gwarantowana między plikami obiektów (przywołujące obj zawierały), bibliotekami statycznymi (LIBs), bibliotekami dołączanymi dynamicznie (dll) i plikami wykonywalnymi (exe), które zostały skompilowane przy użyciu różnych wersji zestawu narzędzi kompilatora i biblioteki środowiska uruchomieniowego.

W programie Visual Studio 2015 i nowszych głównym C++ numerem zestawu narzędzi jest 14 (wersji 140 for visual Studio 2015, najnowsze 141 for visual Studio 2017 i V142 for visual Studio 2019). Ta numeracja odzwierciedla fakt, że zarówno biblioteki środowiska uruchomieniowego, jak i aplikacje skompilowane przy użyciu dowolnej z tych wersji kompilatora są zgodne ze standardami binarnymi. W związku z tym, jeśli masz bibliotekę innej firmy, która została skompilowana przy użyciu programu Visual Studio 2015, nie musisz jej ponownie skompilować, aby wykorzystać ją z aplikacji skompilowanej za pomocą programu Visual Studio 2017 lub Visual Studio 2019.

Jedyny wyjątek od tej reguły polega na tym, że biblioteki statyczne lub pliki obiektów, które są kompilowane za pomocą przełącznika kompilatora `/GL` *nie* są zgodne ze standardami binarnymi.

Gdy Mieszasz pliki binarne skompilowane z różnymi obsługiwanymi wersjami zestawu narzędzi firmy Microsoft C++ (MSVC C++ ), pakiet redystrybucyjny wizualizacji, w której aplikacja jest uruchomiona, nie może być starsza niż dowolna z wersji zestawu narzędzi używanych do kompilowania aplikacji lub wszelkich bibliotek, których używa.

## <a name="upgrade-the-microsoft-visual-c-redistributable-from-visual-studio-2015-or-2017-to-visual-studio-2019"></a>Uaktualnij pakiet redystrybucyjny Microsoft Visual C++ w programie visual Studio 2015 lub 2017 do programu visual Studio 2019

Ponieważ zachowano zgodność binarną i zachowano wersję główną (14) w ramach pakietu redystrybucyjnego C++ firmy Microsoft dla programu visual Studio 2015, 2017 i 2019, można jednocześnie zainstalować tylko jedną wersję C++ elementu redystrybucyjnego wizualizacji. Nowsza wersja zastępuje starszą wersję, która jest już zainstalowana. Jeśli masz pakiet redystrybucyjny wizualizacji C++ z programu visual Studio 2015 lub 2017, a następnie zainstalujesz program visual Studio 2019, wersja 2019 zastępuje starszą wersję. Ze względu na to, że Najnowsza wersja zawiera wszystkie najnowsze funkcje i poprawki błędów (w tym poprawki zabezpieczeń), zawsze zalecamy uaktualnienie do najnowszej dostępnej wersji.

Podobnie nie można zainstalować starszej wersji pakietu redystrybucyjnego wizualizacji C++ na komputerze, na którym już zainstalowano nowszą wersję. Instalowanie pakietu redystrybucyjnego wizualizacji C++ z programu visual Studio 2015 lub 2017 na komputerze, na którym jest już zainstalowana wersja 2019, wyzwala błąd instalacji. Błąd jest podobny do następującego:

```Output
0x80070666 - Another version of this product is already installed. Installation of this version cannot continue. To configure or remove the existing version of this product, use Add/Remove Programs on the Control Panel.
```

Ten błąd jest zaprojektowany. Zalecamy pozostawienie zainstalowanej najnowszej wersji.

## <a name="see-also"></a>Zobacz także

* [Historia C++ zmian wizualnych](../porting/visual-cpp-change-history-2003-2015.md)
* [Najnowsze obsługiwane pliki redystrybucyjne wizualizacji C++](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) 
