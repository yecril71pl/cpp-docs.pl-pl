---
title: Dyrektywy asemblera ARM | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9cfa8896-ec10-4e77-855a-3135c40d7d2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5c37e010caa6c7cfb44ddaf2f7dd1e28bbb5c291
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717707"
---
# <a name="arm-assembler-directives"></a>Dyrektywy ARM dotycząca asemblera

W większości przypadków asemblera ARM firmy Microsoft używa języka asemblera ARM, który został opisany w [armasm ARM kompilator podręcznik](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html). Jednak implementacji Microsoft niektórych dyrektyw zestawu różnią się od dyrektyw zestawu ARM. W tym artykule wyjaśniono różnice.

## <a name="microsoft-implementations-of-arm-assembly-directives"></a>Implementacje dyrektyw zestawu ARM firmy Microsoft

- AREA

   Asemblera ARM firmy Microsoft obsługuje te `AREA` atrybuty: `ALIGN`, `CODE`, `CODEALIGN`, `DATA`, `NOINIT`, `READONLY`, `READWRITE`, `THUMB`, `ARM`.

   Wszystkie regiony z wyjątkiem `THUMB` i `ARM` działają zgodnie z opisem w [armasm ARM kompilator podręcznik](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html).

   W asemblera ARM firmy Microsoft `THUMB` wskazuje, że `CODE` sekcja zawiera kod Thumb i jest ustawieniem domyślnym dla `CODE` sekcje.  `ARM` Wskazuje, że sekcja zawiera kod ARM.

- ATTR

   Nieobsługiwane.

- — KOD 16

   Nieobsługiwane, ponieważ jej działanie polega na pre-UAL Thumb składni, która asemblera ARM firmy Microsoft nie zezwala.  Użyj `THUMB` dyrektywy zamiast tego wraz ze składnią usługi rejestrowania dostępu użytkowników.

- WSPÓLNE

   Specyfikacja wyrównania dla typowych regionu nie jest obsługiwana.

- DCDO

   Nieobsługiwane.

- `DN`, `QN`, `SN`

   Specyfikacja typu lub lane na alias rejestru nie jest obsługiwana.

- ENTRY

   Nieobsługiwane.

- EQU

   Specyfikacja typu zdefiniowany symbol nie jest obsługiwana.

- `EXPORT` i `GLOBAL`

   Określa eksportu przy użyciu następującej składni:

   > **EKSPORTUJ**|**GLOBAL** <em>sym</em>{**[**<em>typu</em>**]**}

   *Sym* jest symbol do wyeksportowania.  [*typu*], jeśli określony, może być `[DATA]` do wskazania, że symbol punktów danych lub `[FUNC]` do wskazania, że symbol wskazuje kod. `GLOBAL` jest synonimem dla `EXPORT`.

- EXPORTAS

   Nieobsługiwane.

- RAMKI

   Nieobsługiwane.

- `FUNCTION` i `PROC`

   Mimo że składnia zestawu obsługuje specyfikację niestandardowego konwencji wywoływania na procedurach, wyświetlając listę rejestrów, które są Zapisz obiekt wywołujący i te, które są / / wywoływany Zapisz asemblera ARM firmy Microsoft akceptuje składnię ale ignoruje list rejestru.  Informacje o debugowaniu, który jest wytwarzany przez asembler obsługuje tylko domyślną konwencję wywoływania.

- `IMPORT` i `EXTERN`

   Określa import przy użyciu następującej składni:

   > **IMPORTUJ**|**EXTERN** *sym*{**, słabe** *alias*{**, typ** *t*}}

   *Sym* nazywa się symbol do zaimportowania.

   Jeśli `WEAK` *alias* jest określony, oznacza to, że *sym* jest słabe zewnętrznym. Brak definicji znajduje się w czasie, a następnie wszystkie odwołania do niego powiązać zamiast *alias*.

   Jeśli `TYPE` *t* jest określony, następnie *t* wskazuje, jak konsolidator powinien próbować rozpoznać *sym*.  Te wartości w celu *t* są możliwe:

   |Wartość|Opis|
   |-|-|
   |1|Nie wykonuj wyszukiwanie biblioteki *symboli*|
   |2|Wyszukaj bibliotekę *symboli*|
   |3|*Sym* jest aliasem dla *alias* (ustawienie domyślne)|

   `EXTERN` jest synonimem dla `IMPORT`, chyba że *sym* są importowane tylko wtedy, gdy istnieją odwołania do niego w bieżącym zestawie.

- MACRO

   Użycie zmiennej do przechowywania kodu warunku makra nie jest obsługiwana. Wartości domyślne dla makra, które parametry nie są obsługiwane.

- NOFP

   Nieobsługiwane.

- `OPT`, `TTL`, `SUBT`

   Nieobsługiwane, ponieważ asemblera ARM firmy Microsoft nie daje ofert.

- PRESERVE8

   Nieobsługiwane.

- RELOC

   `RELOC n` tylko wykonać instrukcję lub dyrektywy definicji danych. Nie ma żadnych "anonimowy symbol", który może zostać przeniesiona.

- WYMAGAJ

   Nieobsługiwane.

- REQUIRE8

   Nieobsługiwane.

- THUMBX

   Nie jest obsługiwana, ponieważ asemblera ARM firmy Microsoft nie obsługuje zestawu instrukcji Thumb-2EE.

## <a name="see-also"></a>Zobacz także

[Dokumentacja wiersza polecenia asemblera ARM](../../assembler/arm/arm-assembler-command-line-reference.md)<br/>
[Komunikaty diagnostyczne asemblera ARM](../../assembler/arm/arm-assembler-diagnostic-messages.md)<br/>
