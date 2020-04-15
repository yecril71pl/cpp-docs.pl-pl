---
title: Włączanie internacjonalizacji
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- strings [C++], international enabling
- localization [C++], character sets
- MBCS [C++], enabling
- Unicode [C++], enabling
ms.assetid: b077f4ca-5865-40ef-a46e-d9e4d686ef21
ms.openlocfilehash: b6c645bafef87ed0b2d43903f4752ef659d79f89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375808"
---
# <a name="international-enabling"></a>Włączanie internacjonalizacji

Większość tradycyjnych kod C i C++ sprawia, że założenia dotyczące manipulacji znak i ciąg, które nie działają dobrze dla aplikacji międzynarodowych. Podczas gdy zarówno MFC, jak i biblioteka w czasie wykonywania obsługują unicode lub MBCS, nadal jest do wykonania. Aby cię poprowadzić, w tej sekcji wyjaśniono znaczenie "międzynarodowego włączania" w języku Visual C++:

- Unicode i MBCS są włączone za pomocą przenośnych typów danych na listach parametrów funkcji MFC i typach zwracanych. Typy te są warunkowo zdefiniowane w odpowiedni sposób, `_UNICODE` w zależności `_MBCS` od tego, czy kompilacja definiuje symbol, czy symbol (co oznacza DBCS). Różne warianty bibliotek MFC są automatycznie połączone z aplikacją, w zależności od tego, który z tych dwóch symboli kompilacji definiuje.

- Kod biblioteki klas używa przenośnych funkcji wykonywania i innych środków w celu zapewnienia prawidłowego zachowania Unicode lub MBCS.

- Nadal należy obsługiwać pewne rodzaje zadań internacjonalizacji w kodzie:

  - Użyj tych samych funkcji przenośnego czasu wykonywania, które sprawiają, że MFC przenośne w obu środowiskach.

  - Aby dosłowne ciągi i znaki były `_T` przenośne w każdym środowisku, używając makra. Aby uzyskać więcej informacji, zobacz [Mapowania tekstu ogólnego w tchar.h](../text/generic-text-mappings-in-tchar-h.md).

  - Należy podjąć środki ostrożności podczas analizowania ciągów w mbcs. Te środki ostrożności nie są potrzebne w ramach Unicode. Aby uzyskać więcej informacji, zobacz [Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md).

  - Należy uważać, jeśli mieszasz znaki ANSI (8-bitowe) i Unicode (16-bitowe) w aplikacji. W niektórych częściach programu można używać znaków ANSI, a w innych znaków Unicode, ale nie można ich mieszać w tym samym ciągu.

  - Nie należy wykonywać ciągów kodu twardego w aplikacji. Zamiast tego, uczynić je stringtable zasobów, dodając je do pliku .rc aplikacji. Aplikacja może być następnie zlokalizowane bez konieczności zmiany kodu źródłowego lub ponownej kompilacji. Aby uzyskać więcej informacji na temat zasobów STRINGTABLE, zobacz [Edytor ciągów](../windows/string-editor.md).

> [!NOTE]
> Europejskie i MBCS zestawy znaków mają pewne znaki, takie jak litery akcentowane, z kodami znaków większymi niż 0x80. Ponieważ większość kodu używa znaków podpisanych, znaki te większe niż 0x80 są rozszerzane na znaki po przekonwertowaniu **na int**. Jest to problem dla indeksowania tablicy, ponieważ znaki rozszerzone znak, są ujemne, indeksuje poza tablicy. Języki, które używają MBCS, takich jak japoński, są również unikatowe. Ponieważ znak może składać się z 1 lub 2 bajtów, należy zawsze manipulować oba bajty w tym samym czasie.

## <a name="see-also"></a>Zobacz też

[Unicode i MBCS](../text/unicode-and-mbcs.md)<br/>
[Strategie internacjonalizacji](../text/internationalization-strategies.md)
