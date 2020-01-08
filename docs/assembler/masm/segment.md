---
title: SEGMENT
ms.date: 12/16/2019
f1_keywords:
- SEGMENT
helpviewer_keywords:
- SEGMENT directive
ms.assetid: e6f68367-6714-4f06-a79c-edfa88014430
ms.openlocfilehash: 569604bfd6ed11039ce5492223b8d5f986ceea7a
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318465"
---
# <a name="segment"></a>SEGMENT

Definiuje segment *programu o nazwie* z atrybutami segmentu

## <a name="syntax"></a>Składnia

> **segment** nazw ⟦**ReadOnly**⟧ ⟦*align*⟧ ⟦*Połącz*⟧ ⟦*Użyj*⟧ ⟦*cechy*⟧ **alias (** _String_ **)** ⟦ __"__ *Class* __"__ ⟧ \
> *instrukcje*\
> **koniec** nazwy

#### <a name="parameters"></a>Parametry

*wyrównaj*\
Zakres adresów pamięci, z którego można wybrać adres początkowy segmentu. Typ wyrównania może mieć jedną z następujących wartości:

|Typ wyrównania|Adres początkowy|
|----------------|----------------------|
|**BAJC**|Adres następnego dostępnego bajtu.|
|**WORD**|Adres następnego dostępnego wyrazu (2 bajty na słowo).|
|**DWORD**|Następny dostępny podwójny adres wyrazu (4 bajty na podwójny wyraz).|
|**PARA**|Adres następnego dostępnego akapitu (16 bajtów na akapit).|
|**PAGE**|Następny dostępny adres strony (256 bajtów na stronę).|
|**Wyrównaj**(*n*)|Następny dostępny *n*adres bajtowy. Aby uzyskać więcej informacji, zobacz sekcję Uwagi.|

Jeśli ten parametr nie jest określony, **para** jest używana domyślnie.

*Połącz* (tylko 32-bitowe MASM) \
**Publiczne**, **stos**, **Common**, **pamięć**, **pod**<em>adresem</em>, **prywatny**

*Użyj* (32-bitowy MASM tylko) \
**USE16**, **USE32**, **Flat**

*charakterystyka*\
**Informacje**, **Odczyt**, **zapis**, **wykonywanie**, **udostępnianie**, **nopage**, **nocache**i **DISCARD**

Są one obsługiwane tylko w przypadku formatu COFF i odpowiadają charakterystykom sekcji COFF o podobnej nazwie (na przykład **współdzielona** odnosi się do IMAGE_SCN_MEM_SHARED). Odczyt ustawia flagę IMAGE_SCN_MEM_READ. Przestarzała flaga READONLY spowodowała, że sekcja czyści flagę IMG_SCN_MEM_WRITE. Jeśli są ustawione jakiekolwiek *Właściwości* , właściwości domyślne nie są używane i są stosowane tylko flagi określone przez programistę.

_ciąg_\
Ten ciąg jest używany jako nazwa sekcji w emitowanym obiekcie COFF.  Tworzy wiele sekcji o tej samej nazwie zewnętrznej z odrębnymi nazwami segmentów MASM.

Nieobsługiwane w przypadku **/OMF**.

\ *klasy*
Określa, jak segmenty mają być połączone i uporządkowane w zmontowanym pliku. Typowe wartości to, `'DATA'`, `'CODE'`, `'CONST'` i `'STACK'`

## <a name="remarks"></a>Uwagi

W przypadku `ALIGN(n)`*n* może być dowolną potęgą od 1 do 8192; nieobsługiwane w przypadku **/OMF**.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
