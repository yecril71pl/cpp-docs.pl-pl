---
title: ALIGN (MASM)
ms.date: 01/02/2019
f1_keywords:
- align
helpviewer_keywords:
- ALIGN directive
ms.assetid: 1c386b23-439f-4ec3-a6de-74427b25e47f
ms.openlocfilehash: eb42b1952b3fd59438f0dd4c29d48c91c4d8864d
ms.sourcegitcommit: cce52b2232b94ce8fd8135155b86e2d38a4e4562
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54031229"
---
# <a name="align-masm"></a>ALIGN (MASM)

**WYRÓWNAJ** dyrektywy wyrównuje następnego elementu danych lub instrukcji pod adresem, który jest wielokrotnością liczby jako parametr. Parametr musi być potęgą liczby 2 (na przykład 1, 2, 4 i tak dalej) oznacza to mniejsze niż lub równe wyrównanie segmentu.

## <a name="syntax"></a>Składnia

> WYRÓWNAJ [[*numer*]]

## <a name="remarks"></a>Uwagi

**WYRÓWNAJ** dyrektywy pozwala określić Przesunięcie początku elementu danych lub instrukcji. Wyrównanych danych może zwiększyć wydajność kosztem nieużywanego miejsca między elementami danych. Duży przyrost wydajności są widoczne, gdy uzyskuje dostęp do danych znajdują się w granicach, które mieszczą się w pamięci podręcznej wierszy. Uzyskuje dostęp do na naturalnych dla natywnych typów oznacza mniej czasu spędzony w mikrokodu Wyrównaj ponownie wewnętrznego sprzętowego.

Potrzebę wyrównany instrukcji jest rzadki w nowoczesnych procesorów, które korzystają z prostego modelu adresowania, ale może być wymagane dla celów szybkiego dostępu w starszego kodu dla innych modeli adresowania.

Gdy dane są wyrównane, pominięto miejsca są dopełniane zerami. Instrukcje są wyrównane, pominięto miejsca jest wypełniony instrukcje NOP nieodpowiedni rozmiar.

## <a name="see-also"></a>Zobacz także

[EVEN](even.md)<br/>
[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>