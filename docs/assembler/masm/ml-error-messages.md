---
title: Komunikaty o błędach ML
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- vc.errors.ml
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), ML error messages
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
ms.openlocfilehash: b9238591ae025c4af258d8b5feda6e05c8bd291b
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397183"
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
