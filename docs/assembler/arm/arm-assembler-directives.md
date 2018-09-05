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
ms.openlocfilehash: 282d8bbd55bec8053961c709eb3733a65972b187
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693116"
---
# <a name="arm-assembler-directives"></a>Dyrektywy ARM dotycząca asemblera

W większości przypadków asemblera ARM firmy Microsoft używa języka asemblera ARM, który został opisany w [armasm ARM kompilator podręcznik](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html). Jednak implementacji Microsoft niektórych dyrektyw zestawu różnią się od dyrektyw zestawu ARM. W tym artykule wyjaśniono różnice.

## <a name="microsoft-implementations-of-arm-assembly-directives"></a>Implementacje dyrektyw zestawu ARM firmy Microsoft

`AREA`<br/>
Asemblera ARM firmy Microsoft obsługuje te `AREA` atrybuty: `ALIGN`, `CODE`, `CODEALIGN`, `DATA`, `NOINIT`, `READONLY`, `READWRITE`, `THUMB`, `ARM`.

Wszystkie regiony z wyjątkiem `THUMB` i `ARM` działają zgodnie z opisem w [armasm ARM kompilator podręcznik](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html).

W asemblera ARM firmy Microsoft `THUMB` wskazuje, że `CODE` sekcja zawiera kod Thumb i jest ustawieniem domyślnym dla `CODE` sekcje.  `ARM` Wskazuje, że sekcja zawiera kod ARM.

`ATTR`<br/>
Nieobsługiwane.

`CODE16`<br/>
Nieobsługiwane, ponieważ jej działanie polega na pre-UAL Thumb składni, która asemblera ARM firmy Microsoft nie zezwala.  Użyj `THUMB` dyrektywy zamiast tego wraz ze składnią usługi rejestrowania dostępu użytkowników.

`COMMON`<br/>
Specyfikacja wyrównania dla typowych regionu nie jest obsługiwana.

`DCDO`<br/>
Nieobsługiwane.

`DN`, `QN`, `SN`<br/>
Specyfikacja typu lub lane na alias rejestru nie jest obsługiwana.

`ENTRY`<br/>
Nieobsługiwane.

`EQU`<br/>
Specyfikacja typu zdefiniowany symbol nie jest obsługiwana.

`EXPORT` i `GLOBAL`

> **EKSPORTUJ** <em>sym</em>{**[**<em>typu</em>**]**}

*Sym* jest symbol do wyeksportowania.  [*typu*], jeśli określony, może być `[DATA]` do wskazania, że symbol punktów danych lub `[FUNC]` do wskazania, że symbol wskazuje kod.

`GLOBAL` jest synonimem dla `EXPORT`.

`EXPORTAS`<br/>
Nieobsługiwane.

`FRAME`<br/>
Nieobsługiwane.

`FUNCTION` i `PROC`<br/>
Mimo że składnia zestawu obsługuje specyfikację niestandardowego konwencji wywoływania na procedurach, wyświetlając listę rejestrów, które są Zapisz obiekt wywołujący i te, które są / / wywoływany Zapisz asemblera ARM firmy Microsoft akceptuje składnię ale ignoruje list rejestru.  Informacje o debugowaniu, który jest wytwarzany przez asembler obsługuje tylko domyślną konwencję wywoływania.

`IMPORT` i `EXTERN`

> **IMPORTUJ** *sym*{**, słabe** *alias*{**, typ** *t*}}

*Sym* nazywa się symbol do zaimportowania.

Jeśli `WEAK` *alias* jest określony, oznacza to, że *sym* jest słabe zewnętrznym. Brak definicji znajduje się w czasie, a następnie wszystkie odwołania do niego powiązać zamiast *alias*.

Jeśli `TYPE` *t* jest określony, następnie *t* wskazuje, jak konsolidator powinien próbować rozpoznać *sym*.  Te wartości w celu *t* są możliwe:<br/>
1 — nie należy wykonywać wyszukiwania biblioteki *symboli*<br/>
2 — Biblioteka wyszukać *symboli*<br/>
3 —*sym* jest aliasem dla *alias* (ustawienie domyślne)

`EXTERN` jest synonimem dla `IMPORT`, chyba że *sym* są importowane tylko wtedy, gdy istnieją odwołania do niego w bieżącym zestawie.

`MACRO`<br/>
Użycie zmiennej do przechowywania kodu warunku makra nie jest obsługiwana. Wartości domyślne dla makra, które parametry nie są obsługiwane.

`NOFP`<br/>
Nieobsługiwane.

`OPT`, `TTL`, `SUBT`<br/>
Nieobsługiwane, ponieważ asemblera ARM firmy Microsoft nie daje ofert.

`PRESERVE8`<br/>
Nieobsługiwane.

`RELOC`<br/>
`RELOC n` tylko wykonać instrukcję lub dyrektywy definicji danych. Nie ma żadnych "anonimowy symbol", który może zostać przeniesiona.

`REQUIRE`<br/>
Nieobsługiwane.

`REQUIRE8`<br/>
Nieobsługiwane.

`THUMBX`<br/>
Nie jest obsługiwana, ponieważ asemblera ARM firmy Microsoft nie obsługuje zestawu instrukcji Thumb-2EE.

## <a name="see-also"></a>Zobacz także

[Dokumentacja wiersza polecenia asemblera ARM](../../assembler/arm/arm-assembler-command-line-reference.md)<br/>
[Komunikaty diagnostyczne asemblera ARM](../../assembler/arm/arm-assembler-diagnostic-messages.md)<br/>
