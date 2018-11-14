---
title: Ograniczniki tagów dokumentacji Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- XML documentation, delimiters
ms.assetid: debfbdd9-63fa-4c58-a18e-a4d203d241d7
ms.openlocfilehash: 709c17138032a98ec2f8ff978d9b8364241989b1
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326488"
---
# <a name="delimiters-for-visual-c-documentation-tags"></a>Ograniczniki tagów dokumentacji Visual C++

Korzystanie z tagów dokumentacji wymaga ograniczników, które wskazują kompilatora, gdzie rozpoczyna się i kończy w komentarzu dokumentacji.

Za pomocą następujących rodzajów ograniczniki tagów dokumentacji XML:

| | |
|-|-|
| `///` | Jest to forma, pokazano w przykładach dokumentacji i używane przez Szablony projektów Visual C++.  |
| `/** */`  | Są to wielowierszowy ograniczników.  |

Istnieją reguły niektóre formatowania, korzystając z `/** */` ograniczniki:

- Dla wiersza, który zawiera `/**` ogranicznik, jeśli pozostałą część wiersza jest biały znak, wiersz nie został przetworzony komentarzy. Jeśli pierwszy znak odstępu, że biały znak jest ignorowana, a pozostała część wiersza jest przetwarzany. W przeciwnym razie cały tekst wiersza po `/**` ogranicznik jest przetwarzany jako część komentarza.

- Dla wiersza, który zawiera `*/` ogranicznik, jeśli występuje maksymalnie białych znaków `*/` ogranicznik, w tym wierszu jest ignorowany. W przeciwnym razie tekst w wierszu do `*/` ogranicznik jest przetwarzany jako część komentarza, zgodnie z regułami dopasowywania wzorca opisanego w następny.

- Wiersze po ten, który rozpoczyna się od `/**` ogranicznik, kompilator szuka wspólny wzorzec na początku każdego wiersza, opcjonalny odstęp i znak gwiazdki (`*`), a następnie więcej opcjonalny odstęp. Jeśli kompilator znajdzie ze wspólnego zestawu znaków na początku każdego wiersza, zignoruje ten wzorzec dla wszystkich wierszy po `/**` ogranicznika, prawdopodobnie łącznie wiersza, który zawiera `*/` ogranicznika.

Kilka przykładów:

- To jedyna część Poniższy komentarz, które będą przetwarzane jest wiersz, który rozpoczyna się od `<summary>`. Następujące dwa formaty generuje ten sam komentarzy:

    ```cpp
    /**
    <summary>text</summary>
    */
    /** <summary>text</summary> */
    ```

- Kompilator stosuje wzorzec " \* " ignorowanie na początku linii drugiego i trzeciego.

    ```cpp
    /**
     * <summary>
     *  text </summary>*/
    ```

- Kompilator znajdzie nie wzorca w komentarz, ponieważ nie istnieje żadne gwiazdki w drugim wierszu. W związku z tym, cały tekst w wierszach drugi i trzeci do `*/`, będą przetwarzane w ramach komentarza.

    ```cpp
    /**
     * <summary>
       text </summary>*/
    ```

- Kompilator znajduje nie wzorca w ten komentarz z dwóch przyczyn. Po pierwsze jest nie wiersza, który rozpoczyna się od spójne liczby spacji przed znakiem gwiazdki. Po drugie piąty wiersz rozpoczyna się od kartę, która jest niezgodna z miejsc do magazynowania. W związku z tym, cały tekst z drugiego wiersza do momentu `*/` będą przetwarzane w ramach komentarza.

    ```cpp
    /**
      * <summary>
      * text
     *  text2
       *  </summary>
    */
    ```

## <a name="see-also"></a>Zobacz też

[Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)