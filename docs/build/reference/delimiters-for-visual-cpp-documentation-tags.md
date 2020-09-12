---
title: Ograniczniki znaczników dokumentacji Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- XML documentation, delimiters
ms.assetid: debfbdd9-63fa-4c58-a18e-a4d203d241d7
ms.openlocfilehash: e8e312eacb46d82270d7ca1782b04d06012b207d
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041539"
---
# <a name="delimiters-for-visual-c-documentation-tags"></a>Ograniczniki znaczników dokumentacji Visual C++

Użycie tagów dokumentacji wymaga ograniczników, które wskazują kompilatorowi, w którym komentarz do dokumentacji rozpoczyna się i zamyka.

Do tagów dokumentacji XML można używać następujących rodzajów ograniczników:

| Ogranicznik | Opis |
|-|-|
| `///` | Jest to formularz, który jest wyświetlany w przykładach dokumentacji i używany przez szablony projektu Visual Studio C++.  |
| `/** */`  | Są to ograniczniki wielowierszowe.  |

W przypadku używania ograniczników istnieją pewne reguły formatowania `/** */` :

- W przypadku wiersza zawierającego `/**` ogranicznik, jeśli pozostała część wiersza jest białym znakiem, wiersz nie jest przetwarzany dla komentarzy. Jeśli pierwszy znak jest białych znaków, oznacza to, że biały znak jest ignorowany i pozostała część wiersza jest przetwarzana. W przeciwnym razie cały tekst wiersza po `/**` ograniczniku zostanie przetworzony jako część komentarza.

- W wierszu zawierającym `*/` ogranicznik, jeśli występuje tylko biały znak do `*/` ogranicznika, ten wiersz jest ignorowany. W przeciwnym razie tekst w wierszu do `*/` ogranicznika jest przetwarzany jako część komentarza, zgodnie z regułami dopasowania do wzorca opisanymi w następującym punkcie.

- Dla wierszy po tym, które zaczyna się od `/**` ogranicznika, kompilator szuka wspólnego wzorca na początku każdego wiersza, który składa się z opcjonalnego odstępu i gwiazdki ( `*` ), a następnie więcej opcjonalnego odstępu. Jeśli kompilator odnajdzie wspólny zestaw znaków na początku każdego wiersza, zignoruje ten wzorzec dla wszystkich wierszy po `/**` ograniczniku, do i prawdopodobnie, włącznie z wierszem zawierającym `*/` ogranicznik.

Oto niektóre przykłady:

- Jedyną częścią poniższego komentarza, który zostanie przetworzony, jest wiersz zaczynający się od `<summary>` . Następujące dwa formaty tagów będą generować te same Komentarze:

    ```cpp
    /**
    <summary>text</summary>
    */
    /** <summary>text</summary> */
    ```

- Kompilator stosuje wzorzec " \* " do ignorowania na początku drugiego i trzeciego wiersza.

    ```cpp
    /**
     * <summary>
     *  text </summary>*/
    ```

- Kompilator nie znalazł wzorca w tym komentarzu, ponieważ nie ma gwiazdki w drugim wierszu. W związku z tym cały tekst w drugim i trzecim wierszu, aż do `*/` , zostanie przetworzony w ramach komentarza.

    ```cpp
    /**
     * <summary>
       text </summary>*/
    ```

- Kompilator nie znalazł wzorca w tym komentarzu z dwóch przyczyn. Po pierwsze nie istnieje linia rozpoczynająca się od spójnej liczby spacji przed gwiazdką. Sekunda, piąta linia zaczyna się od karty, która nie jest zgodna z spacjami. W związku z tym cały tekst z drugiego wiersza do momentu, aż `*/` zostanie przetworzony jako część komentarza.

    ```cpp
    /**
      * <summary>
      * text
     *  text2
       *  </summary>
    */
    ```

## <a name="see-also"></a>Zobacz także

[Dokumentacja XML](xml-documentation-visual-cpp.md)
