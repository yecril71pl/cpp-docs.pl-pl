---
title: Dyrektywy Dot
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, dot directives
- dot directives in NMAKE
ms.assetid: ab35da65-30b6-48b7-87d6-61503d7faf9f
ms.openlocfilehash: 2c21e8a18c76331f86a4e8966b4f67c9c9bc9b7d
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342825"
---
# <a name="dot-directives"></a>Dyrektywy Dot

Określ dyrektywy dot poza blokiem opis na początku wiersza. Dyrektywy dot rozpoczyna się kropką (. ) i następują dwukropek (:). Karty i spacje są dozwolone. Nazwy dyrektyw kropka jest uwzględniana wielkość liter i są wielkie litery.

|— Dyrektywa|Cel|
|---------------|-------------|
|**. IGNORUJ:**|Ignoruje kody zakończenia różny od zera, zwracane przez polecenia z miejscem, w którym jest określony na końcu pliku reguł programu make. Domyślnie NMAKE przerywa, jeśli polecenie zwróci kod zakończenia różny od zera. Aby przywrócić, sprawdzanie błędów, należy użyć **! CMDSWITCHES**. Ignorowanie kodu wyjścia dla jednego polecenia, użyj modyfikatora kreski (-). Aby zignorować kody zakończenia dla całego pliku, użyj / I.|
|**. METALI:** *elementów docelowych*|Zachowuje *cele* na dysku, jeśli te polecenia, aby je zaktualizować jest zatrzymany; nie ma wpływu Jeśli polecenie obsługuje przerwania poprzez usunięcie pliku. Rozdziel nazwy docelowego miejsca do magazynowania lub karty. Domyślnie NMAKE usuwa obiekt docelowy, jeśli kompilacja zostanie przerwana, CTRL + C lub CTRL + BREAK. Każde użycie **. CENNEGO** ma zastosowanie do całego pliku reguł programu make; kumulują wielu specyfikacji.|
|**. CICHY:**|Pomija wyświetlanie wykonane polecenia z miejscem, w którym jest określony na końcu pliku reguł programu make. Domyślnie NMAKE wyświetlane polecenia, który ją wywołuje. Aby przywrócić, wyświetlania, należy użyć **! CMDSWITCHES**. Aby pominąć wyświetlania dla jednego polecenia, należy użyć **@** modyfikator. Aby pominąć wyświetlania dla całego pliku, użyj/S.|
|**. SUFIKSY NAZW:** `list`|Wyświetla listę rozszerzeń, reguła wnioskowania dopasowanie; wstępnie zdefiniowane uwzględnienie następujących rozszerzeń: .exe .obj .asm .c .cpp .cxx .bas .cbl tego .pas .res .rc .f .f90|

Aby zmienić **. SUFIKSY** listy kolejności lub aby określić nową listę, wyczyść listę, a następnie określ nowe ustawienie. Aby wyczyścić listę, należy określić Brak rozszerzeń po dwukropku:

```
.SUFFIXES :
```

Aby dodać dodatkowe sufiksy na końcu listy, określ

```
.SUFFIXES : suffixlist
```

gdzie *suffixlist* znajduje się lista sufiksów, rozdzielone spacjami lub karty. Aby wyświetlić bieżące ustawienie **. SUFIKSY**, uruchomienie NMAKE z/p.

## <a name="see-also"></a>Zobacz także

[NMAKE — dokumentacja](nmake-reference.md)
