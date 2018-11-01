---
title: Modyfikatory poleceń
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, command modifiers
- command modifiers
ms.assetid: b661c432-210f-4f05-bc56-744a46e0fc0b
ms.openlocfilehash: a9a79364880cf95adca6066b48f0d786391c8ba0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431815"
---
# <a name="command-modifiers"></a>Modyfikatory poleceń

Można określić co najmniej jeden Modyfikatory poleceń poprzedzającego polecenia, opcjonalnie rozdzielonych spacjami lub karty. Podobnie jak w przypadku poleceń, można wcięcia modyfikatory.

|Modyfikator|Cel|
|--------------|-------------|
|\@*Polecenie*|Uniemożliwia wyświetlanie polecenia. Wyświetlanie za pomocą poleceń nie jest pomijane. Domyślnie NMAKE funkcją wszystkie wykonane polecenia. Umożliwia /S Pomiń wyświetlanie dla całego pliku reguł programu make; Użyj **. DYSKRETNEJ** Pomija wyświetlanie części pliku reguł programu make.|
|**-**\[*Liczba*] *polecenia*|Wyłącza sprawdzanie błędów *polecenia*. Domyślnie NMAKE zatrzymuje, gdy polecenie zwróci kod zakończenia różny od zera. IF -*numer* jest używany, NMAKE zatrzymuje, jeśli kod zakończenia przekracza *numer*. Spacje lub tabulatory nie może występować między kreska i *numer.* Co najmniej jeden spacja lub tabulator musi znajdować się między `number` i *polecenia*. Użyj/i wyłączyć sprawdzanie błędów dotyczących całego pliku reguł programu make; Użyj **. Ignoruj** wyłączyć sprawdzanie część pliku reguł programu make.|
|**\!** *Polecenie*|Wykonuje *polecenia* dla każdego pliku zależnego Jeśli *polecenia* używa <strong>$ \* \*</strong> (wszystkie pliki zależne w zależności) lub **$?** (wszystkie pliki zależne powstanie zależności z sygnaturą czasową nowszy niż element docelowy).|

## <a name="see-also"></a>Zobacz też

[Polecenia w pliku reguł programu Make](../build/commands-in-a-makefile.md)
