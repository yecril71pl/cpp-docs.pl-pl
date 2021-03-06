---
title: Strategie internacjonalizacji
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- language-portable code [C++]
- MBCS [C++], internationalization strategies
- Windows API [C++], international programming strategies
- Win32 [C++], international programming strategies
- Unicode [C++], globalizing applications
- character sets [C++], international programming strategies
- localization [C++], character sets
ms.assetid: b09d9854-0709-4b9a-a00c-b0b8bc4199b1
ms.openlocfilehash: f8c5cec680072ffa34b1ee0bef9e09231de5f1ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410632"
---
# <a name="internationalization-strategies"></a>Strategie internacjonalizacji

W zależności od systemów operacyjnych i rynków masz kilka strategie internacjonalizacji:

- Twoja aplikacja używa Unicode.

   Możesz korzystać z funkcji specyficznych dla standardu Unicode i wszystkie znaki są szerokie 16 bitów (chociaż znaki ANSI w niektórych części programu służy do celów specjalnych). Biblioteki wykonawczej C zawiera funkcje, makr i typy danych do programowania tylko standardu Unicode. MFC jest w pełni obsługuje standard Unicode.

- Aplikacja używa MBCS i może działać na dowolnej platformie systemu Win32.

   Możesz skorzystać z funkcji specyficznych dla MBCS. Ciągi może zawierać znaków jednobajtowych i dwubajtowych znaków. Biblioteki wykonawczej C zawiera funkcje, makr i typy danych, do MBCS — tylko do programowania. MFC jest MBCS — włączone w pełnym zakresie.

- Kod źródłowy aplikacji są zapisywane pełne przenośności — przez kompilację z symbolem `_UNICODE` lub symbol `_MBCS` zdefiniowane, możesz utworzyć różne wersje korzystających z jedną. Aby uzyskać więcej informacji, zobacz [mapowania typ ogólny-tekst w pliku tchar.h](../text/generic-text-mappings-in-tchar-h.md).

   Można użyć w pełni przenośne C czasu wykonywania funkcji, makr i danych typów. Elastyczność MFC obsługuje jedną z następujących strategii.

W pozostałej części tych tematów skoncentrować się na pisaniu całkowicie przenośny kod, który może stworzyć jako Unicode lub MBCS.

## <a name="see-also"></a>Zobacz także

[Unicode i MBCS](../text/unicode-and-mbcs.md)<br/>
[Ustawienia regionalne i strony kodowe](../text/locales-and-code-pages.md)
