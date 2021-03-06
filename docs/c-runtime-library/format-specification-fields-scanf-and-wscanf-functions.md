---
title: Pola specyfikacji formatu dla funkcji wscanf
ms.date: 11/04/2016
ms.topic: reference
ms.custom: contperfq1
helpviewer_keywords:
- width, specifications in scanf function
- scanf format specifications
- scanf width specifications
- scanf type field characters
- type fields, scanf function
- format specification fields for scanf function
- type fields
ms.assetid: 7e95de1b-0b71-4de3-9f81-c9560c78e039
ms.openlocfilehash: 4be7aa5e0790f0124890ee981ffd58e3027ea59b
ms.sourcegitcommit: 111ee74772d7f308d3414b5d42cbc1e90287f081
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2020
ms.locfileid: "88659334"
---
# <a name="format-specification-fields-scanf-and-wscanf-functions"></a>Pola specyfikacji formatu dla funkcji wscanf

Informacje zawarte w tym artykule dotyczą całej `scanf` rodziny funkcji, w tym bezpiecznych wersji i opisują symbole używane do poinformowania `scanf` funkcji, jak przeanalizować strumień wejściowy, taki jak strumień wejściowy `stdin` dla `scanf` , do wartości, które są wstawiane do zmiennych programu.

Specyfikacja formatu ma następującą postać:

`%`[ `*` ] [[Width](../c-runtime-library/scanf-width-specification.md)] [{[h &#124; l &#124; szystkie &#124; I64 &#124; l](../c-runtime-library/scanf-width-specification.md)}][type](../c-runtime-library/scanf-type-field-characters.md)

`format`Argument określa interpretację danych wejściowych i może zawierać co najmniej jedną z następujących wartości:

- Znaki odstępu: puste (' '); Karta ("\t"); lub nowy wiersz ("\n"). Biały znak powoduje `scanf` odczytanie, ale nie przechowywanie, wszystkich kolejnych białych znaków w danych wejściowych do kolejnego niebiałego znaku. Jeden znak odstępu w formacie dopasowuje dowolną liczbę (w tym 0) i kombinację białych znaków w danych wejściowych.

- Znaki inne niż białe, z wyjątkiem znaku procentu ( `%` ). Znak niebędący odstępem powoduje `scanf` odczytanie, ale nie przechowywanie, odpowiadającego znaku niebiałego odstępu. Jeśli następny znak w strumieniu wejściowym nie jest zgodny, `scanf` kończy się.

- Specyfikacje formatu wprowadzone przez znak procentu ( `%` ). Specyfikacja formatu powoduje `scanf` odczytywanie i konwertowanie znaków w danych wejściowych na wartości określonego typu. Wartość jest przypisana do argumentu na liście argumentów.

Format jest odczytywany od lewej do prawej. Oczekiwana liczba znaków poza specyfikacją formatu jest zgodna z sekwencją znaków w strumieniu wejściowym. pasujące znaki w strumieniu wejściowym są skanowane, ale nie są przechowywane. Jeśli znak w strumieniu wejściowym powoduje konflikt z specyfikacją formatu, `scanf` kończy się, a znak pozostanie w strumieniu wejściowym, tak jakby nie został odczytany.

Po napotkaniu pierwszej specyfikacji formatu wartość pierwszego pola wejściowego jest konwertowana zgodnie z tą specyfikacją i przechowywana w lokalizacji określonej w pierwszej kolejności `argument` . Druga specyfikacja formatu powoduje, że drugie pole wejściowe jest konwertowane i przechowywane w drugim itd `argument` . na końcu ciągu formatu.

Pole wejściowe jest zdefiniowane jako wszystkie znaki do pierwszego znaku odstępu (spacja, karta lub nowy wiersz) lub do pierwszego znaku, którego nie można przekonwertować zgodnie ze specyfikacją formatu lub do czasu osiągnięcia szerokości pola (Jeśli określono). Jeśli istnieje zbyt wiele argumentów dla podanej specyfikacji, dodatkowe argumenty są oceniane, ale pomijane. Wyniki są nieprzewidywalne, jeśli nie ma wystarczającej liczby argumentów specyfikacji formatu.

Każde pole specyfikacji formatu jest pojedynczym znakiem lub liczbą oznaczającą określoną opcję formatu. `type`Znak, który pojawia się po ostatnim polu formatu opcjonalnego, określa, czy pole wejściowe jest interpretowane jako znak, ciąg czy liczba.

Najprostsza specyfikacja formatu zawiera tylko symbol procentu i `type` znak (na przykład `%s` ). Jeśli po znaku procentu ( `%` ) następuje znak, który nie ma znaczenia jako znaku kontrolnego formatu, ten znak i następujące znaki (aż do następnego znaku procentu) są traktowane jako zwykła sekwencja znaków, czyli sekwencja znaków, która musi być zgodna z danymi wejściowymi. Na przykład, aby określić, że znak procentu ma być wprowadzany, użyj `%%` .

Gwiazdka ( `*` ) po znaku procentu pomija przypisanie następnego pola wejściowego, które jest interpretowane jako pole określonego typu. Pole jest skanowane, ale nie przechowywane.

Bezpieczne wersje (z `_s` sufiksem) `scanf` rodziny funkcji wymagają, aby parametr rozmiaru buforu został przeszedł bezpośrednio po każdym parametrze typu `c` , `C` , `s` , `S` lub `[` . Aby uzyskać więcej informacji na temat bezpiecznych wersji `scanf` rodziny funkcji, zobacz [scanf_s, _scanf_s_l, wscanf_s _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md).

## <a name="see-also"></a>Zobacz także

[scanf — Specyfikacja szerokości](../c-runtime-library/scanf-width-specification.md)<br/>
[scanf — znaki pola typu](../c-runtime-library/scanf-type-field-characters.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)
