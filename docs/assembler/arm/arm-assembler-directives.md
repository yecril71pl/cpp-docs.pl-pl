---
title: Dyrektywy ARM dotycząca asemblera | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 9f5ab97fb9ccdff19206b829383c622efd3f7921
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
ms.locfileid: "32053304"
---
# <a name="arm-assembler-directives"></a>Dyrektywy ARM dotycząca asemblera
W większości przypadków asemblera Microsoft ARM wykorzystuje język asemblera ARM, które opisano w rozdziale 7 [przewodnik narzędzia asemblera ARM](http://go.microsoft.com/fwlink/p/?linkid=246102). Jednak niektóre dyrektywy zestawu implementacje firmy Microsoft różnią się od dyrektywy zestawów ARM. W tym artykule opisano różnice.  
  
## <a name="microsoft-implementations-of-arm-assembly-directives"></a>Implementacje firmy Microsoft dyrektywy zestawów ARM  
 AREA  
 Te atrybuty obszaru obsługuje asemblera ARM firmy Microsoft: WYRÓWNAJ kod, CODEALIGN, dane, NOINIT, tylko do odczytu, READWRITE, THUMB, ARM.  
  
 Wszystkie z wyjątkiem THUMB i ARM działać zgodnie z opisem w [przewodnik narzędzia asemblera ARM](http://go.microsoft.com/fwlink/p/?linkid=246102).  
  
 W asemblera Microsoft ARM THUMB wskazuje, że sekcji kodu zawiera kod Thumb i jest ustawieniem domyślnym dla sekcji kodu.  ARM wskazuje, że sekcja zawiera kod ARM.  
  
 ATTR  
 Nieobsługiwane.  
  
 — KOD 16  
 Nieobsługiwana, ponieważ będzie to oznaczać składni Thumb pre-UAL, która asemblera Microsoft ARM nie zezwala na.  Zamiast tego należy użyć dyrektywy THUMB wraz ze składnią rejestrowania dostępu użytkowników.  
  
 WSPÓLNE  
 Specyfikacja wyrównanie wspólnej region nie jest obsługiwane.  
  
 DCDO  
 Nieobsługiwane.  
  
 DN, QN, SN  
 Specyfikacja typu lub lane na aliasu rejestru nie jest obsługiwana.  
  
 ENTRY  
 Nieobsługiwane.  
  
 EQU  
 Specyfikacja typu zdefiniowany symbol nie jest obsługiwana.  
  
 EKSPORTOWANIE i GLOBALNYCH  
 ```  
EXPORTsym {[type]}  
```  
  
 `sym` jest symbolem do wyeksportowania.  `[type]`, jeśli jest określony, może być albo `[DATA]` wskazująca, czy symbol punktów danych lub `[FUNC]` wskazująca, czy symbol wskazuje kod.  
  
 GLOBALNE jest synonimem eksportu.  
  
 EXPORTAS  
 Nieobsługiwane.  
  
 RAMKI  
 Nieobsługiwane.  
  
 Funkcja i PROCESEM  
 Mimo że składni zestawu obsługuje specyfikację niestandardowego konwencji wywoływania na procedurach poprzez wyszczególnienie rejestry, które są Zapisz obiekt wywołujący oraz te, które są wywoływany zapisem asemblera ARM firmy Microsoft akceptuje składnię ale ignoruje list rejestru.  Informacje o debugowaniu, który jest generowany przez asemblera obsługuje tylko domyślną konwencję wywoływania.  
  
 IMPORTOWANIE i EXTERN  
 ```  
IMPORT sym{, WEAK alias{, TYPE t}}  
```  
  
 `sym` to nazwa symbolu do zaimportowania.  
  
 Jeśli jest to słaby `alias` jest określony, oznacza to, że `sym` jest słaby zewnętrznym. Brak definicji dla niego znajduje się w czasie łącza, a następnie zamiast niej powiązać wszystkie odwołania do niego `alias`.  
  
 Jeśli typ `t` zostanie określona, przyjmowana `t` wskazuje, jak konsolidator powinien próbować rozpoznać `sym`.  Te wartości `t` są możliwe:   
1 — nie wykonuj wyszukiwania biblioteki `sym`  
2 — Biblioteka wyszukiwania dla `sym`  
3 —`sym` jest aliasem `alias` (ustawienie domyślne)  
  
 EXTERN jest synonimem IMPORTU, z wyjątkiem `sym` jest importowany tylko wtedy, gdy istnieją odwołania do niego w bieżącym zestawie.  
  
 MACRO  
 Użycie zmiennej do przechowywania kodu warunku makra nie jest obsługiwane. Wartości domyślne dla makra parametry nie są obsługiwane.  
  
 NOFP  
 Nieobsługiwane.  
  
 OPT, TTL, SUBT  
 Nieobsługiwana, ponieważ asemblera Microsoft ARM nie tworzy listy.  
  
 PRESERVE8  
 Nieobsługiwane.  
  
 RELOC  
 `RELOC n` może następować tylko po instrukcji lub dyrektywy definicji danych. Nie ma żadnych "anonimowe symbol" może zostać przeniesiona.  
  
 WYMAGAJ  
 Nieobsługiwane.  
  
 REQUIRE8  
 Nieobsługiwane.  
  
 THUMBX  
 Nie jest obsługiwana, ponieważ asemblera Microsoft ARM nie obsługuje zestaw instrukcji 2EE przycisku suwaka.  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje w wierszu polecenia asemblera ARM](../../assembler/arm/arm-assembler-command-line-reference.md)   
 [Komunikaty diagnostyczne asemblera ARM](../../assembler/arm/arm-assembler-diagnostic-messages.md)