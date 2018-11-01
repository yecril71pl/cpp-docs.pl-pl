---
title: Komunikaty o błędach ML
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- vc.errors.ml
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), ML error messages
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
ms.openlocfilehash: aa0440afae980e218c32ab3296bd7c6fb2b444d9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677802"
---
# <a name="ml-error-messages"></a>Komunikaty o błędach ML

Komunikaty o błędach generowane przez składniki MASM można podzielić na trzy kategorie:

- **Błędy krytyczne.** Oznaczają one poważny problem, który uniemożliwia ukończenie jego normalnego procesu narzędzie.

- **Błędy niekrytyczne.** Narzędzie może zakończenia procesu. Jeśli tak jest, jego wynik nie jest prawdopodobnie jedną, która ma.

- **Ostrzeżenia.** Te komunikaty wskazują warunki, które mogą uniemożliwić pobieranie wyników, które chcesz.

Wszystkie komunikaty o błędach mieć następującą formę:

> *Narzędzie*: *Filename* (*wiersza*): {*error_type —*} (*kodu*): *Message_text*

gdzie:

*Narzędzie*<br/>
Program, który jest wysyłany komunikat o błędzie.

*Nazwa pliku*<br/>
Plik, który zawiera warunek generowanie błędu.

*Wiersz*<br/>
Przybliżony wiersza, w której istnieje warunek błędu.

*Error_type —*<br/>
Krytyczny błąd, błąd lub ostrzeżenie.

*Kod*<br/>
Unikatowe 5 - lub 6-cyfrowy kod błędu.

*Message_text*<br/>
Krótko- i ogólny opis warunku błędu.

## <a name="see-also"></a>Zobacz także

[Microsoft Macro Assembler — dokumentacja](../../assembler/masm/microsoft-macro-assembler-reference.md)<br/>