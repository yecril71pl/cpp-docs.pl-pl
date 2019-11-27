---
title: COMM
ms.date: 08/30/2018
f1_keywords:
- COMM
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
ms.openlocfilehash: d36161ba54ca80fc0f576c6f0a7c2a9410bf8075
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541034"
---
# <a name="comm"></a>COMM

Tworzy zmienną gminną z atrybutami określonymi w *definicji*.

## <a name="syntax"></a>Składnia

> ⟦ *Definicji* komunikacji __,__ *Definicja* ... ⟧

## <a name="remarks"></a>Uwagi

Zmienne gminne są przydzielone przez konsolidator i nie mogą być inicjowane. Oznacza to, że nie można zależeć od lokalizacji lub sekwencji takich zmiennych.

Każda *Definicja* ma następującą postać:

⟦*Language-Type*⟧ ⟦**blisko** | **dużo**⟧ _etykieta_ **:** _Type_⟦ **:** _Count_⟧

Opcjonalny *Typ języka* ustawia konwencje nazewnictwa dla następującej nazwy. Zastępuje dowolny język określony przez **. Dyrektywa modelu** . Opcjonalna, **zbliżona** lub **znacznie** zastąp bieżący model pamięci. *Etykieta* to nazwa zmiennej. *Typ* może być dowolnym specyfikatorem typu ([Byte](../../assembler/masm/byte-masm.md), [Word](../../assembler/masm/word.md)itd.) lub liczbą całkowitą określającą liczbę bajtów. Opcjonalna *Liczba* określa liczbę elementów w zadeklarowanym obiekcie danych. Domyślna *Liczba* to 1.

## <a name="example"></a>Przykład

Ten przykład tworzy tablicę elementów bajtów 512:

```asm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)
