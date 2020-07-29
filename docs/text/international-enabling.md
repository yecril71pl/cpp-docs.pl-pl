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
ms.openlocfilehash: ff0fb4102a0453b900b5b406739492a9420a5b07
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228092"
---
# <a name="international-enabling"></a>Włączanie internacjonalizacji

Najbardziej tradycyjny kod C i C++ tworzy założenia dotyczące manipulowania znakami i ciągami, które nie działają dobrze w przypadku aplikacji międzynarodowych. Chociaż zarówno MFC, jak i Biblioteka wykonawcza obsługują standard Unicode lub MBCS, nadal można wykonywać zadania. W tej sekcji wyjaśniono znaczenie "włączenia międzynarodowego" w Visual C++:

- Zarówno Unicode, jak i MBCS są włączane za pomocą typu danych przenośnych na listach parametrów funkcji MFC i zwracanych typów. Te typy są definiowane warunkowo w odpowiedni sposób, w zależności od tego, czy kompilacja definiuje symbol, `_UNICODE` czy symbol `_MBCS` (co oznacza DBCS). Różne warianty bibliotek MFC są automatycznie łączone z aplikacją, w zależności od tego, które z tych dwóch symboli definiuje kompilacja.

- Kod biblioteki klas używa przenośnych funkcji czasu wykonywania i innych metod, aby zapewnić poprawne zachowanie w formacie Unicode lub MBCS.

- Nadal musisz obsługiwać pewne rodzaje zadań wielojęzycznych w kodzie:

  - Użyj tych samych przenośnych funkcji środowiska uruchomieniowego, które obsługują MFC w dowolnym środowisku.

  - Wprowadź ciągi literałów i znaki przenośne w obu środowiskach przy użyciu `_T` makra. Aby uzyskać więcej informacji, zobacz [Mapowanie tekstu ogólnego w używanie TCHAR. h](../text/generic-text-mappings-in-tchar-h.md).

  - Podejmuj środki ostrożności podczas analizowania ciągów w obszarze MBCS. Te środki ostrożności nie są niezbędne w standardzie Unicode. Aby uzyskać więcej informacji, zobacz [wskazówki dotyczące programowania MBCS](../text/mbcs-programming-tips.md).

  - Należy zachować ostrożność, jeśli Mieszasz znaki ANSI (8-bitowe) i Unicode (16-bitowe) w aplikacji. Istnieje możliwość używania znaków ANSI w niektórych częściach programu i znaków Unicode w innych, ale nie można ich mieszać w tym samym ciągu.

  - Nie należy określać twardych ciągów w aplikacji. Zamiast tego należy udostępnić im zasoby CIĄGÓW, dodając je do pliku. RC aplikacji. Aplikacja może zostać następnie zlokalizowana bez konieczności zmiany kodu źródłowego lub ponownej kompilacji. Aby uzyskać więcej informacji na temat zasobów CIĄGÓW, zobacz [Edytor ciągów](../windows/string-editor.md).

> [!NOTE]
> Zestawy znaków europejskie i MBCS zawierają kilka znaków, takich jak litery akcentowane, z kodami znaku większymi niż 0x80. Ze względu na to, że większość kodu używa znaków podpisanych, te znaki większe niż 0x80 są po konwersji na **`int`** . Jest to problem z indeksowaniem tablicy, ponieważ znaki, które są znakami, są ujemne, indeksy poza tablicą. Języki, które używają MBCS, takie jak japoński, również są unikatowe. Ponieważ znak może składać się z 1 lub 2 bajtów, zawsze należy manipulować obu bajtami jednocześnie.

## <a name="see-also"></a>Zobacz także

[Unicode i MBCS](../text/unicode-and-mbcs.md)<br/>
[Strategie międzynarodowe](../text/internationalization-strategies.md)
