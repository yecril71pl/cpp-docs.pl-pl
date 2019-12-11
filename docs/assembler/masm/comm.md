---
title: COMM
ms.date: 12/06/2019
f1_keywords:
- COMM
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
ms.openlocfilehash: 93e7c891b1c964eca5b3ff7fd15956ef25ea05e6
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74987940"
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

Opcjonalny *Typ języka* ustawia konwencje nazewnictwa dla następującej nazwy. Zastępuje dowolny język określony przez **. Dyrektywa modelu** . Opcjonalna, **zbliżona** lub **znacznie** zastąp bieżący model pamięci. *Etykieta* to nazwa zmiennej. *Typ* może być dowolnym specyfikatorem typu ([Byte](../../assembler/masm/byte-masm.md), [Word](../../assembler/masm/word.md)itd.) lub liczbą całkowitą określającą liczbę bajtów. Opcjonalna *Liczba* określa liczbę elementów w zadeklarowanym obiekcie danych. Domyślna *Liczba* to 1.

## <a name="example"></a>Przykład

Ten przykład tworzy tablicę elementów bajtów 512:

```asm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)
