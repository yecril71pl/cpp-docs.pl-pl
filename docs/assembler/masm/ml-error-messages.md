---
title: Komunikaty o błędach ML
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- vc.errors.ml
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), ML error messages
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
ms.openlocfilehash: 2db928d22219d33f89396bb29530680d4b3c8dba
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856946"
---
# <a name="ml-error-messages"></a>Komunikaty o błędach ML

Komunikaty o błędach generowane przez składniki MASM wchodzą w skład trzech kategorii:

- **Błędy krytyczne.** Wskazują one na poważny problem, który uniemożliwia wykonanie normalnego procesu przez narzędzie.

- **Błędy niekrytyczne.** Narzędzie może zakończyć proces. Jeśli tak się stanie, jego wynik nie będzie taki sam.

- **Ostrzeżeni.** Te komunikaty wskazują warunki, które mogą uniemożliwić uzyskanie żądanych wyników.

Wszystkie komunikaty o błędach przyjmują następującą formę:

> *Narzędzie*: *filename* (*line*): {*Error_type*} (*kod*): *Message_text*

gdzie:

\ *narzędzi*
Program, który wysłał komunikat o błędzie.

*Nazwa pliku*\
Plik zawierający warunek generowania błędu.

\ *wiersza*
Przybliżony wiersz, w którym występuje warunek błędu.

*Error_type*\
Błąd krytyczny, błąd lub ostrzeżenie.

\ *kodu*
Unikatowy kod błędu 5-lub 6-cyfrowy.

*Message_text*\
Krótki i ogólny opis warunku błędu.

## <a name="see-also"></a>Zobacz także

[Dokumentacja asemblera programu Microsoft Macro](../../assembler/masm/microsoft-macro-assembler-reference.md)
