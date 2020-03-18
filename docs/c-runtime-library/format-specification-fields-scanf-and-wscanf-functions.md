---
title: Pola specyfikacji formatu dla funkcji wscanf
ms.date: 11/04/2016
helpviewer_keywords:
- width, specifications in scanf function
- scanf format specifications
- scanf width specifications
- scanf type field characters
- type fields, scanf function
- format specification fields for scanf function
- type fields
ms.assetid: 7e95de1b-0b71-4de3-9f81-c9560c78e039
ms.openlocfilehash: 025d4c164d3afe1ca6b05c1c8e76441109cbc4ae
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438363"
---
# <a name="format-specification-fields-scanf-and-wscanf-functions"></a>Pola specyfikacji formatu dla funkcji wscanf

Informacje w tym artykule dotyczą całej rodziny `scanf` funkcji, w tym bezpiecznych wersji i opisują symbole używane do podania `scanf` funkcji, jak przeanalizować strumień wejściowy, taki jak strumień wejściowy `stdin` dla `scanf`, do wartości, które są wstawiane do zmiennych programu.

Specyfikacja formatu ma następującą postać:

`%`[`*`] [[Szerokość](../c-runtime-library/scanf-width-specification.md)] [{[h &#124; l &#124; ll &#124; I64 &#124; l](../c-runtime-library/scanf-width-specification.md)[}]](../c-runtime-library/scanf-type-field-characters.md)

Argument `format` określa interpretację danych wejściowych i może zawierać co najmniej jedną z następujących wartości:

- Znaki odstępu: puste (' '); Karta ("\t"); lub nowy wiersz ("\n"). Biały znak powoduje `scanf` odczytywanie, ale nie przechowywanie, wszystkich kolejnych białych znaków w danych wejściowych do kolejnego niebiałego znaku. Jeden znak odstępu w formacie dopasowuje dowolną liczbę (w tym 0) i kombinację białych znaków w danych wejściowych.

- Znaki niebędące znakami odstępu, z wyjątkiem znaku procentu (`%`). Znak niebędący odstępem powoduje, że `scanf` odczytywanie, ale nie przechowywanie, odpowiadającego znaku niebiałego odstępu. Jeśli następny znak w strumieniu wejściowym nie jest zgodny, `scanf` kończy się.

- Specyfikacje formatu wprowadzone przez znak procentu (`%`). Specyfikacja formatu powoduje `scanf` odczytywanie i konwertowanie znaków w danych wejściowych na wartości określonego typu. Wartość jest przypisana do argumentu na liście argumentów.

Format jest odczytywany od lewej do prawej. Oczekiwana liczba znaków poza specyfikacją formatu jest zgodna z sekwencją znaków w strumieniu wejściowym. pasujące znaki w strumieniu wejściowym są skanowane, ale nie są przechowywane. Jeśli znak w strumieniu wejściowym jest w konflikcie ze specyfikacją formatu, `scanf` kończy się, a znak pozostanie w strumieniu wejściowym, tak jakby nie został odczytany.

Po napotkaniu pierwszej specyfikacji formatu wartość pierwszego pola wejściowego jest konwertowana zgodnie z tą specyfikacją i przechowywana w lokalizacji określonej przez pierwsze `argument`. Druga specyfikacja formatu powoduje, że drugie pole wejściowe jest konwertowane i przechowywane w drugim `argument`i tak dalej na końcu ciągu formatu.

Pole wejściowe jest zdefiniowane jako wszystkie znaki do pierwszego znaku odstępu (spacja, karta lub nowy wiersz) lub do pierwszego znaku, którego nie można przekonwertować zgodnie ze specyfikacją formatu lub do czasu osiągnięcia szerokości pola (Jeśli określono). Jeśli istnieje zbyt wiele argumentów dla podanej specyfikacji, dodatkowe argumenty są oceniane, ale pomijane. Wyniki są nieprzewidywalne, jeśli nie ma wystarczającej liczby argumentów specyfikacji formatu.

Każde pole specyfikacji formatu jest pojedynczym znakiem lub liczbą oznaczającą określoną opcję formatu. `type` znak, który pojawia się po ostatnim polu formatu opcjonalne, określa, czy pole wejściowe jest interpretowane jako znak, ciąg czy liczba.

Najprostsza specyfikacja formatu zawiera tylko symbol procentu i znak `type` (na przykład `%s`). Jeśli po znaku procentu (`%`) następuje znak, który nie ma znaczenia jako znaku kontrolnego formatu, ten znak i następujące znaki (do następnego znaku procentu) są traktowane jako zwykła sekwencja znaków, czyli sekwencja znaków, która musi być zgodna z danymi wejściowymi. Na przykład, aby określić, że znak procentu ma być wprowadzany, użyj `%%`.

Gwiazdka (`*`) po znaku procentu pomija przypisanie następnego pola wejściowego, które jest interpretowane jako pole określonego typu. Pole jest skanowane, ale nie przechowywane.

Bezpieczne wersje (z sufiksem `_s`) rodziny funkcji `scanf` wymagają, aby parametr rozmiaru buforu został przeszedł bezpośrednio po każdym parametrze typu `c`, `C`, `s`, `S` lub `[`. Aby uzyskać więcej informacji na temat bezpiecznych wersji `scanf` rodziny funkcji, zobacz [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md).

## <a name="see-also"></a>Zobacz też

[scanf, specyfikacje szerokości](../c-runtime-library/scanf-width-specification.md)<br/>
[scanf, znaki pola typu](../c-runtime-library/scanf-type-field-characters.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)
