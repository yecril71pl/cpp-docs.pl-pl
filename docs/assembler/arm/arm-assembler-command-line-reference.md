---
title: Informacje w wierszu polecenia asemblera ARM | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: f7b89478-1ab5-4995-8cde-a805f0462c45
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2eb6b395ec8f47e820cb3184c0d88b4c91e712eb
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="arm-assembler-command-line-reference"></a>Informacje w wierszu polecenia asemblera ARM
W tym artykule omówiono wiersza polecenia asemblera Microsoft ARM *armasm*, który kompiluje języka zestawu ARMv7 Thumb do przez firmę Microsoft implementacją z typowych Format pliku obiektu (COFF). Konsolidator połączyć COFF kodu za pomocą kodu obiektu, który jest generowany przez asemblera ARM lub za pomocą kompilatora C, wraz z biblioteki obiektów, które są tworzone przez bibliotekarza.  
  
## <a name="syntax"></a>Składnia  
  
```  
armasm [[options]] sourcefile objectfile  
```  
  
```  
armasm [[options]] -o objectfile sourcefile  
```  
  
#### <a name="parameters"></a>Parametry  
 `options`  
 — błędy `filename`  
 Przekieruj błędach i komunikaty ostrzegawcze do `filename`.  
  
 -i `dir[;dir]`  
 Dodaj określone katalogi na ścieżkę wyszukiwania dyrektywy include.  
  
 -wstępnie `directive`  
 Określ SETA, SETL lub zestawy dyrektywy wstępnie symbolu. Przykład: **armasm.exe-wstępnie "COUNT SETA 150" source.asm**. Aby uzyskać więcej informacji, zobacz [przewodnik narzędzia asemblera ARM](http://go.microsoft.com/fwlink/p/?linkid=246102).  
  
 -nowarn  
 Wyłącz wszystkie ostrzeżenia.  
  
 -Ignoruj `warning`  
 Wyłącz określonego ostrzeżenie. Możliwe wartości zobacz sekcję o ostrzeżenia.  
  
 -help  
 Drukuj komunikat pomocy wiersza polecenia.  
  
 -machine `machine`  
 Określ typ urządzenia, które można ustawić w nagłówku PE.  Możliwe wartości `machine` są:  
**ARM**— ustawia typ maszyny IMAGE_FILE_MACHINE_ARMNT. Domyślnie włączone.   
**THUMB**— ustawia typ maszyny IMAGE_FILE_MACHINE_THUMB.  
  
 -oldit  
 Generowanie ARMv7 stylu bloki IT.  Domyślnie ARMv8 zgodnego IT bloki są generowane.  
  
 -via `filename`  
 Przeczytaj dodatkowe argumenty wiersza polecenia z `filename`.  
  
 -16  
 Składanie źródła jako 16-bitowe instrukcje przycisku suwaka.  Domyślnie włączone.  
  
 -32  
 Składanie źródła jako 32-bitowe instrukcje ARM.  
  
 -g  
 Generuj informacje debugowania.  
  
 -errorReport: `option`  
 Określ asemblera jak wewnętrzne błędy są zgłaszane do firmy Microsoft.  Możliwe wartości `option` są:   
**Brak**— nie wysyłaj raportów.   
**wiersz**— Monituj użytkownika, aby bezpośrednio wysyłać raporty.   
**kolejki**— Monituj użytkownika o wysyłanie raportów przy kolejnym zalogowaniu administratora. Domyślnie włączone.   
**Wyślij**— Wyślij raporty automatycznie.  
  
 `sourcefile`  
 Nazwa pliku źródłowego.  
  
 `objectfile`  
 Nazwa pliku obiektu (dane wyjściowe).  
  
 W poniższym przykładzie pokazano sposób użycia armasm w typowy scenariusz. Najpierw użyj armasm do tworzenia pliku źródłowego (.asm) języka zestawu do pliku obiektu (.obj). Następnie użyj CL wiersza polecenia kompilatora C, aby skompilować pliku źródłowego (.c), a także określić opcję konsolidatora Połącz plik z obiektu ARM.  
  
 **armasm myasmcode.asm -o myasmcode.obj**  
  
 **cl myccode.c /link myasmcode.obj**  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty diagnostyczne asemblera ARM](../../assembler/arm/arm-assembler-diagnostic-messages.md)   
 [Dyrektywy ARM dotycząca asemblera](../../assembler/arm/arm-assembler-directives.md)