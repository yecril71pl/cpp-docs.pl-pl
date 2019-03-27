---
title: Formatowanie danych wyjściowych niestandardowego kroku budowania lub zdarzenia kompilacji
ms.date: 08/27/2018
helpviewer_keywords:
- builds [C++], build events
- custom build steps [C++], output format
- events [C++], build
- build events [C++], output format
- build steps [C++], output format
- builds [C++], custom build steps
ms.assetid: 92ad3e38-24d7-4b89-90e6-5a16f5f998da
ms.openlocfilehash: b0e9a7514704742524f97e55c06ef47c7b36631b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823765"
---
# <a name="formatting-the-output-of-a-custom-build-step-or-build-event"></a>Formatowanie danych wyjściowych niestandardowego kroku budowania lub zdarzenia kompilacji

Jeśli w danych wyjściowych niestandardowego kroku budowania lub zdarzenia kompilacji jest prawidłowo sformatowany, użytkownicy uzyskują następujące korzyści:

- Ostrzeżenia i błędy, które są uwzględniane w **dane wyjściowe** okna.

- Dane wyjściowe pojawia się w **listy zadań** okna.

- Kliknięcie na dane wyjściowe w **dane wyjściowe** odpowiedniego tematu jest wyświetlana w oknie.

- Povoleny operace F1 w **listy zadań** okna lub **dane wyjściowe** okna.

Format danych wyjściowych powinien być:

> {<em>filename</em>**(**<em>wiersza #</em> \[ **,** <em>kolumnę #</em>]**)** &#124; *toolname*} **:** \[ <em>dowolny tekst</em> ] {**błąd** &#124;  **Ostrzeżenie**} <em>+ numer</em>**:**<em>możliwych do zlokalizowania ciągu</em> \[ <em>dowolny tekst</em> ]

Gdzie:

- {*a* &#124; *b*} jest wybór albo *a* lub *b*.

- \[<em>element</em>] jest opcjonalny ciąg lub parametr.

- **Pogrubienie** reprezentuje literału.

Na przykład:

> C:\\*sourcefile.cpp*(134): błąd C2143: błąd składniowy: brakuje ";" przed "}"
>
> LINK: błąd krytyczny LNK1104: nie można otworzyć pliku "*somelib.lib*"

## <a name="see-also"></a>Zobacz także

[Ogólne informacje o niestandardowych krokach budowania lub zdarzeniach kompilacji](understanding-custom-build-steps-and-build-events.md)