---
title: SEGMENT
ms.date: 08/30/2018
f1_keywords:
- SEGMENT
helpviewer_keywords:
- SEGMENT directive
ms.assetid: e6f68367-6714-4f06-a79c-edfa88014430
ms.openlocfilehash: f37be47b92a71e20821cd1e40f8cf1350dfedaff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615426"
---
# <a name="segment"></a>SEGMENT

Określa segment program o nazwie *nazwa* mających atrybuty segmentu

## <a name="syntax"></a>Składnia

> *Nazwa* segmentu [[tylko do odczytu]] [[*wyrównać*]] [[*połączyć*]] [[*użyj*]] [[*charakterystyki*]] ALIASU (*ciągu*) [["*klasy*"]]<br/>
> *Instrukcje*<br/>
> *Nazwa* kończy się

#### <a name="parameters"></a>Parametry

*align*<br/>
Zakres adresów pamięci, z których można wybrać początkowy adres dla tego segmentu. Typ wyrównania może być jednym z następujących czynności:

|Typ wyrównania|Adres początkowy|
|----------------|----------------------|
|**BAJTÓW**|Adres następnego dostępnych bajtów.|
|**WORD**|Następny adres dostępne programu word (2 bajty na programu word).|
|**DWORD**|Następny adres dostępne podwójne słowo (4 bajty na podwójne słowo).|
|**PARA**|Następny adres akapitu dostępne (16 bajtów w każdym akapicie).|
|**PAGE**|Następny adres strony dostępne (256 bajtów na każdej stronie).|
|**WYRÓWNAJ**(*n*)|Następny dostępny *n*th bajtowego adresu. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.|

Jeśli ten parametr nie jest określony, **PARA** jest używane domyślnie.

*Łączenie*<br/>
**PUBLICZNE**, **STOSU**, **TYPOWE**, **pamięci**, **na**<em>adres</em>, **Prywatne**

*Użyj*<br/>
**USE16**, **USE32**, **PROSTEGO**

*Właściwości*<br/>
**Informacje o**, **odczytu**, **zapisu**, **EXECUTE**, **SHARED**, **NOPAGE**, **Właściwość NOCACHE**, i **ODRZUCIĆ**

Te są obsługiwane tylko dla COFF i odnoszą się do właściwości sekcji COFF o podobnej nazwie (na przykład **SHARED** odpowiada IMAGE_SCN_MEM_SHARED). Odczyt ustawia flagę IMAGE_SCN_MEM_READ. Przestarzałe flagi tylko do odczytu spowodowane sekcji wyczyścić flagę IMG_SCN_MEM_WRITE. Jeśli istnieją *charakterystyki* są ustawione domyślne parametry nie są używane i obowiązują tylko określone przez programistę flagi.

`ALIAS(` *ciąg* `)`<br/>
Ten ciąg jest używany jako nazwa sekcji emitowany obiektu COFF.  Tworzy wiele sekcji o takiej samej nazwie zewnętrznego, z różnymi nazwami segmentu MASM.

Nieobsługiwane za pomocą **/omf**.

*class*<br/>
Określa, jak łączyć i uporządkowane w pliku zmontowanych segmentów. Typowe wartości są, `'DATA'`, `'CODE'`, `'CONST'` i `'STACK'`

## <a name="remarks"></a>Uwagi

Aby uzyskać `ALIGN(n)`, *n* może być dowolnym potęgą liczby 2 z zakresu od 1 do 8192; nie jest obsługiwana przy użyciu **/omf**.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>