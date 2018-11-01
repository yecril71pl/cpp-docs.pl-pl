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
ms.openlocfilehash: 4476b0805c8806d344a9290ba190aed7c7697a8f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514637"
---
# <a name="international-enabling"></a>Włączanie internacjonalizacji

Założeń dotyczących znakowe i manipulowania, które nie będą działać dobrze sprawdza się w aplikacjach międzynarodowych sprawia, że tradycyjnych kodu C i C++. Chociaż MFC i biblioteki wykonawczej obsługi standardu Unicode i MBCS, ma nadal pracy należy wykonać. Przeprowadzenie Cię w tej sekcji wyjaśniono znaczenie "Włączanie internacjonalizacji" w programie Visual C++:

- Unicode i MBCS są włączane przy użyciu przenośne typy danych w listy parametrów funkcji MFC i zwracanych typów. Te typy warunkowe są definiowane w odpowiedni sposób, w zależności od tego, czy kompilacja definiuje symbol `_UNICODE` lub symbol `_MBCS` (co oznacza DBCS). Różne rodzaje biblioteki MFC są automatycznie łączeni ze swoją aplikacją, w zależności od tego, który z tych dwóch symboli definiuje kompilacji.

- Kod biblioteki klasy używa przenośnej funkcji wykonawczej i inny sposób do zapewnienia poprawnego zachowania Unicode i MBCS.

- Możesz nadal obsługiwać niektórych rodzajów zadań internacjonalizacji w kodzie:

   - Użyj tych samych funkcji wykonawczej przenośne wchodzące w MFC przenośne w ramach jednego środowiska.

   - Wprowadzić ciągi literałów i znaki przenośne w ramach jednego środowiska za pomocą `_T` makra. Aby uzyskać więcej informacji, zobacz [mapowania typ ogólny-tekst w pliku Tchar.h](../text/generic-text-mappings-in-tchar-h.md).

   - Podczas analizowania ciągów, w obszarze MBCS, należy zachować środki ostrożności. Te środki ostrożności nie są potrzebne w ramach standardu Unicode. Aby uzyskać więcej informacji, zobacz [porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md).

   - Zajmujemy się po przemieszaniu ANSI (8-bitowa) i Unicode (16-bitowy) znaki w aplikacji. Można używać znaków ANSI w niektórych części programu i znaki Unicode w innych, ale nie można mieszać je w ten sam ciąg.

   - Nie nie trwale kodować ciągów w aplikacji. Zamiast tego należy wprowadzić je STRINGTABLE zasobów przez dodanie ich do pliku .rc w aplikacji. Aplikacja może być lokalizowana następnie bez konieczności zmiany kodu źródłowego lub ponownej kompilacji. Aby uzyskać więcej informacji na temat zasobów STRINGTABLE zobacz [edytor ciągów](../windows/string-editor.md).

> [!NOTE]
>  Zestawy znaków Europejską i MBCS mają niektórych znaków, takich jak akcentowanych liter z kody znaków jest większa od 0x80. Ponieważ większość kodu używa znaków podpisem, te znaki, które są większe niż 0x80 są rozszerzona o znak po przekonwertowaniu do **int**. Jest to problem dla indeksowania tablic, ponieważ znaki znakiem jest ujemna, indeksuje spoza tablicy. Języki, które używają MBCS, takich jak japoński, są również unikatowe. Ponieważ znak może składać się z 1 lub 2 bajtów, należy zawsze manipulować zarówno w bajtach, w tym samym czasie.

## <a name="see-also"></a>Zobacz też

[Unicode i MBCS](../text/unicode-and-mbcs.md)<br/>
[Strategie internacjonalizacji](../text/internationalization-strategies.md)