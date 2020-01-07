---
title: Komunikaty o błędach ML
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- vc.errors.ml
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), ML error messages
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
ms.openlocfilehash: 1b065433a1a6baf9bf2631aeb2f53421f8efb83b
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75312628"
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

[Dokumentacja asemblera programu Microsoft Macro](microsoft-macro-assembler-reference.md)
