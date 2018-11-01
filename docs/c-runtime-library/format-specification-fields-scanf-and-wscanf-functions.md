---
title: Pola specyfikacji formatu dla funkcji wscanf
ms.date: 11/04/2016
apilocation:
- msvcr80.dll
- msvcr110.dll
- msvcr90.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- wscanf
- scanf
helpviewer_keywords:
- width, specifications in scanf function
- scanf format specifications
- scanf width specifications
- scanf type field characters
- type fields, scanf function
- format specification fields for scanf function
- type fields
ms.assetid: 7e95de1b-0b71-4de3-9f81-c9560c78e039
ms.openlocfilehash: 83c380adc1a8985bb232d70c6d7c4cb4a885e789
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625943"
---
# <a name="format-specification-fields-scanf-and-wscanf-functions"></a>Pola specyfikacji formatu dla funkcji wscanf

Informacje w tym miejscu ma zastosowanie do całej `scanf` rodziny funkcji, w tym bezpieczne wersje i symbole używane, aby poinformować opisuje `scanf` działa jak przeanalizować strumienia wejściowego, takich jak strumień wejściowy `stdin` dla `scanf`, do wartości, które są wstawiane do zmiennych program.

Specyfikacja formatu ma następującą postać:

`%`[`*`] [[szerokość](../c-runtime-library/scanf-width-specification.md)] [{[h &#124; l &#124; ll &#124; I64 &#124; L](../c-runtime-library/scanf-width-specification.md)}][typu](../c-runtime-library/scanf-type-field-characters.md)

`format` Argument określa interpretacji danych wejściowych i może zawierać jeden lub więcej z następujących czynności:

- Znaki odstępu: pusty (""); Karta ("\t"); lub nowego wiersza (\n). Powoduje, że znak odstępu `scanf` do odczytu, ale nie są przechowywane, wszystkich następujących po sobie znaki odstępu w danych wejściowych do następnego znaku bez odstępu. Jeden znak odstępu, w formacie dopasowuje dowolną liczbę, o których (w tym 0) i kombinacji znaków odstępu w danych wejściowych.

- -Non białe znaki z wyjątkiem znaku procentu (`%`). Powoduje, że znak inny niż biały `scanf` do odczytu, ale nie są przechowywane, pasującego znaku bez odstępu. Jeśli następny znak w strumieniu wejściowym nie jest zgodny, `scanf` kończy.

- Format specyfikacji, wprowadzone przez znak procentu (`%`). Specyfikacja formatu powoduje konwersję `scanf` odczytu i konwertowania znaków w danych wejściowych na wartości określonego typu. Wartość jest przypisywana do argumentu na liście argumentów.

Format jest odczytywany od lewej do prawej. Znaki spoza specyfikacji formatu powinny pasuje do sekwencji znaków w strumieniu wejściowym; pasujących znaków w strumieniu wejściowym są skanowane, ale nie jest przechowywane. Jeśli znak w strumieniu wejściowym powoduje konflikt z specyfikacji formatu `scanf` kończy działanie, a znak pozostanie w strumieniu wejściowym tak, jakby były nie został odczytany.

Po napotkaniu pierwszą specyfikację formatu wartość pierwszego pola wejściowego jest konwertowane zgodnie z tą specyfikacją i przechowywane w lokalizacji, który jest określony przez pierwszy `argument`. Druga specyfikacja formatu powoduje konwersję drugiego pole wejściowe przekonwertować i przechowywać w drugim `argument`, i tak dalej do końca ciągu formatu.

Pola wejściowego jest zdefiniowany jako wszystkie znaki do pierwszego znaku odstępu (miejsca, tabulatorem ani), lub do pierwszego znaku, który nie może zostać skonwertowany według specyfikacji formatu lub do szerokości pola (Jeśli określono) zostanie osiągnięty. W przypadku zbyt wiele argumentów dla danego specyfikacje dodatkowe argumenty są obliczono, ale zignorowano. Wyniki są nieprzewidywalne, jeśli nie ma wystarczającej liczby argumentów dla specyfikacji formatu.

Każde pole specyfikacji formatu jest pojedynczym znakiem lub liczbą oznaczającą opcję formatu. `type` Znak, który następuje po ostatnim polu format opcjonalne, określa, czy pole wejściowe, jest interpretowany jako znak, ciąg lub liczba.

Najprostsza specyfikacji formatu zawiera tylko znak procentu i `type` znaków (na przykład `%s`). Jeśli znak procentu (`%`) jest poprzedzony znakiem, ma znaczenia jako znaku kontrolnego formatu, że znak i następujące znaki (maksymalnie następny znak procentu) są traktowane jako zwykły ciąg znaków, oznacza to, sekwencji znaki, które muszą być zgodne z danych wejściowych. Na przykład aby określić, że znak procentu ma być użyty jako wejście, należy użyć `%%`.

Znak gwiazdki (`*`) po znaku procentu pomija przypisania dalej pola wejściowego jest interpretowany jako pola określonego typu. Pole jest skanowany, ale nie są przechowywane.

Bezpieczne wersje (z `_s` sufiks) z `scanf` rodzinę funkcji wymagają, że parametr rozmiaru buforu można przekazać bezpośrednio po każdego parametru typu `c`, `C`, `s`, `S`lub `[`. Aby uzyskać więcej informacji na temat bezpieczne wersje `scanf` rodzinę funkcji, zobacz [scanf_s, _scanf_s_l —, wscanf_s —, _wscanf_s_l —](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md).

## <a name="see-also"></a>Zobacz też

[scanf, specyfikacje szerokości](../c-runtime-library/scanf-width-specification.md)<br/>
[scanf, znaki pola typu](../c-runtime-library/scanf-type-field-characters.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)