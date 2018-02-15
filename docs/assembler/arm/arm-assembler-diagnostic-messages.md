---
title: Komunikaty diagnostyczne asemblera ARM | Dokumentacja firmy Microsoft
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
ms.assetid: 52b38267-6023-4bdc-a0ef-863362f48eec
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 54dca3a864ca34107314ad33725793297fd93e4a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="arm-assembler-diagnostic-messages"></a>Komunikaty diagnostyczne asemblera ARM
Asemblera ARM firmy Microsoft (*armasm*) emituje diagnostycznych ostrzeżenia i błędy po napotkaniu je. W tym artykule opisano najbardziej powszechnie napotkano wiadomości.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
filename(lineno) : [error|warning] Anum: message  
```  
  
## <a name="diagnostic-messages"></a>Komunikaty diagnostyczne  
  
### <a name="errors"></a>błędy  
 A2193: Ta instrukcja generuje nieprzewidywalne zachowanie  
 Architektura ARM nie może zagwarantować, co się stanie po wykonaniu tej instrukcji.  Aby uzyskać szczegółowe informacje dotyczące dobrze zdefiniowany formy tej instrukcji, zapoznaj się [ręczne odwołanie do architektury ARM](http://go.microsoft.com/fwlink/p/?linkid=246464).  
  
```  
  
ADD r0, r8, pc         ; A2193: this instruction generates unpredictable behavior  
  
```  
  
 A2196: instrukcja nie może zostać zakodowany w 16 bitów  
 Określona instrukcja nie może zostać zakodowany jako instrukcji Thumb 16-bitowych.  Określ instrukcję 32-bitowej lub rozmieszczanie kodu można wyświetlić etykiety docelowego w zakresie instrukcji 16-bitowych.  
  
 Asembler może podejmować kodowanie gałąź w 16 bitów i zakończyć się niepowodzeniem z powodu następującego błędu, nawet jeśli oddział 32-bitowych jest można kodować. Problem można rozwiązać przy użyciu `.W` specyfikator jawnie zaznaczania gałęzi jako 32-bitowych.  
  
```  
  
  ADD.N r0, r1, r2      ; A2196: instruction cannot be encoded in 16 bits  
  
  B.W label             ; OK  
  B.N label             ; A2196: instruction cannot be encoded in 16 bits  
  SPACE 10000  
label  
  
```  
  
 A2202: Składnia instrukcji Pre-UAL niedozwolone w regionie przycisku PRZEWIJANIA  
 Kod przenośny, należy użyć składni Unified języka asemblera (UAL).  Stara składnia nie jest akceptowany.  
  
```  
  
ADDEQS r0, r1         ; A2202: Pre-UAL instruction syntax not allowed in THUMB region  
ADDSEQ r0, r1         ; OK  
  
```  
  
 A2513: Obrotu musi być parzysta  
 W trybie ARM jest alternatywny składnia określająca stałe.  Zamiast zapisywania `#<const>`, można napisać `#<byte>,#<rot>`, reprezentuje stałą wartość, jak są uzyskiwane przez obrócenie wartość `<byte>` prawo `<rot>`.  Korzystając z następującej składni, należy się upewnić wartość `<rot>` nawet.  
  
```  
  
MOV r0, #4, #2       ; OK  
MOV r0, #4, #1       ; A2513: Rotation must be even  
  
```  
  
 A2557: Niepoprawna liczba bajtów do zapisania  
 W strukturze NEON obciążenia i przechowywać instrukcje (`VLDn`, `VSTn`), jest alternatywny składnię służącą do zapisu do rejestru podstawowej.  Zamiast umieszczanie wykrzyknika (!) po adres, można określić natychmiastowego wartość, która wskazuje przesunięcia, które mają zostać dodane do podstawowej rejestru.  Jeśli używasz tej składni, należy określić dokładną liczbę bajtów, które zostały załadowane lub przechowywane przez instrukcję.  
  
```  
  
VLD1.8 {d0-d3}, [r0]!         ; OK  
VLD1.8 {d0-d3}, [r0], #32     ; OK  
VLD1.8 {d0-d3}, [r0], #100    ; A2557: Incorrect number of bytes to write back  
  
```  
  
### <a name="warnings"></a>Ostrzeżenia  
 A4228: Wartość wyrównania przekracza wyrównania obszaru; wyrównanie nie jest gwarantowana  
 Wyrównanie, który jest określony w `ALIGN` dyrektywa jest większa niż wyrównanie otaczający `AREA`.  W związku z tym asemblera nie może zagwarantować, że `ALIGN` będą honorowane dyrektywy.  
  
 Aby rozwiązać ten problem, można określić na `AREA` dyrektywy `ALIGN` atrybut, który jest równa lub większa niż żądany wyrównania.  
  
```  
  
AREA |.myarea1|  
ALIGN 8           ; A4228: Alignment value exceeds AREA alignment; alignment not guaranteed  
  
AREA |.myarea2|,ALIGN=3  
ALIGN 8           ; OK  
  
```  
  
 A4508: Użyj tego obrócony stała jest przestarzały.  
 W trybie ARM jest alternatywny składnia określająca stałe.  Zamiast zapisywania `#<const>`, można napisać `#<byte>,#<rot>`, reprezentuje stałą wartość, jak są uzyskiwane przez obrócenie wartość `<byte>` prawo `<rot>`.  W niektórych kontekstach ARM jest przestarzała stosowania tych obrócony stałe. W takich przypadkach należy korzystać z podstawowego `#<const>` składni zamiast tego.  
  
```  
  
ANDS r0, r0, #1                ; OK  
ANDS r0, r0, #4, #2            ; A4508: Use of this rotated constant is deprecated  
  
```  
  
 A4509: Ten formularz instrukcji warunkowej jest przestarzały.  
 Ten formularz instrukcji warunkowej została zastąpiona przez RAMIĘ architektury ARMv8. Firma Microsoft zaleca zmianę kodu w celu użycia warunkowych gałęzi. Aby zobaczyć, które instrukcje warunkowego nadal są obsługiwane, zapoznaj się [ręczne odwołanie do architektury ARM](http://go.microsoft.com/fwlink/p/?linkid=246464).  
  
 To ostrzeżenie nie jest wysyłanego, gdy `-oldit` jest używany przełącznik wiersza polecenia.  
  
```  
  
ADDEQ r0, r1, r8              ; A4509: This form of conditional instruction is deprecated  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje w wierszu polecenia asemblera ARM](../../assembler/arm/arm-assembler-command-line-reference.md)   
 [Dyrektywy ARM dotycząca asemblera](../../assembler/arm/arm-assembler-directives.md)