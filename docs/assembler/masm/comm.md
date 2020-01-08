---
title: COMM
ms.date: 12/06/2019
f1_keywords:
- COMM
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
ms.openlocfilehash: 0ea02806cae3295af0846baa6c4e9049d54c271b
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75315176"
---
# <a name="comm"></a>COMM

Tworzy zmienną gminną z atrybutami określonymi w *definicji*.

## <a name="syntax"></a>Składnia

> ⟦ *Definicji* komunikacji __,__ *Definicja* ... ⟧

## <a name="remarks"></a>Uwagi

Zmienne gminne są przydzielone przez konsolidator i nie mogą być inicjowane. Oznacza to, że nie można zależeć od lokalizacji lub sekwencji takich zmiennych.

Każda *Definicja* ma następującą postać:

⟦*Language-Type*⟧ ⟦**blisko** | **dużo**⟧ _etykieta_ **:** _Type_⟦ **:** _Count_⟧

Argumenty *typu Language*, **Near**i **daleko** są prawidłowe tylko w 32-bitowym MASM.

Opcjonalny *Typ języka* ustawia konwencje nazewnictwa dla następującej nazwy. Zastępuje dowolny język określony przez **. Dyrektywa modelu** . Opcjonalna, **zbliżona** lub **znacznie** zastąp bieżący model pamięci. *Etykieta* to nazwa zmiennej. *Typ* może być dowolnym specyfikatorem typu ([Byte](byte-masm.md), [Word](word.md)itd.) lub liczbą całkowitą określającą liczbę bajtów. Opcjonalna *Liczba* określa liczbę elementów w zadeklarowanym obiekcie danych. Domyślna *Liczba* to 1.

## <a name="example"></a>Przykład

Ten przykład tworzy tablicę elementów bajtów 512:

```asm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
